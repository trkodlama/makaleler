---
ID: 162
post_title: Temel ASP Bilgileri
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/temel-asp-bilgileri-162.html
published: true
post_date: 2011-04-29 18:37:37
---
Asp dilinde veritabanına bağlanmayı, veri çekmeyi ve güncellemeyi öğrenmeden önce bazı temel bilgileri daha öğrenmeniz gerekecek.

Başlıyoruz ...

- Asp dilinde yaşanılan zamanın sadece yıl kısmını almak için (Örnek : 2009) kod olarak şu yazılmalıdır "&lt;%=year(date)%&gt;".

Yukarıdaki kodda asp dilinde zamanın yılını alma anlamına geliyor. Eğer tek bir veri çekecek veya işlem yaptıracak isek "&lt;%=" kullanılır ve kod yazıldıktan sonuna "%&gt;" yazılır.

- "Now()" kodu yaşanılan zamanın gününü, ayını, yılını, saatini, dakikasını ve saniyesini belirtir. Bu kod ile tarih hakkında ayrıntılı bir bilgiye sahip olmak mümkün. Bu kod "&lt;%=Now()%&gt;" şeklinde kullanılabilir.

- "FormatDateTime" fonksiyonu ile yaşanılan zamanı veya veritabanından çekilen bir tarihi verinin sadece gün,ay ve yıl olarak yazılmasını sağlayabilirsiniz. Bu kod "&lt;%=FormatDateTime(tarih)%&gt;" şeklinde kullanılabilir.

- "Response.write" komutu ile sunucudan tarayıcınıza kodlar yazdırabilirsiniz. Kodu yazdıktan sonra "" satırlarını ekleyerek arasına yazmak istediğin metinleri yazabilirsiniz. Bu kod "&lt;% response.write "Metin" %&gt;" şeklinde kullanılabilir.

- "Response.redirect" komutu ile sayfa yönlendirmesi yapabilirsiniz. Örnek olarak kayıt tamamlandıktan sonra veye üye girişi gerçekleştikten sonra anasayfaya yönlendirebilirsiniz. Kodu "Response.redirect" yazdıktan sonra "" satırlarını ekleyerek arasına yönlendireceğiniz sayfayı ve uzantısını yazabilirsiniz. Bu kod "&lt;% Response.redirect "default.asp" %&gt;" şeklinde kullanılabilir.

- "&lt;a href="" target=""&gt;" komutu ile "href" yazan kısma yönlendirilecek sayfayı "target" kısmına ise "_blank" yeni sayfa ve "_self" aynı sayfada yönlendirme gibi bazı ayarları yapabilirsiniz. Daha sonra komut sonuna "&lt;/a&gt;" yazmanız gerekecek. Bu kodun arasına resim, metin tıklandığında yönlendirmesini istediğiniz herşeyi yapabilirsiniz. Kodu "&lt;a href="default.asp" target="_self"&gt;Anasayfaya Git&lt;/a&gt;" şeklinde kullanabilirsiniz.

- Resim eklemek için "&lt;img src="" border="" height="" width="" alt="" align=""&gt;" komut satırını kullanabilirsiniz. "src" kısmı resmin bulunduğu yol, "border" çerçeve kalınlığı, "height" resmin boyu, "width" resmin eni, "alt" resme gelince çıkacak metin ve "align" ise resmi hizalamak için kullanılır. "border" sayıdır, "align" ise "absmiddle, right, left" gibi değerler alır. Bu kod örnek olarak "&lt;img src="images/logo.gif" width="468" height="60" border="0" alt="Pckoruma Logo" algin="absmiddle"&gt;" şeklinde kullanılabilir.

- "&lt;font color="" style=""&gt;" komutu ile yazınızın sitilini belirleyebilirsiniz. "&lt;font&gt;" şeklinde kullanırsınız. Komut satırı sonuna ise "&lt;/font&gt;" yazmanız gerekmektedir. Asp dilinde açılan her tag kapatılmalıdır. "color" ile karşınıza çıkan listeden renk seçebilir veya renk kodlarını biliyorsanız (Örnek : #000000 -&gt; siyah) kendiniz de yazabilirsiniz. Css bilgisi olanlar "style" özelliğini rahatlıkla kullanacaklardır. Her bir özellik sonunda ek özellik ekleyecek iseniz ";" kullanmalısınız. Mesela font büyüklüğünü belirledikten sonra ";" yazıp sonra font türünü belirlersiniz. Bu kod örnek olarak "&lt;font color="#000000" style="font-family:Arial; font-size:9px"&gt;Metin&lt;/font&gt;" şeklinde kullanabilirsiniz.