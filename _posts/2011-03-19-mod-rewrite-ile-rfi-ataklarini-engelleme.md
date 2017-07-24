---
ID: 123
post_title: >
  Mod Rewrite ile RFI Ataklarını
  Engelleme
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/guvenlik/mod-rewrite-ile-rfi-ataklarini-engelleme-123.html
published: true
post_date: 2011-03-19 16:21:44
---
Merhaba arkadaşlar,

Bugün size web sitenize RFI(Remote File Inclusion) ataklarından nasıl korunabileceğiniz göstereceğim. Öncelikle RFI atak neymiş kısaca bir anlatalım.

RFI atak uzaktan dosya dahil etmektir. PHP scriptlerde bulunan bir açıktır. Web sitesine uzaktan bir dosya eklemenizi sağlar. Değişkenlerinizin tanımlı olmadığı yerlerde yani değişkenleriniz boş olduğu anda buralarda RFI açıklar meydana gelir. RFI atağı ile o değişkene uzaktan eklenen dosyanın değeri atanır. Bu işlemin file upload işlemleriyle alakası yoktur. Shell dosyaları ile yapılır.

Şimdi http://, https:// veya ftp:// için yapılan sorgu satırlarımızı kontrol edelim:
<pre class="prettyprint lang-apache_conf" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">RewriteCond %{QUERY_STRING} (.*)(http|https|ftp)://(.*)</pre>
Eğer bu rewrite koşulunu .htaccess dosyanızda kullanıyorsunuz bütün benzer istekleri aşağıdaki komutlar ile engelleyelim:
<pre class="prettyprint lang-apache_conf" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">RewriteRule ^(.+)$ - [F]</pre>
Eğer vHost'unuza erişim izniniz varsa bu denemleri kayıt altına alabilirsiniz:
<pre class="prettyprint lang-apache_conf" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;IfModule mod_rewrite.c&gt;
RewriteEngine on
RewriteCond %{QUERY_STRING} (.*)(http|https|ftp)://(.*)
RewriteRule ^(.+)$ - [env=rfi:true]
&lt;/IfModule&gt;
CustomLog /kayitlarinizin/tutuldugu/dizin/rfi.log combined env=rfi</pre>
Aynı zamanda yukarıdaki rewrite komutlarından kaynaklanan istekleride engelleyebilirsiniz:
<pre class="prettyprint lang-apache_conf" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">Deny from env=rfi</pre>
Umarım kimsenin başına gelmeden tedbirinizi almış olursunuz. Kolay gelsin,