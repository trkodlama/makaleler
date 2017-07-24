---
ID: 35
post_title: PHP-MySQL ile Sonuçları Sıralama
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/yeni-baslayanlar/mysqlde-siralama-35.html
published: true
post_date: 2009-06-11 07:18:54
---
Bu makaleyi kendimde bulduğum bir eksiklikten dolayı yazma ihtiyacı duydum. Belki ihtiyacı olan başkalarına da faydalı olur. MySQL'da sıralama, belli bir kolon adına göre A-Z'ye(asc) veya Z-A'ya(desc) şeklinde sıralamaya denir. Örnek:
<pre class="prettyprint lang-mysql" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">mysqli_fetch_assoc(mysqli_query($db, "SELECT * FROM tablo_adi ORDER BY kolon_1 ASC"));</pre>
Yukarı tablo_adi isimli tabloda bilgileri çekerken A-Z'ye doğru kolon_1'e göre sıraladık. Yani kolon_1 tablosundaki değerler "s", "a", "uy" vb. şeklinde olsaydı şu şekilde sıralanacaktı: "a", "s", "uy" vb. Bu sıralamayı yaparken diğer parametreleri de kullanabilirsiniz (örn.: where, like). Sıralama yaparken tek bir kolona bağlı kalmayabilirsiniz. Yani sadece kolon_1'e göre değil aynı zamanda kolon_2'ye göre de sıralama yapabilirsiniz. Örnek:
<pre class="prettyprint lang-php" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;?php
$sorgu=mysqli_query($db, "select * from tablo_adi order by kolon_1 asc, kolon_2 desc");
while($s=mysqli_fetch_array($sorgu)){
    // Çıktıyı işleyin...
}
?&gt;</pre>
Yukarı tablo_adi isimli tabloda bilgileri çekerken A-Z'ye doğru kolon_1'e göre sıraladık ve elde ettiğimiz sırayı bu sefer Z-A'ya kolon_2'ye göre tekrar sıraladık.

Umarım faydalı bir makale olmuştur. Hepinizin işine yarayacağını düşünüyorum.

İyi çalışmalar,