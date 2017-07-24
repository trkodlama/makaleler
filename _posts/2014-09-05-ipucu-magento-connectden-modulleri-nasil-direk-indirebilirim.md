---
ID: 5436
post_title: 'İPUCU: Magento Connect&#8217;den Modülleri Nasıl Direk İndirebilirim?'
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/ipucu-magento-connectden-modulleri-nasil-direk-indirebilirim-5436.html
published: true
post_date: 2014-09-05 18:33:58
---
Merhaba arkadaşlar,

Yazı yazmayalı oldukça uzun bir süre oldu. Bugün <a href="http://www.magentocommerce.com/magento-connect/" target="_blank">Magento Connect</a>'den bulduğunuz modülleri/eklentileri bilgisayarınıza nasıl indireceğinizi göstereceğim.

Neden bu şekilde indirmeyi tercih edebilirsiniz?
<ol>
	<li>Downloader'ınızda bir sıkıntı yaşıyor olabilirsiniz.</li>
	<li>Eklentiyi önce kurcalamayı tercih etmiş olabilirsiniz.</li>
</ol>
Bu modülleri dilediğiniz tarayıcıdan indirebilirsiniz.

<strong>URL'nin Formatı</strong>

http://connect20.magentocommerce.com/community/<span style="color: #33cccc;">{PAKET ADI}</span>/<span style="color: #339966;">{VERSİYON}</span>/<span style="color: #33cccc;">{PAKET ADI}</span>-<span style="color: #339966;">{VERSİYON}</span>.tgz

Bir örnekle bunu pekiştirelim.

<a href="http://www.magentocommerce.com/magento-connect/yotpo-product-reviews.html" target="_blank">Yotpo Product Rewievs</a> eklentisini baz alalım. Eklenti sayfasına gittiğiniz de <strong>Install Now</strong> butonuna tıklayın ve <strong>Magento Connect 2.0</strong>'ı seçin. Lisans anlaşmasını onaylayın ve <strong>Get Extension Key</strong> butonuna tıklayın. Karşınıza şu şekilde bir url gelecek:

http://connect20.magentocommerce.com/community/<strong>yotporeviews</strong>

Bu URL'de kalın olarak yazılmış kısım(<strong>yotporeviews</strong>) bizim <strong>paket</strong> <strong>adı</strong>mız oluyor. Versiyonu da yine eklenti sayfamızda <strong>Release Notes </strong>sekmesine tıklayarak görebilirsiniz. Şu anda bu eklentinin versiyonu şu şekilde belirtilmiş
<ul>
	<li>Version number: <strong>1.6.2</strong></li>
</ul>
<strong>1.6.2</strong>'de bizim versiyonumuz. O zaman bu eklentiyi direk indirmek için aşağıdaki URL'ye tıklamamız gerekiyor:

<a href="http://connect20.magentocommerce.com/community/yotporeviews/1.6.2/yotporeviews-1.6.2.tgz" target="_blank">http://connect20.magentocommerce.com/community/yotporeviews/1.6.2/yotporeviews-1.6.2.tgz</a>

Umarım faydalı olmuştur.