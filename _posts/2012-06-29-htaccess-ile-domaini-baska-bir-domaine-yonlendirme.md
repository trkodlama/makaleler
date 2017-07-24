---
ID: 917
post_title: '.htaccess ile Domain&#8217;i Başka Bir Domain&#8217;e Yönlendirme'
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/htaccess-ile-domaini-baska-bir-domaine-yonlendirme-917.html
published: true
post_date: 2012-06-29 12:35:54
---
Merhaba,

Bu makalemde sizlere <strong>.htaccess </strong>ile bir domain'i başka bir domain'e nasıl yönlendireceğimizi anlatıyorum.

Bu yönlendirmeyi yaparken kullanacağımız yegane modül <strong>mod_rewrite</strong> modülüdür. Bu modülün sunucunuzda yüklü olup olmadığına dikkat etmelisiniz. Eğer yüklü değilse lütfen öncelikle mod_rewrite'ı sunucunuza kurun veya hizmet aldığınız yere kurmalarını talep edin.

Yönlendirme yaparken dikkat etmemiz gereken bir nokta var. 301 mi 302 mi? Bir çok webmaster bu ayrıma dikkat etmez. 301 yönlendirmesi ile 302 yönlendirmesi farklı kavramlardır.

301 yönlendirmesi ile tarayıcıya, arama motorlarına bu adres şu adrese tamamen yönlendirilmiştir şeklinde bir uyarı yaparsınız. Fakat 302 yönlendirmesi ile geçici bir süreliğine yönlendirilmiştir dersiniz. Öncelikle hangisi ile yönlendireceğinize karar verin. Ondan sonra aşağıdaki kodu .htaccess dosyanıza kopyalaın. 301 ve 302 yönlendirmesi hakkında detaylı bilgi için <a href="https://plus.google.com/106772862908865768242/posts" target="_blank">Jonathan Hochman</a>'ın yazdığı <a href="http://www.hochmanconsultants.com/articles/301-versus-302.shtml" target="_blank">yazıyı</a> okuyabilirsiniz.

<hr />

<h3>eskidomain.com'u yenidomain.com'a Taşıma</h3>
eskidomain.com adresindeki alan adınızı yenidomain.com'a taşımak istiyorsanız bu makale sizin için muhteşem bir kaynak. Eskidomain'inize erişmek isteyen herkes otomatik olarak Yenidomain'inize yönlendirilecek. Hem de sorgu direkt olarak sorgu yapılan sayfaya!
<blockquote><strong>eskidomain.com/urunler/urun_adi.html</strong> adresine girmeye çalışan birisi otomatik olarak
<strong>yenidomain.com/urunler/urun_adi.html</strong> adresine yönlendirilecek.</blockquote>
Bunu yapmanız için .htaccess dosyanıza aşağıdaki kodu eklemeniz yeterlidir. Ben yönlendirmeyi örnek teşkil etmesi açısından 301 olarak yapıyorum. Siz kendinize hangisi uygunsa onu yazın lütfen:

[text]RewriteEngine On
RewriteCond %{HTTP_HOST} ^(www\.)?eskidomain\.com [NC]
RewriteRule ^(.*)$ http://www.yenidomain.com/$1 [R=301,L][/text]