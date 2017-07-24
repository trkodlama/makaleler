---
ID: 49
post_title: PHP ile Email Doğrulama
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/php-ile-email-dogrulama-49.html
published: true
post_date: 2009-08-05 07:27:25
---
Merhaba arkadaşlar, Bu fonksiyon aracılığıyla mail adreslerinin standart formlarda olup olmadığını kontrol edeceğiz. Eğer sunucunuzdaki PHP sürümü 5.2'den düşükse aşağıdaki fonksiyonu kullanabilirsiniz:
[sourcecode lang="php"]&amp;lt;?php  
function email($email){  
   return eregi(&amp;quot;^[_a-z0-9-]+(.[_a-z0-9-]+)*@[a-z0-9-]+(.[a-z0-9-]+)*(.[a-z]{2,3})$&amp;quot;, $email);  
}   
?&amp;gt;[/sourcecode]
Fonksiyonun kullanımı oldukça basittir. Nasıl kullanacağını gösteriyorum:
[sourcecode lang="php"]&amp;lt;?php  
$email=&amp;quot;email@adresi.com&amp;quot;; // Bir email belirledik  
if(email($email)==1) echo &amp;quot;Geçerli&amp;quot;;  
else echo &amp;quot;Geçersiz&amp;quot;; // Geçerli döndürür. Çünkü belirlediğimiz mail adresi geçerli.  
?&amp;gt;  [/sourcecode]
Eğer sunucunuzdaki PHP sürümü 5.2 ve yukarısıysa PHP grubu bizim için artık bir fonksiyon üretmiş. filter_var() fonksiyonunu FILTER_VALIDATE_EMAIL parametresiyle nasıl kullanacağımızı görelim:
[sourcecode lang="php"]&amp;lt;?php  
$email=&amp;quot;email@adresi.com&amp;quot;; // Yine bir mail adresi. Gerçek  
if(filter_var($email, FILTER_VALIDATE_EMAIL)) // Kullanım bu şekilde. 1 veya 0 döndürür.  
   echo &amp;quot;Geçerli&amp;quot;;  
else  
   echo &amp;quot;Geçersiz&amp;quot;; // Geçerli yazdırır..  
?&amp;gt;  [/sourcecode]
Ayrıca mail adreslerinizdeki zararlı karakterleri temizlemek isterseniz-ki bunun için PHP sürümünüz yine 5.2'den yüksek olmalıdır- PHP'nin ürettiği FILTER_SANITIZE_EMAIL'i deneyin:
[sourcecode lang="php"]&amp;lt;?php  
$email=&amp;quot;em(ail) @adresi.com&amp;quot;;  
$email=filter_var($email, FILTER_SANITIZE_EMAIL);  
echo $email; // ekran görüntüsü: email@adresi.com  
?&amp;gt;  [/sourcecode]
FILTER_SANITIZE_EMAIL ile [b]$-_.+!*'{}|^~[]`#%/?@&=[/b] karakterleri dışındaki bütün karakterleri temizleyebilirsiniz.