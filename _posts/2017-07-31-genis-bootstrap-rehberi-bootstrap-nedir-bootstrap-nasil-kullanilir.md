---
ID: 9384
post_title: 'Geniş Bootstrap Rehberi &#8211; Bootstrap Nedir? Bootstrap Nasıl Kullanılır?'
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/web-tasarim-2/bootstrap/genis-bootstrap-rehberi-bootstrap-nedir-bootstrap-nasil-kullanilir-9384.html
published: true
post_date: 2017-07-31 17:09:20
---
Web geliştirmeye biraz olsun merakınız varsa <a href="http://getbootstrap.com/" target="_blank" rel="noopener">Bootstrap</a> kelimesini duymuşsunuz. Resmi web sitesine göre, <strong>Bootstrap, duyarlı ve mobil öncelikli web sitesi geliştirmek için kullanılan en popüler HTML, CSS ve JavaScript framework'dür</strong>. Müthiş bir açıklama ama nasıl kullanacağız?

Bu aşamada sizi <strong>Bootstrap</strong>'ın <a href="http://getbootstrap.com/getting-started/" target="_blank" rel="noopener">Getting Started</a> sayfasına yönlendirmek yapılacak en kolay iş olurdu muhtemelen. Çünkü kurulum rehberleri gerçekten çok faydalı bilgiler içeriyor - CDN linkleri, Bower, npm ve Composer ile nasıl kurulacağı, Autoprefixer ve LESS entegrasyonu, bir kaç tema, lisanslar ve tercümeler - ama en nihayetinde bu sayfa adım-adım bir başlangıç rehberi pek sayılmaz.

Bir kaç sene önce Bootstrap'ı ilk keşfettiğimde responsive tasarım şimdiki kadar popüler değildi. Resmi dökümanlarını incelerken kafam biraz karışmıştı. Şöyle ki rehberleri komponent bazında inceleyip birbirleriyle yoğurma kısmını çok kolay idrak edememiştim. Yeni başlayanlar içinde oldukça karışık bir rehber olduğunun farkındayım.

Bu rehberi Bootstrap'a yeni başlayanların anlayabileceği bir giriş rehberi niteliğinde hazırlıyorum. Yani LESS ve Sass entegrasyonuna hiç değinmeyeceğim ki bunlar orta ve ileri konseptlerdir.
<h3>Hedefler</h3>
<ul>
 	<li>Front-end framework nedir ve nasıl kullanışlı olurlar</li>
 	<li>Bootstrap CSS ve JS dosyalarını ekleyip çalışmaya başlamak</li>
</ul>
<h3>Gereksinimler</h3>
<ul>
 	<li>Temel HTML ve CSS bilgisi</li>
</ul>
<h2>Bootstrap Nedir?</h2>
Bootstrap'ı üç ana dosya olarak düşünebiliriz:
<ul>
 	<li><a href="https://github.com/twbs/bootstrap/blob/master/dist/css/bootstrap.css">bootstrap.css</a> - CSS Framework</li>
 	<li><a href="https://github.com/twbs/bootstrap/blob/master/dist/js/bootstrap.js">bootstrap.js</a> - JavaScript/jQuery Framework</li>
 	<li><a href="http://getbootstrap.com/components/#glyphicons">glyphicons</a> - İkon seti</li>
</ul>
Bunlara ek olarak Bootstrap'ın düzgün çalışması için <a href="https://jquery.com/">jQuery</a> kütüphanesine de ihtiyacı vardır. jQuery en popüler ve en yaygın olarak kullanılan JavaScript kütüphanesidir. JavaScript işlemlerinizi kolaylaştırırken her tarayıcıda düzgün çalışmasını sağlar.

