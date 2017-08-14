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
Bir sayfada kullanıcı emaillerini göstermek istiyorsunuz ama tamamı gözükmesin mi istiyorsunuz? İşte bu sansürleme fonksiyonu tam size göre.. Yaptığı işlem ise şu:
<blockquote>Orjinal email: ounal@trkodlama.com

Sansürlü email: o***l@trkodlama.com</blockquote>
Hemen gerekli fonksiyonu sizlerle paylaşıyorum:
<pre class="line-numbers"><code class="language-php">function emailSansur($email, $isaret = "*") {
    $diziEmail = explode("@", $email);

    for ($i = 1; $i&lt;= (strlen($diziEmail[0]) - 2);$i++) {
        $isaretEkle .= $isaret;
    }

    return $diziEmail[0]{0}.substr_replace($diziEmail[0], $isaretEkle, 0, strlen($diziEmail[0])).$diziEmail[0]{strlen($diziEmail[0])-1}."@".$diziEmail[1];
}</code></pre>
<code>$isaret</code> parametresini tanımladığınız anda sansürlenen yerlere tanımladığınız veri yazılacaktır. Mesela varsayılan olarak "*" tanımladım. Mailler o***l@trkodlama.com olacak. Siz "x" tanımlarsanız oxxxl@trkodlama.com olacaktır. Kullanımı çok basittir:
<pre class="line-numbers"><code class="language-php">emailSansur("ounal@trkodlama.com", "TR");</code></pre>
Kolay gelsin,