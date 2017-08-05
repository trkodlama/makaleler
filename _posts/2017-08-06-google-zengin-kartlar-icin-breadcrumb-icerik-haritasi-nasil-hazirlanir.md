---
ID: 9934
post_title: >
  Google Zengin Kartlar için Breadcrumb
  (İçerik Haritası) Nasıl
  Hazırlanır?
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/web-tasarim-2/google-zengin-kartlar-icin-breadcrumb-icerik-haritasi-nasil-hazirlanir-9934.html
published: true
post_date: 2017-08-06 01:49:23
---
Yazının detaylarına inmeden önce <strong>Breadcrumb</strong> nedir ona değinmek istiyorum. Ayrıca Türkçe tanımını da belirtmek gerekirse "İçerik Haritası" demek yanlış olmaz. Aslında <em>Google Translate</em> ile bunu söylüyorum. Çünkü ingilizcede <strong>bread</strong> ekmek, <strong>crumb</strong> da kırıntı demek. Mantık olarak düşünürsek içinde bulunduğumuz sayfaya nasıl geldiğimizi ekmek kırıntılarıyla anlamamızı sağlıyor. Yani içeriğe doğru uzanan kaç seviye olduğunu bilmemizi sağlıyor. Bir masal vardı, <em>Hansel &amp; Gratel</em> masalın adı ama içeriğini hatırlamıyorum, birisi kaçırılan diğerini ekmek kırıntılarını takip ederek buluyordu. Temeli buna dayanıyor.
<h2>Breadcrumb Nedir?</h2>
Daha detaylı ve teknik olarak breadcrumb nediri anlatıp neden kullanıldığına değinmek istiyorum. Breadcrumb aslında sayfa işaretleri yolu'dur. Breadcrumblar ziyaretçilerinize ve Google'a internet sitenizin hangi sayfasında olduklarını ve bu sayfanın sitenizin hiyerarşik düzeninin neresinde olduğunu gösterir. Bu içerik haritaları, sayfa erişme metodunuza bağlı olarak değişmez. Örneğin bu makaleye direk Google'dan geldiğinizde veya anasayfadan görüp tıklayarak geldiğiniz veya arama formumuzu kullanarak bulduğunuzda göreceğiniz içerik haritası "Web Tasarım &gt; SEO" olacaktır. Bu sayede bu makalenin Web Tasarım ana kategorisine ait olduğunu ve ayrıca Web Tasarım kategorisinin SEO alt kategorisinde bulunduğunu rahatlıkla anlayabileceksiniz. Bu makale ilginizi çekmeye başladıysa bu içerik haritalarından SEO linkine tıklarak daha fazla SEO kategorisinde makale okuyabilirsiniz ki bu da içerik haritalarının en önemli özelliğidir bence. Özelliklerini kısaca listelemek gerekirse (<a href="https://zeo.org/tr/blog/breadcrumb-seo-iliskisi/">kaynak</a>):
<ol>
 	<li>Ziyaretçilerin web sitenizin düzenini daha iyi anlamasını sağlar, bir üst kategoriye dönmeleri veya benzer sayfalar arasında gezinmeleri kolaylaşır,</li>
 	<li>Kullanıcıların sayfalar arasında gezinme hızını artırır,</li>
 	<li>Az yer kapladıkları için, bu yapıdan faydalanmamayı tercih eden kullanıcıları rahatsız etme ihtimali yoktur,</li>
 	<li>Anlaşılması kolaydır, kullanıcılar bu sistemi kullanmakta zorlanmazlar,</li>
 	<li>Web sitenizi tanımadan dışarıdan bir link ile gelen ziyaretçiler, bu yapı sayesinde sayfalar arasında kolayca gezinebilir.</li>
</ol>
<h2>Breadcrumb ve SEO İlişkisi</h2>
Kullanıcı deneyimini iyileştirmesinin yanısıra Arama Motorları Optimizasyonu içinde faydalıdır. Nasıl mı? Google web sitelerinizi dizine eklediğinde içerik sayfalarınızın değerinin artmasını sağlar. Bu sayede üst seviye kategori sayfalarıyla içerik sayfanız arasında bir değer farkı ortaya çıkar. Ayrıca arama sonuçların web adresiniz listelenirken Breadcrumb'a önem vermeyenlerden daha farklı görünmek sizi bir adım daha tıklanmaya teşvik edecektir.

