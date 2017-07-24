---
ID: 1467
post_title: >
  WordPress Eklentisini Kodla
  Aktifleştirme
author: Oral ÜNAL
post_excerpt: |
  Bu makale de wordpress eklentilerinin programlamayla nasıl aktifleştirileceğini göreceğiz.
  Eğer devre dışı bırakılmasını istemediğiniz eklentiler varsa bu yazı tam sizlik. Aşağıdaki kod sayesinde Eklentiler sayfasından eklenti devre dışı bırakılmış olarak görünse bile aslında devre dışı bırakılmıyor. Bu sayede başkaları kurcalasa da değişen bir şey olmayacak eklentide :)
  Yazıdaki kodu temanızın <strong>functions.php </strong>eklemeniz yeterli olacaktır. Tabii kendinize göre düzenledikten sonra...
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/wordpress-eklentisini-kodla-aktiflestirme-1467.html
published: true
post_date: 2013-01-20 03:01:53
---
Merhaba,

Şu sıralar WordPress'le ilgili biraz daha ağırlıklı yazıyorum herhalde. Bu da WordPress'le ilgili yazdığım başka bir yazı. Bu makale de wordpress eklentilerinin programlamayla nasıl aktifleştirileceğini göreceğiz.

Eğer devre dışı bırakılmasını istemediğiniz eklentiler varsa bu yazı tam sizlik. Aşağıdaki kod sayesinde Eklentiler sayfasından eklenti devre dışı bırakılmış olarak görünse bile aslında devre dışı bırakılmıyor. Bu sayede başkaları kurcalasa da değişen bir şey olmayacak eklentide :)

Aşağıdaki kodu temanızın <strong>functions.php </strong>eklemeniz yeterli olacaktır. Tabii kendinize göre düzenledikten sonra.

<pre class="lang:php decode:1 " >// Aktif eklentileri alalım
$aktif_eklentiler = get_option(&amp;quot;active_plugins&amp;quot;);

if(count($current_plugin)&amp;gt;0)
{
  // Her zaman aktif olmasını istediğiniz eklentileri diziye atayalım
  $daima_aktif = array(&amp;quot;eklenti_x&amp;quot;, &amp;quot;eklenti_y&amp;quot;, &amp;quot;eklenti_z&amp;quot;);
  
  // Aktif eklentileri d&ouml;ng&uuml;ye sokalım
  foreach ($daima_aktif as $eklenti)
  {
    // Eğer eklenti aktif değilse listeye ekleyelim
    if(!in_array($eklenti, $aktif_eklentiler)) 
    {
      array_push($aktif_eklentiler ,$eklenti);
    }
  }
  // Son olarak eklentileri g&uuml;ncelleyelim
  update_option('active_plugins',$aktif_eklentiler );
}</pre>

İşte bu kadar. Artık seçtiğimiz eklentiler yönetici panelinden devre dışı bırakılmış bile olsa asla devre dışı bırakılamazlar(tabii bu tedbir farkedilmedikçe). Umarım faydalı olur, kolay gelsin,