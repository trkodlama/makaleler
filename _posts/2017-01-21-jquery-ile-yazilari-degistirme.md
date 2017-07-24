---
ID: 6300
post_title: jQuery ile Yazıları Değiştirme
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/javascript/jquery-ile-yazilari-degistirme-6300.html
published: true
post_date: 2017-01-21 09:03:56
---
jQuery ile yazıları değiştirme olarak başlık attım fakat işin aslı JavaScript ile yazıları değiştirme olmalıydı. Çünkü bu işlemi yaparken <code class="prettyprint lang-javascript" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">.replace()</code> fonksiyonunu kullanacağız ki bu JavaScript fonksiyonudur.

Aslında göstereceğim işlem PHP'nin str_replace() fonksiyonuyla aynı. Bir inputun veya yazı bloğunun içinde aradığınız terimi seçtiğiniz bir başka terimle değiştirmeyi göstereceğim. Aşağıdaki örnek'te inputa girilen sayıdaki "," işaretini "." olarak güncelleyeceğiz.
<pre class="prettyprint lang-html" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;input type="text" name="fiyat" value="144,90"&gt;</pre>
<pre class="prettyprint lang-javascript" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">var fiyat = $("input[name='fiyat']").val(); // Input daki fiyat değerini aldık
var NoktaliFiyat = fiyat.replace(",", "."); // Virgülü nokta ile değiştirdik.</pre>
Bu şekilde aradığımız terimi değiştirdik. Fakat bu şekilde sadece ilk gördüğü "," işaretini "." olarak değiştirecektir. Bütün ","leri değiştirmek için düzenli ifadelerden (regular expressions) kullanmalıyız. Şöyle ki:
<pre class="prettyprint lang-javascript" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">var fiyat = $("input[name='fiyat']").val(); // Input daki fiyat değerini aldık
var NoktaliFiyat = fiyat.replace(/,/g, "."); // Virgülü nokta ile değiştirdik.</pre>
Burada <strong>/,/g </strong>yazarak bütün "," işaretlerini "." işaretine çeviriyoruz. <strong>g</strong> düzenli ifademize <strong>global</strong> özelliği ekliyor. Bu sayede tamamında arama yapılıyor.

Peki bir soru daha! Düzenli ifadelerle verdiğimiz terimi aramayı gördük fakat direk ifade yerine bir değişken kullanabilir miydik? Tabii ki evet, o da şu şekilde:
<pre class="prettyprint lang-javascript" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">var fiyat = $("input[name='fiyat']").val(); // Input daki fiyat değerini aldık
var aranan = ","; // Aranan terimi değişkende belirttik
var regex = new RegExp('{'+aranan+'}', "igm"); // Aranan terimin RexExpini oluşturduk
var NoktaliFiyat = fiyat.replace(regex, "."); // Yeni haliyle tekrar değiştirme işlemini yaptık.</pre>
Faydalı olup işinize yaraması dileğiyle, sorularınızı yorum olarak sorabilirsiniz.