Kısacası Breadcrumb sayesinde arama motorları sitenizdeki hiyerarşiyi algılayabilecektir. Ayrıca breadcrumb'ınıza <a href="http://schema.org/"><strong>Schema</strong></a> parametreleri ekleyerek daha şık bir görünüme kavuşabilirsiniz.
<h2>Google Zengin Kartlar için Breadcrumb Nasıl Oluşturulur?</h2>
Aslında bu konu için Google bir <a href="https://developers.google.com/search/docs/data-types/breadcrumbs">sayfa</a> hazırlamış. Dilerseniz oradan devam edebilirsiniz. Dilerseniz de buradan devam edebiliriz. Breadcrumb örneklerini gösterirken kodlarımı <a href="https://www.trkodlama.com/kategori/web-tasarim-2/bootstrap">Bootstrap4</a> kullanarak hazırlayacağım. Bootstrap ne demek bilmiyorsanız <a href="https://www.trkodlama.com/web-tasarim-2/genis-bootstrap-rehberi-bootstrap-nedir-bootstrap-nasil-kullanilir-9384.html">Bootstrap Rehberi</a>ni okumanızı tavsiye ederim. Aşağıdaki gibi bir içerik haritamız olduğunu düşünün:
<pre class="line-numbers"><code class="language-markup">&lt;ol class="breadcrumb"&gt;
	&lt;li class="breadcrumb-item"&gt;&lt;a href="//www.trkodlama.com"&gt;Anasayfa&lt;/a&gt;&lt;/li&gt;
	&lt;li class="breadcrumb-item"&gt;&lt;a href="//www.trkodlama.com/kategori/makaleler"&gt;Kodlama&lt;/a&gt;&lt;/li&gt;
	&lt;li class="breadcrumb-item active"&gt;İçerik Sayfası Başlığı&lt;/li&gt;
&lt;/ol&gt;</code></pre>
Oldukça basit değil mi? İçerik haritamız hazır fakat Google hala arama sonunçlarında bizi istediğimiz gibi listelemiyor. Bunun sebebi Google Zengin Kartlar özelliğinden henüz faydalanmadık. Google zengin kartlardan faydalanmak için içerik haritamızı <a href="http://schema.org/BreadcrumbList">Schema Breadcrumbs</a>'a uygun olarak güncellemeliyiz. Kodumuzun güncellenmiş hali aşağıdaki gibidir:
<pre class="line-numbers"><code class="language-markup">&lt;ol class="breadcrumb" itemscope itemtype="http://schema.org/BreadcrumbList"&gt;
	&lt;li class="breadcrumb-item" itemprop="itemListElement" itemscope itemtype="http://schema.org/ListItem"&gt;
		&lt;a itemprop="item" href="//www.trkodlama.com"&gt;
			&lt;span itemprop="name"&gt;Anasayfa&lt;/span&gt;
			&lt;meta itemprop="position" content="1" /&gt;
		&lt;/a&gt;
	&lt;/li&gt;
	&lt;li class="breadcrumb-item" itemprop="itemListElement" itemscope itemtype="http://schema.org/ListItem"&gt;
		&lt;a itemprop="item" href="//www.trkodlama.com/kategori/makaleler"&gt;
			&lt;span itemprop="name"&gt;Kodlama&lt;/span&gt;
			&lt;meta itemprop="position" content="2" /&gt;
		&lt;/a&gt;
	&lt;/li&gt;
	&lt;li class="breadcrumb-item active" itemprop="itemListElement" itemscope itemtype="http://schema.org/ListItem"&gt;
		&lt;span itemprop="name"&gt;İçerik Sayfası Başlığı&lt;/span&gt;
		&lt;meta itemprop="position" content="3" /&gt;
	&lt;/li&gt;
&lt;/ol&gt;</code></pre>
HTML kodumuz oldukça büyümüş gibi görünebilir ama aynı şeyleri tekrar tekrar yazdırıyoruz sadece. Bu şekilde içerik haritalarınızı oluşturursanız Google arama sonuçlarında web sitenizi şu şekilde gösterecektir:

<img class="aligncenter size-full wp-image-9935" src="https://www.trkodlama.com/wp-content/uploads/2017/08/breadcrumbs01.png" alt="" width="762" height="672" />

Artık sizinde web siteniz bu şekilde gösterilmeye başlayacak. Rakiplerinizden bir adım daha önce geçtiğiniz için sizi tebrik ederim.

Sorularınızı yorum olarak sormaktan çekinmeyin lütfen.

&nbsp;