---
ID: 5690
post_title: 'Magento: Yönetici Paneli Bilgilendirme Popup&#8217;ını Devre Dışı Bırakma'
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/magento-yonetici-paneli-bilgilendirme-popupini-devre-disi-birakma-5690.html
published: true
post_date: 2014-09-16 01:14:58
---
Magento Yönetici paneline her giriş yaptığınızda sizi güncellemelerden haberdar eden bir Popup karşılıyor.

<a href="http://www.trkodlama.com/wp-content/uploads/2014/09/admin_notification.jpg"><img class="aligncenter size-medium wp-image-5691" src="http://www.trkodlama.com/wp-content/uploads/2014/09/admin_notification-300x116.jpg" alt="admin_notification" width="300" height="116" /></a>

Bu mesaj aslında yazılımınızın güncel kalması için iyi bir özellik fakat daha çok geliştiricilerin ihtiyaç duyduğu bir özellik. Son kullanıcı gün içerisinde defalarca giriş yapıp her girdiğinde bu uyarıyı alması ultra sıkıcı hale getirebiliyor.

Bu yazıda hızlı bir şekilde bu Popup'ları ortadan kaldırmayı göstereceğim. Oldukça basit bir kaç adımdan oluşmaktadır.

Yönetici panelinden modülleri aktifleştirip devre dışı bırakabildiğimiz bir sayfamız var. Şimdi ona geçelim:
<ol>
	<li>Yönetici panelinize giriş yapın. Şimdi sizi Pop-up karşıladı :)</li>
	<li>Şuraya gidin =&gt; System &gt;&gt; Configuration &gt;&gt; Advance veya Sistem &gt;&gt; Ayarlar &gt;&gt; Gelişmiş</li>
	<li>"Mage_AdminNotification" modülünü devre dışı bırakın. Resimden yardım alabilirsiniz:</li>
</ol>
<img class="aligncenter size-full wp-image-5692" src="http://www.trkodlama.com/wp-content/uploads/2014/09/magento_notification_module.jpg" alt="magento_notification_module" width="557" height="154" />

Şimdi Magento önbelleğini temizleyin. Çıkış yapın. Giriş yaptığınızda o Popup daha fazla canınızı sıkmayacak.