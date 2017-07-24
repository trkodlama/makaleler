---
ID: 9149
post_title: >
  WordPress Temalarınızın Menülerini
  Mobil Uyumlu Hale Getirin
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/wordpress/wordpress-temalarinizin-menulerini-mobil-uyumlu-hale-getirme-9149.html
published: true
post_date: 2017-02-11 03:36:36
---
Websitenizin mobil cihazlarda iyi görünmesi ve düzgün çalışması artık isteğe bağlı bir durum olmaktan çıktı. 2017'nin başından beri bakılırsa internet trafiğinin %68'ini mobil cihazlar oluşturuyor. Ayrıca websitenizin mobil için optimizasyonu SEO skorunuzu doğrudan etkiler. Eğer arama motorlarındaki konumlarınızı kaybetmek istemiyorsanız kesinlikle mobil optimizasyona önem vermelisiniz.

Günümüzde hazırlanan ücretli veya ücretsiz hazır temaların çoğu uyumlu tasarımdır. Yani hem bilgisayarlardan hem mobil cihazlardan düzgün görünmek üzere hazırlanmıştır. Fakat kendi temasını kendileri yazanlar uyumlu tasarımlar ortaya çıkarmak için devamlı pratik çözüm arayışı içindeler.

Bugün sizlere WordPress temanızın menüsünü nasıl uyumlu tasarım için uygun bir hale getireceğinizi anlatıyorum. Birazcık kod düzenleme ve FTP ile dosya indirip yüklemeye aşinaysanız kolaylıkla bu işlemi uygulayabilirsiniz. Hadi başlayalım!

<strong>Nelere İhtiyacınız Var</strong>
<ul>
 	<li><strong>WordPress Teması</strong> – Tabii ki öncelikle bir WordPress temanız olmalı. Yeni geliştiriyor da olabilirsiniz, mevcut temanız üzerinde de çalışabilirsiniz. Eğer mevcut temanıza uygulayacaksınız <strong>child</strong> üzerinde çalışmanızı öneririm..</li>
 	<li><a href="http://slicknav.com/" target="_blank"><strong>SlickNav</strong></a> – Ücretsiz ve temanıza entegre etmesi kolay bir script. Mobil cihazlarınızda çalışacak ARIA uyumlu menü hazırlamanızı sağlacak basit bir eklenti. Yalnız SlickNav'ı kullanmak için jQuery kütüphanesine ihtiyacınız olduğunu unutmayın. Kaldı ki WordPress'de varsayılan olarak mevcut.</li>
 	<li><strong>FTP Erişimi</strong> -  FTP erişiminiz olmazsa zaten pek bir iş yapılmaz.</li>
</ul>
<strong>Uyarı:</strong> Çalışmaya başlamadan önce yayındaki sitenizi indirin ve lokal bilgisayarınızda çalıştırın. Böylelikle ters giden bir şeyler olursa canınız fazla sıkılmaz.
<h2>Adım 1 - SlickNav'ı Yükleyin</h2>
<img class="aligncenter size-full wp-image-9150" src="https://www.trkodlama.com/wp-content/uploads/2017/02/mobile-menu-wp-theme-01.png" alt="" width="750" height="300" />

SlickNav oldukça küçük bir eklenti aslında. Mobil menünüzün oluşturmak için sadece iki adet dosyaya ihtiyaç duyuyor. Bunlarda kullanıcılarınızın sayfa yüklenme deneyimini olumsuz etkilemiyor:
<ul>
 	<li>jquery.slicknav.min.js</li>
 	<li>slicknav.css (sitenizin tasarımına göre düzenleyin bu dosyayı)</li>
</ul>
Bu iki dosyayı tema klasörünüzün içinde bir yere yükleyin. Fakat nereye yüklediğinize aklınızda tutun veya not edin. İhtiyacımız olacak ileride.
<h2>Adım 2 - JavaScript Dosyası Oluşturun</h2>
SlickNav'ı web sitenizde çalıştırmak onu JavaScript ile çağırmanız gerekir. Aşağıdaki kodu script etiketleri arasında direkt olarak <strong>header.php</strong> dosyanıza da ekleyebilirsiniz fakat WordPress'e JS kodlarınızı harici bir dosya ile yüklemeniz tavsiye ediliyor.

