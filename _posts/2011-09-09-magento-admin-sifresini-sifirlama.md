---
ID: 251
post_title: Magento Admin Şifresini Sıfırlama
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/magento-admin-sifresini-sifirlama-251.html
published: true
post_date: 2011-09-09 01:33:43
---
Merhaba arkadaşlar

Bugünkü makalem yine Magento ile ilgili. Magento dünyada görüp görebileceğiniz en iyi ve en gelişmiş açık kaynak kodlu PHP ile yazılmış e-ticaret sistemidir.

Şimdi gelelim probleme, Magento admin şifrenizi unuttunuz ve yenilemeniz gerekiyor ama nasıl yapacağınızı bilmiyor musunuz? İşte sizlere bu konuda yardımcı olabilecek bir SQL kodu paylaşıyorum. Aşağıdaki SQL kodunu çalıştırarak çok rahat bir şekilde yönetici şifrenizi değiştirebilirsiniz(Yönetici şifrenizi hatırlamak şartıyla).

Bu örneğimizde yönetici kullanıcı adı <strong>admin</strong> olsun. Aşağıdaki SQL kodunu çalıştırdığınızda şifrenizi yenilemiş olacaksınız:

<pre class="lang:sql decode:1 " >UPDATE admin_user SET password=CONCAT(MD5('TRKodlamaYeniSifre'), ':TRKodlama') WHERE username='admin';</pre>

Yukarıdaki kodda sadece<strong> YeniSifre</strong> kısmı değiştirin. Bu SQL kodu <strong>admin </strong>kullanıcısının şifresini<strong>YeniSifre</strong> yapacaktır. Artık kullanıcı adı <strong>admin</strong>, şifresi <strong>YeniSifre</strong> ile yönetici paneline erişebilirsiniz.

Umarım bu makale de faydalı bir makale, herkese kolay gelsin,