---
ID: 1245
post_title: >
  Zeus Web Sunucusunda WordPress URL
  Rewrite
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/zeus-web-sunucusunda-wordpress-url-rewrite-1245.html
published: true
post_date: 2012-08-20 18:07:00
---
Bu makalede Zeus web sunucusu kullanan hosting firmalarında Wordpress Url Rewrite'ın nasıl çalışabileceğinin gösteriyorum. <strong>Namesco</strong> firması apache yerine Zeus web sunucusunu kullanıyormuş.

Bir arkadaşım wordpress kurmam için rica etti. Bende kırmamak için tamam dedim. Dosyaları yükledik. Siteyi kurduk. URL yapısını sef link haline çevirdim. Site çalışmamaya başladı. Yani linkler çalışmıyor. Nereye tıkladıysa 404 sayfası ile karşılaştım. Ararken tararken en son sunucunun <strong>Apache</strong> yerine <strong>Zeus</strong> olduğunu farkettim.

Google'da kısa bir araştırma sonrasında Apache'de kullanılan <strong>.htaccess</strong> dosyası yerine Zeus'da <strong>rewrite.script</strong> script dosyası kullanılıyormuş.
<blockquote>
<p style="text-align: left;"><strong>Zeus web sunucusu <em>.htaccess </em>yerine <em>rewrite.script</em> dosyası kullanıyormuş.</strong></p>
</blockquote>
<p style="text-align: left;">Aşağıdaki dosya güncel sürüm ile başarılı bir şekilde çalışmaktadır. <em>rewrite.script</em> dosyanızın içine aşağıdaki kodu eklemeniz yeterli olacaktır.</p>

[text]# Zeus web sunucusu için Wordpress Url Rewrite
# mod_rewrite kuralları
map path into SCRATCH:path from %{URL}
look for file at %{SCRATCH:path}
if exists then goto END
look for dir at %{SCRATCH:path}
if exists then goto END
##### Giriş/Şifremi Unuttum/Admin vb. için kontrol #####
match URL into $ with ^/wp-.*$
if matched then goto END
set URL = /index.php[/text]

Kolay gelsin,