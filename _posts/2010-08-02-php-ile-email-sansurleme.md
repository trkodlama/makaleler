---
ID: 76
post_title: PHP ile Email Sansürleme
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/php-ile-email-sansurleme-76.html
published: true
post_date: 2010-08-02 08:14:41
---
Bir sayfada kullanıcı emaillerini göstermek istiyorsunuz ama tamamı gözükmesin mi istiyorsunuz? Ä°şte bu sansürleme fonksiyonu tam size göre.. Yaptığı işlem ise şu:
Orjinal email: ounal@trkodlama.com
Sansürlü email: o***l@trkodlama.com
Hemen gerekli fonksiyonu sizlerle paylaşıyorum:
[sourcecode lang="php"]function emailSansur($email, $isaret = &quot;*&quot;) {
 $diziEmail = explode(&quot;@&quot;, $email);

 for ($i = 1; $i&lt;= (strlen($diziEmail[0]) - 2);$i++) {
  $isaretEkle .= $isaret;
 }

 return $diziEmail[0]{0}.substr_replace($diziEmail[0], $isaretEkle, 0, strlen($diziEmail[0])).$diziEmail[0]{strlen($diziEmail[0])-1}.&quot;@&quot;.$diziEmail[1];
}[/sourcecode]

$isaret parametresini tanımladığınız anda sansürlenen yerlere tanımladığınız veri yazılacaktır. Mesela varsayılan olarak "*" tanımladım. Mailler o***l@trkodlam.com olacak. Siz "x" tanımlarsanızoxxxl@trkodlama.com olacaktır. Kullanımı çok basittir:

[sourcecode lang="php"]emailSansur(&quot;ounal@trkodlama.com&quot;, &quot;TR&quot;); [/sourcecode]

Kolay gelsin,