---
ID: 6456
post_title: >
  WHM’yi / cPanel’i Komut Satırı
  (SSH) İle Güncelleştirme
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/whmyi-cpaneli-komut-satiri-ssh-ile-guncellestirme-6456.html
published: true
post_date: 2017-01-30 08:35:55
---
Nadirde olsa WHM veya cPanel’ini sadece yazılımı güncellediğinizde çözülebilecek hatalarla karşılaşabilirsiniz. cPanel yazılımınızı komut satırı ile güncelleştirmek için sunucunuza root olarak SSH ile bağlanarak işe koyulalım.

Bağlandığınızda, aşağıdaki komutu çalıştırın:

<pre class="prettyprint lang-sh" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">/scripts/upcp</pre>

Bu komut sizin WHM kurulumunuzu güncelleyecektir. Bilgileriniz bu güncellemeden etkilenmeyecektir. Eğer WHM kurulumunuz zaten güncelse yine de bu güncellemeyi yapmaya zorlayabilirsiniz. Aslında buna ayarlarınızı tutarak WHM’yi yeniden kurmanız desek yanlış olmaz. Güncellemeye zorlamak için aşağıdaki komutu çalıştırın:

<pre class="prettyprint lang-sh" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">/scripts/upcp --force</pre>

Tekrar hatırlatıyorum, verileriniz güncelleme işlemi ile kaybolmaz. Güncelleme yaparken sıkıntı yaşadıysanız veya yaşadığınız problemi güncelleme yaparak gidermeye çalıştığınızda sorun hala yok olmadıysa cPanel iletişime geçmekten çekinmeyin. Dişe tırnağa dokunur etkili bir destek anlayışları var.

Ayrıca sunucu yönetimine dair pek bir bilginiz yoksa zaten hiç bir şeye dokunmamanız gerektiğini söylememe gerek yok sanırım.

Kolay gelsin dilerim,