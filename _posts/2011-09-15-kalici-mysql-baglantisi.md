---
ID: 257
post_title: Kalıcı MySQL Bağlantısı
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/kalici-mysql-baglantisi-257.html
published: true
post_date: 2011-09-15 01:48:22
---
Sevgili TR Kodlama Ziyaretçileri,

Bu makalemde yoğun trafiğe sahip web sitelerinin kullanmasını tavsiye ettiğim bir php fonksiyonunu anlatacağım sizlere. Bu fonksiyon sunucuları büyük bir zahmetten kurtaracaktır. Bu vesile ile sunucularınızda çıkan sorunlarıda azaltacağından sizleri de rahatlatacaktır.

Bu fonksiyonun adı <strong><a href="http://php.net/manual/tr/function.mysql-pconnect.php" target="_blank">mysql_pconnect()</a></strong>'dir. Bu fonksiyonun kulanım şekli <strong><a href="http://php.net/manual/tr/function.mysql-connect.php" target="_blank">mysql_connect()</a></strong> ile aynıdır.

<pre class="lang:php decode:1 " >&amp;lt;?php
$baglanti = mysql_pconnect($vt_sunucusu, $vt_kullanici_adi, $vt_kullanici_sifresi);
?&amp;gt;</pre>

Bu fonksiyonun fark açık kalmasıdır. Bildiğiniz gibi mysql_connect fonksiyonunu her yeni sayfa geçişinde kullanmak durumundayız fakat bu fonksiyonla bağlantı bir kere açılır. Yani bir kullanıcı sitenize gelir mysql_pconnect ile sunucuya bağlanılır ve kullanıcı her sayfa gezdiğinde yeni bir mysql bağlantısı açılmaz. Yani apache sayfa PHP'nizi yorumladıktan sonra mysql sunucunuz kapatılmaz. Bir sonraki sayfada da tekrar açılmaz. Kalıcı bağlantılar kalıcı olmayan bağlantılardan fazla bir özelliğe sahip değildirler.

Kalıcı bağlantılar ek bir işlevselliğe sahip değilseler bunlar neden tercih ediliyorlar, diye soranlar olabilir. Yanıtı oldukça basittir: Verimlilik. SQL sunucunuza bağlantı açmak çok masraflıysa kalıcı bağlantılar kurmak daha iyidir. Bu bedel gerçekte birçok sebebe bağlı olabileceği gibi olmayabilir de. Bu, veritabanının, HTTP sunucunun bulunduğu makinede olup olmamasından SQL sunucusunun makineye ne kadar yük bindirdiğine kadar geniş bir yelpazede değerlendirilebilir. Son değerlendirmede, eğer bu bedel yüksekse kalıcı bağlantıların büyük ölçüde yardımı olacaktır. SQL sunucuya yapılan her bağlantı isteğinde alt süreç sadece o sayfayı işleyeceği yerde, kalıcı bağlantı durumunda her alt sürecin ömrü boyunca bir bağlantı kurmasına olanak tanınır. Yani, bir kalıcı bağlantı açmış her alt sürecin kendine ait bir kalıcı bağlantısı vardır. Örneğin, SQl sunucunuza kalıcı bağlantı açan betiğiniz 20 ayrı alt süreç çalıştırıyorsa alt süreç başına bir tane olmak 20 ayrı bağlantı var demektir.

<strong>Önemli Not: Ancak şuna dikkat edin</strong>, bağlantı sayısı sınırlı bir veritabanını bu sınırın üstünde kalıcı bağlantılarla kullanıyorsanız bunun bazı götürüleri olabilir. Eğer veritabanınız aynı anda 16 bağlantılık bir sınıra sahipse ve çok meşgul bir sunucu oturumunda 17 alt evre bağlantı açmaya çalışıyorsa biri bunu<strong>başaramayacaktır</strong>. Eğer betiğinizde (sonsuz döngü gibi durumlarda) bağlantıların kapatılmasına izin vermeyen hatalar varsa, veritabanı sadece 16 bağlantı ile hızla <strong>batağa saplanacaktır</strong>.

Zaman aşımı vb. durumlarda mysql bağlantınız kapanacaktır. Bu tip durumlarda mysql_ping ile kontrol edebiliriz. Bu fonksiyon mysql bağlantısı kontrol ettiği gibi tekrar bağlanması için de çaba sarfeder. Biz bunu daha etkili kılmak için şöyle bir yol izleyeceğiz:

<pre class="lang:php decode:1 " >&amp;lt;?php
$vt = mysql_pconnect($sunucu, $kullanici, $sifre);

if(!mysql_ping($vt)){
      $vt = mysql_pconnect($sunucu, $kullanici, $sifre);
}
/*
      İşlemleriniz
*/
?&amp;gt;&nbsp;</pre>

Bu şekilde amacımıza tam olarak ulaşmış oluyoruz. Yukarıdaki <strong>notu</strong> dikkate alarak bu fonksiyonu kullanabilirsiniz. Herkese kolay gelsin,
<div><span style="font-family: 'Lucida Sans Unicode', 'Lucida Grande', sans-serif; line-height: 20px; background-color: #ffffff; font-size: small;">
</span></div>