---
ID: 205
post_title: >
  Yönlendirmeli Sayfanın
  Yönlendirildiği Sayfayı Bulma
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/yonlendirmeli-sayfanin-yonlendirildigi-sayfayi-bulma-205.html
published: true
post_date: 2011-06-29 22:45:31
---
Merhaba arkadaşlar,

Bugünkü makalemde sizlere PHP ile bağlanmaya çalıştığınız sayfada 301 veya 302 HTTP yönlendirmesi varsa bu sayfanın hangi sayfaya yönlendirdiğini bulmanızı sağlayacak bir fonksiyon veriyorum. Fonksiyonumuz aşağıdaki gibidir:

<pre class="lang:php decode:1 " >function asil_url( $url,  $javascript_dongu = 0, $zaman_asimi = 5 ){
    $url = str_replace( &amp;quot;&amp;amp;&amp;quot;, &amp;quot;&amp;amp;&amp;quot;, urldecode(trim($url)));
    $cerez = tempnam (&amp;quot;/tmp&amp;quot;, &amp;quot;CURLCOOKIE&amp;quot;);
    $curl = curl_init();
    curl_setopt( $curl, CURLOPT_USERAGENT, &amp;quot;Mozilla/5.0 (Windows; U; Windows NT 5.1; rv:1.7.3) Gecko/20041001 Firefox/0.10.1&amp;quot; );
    curl_setopt( $curl, CURLOPT_URL, $url );
    curl_setopt( $curl, CURLOPT_RETURNTRANSFER, 1 );
    curl_setopt( $curl, CURLOPT_MAXREDIRS, 10 );
    $content = curl_exec( $curl );
    $cevap = curl_getinfo( $curl );
    curl_close ( $curl );
    if ($cevap['http_code'] == 301 || $cevap['http_code'] == 302){
        ini_set(&amp;quot;user_agent&amp;quot;, &amp;quot;Mozilla/5.0 (Windows; U; Windows NT 5.1; rv:1.7.3) Gecko/20041001 Firefox/0.10.1&amp;quot;);
        if ($baslik = get_headers($cevap['url'])){
            foreach($baslik as $deger){
                if ( substr( strtolower($deger), 0, 9 ) == &amp;quot;location:&amp;quot; )
                    return get_url( trim( substr( $deger, 9, strlen($deger) ) ) );
            }
        }
    }
    if (( preg_match(&amp;quot;/&amp;gt;[[:space:]]+window.location.replace('(.*)')/i&amp;quot;, $content, $deger) || preg_match(&amp;quot;/&amp;gt;[[:space:]]+window.location=&amp;quot;(.*)&amp;quot;/i&amp;quot;, $content, $deger)) &amp;amp;&amp;amp; $javascript_dongu &amp;lt; 5){
        return get_url( $deger[1], $javascript_dongu+1 );
    }
    else{
        return array( $content, $cevap );
    }
}

// fonksiyonun kullanımı
echo asil_url(&amp;quot;http://trkodlama.com&amp;quot;); // Ekran &ccedil;ıktısı http://www.trkodlama.com olacaktır.</pre>

Önceki makalemde HTTP durum kodunu en başarılı nasıl bulabileceğinizi anlatmıştım. O fonksiyon aracılığıyla önce HTTP durum kodunu kontrol edebilirsiniz eğer 301 veya 302 varsa şimdi paylaştığım fonksiyon aracılığıyla yönlendirme sonucu gidilen adresi bulabilirsiniz.

Umarım faydalı olur, birinin işine de yarar.. Kolay gelsin arkadaşlar