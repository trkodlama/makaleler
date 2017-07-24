---
ID: 118
post_title: CSS ile Nasıl Başlık Tasarlanır
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/css-ile-nasil-baslik-tasarlanir-118.html
published: true
post_date: 2011-03-17 16:03:35
---
Başlıklar bir web sitesinin olmazsa olmazlarıdır. Bu nedenle herhangi bir sayfanızda en az bir tane başlık kullanmalısınız, bu sayede ziyaretçilerinizin o anda neyi okuduğunu bilmesini sağlarsınız. HTML size 6 tane önce de hazırlanmış başlık etiketi imkanı sunuyor. Fakat incelediğim birçok web sayfası başlıkları şu şekilde belirliyor:
<pre class="lang:html decode:1 " >&amp;lt;div id=&amp;quot;baslik&amp;quot; class=&amp;quot;baslik&amp;quot;&amp;gt;İşte Burası Başlığım&amp;lt;/div&amp;gt;</pre>
Bu şekilde baslik ID'si ve baslik class'ı ile isteği sonucu üretiyor. Fakat h1 etiketi kullanmıyor:
<h1>oldukça büyük, kalın ve çirkin</h1>  
Elbette eğer siz h1 etiketlerine stil vermezseniz haliyle büyük, kalın ve çirkin görünecektir. Halbuki div'i stillendireceğiniz h1'i stillendirmeniz daha mantıklı. En azından SEO açısından. Web sayfalarınızda bir tane h1 etiketi arama motoru botlarının dikkatini çok fazla çeker. Fakat bir tanesi de yeterlidir.

<strong>Neden DIV yerine Başlık Etiketini Kullanalım</strong>
<ul>
	<li>Arama motorları başlık etiketini severler</li>
	<li>Başlıklarınız için hangi class'ı kullandığınızı hatırlamak zorunda kalmazsınız</li>
	<li>Sağlam bir sayfa düzeni için idealdir.</li>
	<li>Stiller kapalı olduğunda bile neyin ne olduğu anlaşılabilir</li>
</ul>

<strong>Başlıklarınıza Stil Oluşturalım</strong>
Başlık etiketlerinizi "büyük, kalın ve çirkin" olmaktan kurtarmak için öncelikle nasıl görünmesini istiyorsak o şekilde stillendirelim. Bu nedenle bir web sitesi üzerinde çalıştığım zaman öncelikle paragraf, h1, h2 ve h3 stillerini belirlerim. Örneğin yeni bir sitenizin stil dosyası başlangıçta bu olabilir:
<pre class="lang:css decode:1 " >body, html { margin: 0; padding: 0; }  
p { font: 1em Arial, Geneva, Helvetica, sans-serif; }  
h1 { font: bold 2em &amp;quot;Times New Roman&amp;quot;, Times, serif; }  
h2 { font: bold 1.5em &amp;quot;Times New Roman&amp;quot;, Times, serif; }  
h3 { font: bold 1.2em Arial, Geneva, Helvetica, sans-serif; } </pre>
Bundan sonraki adımda başlık etiketinizin font türünü ve font rengini düzenleyin. Bu sayede sayfa yapınıza biraz daha uygun hale gelecektir.
<pre class="lang:css decode:1 " >h1 {  
font: bold italic 2em/1em &amp;quot;Times New Roman&amp;quot;, &amp;quot;MS Serif&amp;quot;, &amp;quot;New York&amp;quot;, serif;  
margin: 0;  
padding: 0;  
color: #e7ce00;  
}</pre>

<strong>Çerçeveler Başlıklarınızı Çıplaklıktan Kurtarır</strong>
Çerçeveler başlıklarınızı geliştirmek için muhteşem bir yoldur. Fakat her başlığınızda çerçeve olmasına da gerek yoktur. Önemli olan sitenizle uyum içinde olmasıdır.
<pre class="lang:css decode:1 " >h1 {  
font: bold italic 2em/1em &amp;quot;Times New Roman&amp;quot;, &amp;quot;MS Serif&amp;quot;, &amp;quot;New York&amp;quot;, serif;  
margin: 0;  
padding: 0;  
color: #e7ce00;  
border-top: solid #e7ce00 medium;  
border-bottom: dotted #e7ce00 thin;  
width: 600px;  
} </pre>
Yukarıdaki örnekte başlığın üstüne düz bir çizgi altına ise noktlar kümesinden oluşan bir çizgi ekledim.

<strong>Başlığınıza bir arka plan resmi eklmek çok şık bir görüntü katabilir</strong>
Birçok web sitesinin üst kısmnıda başlık kısmı yer alır. Genellikle site başlığı ve grafik. Birçok tasarımcı bunları iki farklı element olarak ele alır  ve o şekilde hazırlar. Neden siz de öyle yapasınız ki? Şimdi başlığımızın arkasına bir de resim yerleştirelim:
<pre class="lang:css decode:1 " >h1 {  
font: bold italic 3em/1em &amp;quot;Times New Roman&amp;quot;, &amp;quot;MS Serif&amp;quot;, &amp;quot;New York&amp;quot;, serif;  
background: #fff url(&amp;quot;baslik_arka.jpg&amp;quot;) repeat-x bottom;  
padding: 0.5em 0 90px 0;  
text-align: center;  
margin: 0;  
border-bottom: solid #e7ce00 0.25em;  
color: #e7ce00;  
} </pre>
Hayalim de eklediğim resmin yüksekliği 90px idi. O nedenle padding: 0.5em 0 90px 0; yaptım. Bu sayede alttan 90 piksellik padding verdim. Daha farklı yöntemlerde var. Line-height, margin gibi.

Umarım anlatabilmişimdir.

Kolay gelsin