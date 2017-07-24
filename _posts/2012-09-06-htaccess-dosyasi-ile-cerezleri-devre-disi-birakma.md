---
ID: 1264
post_title: >
  .htaccess Dosyası ile Çerezleri Devre
  Dışı Bırakma
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/htaccess-dosyasi-ile-cerezleri-devre-disi-birakma-1264.html
published: true
post_date: 2012-09-06 01:15:13
---
Merhaba,

Bu yazımda size basit ama etkili küçücük bir ipucundan bahsedeceğim. <strong>Bu sitenizde Çerezleri devre dışı bırakma ile ilgili bir ipucu.</strong>

Şaşırmış olabilirsiniz çünkü kim, neden sitesinde çerezleri devre dışı bırakmak istesin, değil mi? Bu çok doğru ve güzel bir soru olurdu fakat bazı <strong>Çerezsiz Siteler</strong>de  çerezleri devre dışı bırakmak çok güzel bir işlem olurdu.
<h2>Çerezsiz Site?</h2>
Çerezsiz site var olan bir kavram değil, tamamen ben uydurdum. Çerezsiz siteden kastettiğim ana domainde veya sub-domainde statik bir sitenin olması. Yani içerik statik, dinamik bir yapıya sahip değil. Farklı bir örnek vereyim. Statik içerik bulunan sub-domaininizde performansı arttırmak için çerezler devre dışı bırakılabilir. Daha detaylı bilgiyi <strong>Faydası</strong> bölümünde göreceksiniz.
<h3>.htaccess ile Çerezleri Devre Dışı Bırakma</h3>
Aşağıdaki iki satır <strong>.htaccess ile çerezleri devre dışı bırakmayı gösteriyor:</strong>

[text]Header unset Cookie
Header unset Set-Cookie[/text]
<h2>Faydası</h2>
Tarayıcı sunucuyu sorgu yaptığı zaman bütün çerezleri header'la beraber gönderir. Şimdi düşünün ki çerezin boyutu 1 KB fakat sunucuya 100 sorgu yapıyorsunuz ve 1 KB olan çerez sunucuya 100 sefer gönderilmiş oluyor hatta sunucu da size bu bilgileri tekrar geri gönderiyor.

İşte bu kod sayesinde sunucunuzu bu fazla sorgulardan kurtarmış oluyorsunuz, doğal olarak da rahatlatıyorsunuz. Yeterince faydalı olduğu zaten aşikar.

Subdomain'e çerezsiz siteler kurmak isterseniz <a href="http://www.trkodlama.com/makaleler/php/htaccess-dosyasi-ile-cerezleri-devre-disi-birakma-1264.html">bu makaleyi seveceksiniz</a>. Umarım işinize yarar. Eğer bu makaleyi beğendiyseniz bizi sosyal medyada takip edebilir veya haber bültenimize abone olabilirsiniz.