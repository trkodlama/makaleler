---
ID: 241
post_title: PHP İçinde XML Kullanmak
author: damatmedya
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/uyelerimizden-php-icinde-xml-kullanmak-241.html
published: true
post_date: 2011-09-04 00:52:06
---
Bu makalede size hakkimizda.php'yi nasıl hakkimizda.xml olarak gösterip işleyeceğimizi anlatıyorum.
Örneğin hakkinda.xml isimli bir dosyamız olsun bu dosyayı swf dosyası çekiyor olsun. İçeriğide:

<pre class="lang:xml decode:1 " >&amp;lt;?xml version=&amp;quot;1.0&amp;quot; encoding=&amp;quot;utf-8&amp;quot;?&amp;gt;
&amp;lt;content&amp;gt;&amp;lt;![CDATA[Hakkında yazısı]]&amp;gt;&amp;lt;/content&amp;gt;</pre>
olsun.
XML dosyasının bulunduğu klasörün içine aynı isimde bir php dosyası oluşturun. Mesela hakkinda.xml dosyası için hakkinda.php olarak bir dosya oluşturun.
hakkinda.xml dosyasındaki kodları hakkinda.php dosyasına kopyalayıp echo ile yazdırıyoruz. Örneğe göre kodlar şu şekilde olmalı:

<pre class="lang:php decode:1 " >&amp;lt;?php echo '&amp;lt;?xml version=&amp;quot;1.0&amp;quot; encoding=&amp;quot;utf-8&amp;quot;?&amp;gt;
&amp;lt;content&amp;gt;&amp;lt;![CDATA['; ?&amp;gt;
&amp;lt;?php echo 'Hakkında yazısı'; ?&amp;gt;
&amp;lt;?php echo ']]&amp;gt;&amp;lt;/content&amp;gt;'; ?&amp;gt;</pre>

Daha sonra yapmamız gereken hakkinda.php dosyamızla aynı klasör içinde .htaccess dosyası oluşturmak ve içine şunları yazmak:

[sourcecode]RewriteEngine on
RewriteRule ^hakkinda.xml hakkinda.php[/sourcecode]

Daha sonra hakkinda.xml dosyasını silebiliriz. Artık tarayıcıdan hakkinda.xml dosyasına erişilmeye çalışıldığında aslında hakkinda.php dosyası çalışacaktır. hakkinda.php dosyasında veritabanına bağlanıp veri çekebilirsiniz ve bu verileri kullanabilirsiniz. Aynı mantıkla site haritaları da rahatlıkla oluşturabilirsiniz.