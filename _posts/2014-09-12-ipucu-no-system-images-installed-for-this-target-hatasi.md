---
ID: 5687
post_title: >
  No System Images Installed For This
  Target Hatası
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  http://www.trkodlama.com/makaleler/ipucu-no-system-images-installed-for-this-target-hatasi-5687.html
published: true
post_date: 2014-09-12 21:57:10
---
Merhaba arkadaşlar,

Android geliştirmeye merak saldınız ve bir heyecanla Eclipse Android SDK'yı indirdiniz. Okuduğunuz bir makaledeki aşamaları takip ediyorsunuz. Uygulamanızı tamamladınız ve şimdi sanal bir cihazla görüntülemek istediniz. O da ne? Yeni cihaz oluştururken <strong>Target</strong> seçtiniz fakat <strong>CPU/ABI</strong> kısmında şu hata belirdiğinden
<blockquote><strong>No System Images Installed For This Target</strong></blockquote>
bir türlü sanal cihaz oluşturamadınız. Bu hatanın sebebi çalıştığınız Target sürümünün <strong>ARM EABI v7a</strong> sistem resmini yüklemediğinizden kaynaklanıyor.
<h1>ÇÖZÜM</h1>
Çözümü oldukça basit. <strong>Window&gt;&gt;Android SDK Manager</strong>'ı açın. Orada çalıştığınız Target sürümün altında ne var ne yoksa yükleyin. Samples'ı yüklemenize pek de gerek yok.

Yüklemeyi tamamladınız fakat aynı hatayı almaya devam mı ediyorsunuz? Cevabı basit, Eclipse'i açıp kapatmanız yeterli olacaktır.

Umarım işinize yarar, kolay gelsin,