---
ID: 5975
post_title: >
  WordPress için Varnish 4 Örnek VCL
  Dosyası
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/wordpress-icin-varnish-4-ornek-vcl-dosyasi-5975.html
published: true
post_date: 2016-12-29 19:02:58
---
Merhaba arkadaşlar,

WordPress sitelerinizin bulunduğu sunucunuzunun performansını uçurmak <a href="http://www.trkodlama.com/makaleler/varnish-nedir-5816.html">Varnish</a> kurdunuz. Yetmedi birde <a href="http://www.trkodlama.com/makaleler/wordpress-onbellekleme-w3-total-cache-kurulum-rehberi-5946.html">W3 Total Cache</a> eklentisini kurdunuz.

Artık web siteleriniz müthiş hızlı. İşin güzel yanı sunucunuzun load durumu veya kaynak tüketimi neredeyse yok. Herşey güzel. Birde Varnish default.vcl dosyanızı WordPress'inizle müthiş bir uyumla çalışacak hale getirmek ister misiniz? <a href="https://gist.github.com/matthewjackowski" target="_blank">Matthew Jackowski</a> abimiz çok güzel bir VCL dosyası hazırlamış. Sizinde kullanmanızı öneririm, oldukça başarılı. Buyrun default.vcl kodumuz:
<pre class="prettyprint lang-snippets" data-start-line="1" data-visibility="visible" data-highlight="" data-caption=""># A heavily customized VCL to support WordPress
# Some items of note:
# Supports https
# Supports admin cookies for wp-admin
# Caches everything
# Support for custom error html page
vcl 4.0;
import directors;
import std;

# Assumed 'wordpress' host, this can be docker servicename
backend default {
    .host = "wordpress";
    .port = "80";
}

acl purge {
    "localhost";
	"127.0.0.1";
}


sub vcl_recv {



	# Only a single backend
        set req.backend_hint= default;

        # Setting http headers for backend
        set req.http.X-Forwarded-For = client.ip;
    	set req.http.X-Forwarded-Proto = "https";

    	# Unset headers that might cause us to cache duplicate infos
    	unset req.http.Accept-Language;
    	unset req.http.User-Agent;

	# The purge...no idea if this works
		if (req.method == "PURGE") {
		    if (!client.ip ~ purge) {
		      return(synth(405,"Not allowed."));
		    }
		    return (purge);
	  	}
	  	if ( std.port(server.ip) == 6080) {

		set req.http.x-redir = "https://" + req.http.host + req.url;
                return (synth(750, "Moved permanently"));
        }

 		# drop cookies and params from static assets
	  	if (req.url ~ "\.(gif|jpg|jpeg|swf|ttf|css|js|flv|mp3|mp4|pdf|ico|png)(\?.*|)$") {
	    	unset req.http.cookie;
	    	set req.url = regsub(req.url, "\?.*$", "");
	  	}

		# drop tracking params
	  	if (req.url ~ "\?(utm_(campaign|medium|source|term)|adParams|client|cx|eid|fbid|feed|ref(id|src)?|v(er|iew))=") {
	    	set req.url = regsub(req.url, "\?.*$", "");
	  	}

		# pass wp-admin urls
   		if (req.url ~ "(wp-login|wp-admin)" || req.url ~ "preview=true" || req.url ~ "xmlrpc.php") {
    		return (pass);
  		}

		# pass wp-admin cookies
	  	if (req.http.cookie) {
		    if (req.http.cookie ~ "(wordpress_|wp-settings-)") {
	      		return(pass);
		    } else {
		      unset req.http.cookie;
		    }
	  	}
 }



sub vcl_backend_response {
    # retry a few times if backend is down
    if (beresp.status == 503 &amp;&amp; bereq.retries &lt; 3 ) {
       return(retry);
 }

    if (bereq.http.Cookie ~ "(UserID|_session)") {
	# if we get a session cookie...caching is a no-go
        set beresp.http.X-Cacheable = "NO:Got Session";
        set beresp.uncacheable = true;
        return (deliver);

    } elsif (beresp.ttl &lt;= 0s) {
        # Varnish determined the object was not cacheable
        set beresp.http.X-Cacheable = "NO:Not Cacheable";

    } elsif (beresp.http.set-cookie) {
        # You don't wish to cache content for logged in users
        set beresp.http.X-Cacheable = "NO:Set-Cookie";
        set beresp.uncacheable = true;
        return (deliver);

    } elsif (beresp.http.Cache-Control ~ "private") {
        # You are respecting the Cache-Control=private header from the backend
        set beresp.http.X-Cacheable = "NO:Cache-Control=private";
        set beresp.uncacheable = true;
        return (deliver);

    } else {
        # Varnish determined the object was cacheable
        set beresp.http.X-Cacheable = "YES";

        # Remove Expires from backend, it's not long enough
  	unset beresp.http.expires;

        # Set the clients TTL on this object
        set beresp.http.cache-control = "max-age=900";

        # Set how long Varnish will keep it
        set beresp.ttl = 1w;

        # marker for vcl_deliver to reset Age:
        set beresp.http.magicmarker = "1";
    }

	# unset cookies from backendresponse
	if (!(bereq.url ~ "(wp-login|wp-admin)"))  {
		set beresp.http.X-UnsetCookies = "TRUE";
    		unset beresp.http.set-cookie;
    		set beresp.ttl = 1h;
	}

	# long ttl for assets
  	if (bereq.url ~ "\.(gif|jpg|jpeg|swf|ttf|css|js|flv|mp3|mp4|pdf|ico|png)(\?.*|)$") {
	    set beresp.ttl = 365d;

}
 set beresp.grace = 1w;

}

sub vcl_hash {
   if ( req.http.X-Forwarded-Proto ) {
    hash_data( req.http.X-Forwarded-Proto );
}
}

sub vcl_backend_error {
      # display custom error page if backend down
      if (beresp.status == 503 &amp;&amp; bereq.retries == 3) {
          synthetic(std.fileread("/etc/varnish/error503.html"));
          return(deliver);
       }
 }

sub vcl_synth {
    # redirect for http
    if (resp.status == 750) {
        set resp.status = 301;
        set resp.http.Location = req.http.x-redir;
        return(deliver);
    }
# display custom error page if backend down
    if (resp.status == 503) {
        synthetic(std.fileread("/etc/varnish/error503.html"));
        return(deliver);
     }
}


sub vcl_deliver {
    # oh noes backend is down
    if (resp.status == 503) {
        return(restart);
    }
    if (resp.http.magicmarker) {
       # Remove the magic marker
        unset resp.http.magicmarker;

       # By definition we have a fresh object
       set resp.http.age = "0";
     }
   if (obj.hits &gt; 0) {
     set resp.http.X-Cache = "HIT";
   } else {
     set resp.http.X-Cache = "MISS";
   }
   set resp.http.Access-Control-Allow-Origin = "*";
}
sub vcl_hit {
  if (req.method == "PURGE") {
    return(synth(200,"OK"));
  }
}

sub vcl_miss {
  if (req.method == "PURGE") {
    return(synth(404,"Not cached"));
  }
}</pre>
Gerekli açıklamalar ingilizce olarak kodların içinde mevcut. Aklınıza takılanlar için lütfen yorum yapmaktan çekinmeyin.