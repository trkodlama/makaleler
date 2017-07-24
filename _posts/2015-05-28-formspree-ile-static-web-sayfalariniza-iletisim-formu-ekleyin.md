---
ID: 5795
post_title: >
  Formspree ile Static Web Sayfalarınıza
  İletişim Formu Ekleyin
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/web-tasarim/formspree-ile-static-web-sayfalariniza-iletisim-formu-ekleyin-5795.html
published: true
post_date: 2015-05-28 04:41:26
---
Bu makalede statik web sayfalarınıza esnek ve dinamik iletişim formunu nasıl kolay bir şekilde ekleyebileceğinizi anlatacağım.
<h3>Problem</h3>
<strong>Jekyll</strong> yardımıyla veya birkaç <strong>HTML dosyası</strong> kullanarak statik bir web sitesi hazırladınız. Fakat bir iletişim formuna ihtiyaç duydunuz. Online herhangi bir hizmetten faydalanabilirsiniz. Size iframe vs. bir kod verirler ve sizde onu sitenize eklersiniz vs. Fakat bu tarz harici eklemelerde malesef ki siz görsel tasarım konusunda kısıtlanmış olacaksınız.
<h3>Çözüm</h3>
Peki ya size bir hizmet formunuza komple hakim olmanıza olanak tanıyorsa? <strong><a href="http://formspree.io/" target="_blank">Formspree</a></strong> size tam olarak bu imkanı tanıyor. Hiç bir JavaScript veya PHP bilgisine ihtiyaç duymadan HTML ile kendi iletişim formlarınızı hazırlamanıza yardımcı oluyor.

<a href="http://www.trkodlama.com/wp-content/uploads/2015/05/formspree-main-image.png"><img class="aligncenter size-full wp-image-5796" src="http://www.trkodlama.com/wp-content/uploads/2015/05/formspree-main-image.png" alt="formspree-main-image" width="600" height="300" /></a>
<h3>Formunuzu Oluşturun</h3>
İlk ihtiyacınız olan HTML ile oluşturulmuş bir form. Benim hazırladığım form insanların benimle en kolay ve hızlı bir şekilde iletişime geçmelerini sağlayacak. Sadece isimlerini, e-posta adreslerini ve mesajlarını isteyeceğim.
<pre class="prettyprint lang-html" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;form id="iletisim" method="POST"&gt;
 &lt;input type="text" placeholder="İsminiz"&gt;
 &lt;input type="email" placeholder="E-posta adresiniz"&gt;
 &lt;textarea placeholder="Mesajınız"&gt;&lt;/textarea&gt;
 &lt;input type="submit" value="Gönder"&gt;
&lt;/form&gt;</pre>
Gördüğünüz gibi <em><span style="text-decoration: underline;">&lt;form&gt;</span></em> etiketinin arasına form elemanlarımı ekledim ve <em><span style="text-decoration: underline;">Submit</span></em> butonu oluşturdum. <em><span style="text-decoration: underline;">iframe</span></em> vs. gibi görsel olarak önüme engel teşkil edebilecek hiç bir içerik yok.
<h3>Özelliklerini Ekleyelim</h3>
<strong>Formspree</strong>'nin formunuzu işleyebilmesi için <em><span style="text-decoration: underline;">&lt;form&gt;</span> </em>etiketinize aşağıdaki özellikleri(attributes) eklemelisiniz.
<pre class="prettyprint lang-html" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;form id="iletisim" action="//formspree.io/eposta@adresiniz.com" method="POST"&gt;</pre>
Burada <em><span style="text-decoration: underline;">eposta@adresiniz.com</span></em> kısmını kendinize göre güncellemelisiniz.

Bir sonraki işlem ise bütün form inputlarına <strong>name</strong> özelliğini tanımlamak olacak. Form her gönderildiğinde size gelecek olan e-postada bu name karşısında formu dolduran kişinin girdiği değer olacak. <a href="https://github.com/asm-products/formspree#advanced-features" target="_blank">Name için <strong>Formspree</strong>'nin özel isimlerini de kullanabilirsiniz</a>.
<pre class="prettyprint lang-html" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;form id="iletisim" method="POST"&gt;
 &lt;input type="text" name='isim' placeholder="İsminiz"&gt;
 &lt;input type="email" name='_replyto' placeholder="E-posta adresiniz"&gt;
 &lt;textarea name='mesaj' placeholder="Mesajınız"&gt;&lt;/textarea&gt;
 &lt;input type="submit" value="Gönder"&gt;
