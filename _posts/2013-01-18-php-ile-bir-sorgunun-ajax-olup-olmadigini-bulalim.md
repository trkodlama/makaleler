---
ID: 1450
post_title: >
  PHP ile Bir Sorgunun AJAX Olup
  Olmadığını Bulalım
author: Oral ÜNAL
post_excerpt: |
  Bu basit ve ufak ipucu sayesinde bir sayfaya gelen sorgunun AJAX sorgusu mu yoksa normal sorgu mu olup olmadığını ayırt edebileceğiz.
  
  HTML'i yazdıracağımız zaman AJAX sorgusuysa farklı, normal sorguysa farklı bir çıktı verdirmek isteyebiliriz. Bu durumlar da bu basit ipucu hayat kurtarabilir
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/php-ile-bir-sorgunun-ajax-olup-olmadigini-bulalim-1450.html
published: true
post_date: 2013-01-18 16:29:23
---
Merhaba arkadaşlar,

Uzun zamandır bir şeyler yazmadığımın farkındayım. Yazmaya fırsat bulamadığm içindir büyük ihtimalle. Lafı uzatmıyorum hemen konuya giriyorum.

Bu basit ve ufak ipucu sayesinde bir sayfaya gelen sorgunun AJAX sorgusu mu yoksa normal sorgu mu olup olmadığını ayırt edebileceğiz.

HTML'i yazdıracağımız zaman AJAX sorgusuysa farklı, normal sorguysa farklı bir çıktı verdirmek isteyebiliriz. Bu durumlar da bu basit ipucu hayat kurtarabilir:

<pre class="lang:php decode:1 " >$ajax = false;

if(!empty($_SERVER['HTTP_X_REQUESTED_WITH'])
&amp;amp;&amp;amp; strtolower($_SERVER['HTTP_X_REQUESTED_WITH']) == 'xmlhttprequest')
{
  $ajax = true;
}</pre>

Gördüğünüz gibi kullanımı da oldukça basit. Umarım işinize yarar, kolay gelsin.