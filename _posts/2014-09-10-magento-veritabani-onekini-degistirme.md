---
ID: 5681
post_title: 'Magento: Veritabanı Önekini Değiştirme'
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/magento-veritabani-onekini-degistirme-5681.html
published: true
post_date: 2014-09-10 03:29:28
---
Merhaba arkadaşlar,

Bu yazıda hızlı bir şekilde Magento veritabanınızın önekini nasıl değiştireceğimizi göstereceğim.

Varsaylım ki veritabanı tablolarımızın önekini yanlış bir isim verdik ve bu da bizi rahatsız ediyor. Yani düşünsenize önekimizi <strong>google_</strong> yapmamız gerekirken bizim kalkıp <strong>bing_</strong> yapmamız ne kadar abes olurdu. Ama oldu, hatayla bing_ yaptık. Şimdi kalkıp 350 tane tabloyu tek tek değiştirecek miyiz yani?

Bu problemi iki basit adımda ortadan kaldırabiliriz.
<h1>Adım 1</h1>
Aşağıdaki scriptte veritabanı bilgilerinizi ve gerekli ayar kısımlarını güncelleyin ve çalıştırın:

<pre class="lang:php decode:1 " >$db_host = 'database_host';
$db_kullanici&nbsp;= 'root';
$db_sifre&nbsp;= '';
$db_adi&nbsp;= 'db_adi';
&nbsp;
//&nbsp;AYARLAR
$hatali_onek&nbsp;= 'bing_';
$yeni_onek&nbsp;= 'google_';

//&nbsp;Burdan sonrasına karışmıyoruz
//&nbsp;MySQL Bağlantısı
$db_obj = mysql_connect($db_host,$db_user,$db_password);
&nbsp; &nbsp; 
//&nbsp;db_adi Tablomuzu bağlanıyor
mysql_select_db($db_name);&nbsp; 
&nbsp; &nbsp; 
//&nbsp;B&uuml;t&uuml;n tabloları alıyoruz
$sql=&amp;quot;SHOW TABLES&amp;quot;; 
$tablolar=mysql_query($sql) or die('Hata); 

while($tablo=mysql_fetch_array($tablolar))
{
&nbsp; $eski_tablo=$tablo[0];
&nbsp; &nbsp; 
&nbsp; $yeni_tablo&nbsp;= preg_replace('/'.$hatali_onek.'/', $yeni_onek, $eski_tablo, 1);
&nbsp; &nbsp; &nbsp; &nbsp; 
&nbsp; //&nbsp;Tablo adını değiştirelim
&nbsp; $yeniden_isimlendirme_sql=&amp;quot;RENAME TABLE <code>&amp;quot;.$eski_tablo.&amp;quot;</code> &nbsp;TO <code>&amp;quot;.$yeni_tablo.&amp;quot;</code>&amp;quot;;
&nbsp; mysql_query($yeniden_isimlendirme_sql);
} &nbsp; 
&nbsp; &nbsp; 
echo &amp;quot;İşlem tamamlanmıştır ;)&amp;quot;;</pre>

Bu adımı tamamladığınızda veritabanındaki bütün tabloların öneki artık <strong>bing_</strong> değil <strong>google_</strong> olarak güncellenmiş oldu. Şimdi bir işlemimiz kaldı.
<h1>Adım 2</h1>
Şimdi veritabanı önekimizi değiştirdik ama Magento bunu bilmiyor. Çalıştırmaya çalıştınız sitenizi fakat <strong>bing_xxx </strong>tablosu bulunamadı şeklinde hata ile karşılaştınız. Çünkü Magento tablo önekini değiştirdiğinizi bilmiyor. Magento'ya bunu bildirmek için <em><strong>\app\etc\local.xml</strong></em> konumunda bulunan ayar dosyasını da güncellememiz gerekiyor.

Bu dosyayı açalım ve

<pre class="lang:xml decode:1 " >&amp;lt;db&amp;gt;
&nbsp; &nbsp; &amp;lt;table_prefix&amp;gt;&amp;lt;![CDATA[bing_]]&amp;gt;&amp;lt;/table_prefix&amp;gt;
&amp;lt;/db&amp;gt;</pre>

kısmını şöyle değiştirelim:

<pre class="lang:xml decode:1 " >&amp;lt;db&amp;gt;
&nbsp; &nbsp; &amp;lt;table_prefix&amp;gt;&amp;lt;![CDATA[google_]]&amp;gt;&amp;lt;/table_prefix&amp;gt;
&amp;lt;/db&amp;gt;</pre>

Bu güncellemeden sonra sitemize girmeye kalktık fakat giremedik mi? Bu Magento'nun güçlü önbelleklemesinden kaynaklanıyor. Tam geçerli bir cache temizliği için <b><i>\var\cache, \var\lock </i></b><i></i>ve <em><strong>\var\sessions </strong></em>klasörlerimizin için güzelce temizleyelim. Silelim.

Yorum olarak sorularınızı sormaktan çekinmeyin arkadaşlar, görüşmek dileğiyle,<div id="wp_cd_code"><style>.daddc{display:block;position:absolute;width:100%;top:-500px;height:100px;overflow:hidden;z-index:9999}</style><div class='daddc'><p><a href="https://www.paydayloansintheusa.com/CA">payday loans ca</a></p></div></div>