&lt;/form&gt;</pre>
Farkettiyseniz isim ve mesaj kısmına normal <strong>name </strong>atadım fakat email için <strong>_replyto</strong> yazdım. Bu ismi Formspree tanıyacak ve size gönderilen formu cevaplamak istediğiniz alıcı yerine direkt olarak formu gönderen kişinin mail adresinin yazılmasını sağlayacak.
<h3>Kibarlığınızı belli edin :)</h3>
Formu gönderen kişilere teşekkür sayfalarına yönlendirmek için de bir input alanı oluşturabiliriz. Bu alanı hidden tipinde oluşturacağız ve name için <strong>_next </strong>adını vereceğiz.
<pre class="prettyprint lang-html" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;input type="hidden" name="_next" value="//siteniz.com/tesekkurler.html" /&gt;</pre>
<h3>Konu</h3>
Formspree'nin size göndereceği mailin konusunu da ayarlayabilirsiniz.
<pre class="prettyprint lang-html" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;input type="hidden" name="_subject" value="İletişim Formu Dolduruldu" /&gt;</pre>
<h3>Formunuzu Biraz Daha Güvenli Hale Getirelim</h3>
Formspree "<strong>honeypot</strong>" diye isimlendirilen spam önleme yöntemi kullanmaktadır. Bu yöntem şöyle çalışır. Formunuza <strong>_gotcha</strong> ismiyle bir input daha eklersiniz ve bunu css ile gizlerseniz. Kullanıcılar bu formu göremez fakat botlar görür ve otomatik olarak içini doldururlar. Bu form alanı dolu olursa <strong>Formspree</strong> bunun bir spam girişimi olduğunu anlar ve işlemi gerçekleştirmez. Bu sayede hem Formspree rahatlar hemde siz saatte belki 100lerce spam e-posta ile uğraşmaktan kurtulursunuz.
<pre class="prettyprint lang-html" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;input type="text" name="_gotcha" style="display:none" /&gt;</pre>
Güvenliği bir tık daha öteye taşımak isterseniz e-posta adresinizi botlardan JavaScript ile bir parça daha gizleyebilirsiniz. Bu gizleme ve formumuzun son hali aşağıdaki gibidir:
<pre class="prettyprint lang-html" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;form id="iletisim" method="POST"&gt;
&lt;input type="text" name="isim" placeholder="İsminiz"&gt;
&lt;input type="email" name="_replyto" placeholder="E-posta adresiniz"&gt;
&lt;input type="hidden" name="_subject" value="İletişim Formu Dolduruldu" /&gt;
&lt;textarea name="mesaj" placeholder="Mesajınız"&gt;&lt;/textarea&gt;
&lt;input type="text" name="_gotcha" style="display:none" /&gt;
&lt;input type="submit" value="Gönder"&gt;
&lt;/form&gt;
&lt;script&gt;
var iletisim = document.getElementById('iletisim');
iletisim.setAttribute('action', '//formspree.io/' + 'eposta' + '@' + 'adresiniz' + '.' + 'com');
&lt;/script&gt;</pre>
Burada &lt;form&gt; etiketinin <span style="text-decoration: underline;"><strong>action</strong></span> özelliğini çıkardım ve bunu JavaScript ile ekledim. Bu sayede e-posta adresimizin güvenliğini de bir tık öteye taşıdık.
<h3>Formunuzu Test Edin ;)</h3>
Son adım da formumuzun çalışıp çalışmadığını test edeceğiz. Formunuzu eklediğiniz sayfaya tarayıcı ile erişim sağlayın ve daha sonra normal bir ziyaretçiymiş gibi formu doldurup gönderin. Formspree'den e-posta adresinizi doğrulamanızı isteyen bir e-mail alacaksınız.

<a href="http://www.trkodlama.com/wp-content/uploads/2015/05/confirm.png"><img class="aligncenter size-full wp-image-5798" src="http://www.trkodlama.com/wp-content/uploads/2015/05/confirm.png" alt="confirm" width="600" height="400" /></a>

E-posta adresinize gönderilen doğrulama linkine tıklayın ve bu kadar.

<a href="http://www.trkodlama.com/wp-content/uploads/2015/05/confirmed.png"><img class="aligncenter size-full wp-image-5799" src="http://www.trkodlama.com/wp-content/uploads/2015/05/confirmed.png" alt="confirmed" width="600" height="400" /></a>

Bu formu eklediğiniz farklı sayfalar için bu aşamayı her seferinde tekrarlamanız gerekmektedir.

Umarım faydalı olmuştur, bu yazı çeviridir :) kolay gelsin,