Bootstrap dökümanına çalışırken bir çok şeyle - Grunt, Gulp, Sass, LESS, Bower, npm, Composer vs. - karşılabişirsiniz. Fakat bu okuduğunuz yabancı terimlerin çalışmanız için hiç bir önemi yoktur. Bunlar paket yöneticileri(package managers), kurulum yardımcıları(installation aids), dinamik css dosyası işleyicileri(preprocessors) ve görev çalıştırıcıları(task runners) dır. Bu terimler biraz kulağıma yabancı geldiği için orjinal isimlerini de yazmak istedim parantez içine. Bunların birini, bir kaçını veya hiçbirini bilmiyor musunuz? Bu hiç problem değil. Çünkü şu aşamada buna ihtiyacımız yok.
<h2>Framework kullanmak neden önemlidir? Kullanmak zorunda mıyım?</h2>
Kesinlikle framework kullanmak zorunda <em>değilsiniz</em>. Yani demek istediğim şu, duyarlı veya esnek web sitesi hazırlamanın temel mantığını anladığınız ve uygulayabildiğiniz süre bu framework'leri kullanmak zorunda değilsiniz. Fakat frameworkler oldukça popülerdir ve bir çok faydası vardı. Yani onlarla çalışmayı öğrenmek önemlidir.

Frameworkler size şöyle fayda sağlayabilir:
<ul>
 	<li>Projelerinizde aynı şeyleri tekrar tekrar yazmaktan kurtarır ki bu durum oldukça can sıkıcıdır.</li>
 	<li>Web sitesinizi çeşitli ekran boyutları için - mobil, masaüstü, tablet vs. - rahatlıkla hazırlamanıza imkan sağlar.</li>
 	<li>Geliştiriciler ve projeler arasında tasarım ve kodlamada tutarlılık sağlar.</li>
 	<li>Yeni tasarım prototiplerini rahatlıkla hazırlayabilirsiniz.</li>
 	<li>Farklı tarayıcılarda projenizin aynı göründüğünden emin olursunuz.</li>
</ul>
Günümüzde, üzerinde çalıştığınız web projeleri esnek olmalı ve başlıca tarayıcıların hepsinde aynı çalışmalıdır. Ayrıca birazcık eski versiyonları desteklemesinin kimseye bir zararı yok aksine faydası var. Bootstrap'ın gerçekten <a href="https://github.com/twbs/bootstrap">çok büyük açık kaynak geliştirici topluluğu</a> mevcut ki zaten tarayıcı farklılıkları üzerine çok zaman harcıyorlar. Bu sayede sizin bir şey yapmanıza gerek kalmıyor. Ayrıca, birden fazla kişi ile geliştirilen projelerde her geliştiricinin bildiği bir framework'ü kullanmak proje geliştirme sürecini hızlandırıp iyileştirecektir. Geliştirmekte olduğunuz projeye daha sonradan katılanların da adaptasyon sürecini kısaltacaktır.

<a href="https://getbootstrap.com/examples/grid/">Izgaralar</a> muhtemelen framework'ün en önemli özelliklerinden birisidir. Bu, tüm düzenin oluşturulduğu temeldir. Ama genel olarak Bootstrap'ın <a href="https://getbootstrap.com/css/">çekirdek CSS</a>'i formlara, tablolara, butonlara, listelere ve resimlere, tamamen çalışabilir gezinme menüleri hazırlamak gibi, yardımcı stil sınıflarını barındırır. Ki bu da müthiş bir kütüphane oluşturuyor. Ayrıca <a href="https://getbootstrap.com/javascript/">JavaScript çekirdeği</a> sayesinde çok kolaylıkla modal'lar, alert'ler, carousel'ler, popup'lar, dropdown'lar ve accordion'lar oluşturabileceksiniz.

<img class="size-full wp-image-9385" src="https://www.trkodlama.com/wp-content/uploads/2017/07/screen-shot.png" alt="Bootstrap Izgara Yapısı" width="993" height="222" />

Haydi başlayalım!
<h2>Bootstrap Kullanarak Basit Bir Tema Hazırlayalım</h2>
Bootstrap <a href="https://getbootstrap.com/getting-started/#examples">çok basit bir kaç örnekle</a> beraber geliyor. Fakat bu örnekler üzerinden kurcalayarak öğrenmek oldukça basittir. Biz de öyle yapacağız. Öncelikle Bootstrap kullanarak projemizin temelini hazırlayacağız. Daha sonra kendi stil dosyamızı ekleyerek bir şeyleri daha eğlenceli kılacağız.

