---
ID: 254
post_title: 'Centos 5&#8217;e mod_gzip Kurma'
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/centos-5-e-mod_gzip-kurma-254.html
published: true
post_date: 2011-09-14 01:37:01
---
Merhaba arkadaşlar,

Centos 5, mod_gzip ile uyumlu olmayan Apache 2 ile beraber gelmektedir. Centos 5'de mod_gzip karşılığı olarak mod_deflate kullanılır.

Bu modülü Centos 5'e kurmak çok basit bir işlem gerektirir. Bu modül Centos 5'de yer almaktadır ve sadece aktif edilmesi gerekmektedir.

Bu kurulum için<strong> /etc/httpd/conf/httpd.conf</strong> dosyasını açmanız gerekmektedir. Bu düzenlemeleri gerçekleştirmeden önce <strong>httpd.conf</strong> dosyanızın yedeğini almanızı tavsiye ederim.

Aşağıdaki adımları takip ederek projelerinizde <strong>gzip sıkıştırma</strong>yı kullanabilirsiniz.

<strong>1. Öncelikle httpd.conf dosyanızda şu satırı bulun:</strong>

[sourcecode]LoadModule deflate_module modules/mod_deflate.so[/sourcecode]

<strong>2. Yukarıdaki bu satırın başında "#" işareti varsa kaldırın:
</strong>Yukarıdaki satırı bulun ve başında "#" işareti varsa kaldırın. Bu işlemi yapmadan önce /etc/httpd/modules/mod_deflate.so dosyasının var olduğunu kontrol edin. Eğer bu dosya yoksa bırakın # işareti durmaya devam etsin.
<strong>
3. DEFLATE modülünün ayarlarını yapın:
</strong>Aşağıdaki kodu apache konfigürasyon dosyanıza ekleyin.

[sourcecode]&lt;FilesMatch &quot;\\.(js|css|html|htm|php|xml)$&quot;&gt;
     SetOutputFilter DEFLATE
&lt;/FilesMatch&gt;[/sourcecode]

Bu kod html, css, text ve javascript dosyalarınızı sıkıştıracaktır.

<strong>4. Son olarak Apache'nizi yeniden başlatın</strong>

[sourcecode]service httpd restart[/sourcecode]

Sitelerinizi hızlandırmanız için güzel bir yöntem. JavaScript ve CSS dosyalarınızın boyutlarını farkedilir bir oranda azaltır. Fakat bu yöntem sunucuya binen yük miktarını da arttırır. Bu nedenle bunu kullanırken dikkatli olmak gerekir.

Gzip sıkıştırmasının çalışıp çalışmadığını öğrenmek için <strong><a href="http://www.gidnetwork.com/tools/gzip-test.php" target="_blank">bu aracı</a></strong> kullanabilirsiniz.

Umarım işinize yarar, kolay gelsin,

<strong>Son Güncelleme:</strong> 21 Ekim 2012