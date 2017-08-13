---
ID: 108
post_title: >
  Veritabanına Son Eklenen Kayıtın ID
  Bilgisini Alma
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/veritabanina-son-eklenen-kayitin-id-bilgisini-alma-108.html
published: true
post_date: 2011-03-15 08:53:32
---
Veritabanına bir kayıt eklediniz ve daha sonra bu kaydın <em>auto_increment</em> özelliğine sahip sütununa erişmek istediniz ki bu da genellikle <strong>id</strong> isminde olur. Eğer ultra değişik bir algınız yoksa bu <strong>id</strong> olur. ID değerinizi bulmak için <code class="prettyprint lang-php" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">mysqli_insert_id ( mysqli $link )</code> fonksiyonundan faydalanırız. Bir örnekle gösterelim..
<pre class="prettyprint lang-php" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;?php  
/**
 * $db değişkenimizi tanımladık
 */

$ad     = "TR Kodlama";  
$zaman  = time();  
// Tablo yapım id(int, auto_increment) | ad(varchar) | tarih(int)  
mysqli_query($db, "INSERT INTO tablo VALUES(NULL, '$ad', $tarih)");  
$sonId=mysqli_insert_id($db);  
?&gt;</pre>
Bu fonksiyon ile en son eklenen tabloda auto_increment olarak tanımlanan sutuna eklenen son satırın değerini verir. Yani son eklenen satırdaki id değerini $sonId değişkenine atamış olduk.

<code class="prettyprint lang-php" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">mysqli_insert_id()</code> fonksiyonu yapmış olduğunuz bir sorguda AUTO_INCREMENT özelliğine sahip olan kolonun değerini verir. Eğer yaptığınız son veritabanı sorgunuz <strong>INSERT</strong> veya <strong>UPDATE</strong> değilse veya işlem yaptığınız tablonun <strong>AUTO_INCREMENT</strong> özelliğine sahip bir kolonu yoksa bu fonksiyon sıfır olarak döner.

Kolay gelsin,