İlk adım ise <a href="http://getbootstrap.com/getting-started/#download">Bootstrap'ı indir</a>mek! İndireceğiniz zip dosyasının içinde <strong>css, fonts</strong> ve <strong>js</strong> dizinleri olacaktır. Sıkıştırılmış dosyayı bir dizine çıkartın. İndirdiğiniz Bootstrap herhangi bir HTML dosya ile beraber gelmiyor fakat dökümanlarında "Hello, World!" sayfası mevcut. Bizde bunu <strong>index.html</strong> dosyamız olarak kullanacağız.
<h3>Hello, World!</h3>
<pre class="line-numbers"><code class="language-markup">&lt;!DOCTYPE html&gt;
&lt;html lang="en"&gt;
  &lt;head&gt;
    &lt;meta charset="utf-8"&gt;
    &lt;meta http-equiv="X-UA-Compatible" content="IE=edge"&gt;
    &lt;meta name="viewport" content="width=device-width, initial-scale=1"&gt;
    &lt;title&gt;Bootstrap 101 Template&lt;/title&gt;
    &lt;link href="css/bootstrap.min.css" rel="stylesheet"&gt;
    &lt;!--[if lt IE 9]&gt;
      &lt;script src="https://oss.maxcdn.com/html5shiv/3.7.2/html5shiv.min.js"&gt;&lt;/script&gt;
      &lt;script src="https://oss.maxcdn.com/respond/1.4.2/respond.min.js"&gt;&lt;/script&gt;
    &lt;![endif]--&gt;
  &lt;/head&gt;
  &lt;body&gt;
    &lt;h1&gt;Hello, world!&lt;/h1&gt;

    &lt;script src="https://ajax.googleapis.com/ajax/libs/jquery/1.11.3/jquery.min.js"&gt;&lt;/script&gt;
    &lt;script src="js/bootstrap.min.js"&gt;&lt;/script&gt;
  &lt;/body&gt;
&lt;/html&gt;</code></pre>
Başlamak için gayet makul! Temel etiketlerimizden <code>doctype</code>, <code>html</code>, <code>head</code> ve <code>body</code> mevcut. <code>meta name="viewport"</code> etiketi ise esnek tasarımımız için önemlidir - ekran boyutu ile websitenizin 1:1 ölçeğinde bir orana sahip olduğunu bildirir tarayıcıya.

Neler yapıyoruz? <code>&lt;head&gt;</code> etiketi içerisine Bootstrap css dosyamızı ekleyelim...
<pre class="line-numbers"><code class="language-markup">&lt;link href="css/bootstrap.min.css" rel="stylesheet"&gt;</code></pre>
<code>&lt;/body&gt;</code> etiketinden önce jQuery'yi ekliyoruz Google CDN'den...
<pre class="line-numbers"><code class="language-markup">&lt;script src="https://ajax.googleapis.com/ajax/libs/jquery/1.11.3/jquery.min.js"&gt;&lt;/script&gt;</code></pre>
ve jQuery'den hemen sonra Bootstrap JS dosyasını ekleyelim...
<pre class="line-numbers"><code class="language-markup">&lt;script src="js/bootstrap.min.js"&gt;&lt;/script&gt;</code></pre>
<blockquote>Bootstrap JavaScript dosyası ve genellikle sizin hazırladığınız kişisel JavaScript dosyanız dökümana jQuery'den sonra eklenmelidir. Bu örnekte jQuery'yi Google CDN servisinden çağırdık. Bu sizin sunucunuza daha az yüklenilmesini sağlayacaktır. Fakat isterseniz kendiniz <a href="https://jquery.com/download/">indirip</a> ekleyebilirsiniz.</blockquote>
İşte bu kadar! Bootstrap'a aslında kısa bir giriş yapmış olduğunuz. Muhteşem bir görünüme sahip olan bu sitenizi index.html dosyasını tarayıcıda açarak görüntüleyebilirsiniz.

