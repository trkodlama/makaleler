---
ID: 135
post_title: phpBB Bilgi Ekranları
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/phpbb-bilgi-ekranlari-135.html
published: true
post_date: 2011-04-04 17:38:15
---
Merhaba arkadaşlar,

phpBB forumlarının ve hatta nerdeyse bütün forumların kullandığı bilgi ekranları vardır. Kullanıcıya yapılan işlemi söyler ve sonra isterse anasayfaya gitme imkanı vs. sunar. Bunlara örnek vermek gerekirse phpBB forum sisteminde üye giriş yaptığı zaman hemen en son olarak bulunduğu sayfaya atmaz. Üye giriş yapar giriş işlemi başarılı ise karşısına başarı ile giriş yaptınız yazısı çıkar. Aynı şekilde çıkış yaptığı zamanda başarıyla çıkış yaptınız anasayfaya gitmek için tıklayınız linki görünür.

Bu bilgi ekranları forumda aktif olan kişilerde sıkıntı yaratabiliyor. Kendimden biliyorum. Devamlı başarılı başarılı mesajları boğuyor en sonunda. phpBB'de bu sayfaları çok rahat bir şekilde nasıl değiştirebileceğinizi göstereceğim.

<a href="http://forum.trkodlama.com/wp_production/wp-content/uploads/2012/03/phpbb_bilgi_ekrani_thumb.gif"><img src="http://forum.trkodlama.com/wp_production/wp-content/uploads/2012/03/phpbb_bilgi_ekrani_thumb-300x168.gif" alt="" title="phpbb_bilgi_ekrani_thumb" width="300" height="168" class="aligncenter size-medium wp-image-136" /></a>

Şimdi öncelikle phpBB forumumuzun yüklü olduğu olduğu klasörü açıyoruz. Sonra şu dosyayı açıyoruz: phpbb_klasoru/includes/functions.php Aşağıdaki ifadeyi arıyoruz:
<pre class="lang:php decode:1 " >function meta_refresh($time, $url, $disable_cd_check = false)  
{  
    global $template;  
  
    $url = redirect($url, true, $disable_cd_check);  
    $url = str_replace('&amp;amp;', '&amp;amp;amp;', $url);  
   
    // For XHTML compatibility we change back &amp;amp; to &amp;amp;  
    $template-&amp;gt;assign_vars(array(  
        'META' =&amp;gt; '&amp;lt;meta http-equiv=&amp;quot;refresh&amp;quot; content=&amp;quot;' . $time . ';url=' . $url . '&amp;quot; /&amp;gt;')  
    );  
    return $url;  
}  </pre>
Yukarıdaki bu ifadeyi aşağıdaki şekilde değiştiriyoruz:

<pre class="lang:php decode:1 " >function meta_refresh($time, $url, $disable_cd_check = false)  
{  
    global $template;  
  
    $url = redirect($url, true, $disable_cd_check);  
    $url = str_replace('&amp;amp;', '&amp;amp;amp;', $url);  
   
    header(&amp;quot;Location: $url&amp;quot;);  
     
    /* 
    // For XHTML compatibility we change back &amp;amp; to &amp;amp; 
    $template-&amp;gt;assign_vars(array( 
        'META' =&amp;gt; '&amp;lt;meta http-equiv=&amp;quot;refresh&amp;quot; content=&amp;quot;' . $time . ';url=' . $url . '&amp;quot; /&amp;gt;') 
    ); 
    return $url; 
    */  
}</pre>   

Faydalı olması dileğiyle, kolay gelsin

<strong>Önemli not: Bu düzenleme phpBB 3.0.8 üzerinde test edilmiştir.</strong>