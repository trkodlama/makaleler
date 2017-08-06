---
ID: 168
post_title: HTML Bilgileri
author: prodigy
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/web-tasarim-2/html-bilgileri-168.html
published: true
post_date: 2011-04-29 18:40:50
---
Html dosyalarını incelediğinizde her zaman &lt;&gt;, &lt;/&gt; gibi karakterler ve bazı terimlerle karşılaşırsınız. Bunun nedeni html bilgilerinde bu karakterler arası yazılan yazıların "TAG" olmasıdır. Örnek olarak <code>&lt;html&gt;</code>, <code>&lt;/html&gt;</code> bir tag'dır. Bu taglar arası tag ne özellik içeriyorsa o özelliği yaptırabilirsiniz.
<ul>
 	<li><code>&lt;head&gt;</code>, <code>&lt;/head&gt;</code> tagı arasında yer alan Başlık bölümüdür.</li>
 	<li><code>&lt;title&gt;</code>, <code>&lt;/title&gt;</code> tagı <code>&lt;head&gt;</code> tagı arasında bulunur ve web sitenizin başlığını bu tagın arasına yazarak belirleyebilirsiniz.</li>
 	<li><code>&lt;body&gt;</code>, <code>&lt;/body&gt;</code> tagı arasında yer alan Gövde bölümüdür.</li>
</ul>
<strong>Örnek :</strong>
<pre class="line-numbers"><code class="language-markup">&lt;html&gt;
    &lt;head&gt;
        &lt;title&gt;Trkodlama.com&lt;title&gt;
    &lt;/head&gt;
    &lt;body&gt;
        Trkodlama programcılarına ...
    &lt;/body&gt;
&lt;/html&gt;</code></pre>
Yukarıdaki örneği not defterine yazıp *.txt olarak değilde, *.html olarak kaydeder ve açarsanız sayfanın başlığının "Trkodlama.com" olduğunu ve sayfada "Trkodlama programcılarına ..." altında ise "..." yazdığını göreceksiniz.

Unutmayınız ki <strong>&lt;..&gt;</strong> açılan her tag (etiket) <strong>&lt;/..&gt;</strong> olarak kapatılmalıdır. Yani eğer bir tag başlatıyorsanız o tagı kullandıktan sonra kapatmalısınız. Aksi halde istemediğiniz görsel/şekilsel bozukluklar meydana gelebilir.

Eğer özel Türkçe karakterler kullanmak istiyorsanız web sayfanızda (ç,ı,ş,ğ,ö,ü) sayfanızın <code>&lt;head&gt;</code>, <code>&lt;/head&gt;</code> tagı içine ve en başa şu kodu yazarsınız ;
<pre class="line-numbers"><code class="language-markup">&lt;meta http-equiv="Content-Type" content="text/HTML; charset=iso-8859-9"&gt;</code></pre>
Bu kod sayesinde özel Türkçe karakterleri (ç,ı,ş,ğ,ö,ü) kullanabilirsiniz. Sunucudan gelen verileri gösteren web sayfanız tamamıyla html'dir. Asp olarak çalışır web tarayıcınıza html olarak gözükür. Bunu denemek için istediğiniz bir web sayfasını açın ve tarayıcınızda o sayfaya fare yardımıyla "Sağ Tuş" ile bir kere tıklayın. Ardından "Kaynağı Görüntüle/View Source" tıklayın ve karşınıza açılan not defterini inceleyin. Herşeyin html bilgisi olduğunu göreceksiniz.
<ul>
 	<li><code>&lt;b&gt;</code>, <code>&lt;/b&gt;</code> etiketi, arasına yazılan yazıları kalın yapar.</li>
 	<li><code>&lt;u&gt;</code>, <code>&lt;/u&gt;</code> etiketi, arasına yazılan yazıları altı-çizili yapar.</li>
 	<li><code>&lt;i&gt;</code>, <code>&lt;/i&gt;</code> etiketi, arasına yazılan yazıları italik yapar.</li>
 	<li><code>&lt;marquee&gt;</code>, <code>&lt;/marquee&gt;</code> etiketi, arasına yazılan yazıları sağdan-sola doğru kaydırır.</li>
 	<li><code>&lt;br&gt;</code> etiketi, yazınızda bir alt satıra geçmenize olanak tanır.</li>
 	<li><code>&lt;p&gt;</code>, <code>&lt;/p&gt;</code> etiketi, arasına yazılan yazının altına bir boş satır bırakır.</li>
</ul>
Aşağıda kullanabileceğiniz 6 tane başlık etiketi yer alıyor. En büyükleri <code>&lt;h1&gt;</code>, en küçükleri ise <code>&lt;h6&gt;</code>'dır.
<ul>
 	<li><code>&lt;h1&gt;</code>, <code>&lt;/h1&gt;</code> etiketi, arasına yazılan yazının html dilinde hazır en büyük yazı olmasına olanak tanır.</li>
 	<li><code>&lt;h2&gt;</code>, <code>&lt;/h2&gt;</code> etiketi, arasına yazılan yazının html dilinde <code>&lt;h1&gt;</code>'e göre biraz daha küçük olmasına olanak tanır.</li>
 	<li><code>&lt;h3&gt;</code>, <code>&lt;/h3&gt;</code> etiketi, arasına yazılan yazının html dilinde <code>&lt;h2&gt;</code>'ye göre biraz daha küçük olmasına olanak tanır.</li>
 	<li><code>&lt;h4&gt;</code>, <code>&lt;/h4&gt;</code> etiketi, arasına yazılan yazının html dilinde <code>&lt;h3&gt;</code>'e göre biraz daha küçük olmasına olanak tanır.</li>
 	<li><code>&lt;h5&gt;</code>, <code>&lt;/h5&gt;</code> etiketi, arasına yazılan yazının html dilinde <code>&lt;h4&gt;</code>'e göre biraz daha küçük olmasına olanak tanır.</li>
 	<li><code>&lt;h6&gt;</code>, <code>&lt;/h6&gt;</code> etiketi, arasına yazılan yazının html dilinde hazır en küçük yazı olmasına olanak tanır.</li>
</ul>
Bir diğerleri ise:
<ul>
 	<li><code>&lt;sup&gt;</code>, <code>&lt;/sup&gt;</code> etiketi, arasına yazılan yazının üst simge içermesine olanak tanır.</li>
 	<li><code>&lt;sub&gt;</code>, <code>&lt;/sub&gt;</code> etiketi, arasına yazılan yazının alt simge içermesine olanak tanır.</li>
 	<li><code>&lt;code&gt;</code>, <code>&lt;/code&gt;</code> etiketi, arasına yazılan yazının bilgisayar kodu biçiminde yazılmasına olanak tanır.</li>
 	<li><code>&lt;blockquote&gt;</code>, <code>&lt;/blockquote&gt;</code> etiketi, arasına yazılan yazının alıntı biçiminde yazılmasına olanak tanır.</li>
 	<li><code>&lt;font&gt;</code>, <code>&lt;/font&gt;</code> etiketi, arasına yazılan yazının her türlü özelliğinin belirlenmesine olanak tanır (renk, boyut, yazı şekli vb.). Bu özellikler <code>&lt;font color="#000000"&gt;</code> gibi yazılarak yapılır tek başına bir işe yaramaz.</li>
</ul>
Şimdilik en basitinden size aktaracaklarım bunlar. Diğer derslerde görüşürüz.