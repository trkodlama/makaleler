---
ID: 5910
post_title: 'WHM&#8217;den ini_set Fonksiyonunu Devre Dışı Bırakma'
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/whmden-ini_set-fonksiyonunu-devre-disi-birakma-5910.html
published: true
post_date: 2016-11-24 09:21:32
---
Merhaba aradaşlar,

Bugün sunucumda ini_set fonksiyonunu devre dışı bıraktım. Bunun için öncelikle "disable ini_set" gibi bir şeyler aradım fakat böyle bir şey olmadığını sonradan farkettim. <strong>ini_set</strong> fonksiyonunu <strong>disable_functions</strong>'ı kullanarak devre dışı bırakıyoruz. Şu adımları takip edelim:

<ol>
    <li>WHM'ye giriş yapın ve şuraya gidin: WHM Home » Service Configuration » PHP Configuration Editor</li>
    <li>Advanced Mode seçeneğini seçin.</li>
    <li><strong>disable_functions</strong> şeklinde aratın ve karşısındaki kutucuğa <strong>ini_set</strong> ekleyin.</li>
</ol>

İşte bu kadar, bu hızlı güvenlik umarım işinize yarar.

Kolay gelsin,