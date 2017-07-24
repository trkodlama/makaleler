---
ID: 2394
post_title: 'Magento Siparişlerde &#8220;Suspected Fraud&#8221; Problemi'
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/magento-siparislerde-suspected-fraud-problemi-2394.html
published: true
post_date: 2013-09-14 17:41:11
---
Merhaba arkadaşlar,

Bugün sizlere Magento e-ticaretlerde karşılaşılan bir sorundan bahsedeceğim. Magento mağazalarınızda PayPal ile ödemelerinizde kabul ettiğiniz ödemelerde sık karşılaşılan bir problem!

Müşteriniz ödemeyi PayPal ile yaptı. Siz yönetici panelinden kontrol ettiğinizde sipariş durumundan "Suspected Fraud" ibaresini yani dolandırıcılık ibaresini gördünüz. Çok şaşırdınız. Aslında bu bir dolandırıcılık değil fakat Magento bunu öyle değerlendirmiş olabilir. Belki de gerçekten dolandırıcılık girişimidir.

Müşterinin ödemesi gereken tutar 165.68 TL iken müşteriniz PayPal kanalıyla 165.69 TL veya 165.67 TL ödemiş olabilir. Bu durumda Magento 1 kuruş için yorgan yakabiliyor ve suspected fraud olarak işaretliyor siparişi. Bunun sebebi ise Magento ile PayPal'ın yuvarlama kıstaslarının birbirinden farklı oluşudur. Yani korkulacak bir durum değildir. Bununla ilgili kontrol şöyle yapılırsa çözüme kavuşulmuş olur.

<strong>app/code/core/Mage/Sales/Model/Order/Payment.php</strong> dosyasını açın. Bu dosyada aşağıdaki satırı bulun:

<pre class="lang:php decode:1 " >if ($orderGrandTotal == $this-&amp;gt;_formatAmount($this-&amp;gt;getBaseAmountPaid(), true) + $amountToCapture) {</pre>

ve şu şekilde güncelleyin:

<pre class="lang:php decode:1 " >if (abs($orderGrandTotal - ($this-&amp;gt;_formatAmount($this-&amp;gt;getBaseAmountPaid(), true) + $amountToCapture)) &amp;lt;= 0.01) {</pre>

Bu güncellemeden sonra bu problemi bir daha yaşamayacaksınız. Bu çözüm <strong>Magento 1.6.0.2</strong> sürümünde test edilmiştir.

<strong>Magento 1.5.0.1</strong> kullananlar aşağıdaki çözümü kullanabilir. Yine aynı dosyayı açın ve aşağıdaki iki satırı bulun:

<pre class="lang:php decode:1 " >$orderGrandTotal = sprintf('%.4F', $this-&amp;gt;getOrder()-&amp;gt;getBaseGrandTotal());
if ($orderGrandTotal == sprintf('%.4F', ($this-&amp;gt;getBaseAmountPaid() + $amountToCapture))) {</pre>

Bu iki satırı şu şekilde değiştirin:

<pre class="lang:php decode:1 " >$orderGrandTotal =  $this-&amp;gt;getOrder()-&amp;gt;getBaseGrandTotal();
if (abs($orderGrandTotal - ($this-&amp;gt;getBaseAmountPaid() + $amountToCapture)) &amp;lt;= 0.01 ) {</pre>

Umarım faydalı olur, Magento siteleriniz için destek almak isterseniz bana ulaşın.

İyi çalışmalar,