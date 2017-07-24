---
ID: 73
post_title: Bir Element Üç Background
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/bir-element-uc-background-73.html
published: true
post_date: 2010-08-02 08:11:38
---
Merhaba arkadaşlar,

Bugünkü yazımda bir CSS elementine birden fazla nasıl background ekleyebileceğinizden bahsedeceğim. Bu özellik CSS3 ile birlikte kullanılabiliyor. Å?öyle bir örnek ile buna neden ihtiyaç duyabileceğimizi anlatalım.

Bir kutunuz var ve köşelerinin sizin koyduğunuz resimlerden oluşmasını istiyorsanız. Bunun için iki CSS elementi belirliyordunuz ve ayrı ayrı işleme sokuyordunuz. Bu özellik sizi bu ayrımcılıktan kurtarıyor. Lafı fazla uzatmadan nasıl yapıldığını inceleyelim:

[sourcecode lang="css"]/* CSS dosyamız */
.elementAdi{
     background-image: url(&quot;sol_ust.gif&quot;), url(&quot;sag_ust.gif&quot;), url(&quot;resim3.gif&quot;);
     background-position: top left, top right, bottom center;
     background-color: #FFFFFF, #FFFFFF, #DDDDDD;

}[/sourcecode]

Yani her eklediğiniz değeri virgül ile ayırarak yazıyorsunuz. Ama sıralama önemlidir. Yani sol_ust.gif için top left geçerli olacaktır.

Kolay gelsin