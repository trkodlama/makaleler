---
ID: 233
post_title: Twitter Arama Sonuçlarını Çekme
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/twitter-api/twitter-arama-sonuclarini-cekme-233.html
published: true
post_date: 2011-08-26 00:36:25
---
Merhaba arkadaşlar,

Uzun zaman oldu yeni makale eklemeyli. Arayı soğuttum birazcık herhalde. Bugün sizlere Twitter'daki arama sonuçlarını PHP ile nasıl çekeceğinizi anlatıyorum.

Twitter API'sini kullanacağız bu verileri çekerken. Verileri JSON formatında alacağız ve onları işleyeceğiz. Twitter'ın search API'si için daha detaylı bilgi için <a href="https://dev.twitter.com/overview/api" target="_blank">buraya tıklayınız</a>.

Öncelikle PHP fonksiyonumuzu hazırlayalım. Bu fonksiyonu Twitter'da arama sonucu varsa sonuçları döndürecek eğer sonuç yoksa false dönecek şekilde hazırladım.
<pre class="prettyprint lang-php" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">function twitterSonuclari($data){
    $t_search = file_get_contents("http://search.twitter.com/search.json?q=".urldecode($data)."&amp;result_type=recent&amp;rpp=10");
    $results = json_decode($t_search, true);
    if(count($results["results"])&gt;0){
        return $results["results"];
    }
    else{
        return false;
    }
}</pre>
Eğer fonksiyon sonuç bulursa bir dizi döndürür. Bu dizi aşağıdaki gibidir:
<pre class="prettyprint lang-rst" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">Array
(
    [0] =&gt; Array
    (
        [created_at] =&gt; Fri, 26 Aug 2011 00:52:37 +0000
        [from_user] =&gt; oralunal
        [from_user_id] =&gt; 229123064
        [from_user_id_str] =&gt; 229123064
        [geo] =&gt;
        [id] =&gt; 106891765147115520
        [id_str] =&gt; 106891765147115520
        [metadata] =&gt; Array
        (
            [result_type] =&gt; recent
        )

        [profile_image_url] =&gt; http://a2.twimg.com/profile_images/1435376616/MYDC2013_normal.JPG
        [source] =&gt; &lt;a rel="nofollow" href="http://bit.ly"&gt;bitly&lt;/a&gt;
        [text] =&gt; http://t.co/zweOT0v
        http://t.co/gjodqyw
        [to_user_id] =&gt;
        [to_user_id_str] =&gt;
    )

    [1] =&gt; Array
    (
        [created_at] =&gt; Thu, 25 Aug 2011 23:56:56 +0000
        [from_user] =&gt; trkodlama
        [from_user_id] =&gt; 8982188
        [from_user_id_str] =&gt; 8982188
        [geo] =&gt;
        [id] =&gt; 106877753726484481
        [id_str] =&gt; 106877753726484481
        [iso_language_code] =&gt; tr
        [metadata] =&gt; Array
        (
            [result_type] =&gt; recent
        )

        [profile_image_url] =&gt; http://a2.twimg.com/profile_images/349223586/trkodlama_normal.png
        [source] =&gt; &lt;a rel="nofollow" href="http://twitterfeed.com"&gt;twitterfeed&lt;/a&gt;
        [text] =&gt; Forumdan: Her Kadın Güzeldir #forum
        [to_user_id] =&gt;
        [to_user_id_str] =&gt;
    )
)</pre>
Şimdi kontrol edip işleme sayfasına geçelim:
<pre class="prettyprint lang-php" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">$arama = "trkodlama";
if(($results = twitterSonuclari($arama))!=FALSE){
    foreach($results AS $r){
        echo $r['from_user']; // tiviti atan kullanıcı
        echo $r['profile_image_url']; // tiviti atan kullanıcının resmi
        echo $r['text']; // Atılan tivit
    }
}</pre>
Kullanımı kolay ve basit bir API. Umarım faydalı olmuştur, sorularınızı ve yorumlarınızı lütfen bildirin.

Kolay gelsin,