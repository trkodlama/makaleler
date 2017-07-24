---
ID: 332
post_title: 'CentOS&#8217;a mod_pagespeed Kurma'
author: Oral ÜNAL
post_excerpt: "mod_pagespeed açık kaynak kodlu bir Apache modülüdür. Bu modül web sayfalarınızı ve web sayfalarınızda kullanılan kaynakları otomatik olarak optimize eder. Özellikle kullanılan bu kaynakları yeniden yazarak onların en iyi performansı sağlayacakları şekilde değiştirilir. Webmasterlar ve web geliştiricileri içeriklerini Apache HTTP Sunucusu ile sunuyorlarsa mod_pagespeed'i rahatlıkla kullanabilirler."
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/centosa-mod_pagespeed-kurma-332.html
published: true
post_date: 2012-03-09 05:25:57
---
Merhaba arkadaşlar,

Öncelikle mod_pagespeed nedir, faydaları nelerdir, neler yapar sorularının cevaplarını vermekle başlayalım.
<h1>mod_pagespeed nedir?</h1>
mod_pagespeed açık kaynak kodlu bir <strong>Apache</strong> modülüdür. Bu modül web sayfalarınızı ve web sayfalarınızda kullanılan kaynakları otomatik olarak optimize eder. Özellikle kullanılan bu kaynakları yeniden yazarak onların en iyi performansı sağlayacakları şekilde değiştirilir. Webmasterlar ve web geliştiricileri içeriklerini Apache HTTP Sunucusu ile sunuyorlarsa <strong>mod_pagespeed</strong>'i rahatlıkla kullanabilirler.

<strong>mod_pagespeed</strong> bir çok filtreye sahiptir. Bu filtreler sayesinde JavaScript, HTML ve CSS dosyalarınızı en iyi şekilde optimize edere son kullanıcıya gönderir. Ayrıca JPEG ve PNG resim dosyalarını optimize etme yeteneğine sahiptir. Bu filtrelerin temelinde en iyi <a href="http://code.google.com/speed/page-speed/docs/rules_intro.html" target="_blank">web performans artırım uygulamaları</a> yer almaktadır.

mod_pagespeed ile dosyalarınızı gzip sıkıştırma ile sıkıştırabilir, fazla yorum satırlarını kaldırabilir, resimlerinizi optimize edebilir ve bütün dosyalarınızın bu yeni hallerini önbellekleyip sunucuya kaydeder. Bir sonraki seferde sunucudan alır bu dosyaları.
<h1>Faydaları nelerdir?</h1>
<ol>
	<li>Sayfalarınızın HTML çıktılarını gzip yöntemi ile sıkıştırır.</li>
	<li>Bütün JavaScript ve CSS dosyalarınızı gzip yöntemi ile sıkıştırır.</li>
	<li>Mümkün olursa eğer bütün javascript dosyalarınızı tek bir dosyada, bütün CSS dosyalarınızı tek bir dosya da toplamaya çalışır.</li>
	<li>JavaScript ve CSS dosyalarınızdaki ekstra yorum satırlarını veya boşlukları siler.</li>
	<li>Jpeg, png formatlı resimlerinizi optimize eder. Bu optimizasyon sayesinde resimleriniz kaliteleri korunarak sıkıştırılır. Daha küçük resimler elde edersiniz.</li>
	<li>Bu işlemleri yapar ve ilgili işlemler sonucu oluşan yeni dosyaları önbellekte saklar ve daha sonra önbellekten çeker. Her seferin aynı işlemleri tekrarlayarak sunucuya yük bindirmez.</li>
	<li>Sizde kullanıcılarınıza muhteşem hızlı web sayfaları sunarsınız.</li>
</ol>
<h1>mod_pagespeed kurulumu</h1>
Bu kurulumu CentOS 5.5'de denedim. Diğer sistemlerde aynı sonucu verip vermeyeceğinin garantisini veremiyorum ne yazık ki.

Öncelikle SSH ile sunucunuza bağlanın. Daha sonra aşağıdaki komutla sunucumuza <strong><a href="http://code.google.com/p/modpagespeed/" target="_blank">Google Code</a></strong>'dan <strong>mod_pagespeed 0.10.21.2</strong> sürümümüzü indirelim:

[sourcecode]wget https://dl-ssl.google.com/dl/linux/direct/mod-pagespeed-beta_current_i386.rpm[/sourcecode]

Sıradaki aşamada Google anahtarını RPM'nin içine aktarıyoruz aşağıdaki komutla(bu aşamayı yapmanıza gerek olmayabilir):

[sourcecode] wget https://dl-ssl.google.com/linux/linux_signing_key.pub
rpm --import linux_signing_key.pub[/sourcecode]

