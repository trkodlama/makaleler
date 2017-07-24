---
ID: 1236
post_title: >
  WordPress Kullanıcısını Rolüne
  Göre Bir Sayfaya Yönlendirme
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/wordpress/wordpress-kullanicisini-rolune-gore-bir-sayfaya-yonlendirme-1236.html
published: true
post_date: 2012-07-26 21:52:45
---
Wordpress üzerine yazdığımız makaleleri düzenli olarak artırmaya devam ediyoruz. Bugün WordPress makalelerimize bir tanesini daha ekliyoruz.

Bu makale ile WordPress üyelerinizi rolüne göre giriş yaptıktan sonra belirlediğiniz bir sayfaya nasıl yönlendireceğinizi gösteriyorum. Kullanıcı rolünden kasteddiğim "Yönetici, yazar, editör, İçerik Sağlayıcı ve Abone".

Daha fazla zaman kaybetmeden aşağıdaki kodu incelemeye başlayın:
<pre class="prettyprint lang-php" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;?php
function role_gore_yonlendir()
{
    // Kullanıcı neyin nesiymiş o bilgiyi alalım
    global $current_user;
    get_currentuserinfo();

    if ($current_user-&gt;user_level == 0)
    {
     // Kullanıcı tipi Abone
     // İlgili sayfaya yönlendirme işlemleri
    }
    else if ($current_user-&gt;user_level &gt; 1)
    {
      // Kullanıcı tipi İçerik Sağlayıcı
      // İlgili sayfaya yönlendirme işlemleri
    }
    else if ($current_user-&gt;user_level &gt; 8)
    {
      // Kullanıcı tipi Editör
      // İlgili sayfaya yönlendirme işlemleri
    }
    else
    {
      // Kullanıcı tipi bulunamadı
      // Buradan uzaklaş çabuk
    }
}
// Aşağıdaki satır ile yukarıdaki işlemlerin çalışmasını sağlıyoruz.
add_action("admin_init","role_gore_yonlendir");</pre>
Yukarıdaki kodu incelerseniz WordPress'in aktif bir komutunu kullandığımızı farkedeceksiniz. Bu fonksiyon <strong>admin_init</strong> fonksiyonudur.

Yukarıdaki kodda ben yönlendirme işlemlerini yapmayı size bıraktım. İsterseniz WordPress tarafından oluşturulmuş olan <a href="http://codex.wordpress.org/Function_Reference/wp_redirect" target="_blank">wp_redirect</a> fonksiyonunu kullanabilirsiniz.

Merak ettiğiniz soruları yorum yazarak sorabilirsiniz.