Öyleyse js dosyamızı oluşturalım. <strong>mobil_menu.js</strong> isminde bir dosya oluşturun. Bu dosyanın içine aşağıdaki kodu ekleyin(dikkat ederseniz jQuery no-conflict modunda kullandık WP ile uyumlu olması için):
<pre class="prettyprint lang-javascript" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">// SlickNav Mobil Menü
jQuery(function(){
    jQuery('#menu').slicknav();
});</pre>
Yukarıdaki kodda <code class="prettyprint lang-javascript" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">#menu</code> kısmına dikkat edin. Bu isim WordPress temanızda kullanılan ana navigasyon öğenizin ID'si ile eşleşmelidir. Çoğunlukla primary-menu, primary-nav, navigation, menu gibi isimlere sahiptir.

SlickNav'da kullanabileceğiniz bir çok özelliği mevcuttur. SlickNav özelliklerini görmek için linke tıklayınız: <a href="http://slicknav.com/#usage" target="_blank">slicknav.com/#usage</a>
<h2>Adım 3 - functions.php Dosyanızı Düzenleyin</h2>
Sıradaki adım temanızın <strong>functions.php</strong> dosyası aracılığıyla SlickNav'ı ve oluşturduğumuz JavaScript dosyasını temanıza eklemek! Aşağıdaki kodu kendi dosya konumlarınıza göre düzenleyerek functions.php dosyanıza ekleyin:
<pre class="prettyprint lang-php" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;?php
// Mobil Menü
function mobil_menu_CssJs() {
    // SlickNav'ı Ekleyelim
    wp_enqueue_script( 'mobilemenu-slickjs', get_template_directory_uri() . '/yukediginiz/dizin/jquery.slicknav.min.js', array('jquery') );
    
    wp_register_style( 'mobilemenu-css', get_stylesheet_directory_uri() . '/yukediginiz/dizin/slicknav.css');
    wp_enqueue_style( 'mobilemenu-css' );
    
    // Oluşturduğumuz yükleme JS dosyası
    wp_enqueue_script( 'mobilmenu-trkodlama', get_template_directory_uri() . '/yukediginiz/dizin/mobil_menu.js', array('jquery'));
}</pre>
yuklediginiz/dizin kısımlarını dosyaları temanızın içinde yüklediğiniz dizinin ismi şeklinde güncellemelisiniz.

Eğer burada ne yaptığınız tam olarak bilmiyorsanız lütfen web geliştiricinizden destek talep edin.
<h2>Adım 4 - Birazcık CSS ile Şekillendirin</h2>
<img class="aligncenter size-full wp-image-9151" src="https://www.trkodlama.com/wp-content/uploads/2017/02/mobile-menu-wp-theme-02.png" alt="" width="750" height="300" />

Yukarıdaki 3 adımı başarılı bir şekilde tamamladıysanız SlickNav kurulumunu tamamlamışsınız demektir ve web sitenizde otomatik olarak görünecektir - kullanıcının ekran boyutuna bakmadan. CSS dosyamızda bir kaç değişiklik yapmamız icap ediyor. Çünkü her ekran çözünürlüğünde bu menünün görünmesini istemiyoruz. Ekran genişliği 800px veya altında bu SlickNav mobil uyumlu menümüzün gözükmesini ve #menu ID'li asıl menümüzün gözümemesini istiyorsak CSS dosyanıza aşağıdaki kodu eklemelisiniz:
<pre class="prettyprint lang-css" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">.slicknav_menu {
    display:none;
}

@media screen and (max-width: 800px;) {
    #menu {
        display:none;
    }

    .slicknav_menu {
        display:block;
    }
}</pre>
800px değerini kendi isteğinize göre düzenleyebilirsiniz.
<h2>Adım 5 - Dosyalarınızı Yükleyin ve Test Edin</h2>
Son olarak aşağıdaki dosyaların hepsini doğru olarak FTP ile yüklediğinize emin:
<ul>
 	<li>SlickNav dosyaları - tema klasörünüzün içinde istediğiniz klasörün içine yükleyin</li>
 	<li>mobil_menu.js dosyanızı SlickNav dosyalarınız ile aynı dizine yükleyebilirsiniz</li>
 	<li>Düzenlemiş olduğunuz functions.php dosyası</li>
 	<li>Düzenlemiş olduğunuz temel CSS dosyanız</li>
</ul>
Mobil cihazınızdan yeni menünüzün görünümü test edin. Web sitenizle uyumlu olacak şekilde mobil menünüzün stilinde yapacağınız ufak tefek değişikliklerle işleminiz bitti. TR Kodlama'da bende SlickNav kullanıyorum bu arada :)

Umarım faydalı olur,