<img class="aligncenter size-full wp-image-9391" src="https://www.trkodlama.com/wp-content/uploads/2017/07/Screen-Shot-2015-11-09-at-7.32.26-PM-e1501289850322.png" alt="" width="593" height="375" />

Sizce de <strong><em>harika</em></strong> görünmüyor mu? Bence gayet güzel bir çalışma oldu. Burada bırakabiliriz belki de.
<h3>Navigasyon - Menü Barı</h3>
Aslında bizim yapacağımız hiç bir şey yok. Bootstrap dökümanlarında o kadar güzel bir örnek paylaşmış ki bütün projelerimizde bu navigasyon barı temel alarak bir şeyler ortaya çıkarmak oldukça mümkün. Bootstrap <a href="http://getbootstrap.com/components/#navbar">navbar örneğini</a> biraz daha sadeleştirilmiş bir versiyonunu hazırladım. Aşağıdaki kodu <code>&lt;body&gt;</code>  etiketinden hemen sonra yapıştırın.
<pre class="line-numbers"><code class="language-markup">&lt;nav class="navbar navbar-inverse navbar-static-top"&gt;
    &lt;div class="container"&gt;
        &lt;div class="navbar-header"&gt;
            &lt;button type="button" class="navbar-toggle collapsed" data-toggle="collapse" data-target="#bs-example-navbar-collapse-1" aria-expanded="false"&gt;
                &lt;span class="sr-only"&gt;Toggle navigation&lt;/span&gt;
                &lt;span class="icon-bar"&gt;&lt;/span&gt;
                &lt;span class="icon-bar"&gt;&lt;/span&gt;
                &lt;span class="icon-bar"&gt;&lt;/span&gt;
            &lt;/button&gt;
            &lt;a class="navbar-brand" href="#"&gt;Balance Web Development&lt;/a&gt;
        &lt;/div&gt;
        &lt;div class="collapse navbar-collapse" id="bs-example-navbar-collapse-1"&gt;
            &lt;ul class="nav navbar-nav navbar-right"&gt;
                &lt;li&gt;&lt;a href="#"&gt;About&lt;/a&gt;&lt;/li&gt;
                &lt;li class="dropdown"&gt;
                    &lt;a href="#" class="dropdown-toggle" data-toggle="dropdown" role="button" aria-haspopup="true" aria-expanded="false"&gt;Services&lt;span class="caret"&gt;&lt;/span&gt;&lt;/a&gt;
                    &lt;ul class="dropdown-menu"&gt;
                        &lt;li&gt;&lt;a href="#"&gt;Design&lt;/a&gt;&lt;/li&gt;
                        &lt;li&gt;&lt;a href="#"&gt;Development&lt;/a&gt;&lt;/li&gt;
                        &lt;li&gt;&lt;a href="#"&gt;Consulting&lt;/a&gt;&lt;/li&gt;
                    &lt;/ul&gt;
                &lt;/li&gt;
                &lt;li&gt;&lt;a href="#"&gt;Contact&lt;/a&gt;&lt;/li&gt;
            &lt;/ul&gt;
        &lt;/div&gt;
    &lt;/div&gt;
&lt;/nav&gt;</code></pre>
<img class="aligncenter size-full wp-image-9393" src="https://www.trkodlama.com/wp-content/uploads/2017/07/Screen-Shot-2015-11-09-at-7.51.26-PM-e1501292553682.png" alt="" width="868" height="362" />

Çok karmaşık bir kodlamadan oluşmuş gibi görünebilir fakat o kadar da karışış değil. İlk satırda, bütün barın <code>navbar</code>  olduğunu tanımlıyorum ve <code>navbar-inverse</code>  ile koyu tema olmasını sağlıyorum daha sonra <code>navbar-static-top</code>  ile en üste sabitliyorum. Yani yapışkan bir headerımız var artık.
<pre class="line-numbers"><code class="language-markup">&lt;nav class="navbar navbar-inverse navbar-static-top"&gt;</code></pre>
<code>container</code> ise tam genişliğe sahip olan navbar'ınıza bir <code>max-width</code> tanımlar.
<pre class="line-numbers"><code class="language-markup">&lt;div class="container"&gt;</code></pre>
<code>navbar-header</code>  sınıfı ise "marka" bilgisini içerir ki buraya şirket adınızı yazabilir veya logonuzu koyabilirsiniz. Biz hayali bir teknoloji şirketi olan <strong>Balance Web Development</strong> şirketinin sitesini yapacağız.

