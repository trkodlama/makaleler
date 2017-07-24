---
ID: 921
post_title: 'Subdomain&#8217;den Webkit Font Yükleme Sorunu'
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/subdomainden-webkit-font-yukleme-sorunu-921.html
published: true
post_date: 2012-06-30 23:29:07
---
Geçenlerde uğraştığım bir projede değişiklik olsun diye webkit font kullanmak istedim. Projeyi sunucuya atıp çalıştırdığım anda problem yaşadım. Halbuki lokalde çok başarılı bir şekilde çalışıyordu.

Fakat sunucuya atıp test ettiğim zaman fontların tam olarak başarılı yüklenmediğini farkettim. Bu problem sadece Mozilla Firefox'da ve tabii ki Internet Explorer'daydı. Diğer tarayıcılarda bir problem yoktu.

Birazcık araştırmadan sonra bunun için gerekli çözümü buldum. Fontları farklı bir domainden yüklemeye çalışıldığı zaman bu problem ortaya çıkıyor ve benim CSS dosyam subdomainden çekiliyordu.
<h3>Sebebi Nedir?</h3>
Firefox farklı etki alanlarından font yüklenmesinin kötü bir fikir olduğunu düşünüyor. Bu nedenle buna müsade etmiyor. IE için zaten konuşmaya gerek yok. Herşeyi hep geriden takip eder kendisi.
<h3>Çözümü Nedir?</h3>
Dediğim gibi kısa bir araştırmadan sonra sorunun çözümünü buldum. Bu problemi .htaccess dosyasına 3-5 satırlık bir kod ekleyerek çözüme kavuşturacağız. Aşağıdaki kodu .htaccess dosyanıza ekleyerek bütün domainlerden font yüklemesi yapabilirsiniz:

[text]  &lt;filesmatch &quot;\.(ttf|ttc|otf|eot|woff)$&quot;=&quot;&quot;&gt;
    &lt;ifmodule mod_headers.c=&quot;&quot;&gt;
        Header set Access-Control-Allow-Origin &quot;*&quot;
    &lt;/ifmodule&gt;
  &lt;/filesmatch&gt;[/text]
<blockquote>Firefox farklı etki alanlarından font yüklenmesinin kötü bir fikir olduğunu düşünüyor</blockquote>
Belirli domainlerden yüklemek isterseniz de aşağıdaki kodu kullanabilirsiniz:

[text]  &lt;filesmatch &quot;\.(ttf|ttc|otf|eot|woff)$&quot;=&quot;&quot;&gt;
    &lt;ifmodule mod_headers.c=&quot;&quot;&gt;
        Access-Control-Allow-Origin: http://belirlidomain.com
    &lt;/ifmodule&gt;
  &lt;/filesmatch&gt;[/text]

Umarım sorununuzu çözmüştür bu yöntem. Kolay gelsin,