Yukarıdaki adımı uygulamadan önce isterseniz direkt RPM veya YUM komutu ile kurulum yapabilirsiniz fakat yukarıdaki komutu çalıştırmadan deneyen bir çok kişi aşağıdaki hata ile karşılaşmışlar:

[sourcecode]warning: rpmts_HdrFromFdno: Header V3 DSA signature: NOKEY, key ID 7fac5991
Public key for mod-pagespeed-beta_current_i386.rpm is not installed[/sourcecode]

Ben karşılaşmadım. Şimdi dosyamızı sunucuya indirdik. Artık kuruluma geçebiliriz. Kurulum için aşağıdaki komutu yazıyoruz:

[sourcecode][root@localhost ~]# yum localinstall mod-pagespeed-beta_current_i386.rpm[/sourcecode]

Vee kurulum başlıyor...

[sourcecode]Loaded plugins: fastestmirror, priorities
Setting up Local Package Process
Examining mod-pagespeed-beta_current_i386.rpm: mod-pagespeed-beta-0.9.1.1-171.i386
Marking mod-pagespeed-beta_current_i386.rpm to be installed
Loading mirror speeds from cached hostfile
 * addons: mirrors.gitam.edu
 * base: mirrors.gitam.edu
 * epel: bali.idrepo.or.id
 * extras: mirrors.gitam.edu
 * ius: mirror.its.dal.ca
 * updates: mirrors.gitam.edu
Resolving Dependencies
--&gt; Running transaction check
---&gt; Package mod-pagespeed-beta.i386 0:0.9.1.1-171 set to be updated
--&gt; Finished Dependency Resolution

Dependencies Resolved

================================================================================
 Package             Arch  Version      Repository                         Size
================================================================================
Installing:
 mod-pagespeed-beta  i386  0.9.1.1-171  /mod-pagespeed-beta_current_i386  1.5 M

Transaction Summary
================================================================================
Install       1 Package(s)
Upgrade       0 Package(s)

Total size: 1.5 M
Is this ok [y/N]: y
Downloading Packages:
Running rpm_check_debug
Running Transaction Test
Finished Transaction Test
Transaction Test Succeeded
Running Transaction
  Installing     : mod-pagespeed-beta                                       1/1
job 1 at 2010-11-09 09:11

Installed:
  mod-pagespeed-beta.i386 0:0.9.1.1-171

Complete![/sourcecode]

Kurulum bitti! Bu aşamadan sonra Apache'yi yeniden başlatmak en mantıklısı olacaktır.

[sourcecode]/etc/init.d/httpd restart[/sourcecode]

Gelelim ayar dosyasına. Ayar dosyasının yeri <strong><span style="color: #ff0000;">etc/httpd/conf.d/pagespeed.conf</span></strong> şeklindedir. Benim favori ayarlarımı paylaşmadan önce sizlere gerekli bütün ayarların bulunduğu sayfanın adresini vereyim. Ayar için gerekli bilgilere <strong><a href="http://code.google.com/speed/page-speed/docs/config_filters.html" target="_blank">bu sayfadan</a></strong> ulaşabilirsiniz.

Benim favori ayarlarım aşağıdaki gibidir(<strong>pagespeed.conf dosyam aynı zamanda</strong>):

[sourcecode]LoadModule pagespeed_module /usr/lib64/httpd/modules/mod_pagespeed.so

&lt;IfModule !mod_deflate.c&gt;
 LoadModule deflate_module /usr/lib64/httpd/modules/mod_deflate.so
&lt;/IfModule&gt;
&lt;IfModule pagespeed_module&gt;
 SetOutputFilter MOD_PAGESPEED_OUTPUT_FILTER

// &quot;on&quot; ile modülü açıyoruz. &quot;off&quot; ile kapatıyoruz.
ModPagespeed on

# Önbellek klasörlerinin yerini belirtiriyorum
# Bu klasörler Apache tarafından yazılabilir olmalıdır
ModPagespeedFileCachePath &quot;/var/www/mod_pagespeedcache/&quot;
ModPagespeedGeneratedFilePrefix &quot;/var/www/mod_pagespeedfiles/&quot;

# mod_pagespeed'in 3 adet yeniden yazma seviyesi var. Bu seviyeler
# PassThrough, CoreFilters ve TestingCoreFilters.
ModPagespeedRewriteLevel CoreFilters

# Aslında bu kadarla sınırlı değil fakat diğerleri kendiliğinden aktif olarak çalışıyor..
ModPagespeedEnableFilters collapse_whitespace
 ModPagespeedEnableFilters combine_javascript
 ModPagespeedEnableFilters remove_comments
 ModPagespeedEnableFilters defer_javascript

 ModPagespeedRespectVary on

&lt;/IfModule&gt;[/sourcecode]

mod_pagespeed kurulumu bu kadardır arkadaşlar. Sorularınızı forumdan veya yorum ile sorabilirsiniz.

İyi günler,