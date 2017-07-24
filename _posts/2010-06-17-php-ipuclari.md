---
ID: 55
post_title: PHP İpuçları
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/php-ipuclari-55.html
published: true
post_date: 2010-06-17 07:35:55
---
Bu makaledeki verilerden yararlanarak PHP'nin yorumlanma hızını arttırmakla kalmayıp gereksiz kod kalabalığından da kurtulacaksınız.

[sourcecode lang="php"]$deger = $deger + 1;[/sourcecode]

Bu kod aşağıdakiyle aynı anlamdadır:

[sourcecode lang="php"]$deger ++;[/sourcecode]

Bu işlemi çıkarma içinde kullanabilirsiniz:

[sourcecode lang="php"]$deger --;[/sourcecode]

Aynı isimli değişkenleri birleştirmek:

[sourcecode lang="php"]$adim = 'Oral ÜNAL';
$adim = &quot;$adim benim adım!&quot;; // $adim = 'Oral ÜNAL benim adım!';[/sourcecode]

Yerine aşağıdaki gibi ikici defa yazdığımız değişkende "=" işaretinde önce nokta(.) koyarak bu değişkeni birleştirebiliriz:

[sourcecode lang="php"]$adim = 'Oral ÜNAL';
$adim .= &quot; benim adım!&quot;; // $adim = 'Oral ÜNAL benim adım!';[/sourcecode]

Tek tırnak kullanmak çift tırnak kullanmaktan iyidir çünkü daha hızlıdır.

[sourcecode lang="php"]$ad = &quot;Ad Soyad&quot;;
if ($ad == &quot;Ad Soyad&quot;) {
echo &quot;Gerçekten ad soyadmış&quot;; }[/sourcecode]

yerine aşağıdaki gibi kullanılırsa daha hızlı çalışır

[sourcecode lang="php"]$ad = 'Ad Soyad';
if ($ad == 'Ad Soyad') {
echo 'Gerçekten ad soyadmış'; }[/sourcecode]

Şimdi küçük bir püf noktaya değinelim:

[sourcecode lang="php"]echo '$ad, yardımsever birisidir.';
// Çıktısı: $ad, yardımsever birisidir.
echo &quot;$ad, yardımsever birisidir.&quot;;
// Çıktısı: Oral ÜNAL yardımsever birisidir.[/sourcecode]

Farkettiğiniz gibi tek tırnak içinde ki yazılan değişken adları olduğu gibi yazdırılırken çift tırnak içinde yazılan değişkenler değişkenin değeri neyse onu yazdırdı. Tek tırnak kullanacaksanız aşağıdaki gibi kullanmalısınız:

[sourcecode lang="php"]echo $ad . 'yardımsever birisidir.';[/sourcecode]

Eğer if...else kontrollerinizde bir fonksiyon, değişken vb. kullanacaksınız { ... } işaretlerine gerek yoktur.

[sourcecode lang="php"]if($ad==&quot;Oral ÜNAL&quot;) {
echo 'Adı: '.$ad;
} else{
echo 'Adı: '.$ad.' değilmiş';
}[/sourcecode]

Kontrolünde tek işlem kullanıldığı için aşağıdaki gibi de yazılabilirdi:

[sourcecode lang="php"]if($ad==&quot;Oral ÜNAL&quot;) echo 'Adı: '.$ad;
else echo 'Adı: '.$ad.' değilmiş';[/sourcecode]

if kontrolünde boolean türündeki bir değişkeni kontrol edecekseniz "==" veya "!=" sembollerine ihtiyacınız yoktur.

[sourcecode lang="php"]if($birsifir==true) echo &quot;Evet doğru&quot;;
elseif($birsifir!=true || $birsifir==false) echo &quot;Hayır doğru değil&quot;;[/sourcecode]

$birsifir değişkenimiz boolean olduğu içinde aldığı değerler "1 veya 0" olabilir. Bu durumda da true ve false ifadelerine gerek kalmıyor. Aşağıdaki kodları inceleyelim:

[sourcecode lang="php"]if($birsifir) echo &quot;Evet doğru&quot;;
elseif(!$birsifir) echo &quot;Hayır doğru değil&quot;;[/sourcecode]

Bu kısayollar hem sunucunuzun yorumlama hızını arttırıp hemde sizi fazla kalabalıktan kurtarır. Umarım işinize yarar.