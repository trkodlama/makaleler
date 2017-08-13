---
ID: 471
post_title: PHP ile Resmi Yeniden Boyutlandırma
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/php-ile-resmi-yeniden-boyutlandirma-471.html
published: true
post_date: 2012-06-12 01:31:07
---
Merhaba,

Bu makaledeki kodlar benim kendi eserim değildir. Bir blogda gördüm ve sizlerle paylaşmaya karar verdim.
<h2>Bölüm 1 - Bu Sınıf Ne İşe Yarıyor</h2>
<strong>SimpleImage</strong> isimli bu sınıf yolunu belirttiğiniz resimlerin genişliklerini ve yüksekliklerini düzenlemenizi sağlıyor. Bu sınıf sayesinde resimlerinizi %'li değer girerek ölçekleyebilir, genişlik ve yüksekliğini manuel belirleyebilir veya sadece genişlik/yükseklik değerlerinden birini girerek oranları bozmadan yeniden boyutlandırabilirsiniz.

Boyutlandırma işlemlerini en basit yapabileceğini sınıflardan birisi bence bu.
<h2>Bölüm 2 - Sınıf Kodları</h2>
Bu sınıfın kodları aşağıdaki gibidir:
<pre class="prettyprint lang-php" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;?php

/*
* File: SimpleImage.php
* Author: Simon Jarvis
*/

class SimpleImage {

   var $image;
   var $image_type;

   function load($filename) {

      $image_info = getimagesize($filename);
      $this-&gt;image_type = $image_info[2];
      if( $this-&gt;image_type == IMAGETYPE_JPEG ) {

         $this-&gt;image = imagecreatefromjpeg($filename);
      } elseif( $this-&gt;image_type == IMAGETYPE_GIF ) {

         $this-&gt;image = imagecreatefromgif($filename);
      } elseif( $this-&gt;image_type == IMAGETYPE_PNG ) {

         $this-&gt;image = imagecreatefrompng($filename);
      }
   }
   function save($filename, $image_type=IMAGETYPE_JPEG, $compression=75, $permissions=null) {

      if( $image_type == IMAGETYPE_JPEG ) {
         imagejpeg($this-&gt;image,$filename,$compression);
      } elseif( $image_type == IMAGETYPE_GIF ) {

         imagegif($this-&gt;image,$filename);
      } elseif( $image_type == IMAGETYPE_PNG ) {

         imagepng($this-&gt;image,$filename);
      }
      if( $permissions != null) {

         chmod($filename,$permissions);
      }
   }
   function output($image_type=IMAGETYPE_JPEG) {

      if( $image_type == IMAGETYPE_JPEG ) {
         imagejpeg($this-&gt;image);
      } elseif( $image_type == IMAGETYPE_GIF ) {

         imagegif($this-&gt;image);
      } elseif( $image_type == IMAGETYPE_PNG ) {

         imagepng($this-&gt;image);
      }
   }
   function getWidth() {

      return imagesx($this-&gt;image);
   }
   function getHeight() {

      return imagesy($this-&gt;image);
   }
   function resizeToHeight($height) {

      $ratio = $height / $this-&gt;getHeight();
      $width = $this-&gt;getWidth() * $ratio;
      $this-&gt;resize($width,$height);
   }

   function resizeToWidth($width) {
      $ratio = $width / $this-&gt;getWidth();
      $height = $this-&gt;getheight() * $ratio;
      $this-&gt;resize($width,$height);
   }

   function scale($scale) {
      $width = $this-&gt;getWidth() * $scale/100;
      $height = $this-&gt;getheight() * $scale/100;
      $this-&gt;resize($width,$height);
   }

