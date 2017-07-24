---
ID: 5809
post_title: >
  Varnish Önbelleklerini SSH İle
  Temizleme
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/varnish-onbelleklerini-ssh-ile-temizleme-5809.html
published: true
post_date: 2015-06-15 20:33:25
---
Merhaba arkadaşlar,

Bu bir makaleden ziyade aranılan bir komut. <a href="http://www.trkodlama.com/makaleler/varnish-nedir-5816.html">Varnish</a> kullanılan sunucularda önbelleri temizlemek isterseniz aşağıdaki komutu çalıştırmanız yeterli olacaktır.

[text]varnishadm &quot;ban req.url ~ .&quot;[/text]

Umarım faydalı olur, sevgiler,