<code>button</code>  masaüstünden erişildiğinde görünmez olacak ve mobilden erişildiğinde hamburger menüye dönüşecek (her <code>&lt;span class="icon-bar"&gt;</code>  hamburgerde bir satır olacak)
<pre class="line-numbers"><code class="language-markup">&lt;div class="navbar-header"&gt;
    &lt;button type="button" class="navbar-toggle collapsed" data-toggle="collapse" data-target="#bs-example-navbar-collapse-1" aria-expanded="false"&gt;
        &lt;span class="sr-only"&gt;Toggle navigation&lt;/span&gt;
        &lt;span class="icon-bar"&gt;&lt;/span&gt;
        &lt;span class="icon-bar"&gt;&lt;/span&gt;
        &lt;span class="icon-bar"&gt;&lt;/span&gt;
    &lt;/button&gt;
    &lt;a class="navbar-brand" href="#"&gt;Balance Web Development&lt;/a&gt;
&lt;/div&gt;</code></pre>
Geri kalan kodlar sağa yaslanmış olarak masaüstü ve mobilden erişebileceğimizi menü'yü oluşturmaktadır.
<h3>Jumbotron Header</h3>
Sayfalarınızın üst kısmında yer alan, dikkat çekici, büyük yer kaplayan bir kısımdır ve <em>Bootstrap</em> bu alana <strong>Jumbotron</strong> ismini vermektedir. Bununla ilgili dikkate değer pek bir şey bulunmamakta. <code>jumbotron</code> içerisinde <code>container</code> oluşturarak hazırlayabilirsiniz.
<pre class="line-numbers"><code class="language-markup">&lt;div class="jumbotron"&gt;
	&lt;div class="container"&gt;
		&lt;h1&gt;Ready. Set. Code.&lt;/h1&gt;
		&lt;p&gt;Are you ready to boilerstrap your cross-compatible buzzword? We're Sassy, flat and semantic, so what are you waiting for?&lt;/p&gt;
		&lt;br&gt;
		&lt;p&gt;&lt;a class="btn btn-primary btn-lg" href="#" role="button"&gt;Download Free Trial »&lt;/a&gt; &lt;a class="btn btn-primary btn-lg" href="#" role="button"&gt;Learn more »&lt;/a&gt;&lt;/p&gt;
	&lt;/div&gt;
&lt;/div&gt;</code></pre>
Burada bazı istemediğiniz boşluklar mevcut olabilir. Fakat esas vurgulamak istediğim nokta herhangi bir stil düzenlemesi yapmadan Bootstrap'ın bize ne kadar çok fayda sağladığını görmenizi istiyorum. Tek satır CSS yazmadan esnek bir temaya doğru gidiyoruz adım adım.

<img class="aligncenter size-full wp-image-9898" src="https://www.trkodlama.com/wp-content/uploads/2017/07/Screen-Shot-2015-11-09-at-8.36.49-PM-e1501506383690.png" alt="" width="864" height="619" />
<h3>Izgara veya Grid</h3>
Yapacağım son şeyse biraz içerik kısımları eklemek olacak ki bunu ızgara formunda hazırlayacağız. Izgara dediğim olay aslında satırlar. Fakat blok halinde satırlar. Bunu örneklerle biraz daha net anlayabileceğiz.
<pre class="line-numbers"><code class="language-markup">&lt;div class="row"&gt;
&lt;/div&gt;</code></pre>
ile bir satır tanımladık ki bu da kolonlardan oluşacak.
<pre class="line-numbers"><code class="language-markup">&lt;div class="row"&gt;
  &lt;div class="col-md-6"&gt;&lt;/div&gt;
  &lt;div class="col-md-6"&gt;&lt;/div&gt;