   function resize($width,$height) {
      $new_image = imagecreatetruecolor($width, $height);
      imagecopyresampled($new_image, $this-&gt;image, 0, 0, 0, 0, $width, $height, $this-&gt;getWidth(), $this-&gt;getHeight());
      $this-&gt;image = $new_image;
   }

}
?&gt;</pre>
<h2>Bölüm 3 - Sınıfın Kullanımı</h2>
Yukarıdaki sınıfı SimpleImage.php adlı bir dosyaya kaydedin.
<h4>Örnek 1 - GenişlikxYükseklik ayarlama ve farklı isimle kaydetme</h4>
Şimdi picture.jpg adlı resim dosyamızı 250x400 ebatlarında tekrar boyutlandıralım ve picture2.jpg ismiyle kaydedelim:
<pre class="prettyprint lang-php" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;?php
   include('SimpleImage.php');
   $image = new SimpleImage();
   $image-&gt;load('picture.jpg');
   $image-&gt;resize(250,400);
   $image-&gt;save('picture2.jpg');
?&gt;</pre>
<h4>Örnek 2 - Oranları koruyarak sadece genişliği değiştirip farklı bir isimle kaydetme</h4>
Şimdi picture.jpg dosyamızı 250 piksel genişliğinde oranları koruyarak resmi yeniden boyutlandıralım ve picture2.jpg olarak kaydedelim:
<pre class="prettyprint lang-php" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;?php
   include('SimpleImage.php');
   $image = new SimpleImage();
   $image-&gt;load('picture.jpg');
   $image-&gt;resizeToWidth(250);
   $image-&gt;save('picture2.jpg');
?&gt;</pre>
<h4>Örnek 3 - Resmi belirli bir yüzde oranında küçültme</h4>
Şimdi picture.jpg dosyamızı %50 oranında küçültelim ve picture2.jpg ismiyle kaydedelim:
<pre class="prettyprint lang-php" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;?php
   include('SimpleImage.php');
   $image = new SimpleImage();
   $image-&gt;load('picture.jpg');
   $image-&gt;scale(50);
   $image-&gt;save('picture2.jpg');
?&gt;</pre>
<h4>Örnek 4 - Resmi farklı yüksekliklerde farklı isimlerle kaydetme</h4>
Şimdi picture.jpg dosyasının yüksekliğini 500px olarak ayarlayalım ve picture2.jpg olarak kaydedelim aynı anda yüksekliği 200px olarak da picture3.jpg olarak kaydedelim.
<pre class="prettyprint lang-php" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;?php
   include('SimpleImage.php');
   $image = new SimpleImage();
   $image-&gt;load('picture.jpg');
   $image-&gt;resizeToHeight(500);
   $image-&gt;save('picture2.jpg');
   $image-&gt;resizeToHeight(200);
   $image-&gt;save('picture3.jpg');
?&gt;</pre>
<h4>Örnek 5 - Resmi kaydetmeden ekrana küçük resmini çıkartma</h4>
Şimdi picture.jpg dosyamızı yeni bir dosya olarak kaydetmeden nasıl küçük resim olarak gösterebileceğimize bakalım:
<pre class="prettyprint lang-php" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;?php
   header('Content-Type: image/jpeg');
   include('SimpleImage.php');
   $image = new SimpleImage();
   $image-&gt;load('picture.jpg');
   $image-&gt;resizeToWidth(150);
   $image-&gt;output();
?&gt;</pre>
<h4>Örnek 6 - Form uygulaması</h4>
Şimdi formdan yüklediğimiz resmi 150 piksel genişliğinde yeniden boyutlandırıp ekrana basalım:
<pre class="prettyprint lang-php" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;?php
   if( isset($_POST['yukle']) ) {
      header('Content-Type: image/jpeg');
      include('SimpleImage.php');
      $image = new SimpleImage();
      $image-&gt;load($_FILES['resim']['tmp_name']);
      $image-&gt;resizeToWidth(150);
      $image-&gt;output();
   } else {
?&gt;
   &lt;form action="resim_yukle.php" method="post" enctype="multipart/form-data"&gt;

      &lt;input type="file" name="resim" /&gt;

      &lt;input type="submit" name="yukle" value="Yükle" /&gt;

   &lt;/form&gt;
&lt;?php
   }
?&gt;</pre>
<h2>Sonuç</h2>
Bu sınıfla ilgili sorularınızı forumda başlık açarak veya burada yorum yaparak sorabilirsiniz. Resimleri yeniden boyutlandırmak için harika bir sınıf.

Kolay gelsin,