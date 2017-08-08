---
ID: 9960
post_title: >
  WordPress Javascript Dosyalarını
  Footer’a Taşıma
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/wordpress-javascript-dosyalarini-footera-tasima-9960.html
published: true
post_date: 2017-08-09 00:45:40
---
<strong>WordPress</strong> alt yapılı bir siteniz varsa geliştirirken takıldığınız noktalardan birisinin de <code>&lt;head&gt;</code> etiketleri arasında yer alan <strong>javascript dosyaları</strong>nın otomatik olarak <strong>footer’a taşınma</strong>masıdır. Malesef bunu elinizle yapmanız gerekiyor.

Bu noktada devreye WordPress tarafından geliştirilmiş ve çok güzel şekilde çalışan bir fonksiyon giriyor. <code>wp_enqueue_scripts()</code> fonksiyonu içerisine girdiğiniz dosyaları otomatik olarak footer’a taşıma işlemini yapıyor. Ben bunu kendi kullandığım yöntem ile anlatacağım. Öncelikle bir fonksiyon oluşturarak içerisine bazı veriler girmem gerekiyor. Bu veriler ilk olarak daha önceden tanımlı bir dosya için geçerliyse onu iptal etmek ve yeniden footer’da gösterilmek üzere tanıtmak oluyor. <strong>Functions.php</strong> dosyamızı açarak aşağıdaki gibi kodlarımızı giriyoruz.
<pre class="line-numbers"><code class="language-php">// Javascript'leri Footer'a taşıma Kodu
function footera_tasi() {
 
	// Tanımlı dosyaları tanımsız hale getiriyoruz.
	wp_deregister_script( 'jquery' );
	wp_deregister_script( 'jquery-migrate' );
 
	// Dosyaları kodlarımız arasında kaldırıyoruz.
	wp_dequeue_script( 'jquery' );
	wp_dequeue_script( 'jquery-migrate' );
 
	// Kendi dosyalarımızı tanımlıyoruz.
	wp_register_script( 'jquery', get_stylesheet_directory_uri() . '/js/jquery.js', '', '', true );
	wp_register_script( 'jquery-migrate', get_stylesheet_directory_uri() . '/js/jquery-migrate.js', '', '', true );
 
	// Dosyaları kodlarımız arasına ekliyoruz.
	wp_enqueue_script( 'jquery' );
	wp_enqueue_script( 'jquery-migrate' );
 
 
}
add_action('wp_enqueue_scripts', 'footera_tasi', PHP_INT_MAX);</code></pre>
Bu kodu kullanarak WordPress tarafından default olarak gelen ve eklentilerden kaynaklanan javascript dosyalarınızı footer’a taşıyabilirsiniz. Burda kullandığımız <code>wp_register_script()</code> fonksiyonu içerisine 5 parametre alır. Bunlar sırayla, <code>('dosya-ismi', 'dosya-yolu', 'dizisi – default olarak array() alır – ', 'versiyonu', 'footera taşınsın mı?')</code> şeklinde olmalıdır. Biz kodumuzda dosya adı ve dosya yolunu girdikten sonra 3. ve 4. parametrelerimizi boş bırakarak default değerlerini almasını sağladık ama 5. parametremize true değerini vererek kodlarımızı footer’a gönderdik.

<code>wp_register_script()</code> fonksiyonunun <a href="https://developer.wordpress.org/reference/functions/wp_register_script/#core-registered-scripts">Codex</a>'te yer alan sayfasına göz atarsanız WordPress’in içerisinde otomatik olarak tanımlı olan javascript dosyalarının isimlerini görebilirsiniz.

Bunun dışında bu kod nerede işimize yarar diye soracak olursanız, benim oldukça fazla kullandığım yapılar arasında yer alır. Bu kod sayesinde istediğimiz javascript kodunu istediğimiz sayfa veya yazıda aktif edebiliriz. Mesela ben eğer Jetpack eklentisini ve ya Contact Form eklentisini anasayfa içerisinde hiçbir yer kullanmıyor, sadece bir sayfada veya yazı içerisinde kullanıyorsam, bunların anasayfa için yüklenmesi benim sitemi yavaşlatacaktır ki bu hiç istemediğimiz bir durum. Bunun önüne geçmek için aşağıdaki gibi bir yapı kullanabiliriz.
<pre class="line-numbers"><code class="language-php">// Javascript'leri Footer'a taşıma Kodu
function footera_tasi() {

	// Tanımlı dosyaları tanımsız hale getiriyoruz.
	wp_deregister_script( 'jquery' );

	// Dosyaları kodlarımız arasında kaldırıyoruz.
	wp_dequeue_script( 'jquery' );

	// Kendi dosyalarımızı tanımlıyoruz.
	wp_register_script( 'jquery', get_stylesheet_directory_uri() . '/js/jquery.js', '', '', true );

	// Sadece yazı içerisinde jquery dosyamızı kodlarımız arasına ekliyoruz.
	if(is_single()){
		wp_enqueue_script( 'jquery' );
	}
}
add_action('wp_enqueue_scripts', 'footera_tasi', PHP_INT_MAX);</code></pre>
<h2>Wordpress Tarafından Eklenen Javascript'ler</h2>
Son olarak, sitemizde yer alan eklentiler veya <strong>WordPress</strong> tarafından otomatik olarak eklenen javascript dosyalarının neler olduğunu veya adını bilmiyorsanız görünmesini istediğiniz yere
<pre class="line-numbers"><code class="language-php">&lt;?php global $wp_scripts; var_dump($wp_scripts); ?&gt;</code></pre>
yazarak sitenizde bulunan bütün javascript dosyalarını ayrıntılı olarak görebilirsiniz. Sizin kullandığınız dosyalar ise en alt taraflarda bulunan dosyalar olacaktır. Buradan dosyanıza tanımlı kısa isimi öğrenip onu önce o ismi kullanarak tanımsız hale getirip daha sonra istediğiniz şekilde aktif edebilirsiniz. Eklentilerden kaynak dosyaları tekrar aynı isimle aktif ederseniz eklenti ile ilgili problemlerin önüne geçmiş olursunuz.