&lt;/div&gt;</code></pre>
&nbsp;

<strong><em>Bootstrap</em></strong> 12-kolondan oluşan bir sistemle çalışıyor. Yan yana 12 kolon mantığıyla çalışır. Ekran çözünürlüğünüz ne olursa olsun 12-kolon sistemi şaşmayacak. Yukarıdaki örneği incelediğinizde %50 genişliğe sahip iki kolon görmelisiniz. Çünkü 12-kolon sisteminde kolonlardan biri 6 kolonluk diğeri de 6 kolonluk. Fakat mobilden bakıldığında her biri %100 genişliğe sahip olacak. Buna sonra değineceğiz.
<pre class="line-numbers"><code class="language-markup">&lt;div class="container"&gt;
	&lt;div class="row"&gt;
		&lt;div class="col-md-4"&gt;
			&lt;span class="glyphicon glyphicon-cloud" aria-hidden="true"&gt;&lt;/span&gt;
			&lt;h3&gt;Cloud Computable&lt;/h3&gt;
			&lt;p&gt;Donec id elit non mi porta gravida at eget metus. Fusce dapibus, tellus ac cursus commodo, tortor mauris condimentum nibh.&lt;/p&gt;
		&lt;/div&gt;
		&lt;div class="col-md-4"&gt;
			&lt;span class="glyphicon glyphicon-floppy-disk" aria-hidden="true"&gt;&lt;/span&gt;
			&lt;h3&gt;Backwards Compatible&lt;/h3&gt;
			&lt;p&gt;Etiam porta sem malesuada magna mollis euismod. Donec sed odio dui. Lorem ipsum dolor.&lt;/p&gt;
		&lt;/div&gt;
		&lt;div class="col-md-4"&gt;
			&lt;span class="glyphicon glyphicon-console" aria-hidden="true"&gt;&lt;/span&gt;
			&lt;h3&gt;GUI Free&lt;/h3&gt;
			&lt;p&gt;Vestibulum id ligula porta felis euismod semper. Fusce dapibus, tellus ac cursus commodo, tortor mauris condimentum nibh.&lt;/p&gt;
		&lt;/div&gt;
	&lt;/div&gt;
&lt;/div&gt;</code></pre>
Bu örnekte de görebileceğiniz 3 adet 4/12'lik kolonumuz mevcut. Yani her <code>col-md-4</code> ifadesinde sayıları topladığımızda 12 elde ediyoruz (3x4=12). 3 kolondan oluşan 1 satır. Herşey güzel çalışıyor.
<h3>İkonlar</h3>
Yukarıdaki örneği dekorasyon amacıyla bir kaç tane <a href="http://getbootstrap.com/components/#glyphicons">glyphicons</a> ekledim. <strong>Glyphicons</strong>, Bootstrap ile beraber gelen ikon setidir. İndirmiş olduğunuz Bootstrap dosyasının içinde fonts dizininde bu ikonların dosyalarını görüntüleyebilirsiniz. O dosyaları yüklemezseniz veya konumlarını değiştirirseniz bu ikonlar çalışmayacaktır.
<pre class="line-numbers"><code class="language-markup">&lt;span class="glyphicon glyphicon-floppy-disk" aria-hidden="true"&gt;&lt;/span&gt;</code></pre>
glyphicon kullanmak için yukarıdaki kodu bilmeniz yeterlidir. Bu kodu eklediğiniz yerde ikonları rahatlıkla görebilirsiniz. Değişen tek kısım <code>glyphicon-floppy-disk</code> dir. Ki bu da kullanacağınız ikonu seçmenizi sağlar.

Ortaya artık bir tema çıkmaya başlamadı mı sizce de?

