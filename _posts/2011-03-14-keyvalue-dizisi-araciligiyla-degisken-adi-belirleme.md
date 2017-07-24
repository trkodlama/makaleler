---
ID: 92
post_title: '$key=>$value Dizisi Aracılığıyla Değişken Adı Belirleme'
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/keyvalue-dizisi-araciligiyla-degisken-adi-belirleme-92.html
published: true
post_date: 2011-03-14 08:33:07
---
Merhaba arkadaşlar,

Bildiğimiz gibi genelde dizilerde değerlerimizi şu şekilde tutarız: $ayar["ayar_adi"]. Diziler bizi bir çok kafa karıştıracak değişken adlarından kurtarır. Bu nedenle de ben dizileri çok severim fakat onlara ihtiyacım olduğu zaman dizi yerine direkt bir değişkeni çağırmayı tercih ediyorum. Şimdi size $ayar["ayar_adi"] şeklindeki dizi elemanını $ayar_adi=deger şekline nasıl çevirebileceğinizi gösteriyorum. Yöntem aşağıdaki gibidir:

[sourcecode lang="php"]foreach($dizi AS $key=&gt;$value){
    $$key = $value;
    // veya
    ${$key} = $value;
}[/sourcecode]
Fakat bu yöntemi kullanırken $_POST, $_GET ve $_REQUEST işlemlerinde dikkatli olmalısınız. Sitenize uzaktan erişen birinin kendi değişkenleriyle sitenize işlem yaptırması hoş olmaz tabii ki. Bunun için şöyle basit bir önlem alabilir:
[sourcecode lang="php"]$GetIleKabulEdilenler = “/deger1|deger2|deger3|vb/”;
foreach($_GET as $key =&gt; $value) {
    $key = strtolower($key);
    if(preg_match($GetIleKabulEdilenler,$key)) $$key = $value;
}[/sourcecode]
Yukarıdaki örnekle foreach içine alacağımız dizi elemanlarını sınırladık. Sadece $_GET["deger1"], $_GET["deger2"], $_GET["deger3"] ve $_GET["vb"] ifadelerini kullanarak $deger1, $deger2, $deger3 ve $vb değişkenlerini oluşturacak. Normalde dizi elemanları isimleriyle değişken yapan bir PHP fonksiyonu mevcut extract() diye. Fakat bu fonksiyonda $value üzerinde hiçbir değişiklik yapamıyorsunuz. Direk oluşturuyor. Fakat bu yöntemle $value ifadesini addslashes($value) şeklinde de değişkenlere atayıp direk veritabanına rahatlıkla gönderilebilecek hale getirebiliriz.

Umarım faydalı olur, kolay gelsin