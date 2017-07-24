---
ID: 168
post_title: HTML Bilgileri
author: prodigy
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/html-bilgileri-168.html
published: true
post_date: 2011-04-29 18:40:50
---
Html dosyalarını incelediğinizde her zaman &lt;&gt;, &lt;/&gt; gibi karakterler ve bazı terimlerle karşılaşırsınız. Bunun nedeni html bilgilerinde bu karakterler arası yazılan yazıların "TAG" olmasıdır. Örnek olarak &lt;html&gt;, &lt;/html&gt; bir tag'dır. Bu taglar arası tag ne özellik içeriyorsa o özelliği yaptırabilirsiniz.

&lt;head&gt;, &lt;/head&gt; tagı arasında yer alan Başlık bölümüdür.
&lt;title&gt;, &lt;/title&gt; tagı &lt;head&gt; tagı arasında bulunur ve web sitenizin başlığını bu tagın arasına yazarak belirleyebilirsiniz.
&lt;body&gt;, &lt;/body&gt; tagı arasında yer alan Gövde bölümüdür.

<strong>Örnek :</strong>

<pre class="lang:html decode:1 " >&amp;lt;html&amp;gt;
&amp;lt;head&amp;gt;
&amp;lt;title&amp;gt;Trkodlama.com&amp;lt;/title&amp;gt;
&amp;lt;/head&amp;gt;
&amp;lt;body&amp;gt;
Trkodlama programcılarına ...
&amp;lt;/body&amp;gt;
&amp;lt;/html&amp;gt;</pre>

Yukarıdaki örneği not defterine yazıp *.txt olarak değilde, *.html olarak kaydeder ve açarsanız sayfanın başlığının "Trkodlama.com" olduğunu ve sayfada "Trkodlama programcılarına ..." altında ise "..." yazdığını göreceksiniz.

Unutmayınız ki &lt;..&gt; açılan her tag (etiket) &lt;/..&gt; olarak kapatılmalıdır. Yani eğer bir tag başlatıyorsanız o tagı kullandıktan sonra kapatmalısınız. Aksi halde istemediğiniz görsel/şekilsel bozukluklar meydana gelebilir.

Eğer özel Türkçe karakterler kullanmak istiyorsanız web sayfanızda (ç,ı,ş,ğ,ö,ü) sayfanızın &lt;head&gt;, &lt;/head&gt; tagı içine ve en başa şu kodu yazarsınız ;

<pre class="lang:html decode:1 " >&amp;lt;meta http-equiv=&amp;quot;Content-Type&amp;quot; content=&amp;quot;text/HTML; charset=iso-8859-9&amp;quot;&amp;gt;</pre>

Bu kod sayesinde özel Türkçe karakterleri (ç,ı,ş,ğ,ö,ü) kullanabilirsiniz. Sunucudan gelen verileri gösteren web sayfanız tamamıyla html'dir. Asp olarak çalışır web tarayıcınıza html olarak gözükür. Bunu denemek için istediğiniz bir web sayfasını açın ve tarayıcınızda o sayfaya fare yardımıyla "Sağ Tuş" ile bir kere tıklayın. Ardından "Kaynağı Görüntüle/View Source" tıklayın ve karşınıza açılan not defterini inceleyin. Herşeyin html bilgisi olduğunu göreceksiniz.

&lt;b&gt;, &lt;/b&gt; tagı, arasına yazılan yazıları kalın yapar.
&lt;u&gt;, &lt;/u&gt; tagı, arasına yazılan yazıları altı-çizili yapar.
&lt;i&gt;, &lt;/i&gt; tagı, arasına yazılan yazıları italik yapar.
&lt;marquee&gt;, &lt;/marquee&gt; tagı, arasına yazılan yazıları sağdan-sola doğru kaydırır.
&lt;br&gt; tagı, yazınızda bir alt satıra geçmenize olanak tanır.
&lt;p&gt;, &lt;/p&gt; tagı, arasına yazılan yazının altına bir boş satır bırakır.

Aşağıda kullanabileceğiniz 6 tane başlık tagı yer alıyor. En büyükleri &lt;h1&gt;, en küçükleri ise &lt;h6&gt;'dır.

&lt;h1&gt;, &lt;/h1&gt; tagı, arasına yazılan yazının html dilinde hazır en büyük yazı olmasına olanak tanır.
&lt;h2&gt;, &lt;/h2&gt; tagı, arasına yazılan yazının html dilinde &lt;h1&gt;'e göre biraz daha küçük olmasına olanak tanır.
&lt;h3&gt;, &lt;/h3&gt; tagı, arasına yazılan yazının html dilinde &lt;h2&gt;'ye göre biraz daha küçük olmasına olanak tanır.
&lt;h4&gt;, &lt;/h4&gt; tagı, arasına yazılan yazının html dilinde &lt;h3&gt;'e göre biraz daha küçük olmasına olanak tanır.
&lt;h5&gt;, &lt;/h5&gt; tagı, arasına yazılan yazının html dilinde &lt;h4&gt;'e göre biraz daha küçük olmasına olanak tanır.
&lt;h6&gt;, &lt;/h6&gt; tagı, arasına yazılan yazının html dilinde hazır en küçük yazı olmasına olanak tanır.

&lt;sup&gt;, &lt;/sup&gt; tagı, arasına yazılan yazının üst simge içermesine olanak tanır.
&lt;sub&gt;, &lt;/sub&gt; tagı, arasına yazılan yazının alt simge içermesine olanak tanır.
&lt;code&gt;, &lt;/code&gt; tagı, arasına yazılan yazının bilgisayar kodu biçiminde yazılmasına olanak tanır.
&lt;blockquote&gt;, &lt;/blockquote&gt; tagı, arasına yazılan yazının alıntı biçiminde yazılmasına olanak tanır.
&lt;font&gt;, &lt;/font&gt; tagı, arasına yazılan yazının her türlü özelliğinin belirlenmesine olanak tanır (renk, boyut, yazı şekli vb.). Bu özellikler &lt;font color="#000000"&gt; gibi yazılarak yapılır tek başına bir işe yaramaz.

Şimdilik en basitinden size aktaracaklarım bunlar. Diğer derslerde görüşürüz.