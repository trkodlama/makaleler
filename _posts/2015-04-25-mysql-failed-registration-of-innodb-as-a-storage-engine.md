---
ID: 5716
post_title: 'MySQL: Failed Registration of InnoDB as a Storage Engine'
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/mysql-failed-registration-of-innodb-as-a-storage-engine-5716.html
published: true
post_date: 2015-04-25 08:25:41
---
Bu hatayı sayısız kez ve bir çok sebepten ötürü alabilirsiniz.  MySQL Failed! Ufak ayar değişikliklerinden sonra MySQL sunucusunu çalıştırmayı veya yeniden başlatmayı denediğinizde MySQL başlamayı reddeder. Veya, başlasa bile bazı önemli özelliklerinden yoksun başlar, mesela InnoDB desteği olmadan başlar.

Aşağıdaki resimdeki görüntü bir çok Linux kullanıcısına oldukça tanıdık gelecektir :) :

<img class="aligncenter wp-image-5717 size-full" src="http://www.trkodlama.com/wp-content/uploads/2015/04/mysql_blog_post-e1429939676763.png" alt="mysql_blog_post" width="568" height="60" />

Bazı ayar değişikliklerinizden sonra MySQL'i tekrar başlatırken hata alacaksınız fakat neden? Bazı değişiklikler, kayıt dosyalarının boyutu gibi, bu hatalara sebep olabilirler.

Bazen bu hatalar çok can sıkıcı olabilir, özellikle nereye bakmanız gerektiğine dair bir ipucunuz yoksa.

<h2>MySQL Kayıt Tutma</h2>

MySQL'in çeşitli kayıt dosyaları vardır. Sorgu kayıtları, bağlantı kayıtları, hata kayıtları, binary kayıtları, yavaş çalışan sorgu kayıtları vb.

Bu bağlamda, ayar değişiklikleri yaptığınızda eğer MySQL başlamıyorsa neden başlatılamadığına dair ipuçlarını size hata kayıtları söyleyecektir. Bu hata kayıtları eğer <strong>my.cnf</strong>(<em>log-error = /var/....</em>)<strong> </strong>dosyasından değiştirmediyseniz genellikle <em><strong>/var/lib/mysql </strong></em>dizininde bulunur.

<h2>InnoDB Kayıt Dosyaları</h2>

InnoDB kayıt dosyalarının büyüklüklerinin değiştirilmesi MySQL sunucusunun tekrar başlatılamamasından yaygın ayar değişikliklerinden biridir. InnoDB kayıt dosyası bir nevi InnoDB depolama motoru için kurtarma dosyasıdır. Bu dosya MySQL tablosuna işlenen fakat henüz diske yazılmamış işlemleri içerir. MySQL çökerse ve tampon havuzundanki(<em>buffer pool</em>) veriyi kaybedersen bu dosyalar sayesinde kaybolan veriyi kurtarır ve diske yazılmasını sağlar.

<strong>my.cnf </strong>dosyası InnoDB kayıt dosyalarıyla ilgili bir kaç seçenek sunar. Fakat bu yazıda mevzu bahis problemi ilgilendiren seçenek <em><strong>innodb_log_file_size</strong></em>'dır. Bu seçenek InnoDB kayıt dosyası boyutunu belirtmemize imkan sunar.

<h2>InnoDB Depolama Motoru Tanımlanamadı</h2>

Ayar dosyasını kurcalayan kişiler genellikle istem dışı olarak bu seçeneği değiştirmek isterler. Hatta daha fazla veriyi tutayım, garanti olsun mantalitesine giderek değeri artırırlar ve MySQL'i yeniden başlatırlar. Normal ve basit bir prosedür izlenmesine rağmen MySQL başlarken hata verecektir. MySQL bu durumu sizi korkutsa da artık hata kayıtlarından haberdarsınız. MySQL hata kayıtlarına baktığınızda problemin InnoDB kayıt dosyalarının boyutlarıyla ilgili bir problem olduğunu gördünüz.

<em><strong>innodb_log_file_size</strong></em> seçeneğini değiştirdiğinizde aşağıdakine benzer bir hata alırsınız:

<pre class="lang:sql decode:1 " >110509 12:04:27 InnoDB: Initializing buffer pool, size = 384.0M
 110509 12:04:27 InnoDB: Completed initialization of buffer pool
 InnoDB: Error: log file ./ib_logfile0 is of different size 0 5242880 bytes
 InnoDB: than specified in the .cnf file 0 157286400 bytes!
 110509 12:04:27 [ERROR] Plugin 'InnoDB' init function returned error.
 110509 12:04:27 [ERROR] Plugin 'InnoDB' registration as a STORAGE ENGINE failed.
 110509 12:04:27 [ERROR] Unknown/unsupported table type: innodb
 110509 12:04:27 [ERROR] Aborting

110509 12:04:27 [Note] /usr/sbin/mysqld: Shutdown complete</pre>

Bu problemin iki adet çözümü bulunmaktadır:

<ul>
    <li><strong>my.cnf </strong>dosyasını eski haline getirmek. En azından <strong><em>innodb_log_file_size</em></strong> seçeneğini eski değerine getirin.</li>
    <li><em><strong>./ib_logfile0</strong> ve <strong>./ib_logile1</strong></em> isimli dosyalarının ismini değiştirin veya başka bir konuma taşıyın. Daha sonra MySQL sunucusunu rahatlıkla yeniden başlatabilirsiniz. Bu dosyalar genellikle <strong><em>/var/lib/mysql </em></strong>klasöründe bulunur.</li>
</ul>

Orjinal InnoDB kayıt dosyalarını mümkün olduğunca uzun bir süre silmemeye çalışın; veri kurtarma ihtiyacınız doğma ihtimaline karşı. Temennim odur ki böyle bir ihtiyacınız hiç olmasın :)

Umarım faydalı bir yazı olmuştur, herkese keyifli günler dilerim,