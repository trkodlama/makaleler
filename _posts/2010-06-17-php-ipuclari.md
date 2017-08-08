---
ID: 55
post_title: PHP İpuçları Yeni Başlayanlar İçin
author: Oral ÜNAL
post_excerpt: >
  PHP programlama dili için yeni
  başlayanlara yardımcı olacak küçük
  bir set..
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/php-ipuclari-55.html
published: true
post_date: 2010-06-17 07:35:55
---
Bu makaledeki verilerden yararlanarak PHP'nin yorumlanma hızını arttırmakla kalmayıp gereksiz kod kalabalığından da kurtulacaksınız.
<pre class="line-numbers"><code class="language-php">$deger = $deger + 1;</code></pre>
Bu kod aşağıdakiyle aynı anlamdadır:
<pre class="line-numbers"><code class="language-php">$deger ++;</code></pre>
Bu işlemi çıkarma içinde kullanabilirsiniz:
<pre class="line-numbers"><code class="language-php">$deger --;</code></pre>
Aynı isimli değişkenleri birleştirmek:
<pre class="line-numbers"><code class="language-php">$adim = 'Oral ÜNAL';
$adim = "$adim benim adım!";
// Oral ÜNAL benim adım!</code></pre>
Yerine aşağıdaki gibi ikici defa yazdığımız değişkende "=" işaretinde önce nokta(.) koyarak bu değişkeni birleştirebiliriz:
<pre class="line-numbers"><code class="language-php">$adim = 'Oral ÜNAL';
$adim .= " benim adım!"; 
//Oral ÜNAL benim adım!</code></pre>
Tek tırnak kullanmak çift tırnak kullanmaktan iyidir çünkü daha hızlıdır.
<pre class="line-numbers"><code class="language-php">$ad = "Ad Soyad";
if ($ad == "Ad Soyad") {
    echo "Gerçekten ad soyadmış"; 
}</code></pre>
yerine aşağıdaki gibi kullanılırsa daha hızlı çalışır
<pre class="line-numbers"><code class="language-php">$ad = 'Ad Soyad';
if ($ad == 'Ad Soyad') {
    echo 'Gerçekten ad soyadmış'; 
}</code></pre>
Şimdi küçük bir püf noktaya değinelim:
<pre class="line-numbers"><code class="language-php">echo '$ad, yardımsever birisidir.';
// Çıktısı: $ad, yardımsever birisidir.
echo "$ad, yardımsever birisidir.";
// Çıktısı: Oral ÜNAL yardımsever birisidir.</code></pre>
Farkettiğiniz gibi tek tırnak içinde ki yazılan değişken adları olduğu gibi yazdırılırken çift tırnak içinde yazılan değişkenler değişkenin değeri neyse onu yazdırdı. Tek tırnak kullanacaksanız aşağıdaki gibi kullanmalısınız:
<pre class="line-numbers"><code class="language-php">echo $ad . 'yardımsever birisidir.';</code></pre>
Eğer if...else kontrollerinizde bir fonksiyon, değişken vb. kullanacaksınız { ... } işaretlerine gerek yoktur.
<pre class="line-numbers"><code class="language-php">if($ad=="Oral ÜNAL") {
    echo 'Adı: '.$ad;
} else{
    echo 'Adı: '.$ad.' değilmiş';
}</code></pre>
Kontrolünde tek işlem kullanıldığı için aşağıdaki gibi de yazılabilirdi:
<pre class="line-numbers"><code class="language-php">if($ad=="Oral ÜNAL") echo 'Adı: '.$ad;
else echo 'Adı: '.$ad.' değilmiş';</code></pre>
if kontrolünde boolean türündeki bir değişkeni kontrol edecekseniz "==" veya "!=" sembollerine ihtiyacınız yoktur.
<pre class="line-numbers"><code class="language-php">if($birsifir==true) echo "Evet doğru";
elseif($birsifir!=true || $birsifir==false) echo "Hayır doğru değil";</code></pre>
$birsifir değişkenimiz boolean olduğu içinde aldığı değerler "1 veya 0" olabilir. Bu durumda da true ve false ifadelerine gerek kalmıyor. Aşağıdaki kodları inceleyelim:
<pre class="line-numbers"><code class="language-php">if($birsifir) echo "Evet doğru";
elseif(!$birsifir) echo "Hayır doğru değil";</code></pre>
Bu kısayollar hem sunucunuzun yorumlama hızını arttırıp hemde sizi fazla kalabalıktan kurtarır. Umarım işinize yarar.