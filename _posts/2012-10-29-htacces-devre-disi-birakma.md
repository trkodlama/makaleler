---
ID: 1334
post_title: .htacces Devre Dışı Bırakma
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/htacces-devre-disi-birakma-1334.html
published: true
post_date: 2012-10-29 14:49:33
---
Merhaba arkadaşlar,

Google'dan gelen aramaları inceliyorum ve sık sık "<strong>.htaccess devre dışı bırakma</strong>" araması ile karşılaşıyorum. .htaccess dosyasını devre dışı bırakmanın iki yolu var aslında.
<h3>1. Yol</h3>
Bu dosyanın ismini değiştirerek devre dışı bırakabilirsiniz. Örnek olarak "<strong>.trkodlama</strong>" yapın dosyanızın adını ve devre dışı kalsın.
<h3>2. Yol</h3>
2. yol ilkine göre biraz daha zahmetli fakat yine aynı basitlikte. Bütün satırların başına "<strong>#</strong>" işareti koyun.
<h3>Ana Dizindeki .htaccess Alt Dizini Etkilemesin</h3>
Eğer ana dizindeki .htaccess dosyasının alt dizinlerdeki sayfalara etki etmesini istemiyorsanız; bu alt dizinlere içi boş bir .htaccess dosyası koymanız yeterlidir.

Umarım faydalı olur, kolay gelsin,