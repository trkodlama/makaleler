---
ID: 5892
post_title: >
  Bir Elemente Bootstrap Kontrolü ile
  Birden Fazla Data-Toggle Ekleme
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/web-tasarim-2/bir-elemente-bootstrap-kontrolu-ile-birden-fazla-data-toggle-ekleme-5892.html
published: true
post_date: 2016-07-04 16:24:46
---
Merhaba,

Konuya biraz daha açıklık getirmem gerekirse;

<pre class="lang:xhtml decode:true">&lt;a data-toggle="tooltip modal" data-target="#divModal" title="Detaylı bilgi için tıklayınız"&gt;+&lt;/a&gt;</pre>

Bu şekilde bir a elementi üzerinde data-toggle'a hem modal hemde tooltip tanımlayamazsınız. Bunu JavaScript kullanarak rahatlıkla halledebilirsiniz elbette. Fakat HTML kullanarak bu şekilde bir yazım hatalı olur. Bunu çok basit bir hamle çözebiliriz. a etiketimizi sarmalayan bir span etiketi ile problemimizi şöyle çözebiliriz:

<pre class="lang:xhtml decode:true ">&lt;span data-toggle="modal" data-target="#divModal"&gt;
    &lt;a data-toggle="tooltip" title="Detaylı bilgi için tıklayınız"&gt;+&lt;/a&gt;
&lt;/span&gt;</pre>

Umarım faydalı olur ve işinize yarar,

Sevgiler,