<img class="aligncenter size-large wp-image-9899" src="https://www.trkodlama.com/wp-content/uploads/2017/07/Screen-Shot-2015-11-09-at-9.21.20-PM-e1501507264271-1024x627.png" alt="" width="660" height="404" />
<h2>Bootstrap'ı Biraz Kişiselleştirelim</h2>
Tek satır CSS kodlamadan bu şekilde bir site oluşturmak hiç de kötü sayılmaz. Ayrıca bu siteniz şu anda profesyonel, esnek ve tarayıcı dostu. Yaratıcı veya eşi benzer bir tasarım olmayabilir fakat oldukça başarılı! Hazırlamak istediğimiz temanın iskeletini oluşturduk fakat şimdi onu kişiselleştirip renkledirip, yani bize özgü olmasını sağlayalım.

Eğer LESS veya Sass biliyorsunuz "<a href="http://getbootstrap.com/customize/" target="_blank" rel="noopener">Bootstrap’s extensive customization area</a>" adresine gidebilir  ve kendi Bootstrap versiyonunuzu indirebilirsiniz. Biz bu rehberin devamında "vanilla CSS" kullanacağız ki bunun için önişlemci(preprocessor) ihtiyacımız olmayacak. Bootstrap CSS dosyasından sonra kendi CSS dosyamızı ekleyerek kendi temamızı oluşturmaya başlıyoruz.
<blockquote>Bootstrap dosyalarına asla müdahale etmeyin! Unutmayın ki müdahale etmek istediğiniz sınıfları(class) ayrıca eklediğiniz CSS dosyanız aracılığıyla değiştirebilirsiniz!</blockquote>
<pre class="line-numbers"><code class="language-markup">&lt;link href="css/bootstrap.min.css" rel="stylesheet"&gt;
&lt;link href="css/custom.css" rel="stylesheet"&gt;
&lt;link href='https://fonts.googleapis.com/css?family=Montserrat:400,700' rel='stylesheet' type='text/css'&gt;</code></pre>
Yukarıda farketmişsiniz bir de link ekledim ki bu link Google Font'larından Montserrat isimli fontu bizim için yükleyecektir. Bu şekilde Google Font yüklediğinizde tek yapmanız gereken Google'dan aldığınız <code>&lt;link href="..." rel="stylesheet" type="text/css"&gt;</code> kodu html kodunuzun <code>head</code> kısmına ekleyin ve font kullanmak istediğiniz elemanın <code>font-family</code> değerini güncelleyin.

Artık stilimizi oluşturamaya başlayalım. Bir kaç dakika içerisinde sıradan ve sıkıcı Bootstrap temasını sevebileceğiniz bir hale getireceğim. Öncelikle navigasyon ile jumbotron arasında rahatsız edici boşluktan kuruluyorum.
<pre class="line-numbers"><code class="language-css">.navbar {
	margin-bottom: 0;
}</code></pre>
Ana etiketlere bir kaç basit stil tanımlayalım. Ayrıca Montserrat fontunu tüm sayfamda kullanmak istiyorum, başlıkları kalın yapıyorum ve arkaplanı koyu hazırlarken metinleri açık yazdırıyorum:

<pre class="line-numbers"><code class="language-css">body {
	background: #3E4649;
	color: #f7f7f7;
	font-family: 'Montserrat', sans-serif;
}
h1,
h2 {
	font-weight: bold;
}
p {
	font-size: 16px;
	color: #cdcdcd;
}</code></pre>
Jumbotronu yeşil renkte ve metni ortalanmış olarak değiştireceğimz.
<pre class="line-numbers"><code class="language-css">.jumbotron {
	background: #27A967;
	color: white;
	text-align: center;
}
.jumbotron p {
	color: white;
	font-size: 26px;
}</code></pre>
Şimdi butonları "hayalet buton" olarak değiştireceğim ki hayalet butonlar transparan butonlardır ve çerçeveleri(borders) vardır. Ayrıca biraz margin tanımlayacağım mobilde de düzgün bir şekilde yerleşmiş olsunlar.
<pre class="line-numbers"><code class="language-css">.btn-primary {
	color: #fff;
	background-color: transparent;
	border-color: white;
	margin-bottom: 5px;
}
.btn-primary:hover {
	color: #27A967;
	background-color: white;
	border-color: white;
}</code></pre>
Navigasyonu ise farklı bir koyu tonda ve linkleri ise daha açık olacak şekilde ayarlayacağım. Ayrıca linklerin üzerine gelindiğinde arka fonun değişmesini istiyorum.
<pre class="line-numbers"><code class="language-css">.navbar-inverse {
	background: #2E2F31;
	border: 0;
}
.navbar-inverse .navbar-nav li a {
	color: #f7f7f7;
	font-size: 16px;
}
.navbar-inverse .navbar-nav li a:hover {
	background: #27A967;
}</code></pre>
Dropdown yani açılır menülerin kendine ait ayrı sınıfları mevcut. Bunları da güncelleyip biraz boşluk vereceğim.
<pre class="line-numbers"><code class="language-css">.dropdown-menu {
	background: #2E2F31;
	border-radius: 0;
	border: 0;
}
.dropdown-menu li a {
	padding: 10px;
}
.navbar-inverse .navbar-nav .dropdown-menu li a:hover {
	background: #2C463C;
}</code></pre>
HTML dosyamızda ise en son hazırlamış olduğumuz ızgaramızı bir <code>&lt;section&gt;</code> etiketi içine almak istiyorum. Bu etikete de <code>call-to-action</code> isminde sınıf atamak istiyorum. Ayrıca glyphicon'ları tanımladığımız <code>span</code> etiketine <code>glyphicon-large</code> isminde sınıf tanımlamak istiyorum.
<pre class="line-numbers"><code class="language-markup">&lt;section class="call-to-action"&gt;
&lt;!-- .satirlar ve .kolonlar --&gt;
  &lt;span class="glyphicon glyphicon-cloud glyphicon-large" aria-hidden="true"&gt;&lt;/span&gt;
&lt;!-- /.satirlar ve .kolonlar --&gt;
&lt;/section&gt;</code></pre>
Kodumuza son dokunuşumda call-to-action içerisindeki metinlerimizi ortalamak ve p etiketlerine bir miktar margin-bottom vermek olacak. Boşluk bırakmamın sebebi mobilde daha düzgün görünmesini sağlamak. Ayrıca glyphicons ikonlarımı biraz daha büyütmek istiyorum.
<pre class="line-numbers"><code class="language-css">.call-to-action {
	text-align: center;
}
.call-to-action p {
	margin-bottom: 30px;
	font-family: sans-serif;
}
.glyphicon-large {
	font-size: 100px;
}</code></pre>
<img class="aligncenter size-large wp-image-9900" src="https://www.trkodlama.com/wp-content/uploads/2017/07/Screen-Shot-2015-11-09-at-10.22.22-PM-e1501509179428-1024x647.png" alt="" width="660" height="417" />

Çok az bir kodlamayla basit bir web sayfası oluşturduk. Basit demem aldatıcı olmasın, oldukça profesyone bir sayfa oldu.

Ayrıca bu kodları Codepen üzerinden de erişebilirsiniz elbette. Canlı Codepen görüntüsü de aşağıdadır:
<p class="codepen" data-height="265" data-theme-id="0" data-slug-hash="ZJWWZw" data-default-tab="result" data-user="oralunal" data-embed-version="2" data-pen-title="Start Bootstrap">See the Pen <a href="https://codepen.io/oralunal/pen/ZJWWZw/">Start Bootstrap</a> by Oral ÜNAL (<a href="https://codepen.io/oralunal">@oralunal</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://production-assets.codepen.io/assets/embed/ei.js"></script>
<h2>Sonuç</h2>
Umarım biraz da olsa Bootstrap öğrenmenize yardımcı olabilmişimdir. Bu rehberi sıfırdan hazırlamadım, <a href="https://www.taniarascia.com/what-is-bootstrap-and-how-do-i-use-it/" target="_blank" rel="noopener">Tania Rascia</a>'nın hazırlamış olduğu rehberi tercüme ettim. Bazı kısımlarda kendi yorumumu dahil ettim.

Bootstrap rehberinin karmaşıklığını bu rehber ile atlatıp sonrasında kendi Bootstrap temanızı rahatlıkla hazırlayabileceğinize inanıyorum.

Sevgilerimle,