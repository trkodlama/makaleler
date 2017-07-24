---
ID: 2288
post_title: 'Magento&#8217;da Derleme İşlemini Elle İptal Etme'
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/magentoda-derleme-islemini-elle-iptal-etme-2288.html
published: true
post_date: 2013-08-11 05:16:10
---
Merhaba arkadaşlar,

Bu yazım Magento ile ilgili. Magento'yu çok fazla karıştırdınız, karıştırdınız ve karıştırdınız. İstediklerinizi gerçekleştirdiniz ve Magento'nuzun hızlı çalışması için yönetici panelinden derleme işlemini gerçekleştireceksiniz. <strong>Çalıştır</strong> butonuna tıkladınız ve güm! Magento sisteminiz bozuldu. Erişmeye çalıştığınız bütün sayfalarda aşağıdakine benzer(demek istediğim herhangi bir hata) bir hata alıyorsunuz:
<blockquote>Fatal error: Call to a member function getLocaleCode() on a non-object in /home/domain/public_html/includes/src/__default.php on line 34806</blockquote>
İşte bu noktada derleme işlemini geri almanız gerektiğini hissediyorsunuz. Alışkanlıkla bi çırpıda <strong>phpMyAdmin</strong>'ni kurcalamaya başlıyorsunuz. Fakat orada da benzer bir ayar göremiyorsunuz.

Arkadaşlar derleme işlemini iptal etmek için Magento anadizininizdeki <strong>includes/config.php</strong> dosyasını açın. Derleme işlemi çalıştığı zaman bu dosyanın içeriği şöyledir:

<pre class="lang:php decode:1 " >define('COMPILER_INCLUDE_PATH', dirname(__FILE__).DIRECTORY_SEPARATOR.'src');
#define('COMPILER_COLLECT_PATH', dirname(__FILE__).DIRECTORY_SEPARATOR.'stat');</pre>

Derleme işlemini iptal etmek için ikinci satırdan diyez işaretini kaldırıp ilk satırın başına diye işareti ekliyoruz. Yani bu dosyamızın içeriği şöyle olmalıdır:

<pre class="lang:php decode:1 " >#define('COMPILER_INCLUDE_PATH', dirname(__FILE__).DIRECTORY_SEPARATOR.'src');
define('COMPILER_COLLECT_PATH', dirname(__FILE__).DIRECTORY_SEPARATOR.'stat');</pre>

Bu şekilde olduğu taktirde derleme işlemi iptal edilmiş olacaktır.

Umarım faydalı olmuştur, kolay gelsin