---
ID: 88
post_title: >
  HTML Uzantılı Dosyalarda PHP
  Çalıştırma
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/html-uzantili-dosyalarda-php-calistirma-88.html
published: true
post_date: 2010-08-15 08:29:43
---
Bir web sayfasına erişildiğinde sunucu web sayfasının uzantısına bakarak bu dosyayı nasıl işleyeceğine karar verir. Genellikle sayfa uzantısını .htm veya .html olarak görürse direkt olarak tarayıcıya çalıştırması için gönderir. Çünkü bu sayfanın sunucuda yorumlanması gerekmiyor. Fakat eğer uzantıyı .php(.shtml veya .asp vb olabilir) olarak algılarsa bu dosyaların öncelikle sunucu tarafından yorumlanması gerektiğini bilir ve tarayıcıya göndermeden önce yorumlanmasını sağlar.

Şimdi asıl problem şu: Muhteşem bir script buldunuz veya yazdınız ve bunu kendi sitenizin sayfalarına entegre etmek istiyorsunuz fakat sayfalarınızın uzantısı <strong>.php</strong> değil. Yani sayfalarınız dosyam.html şeklinde. Bu sayfalarınıza da PHP kodlarını eklemeniz ekrana aynen basılmalarını sağlamaktan başka birşey yapmayacaktır. Dosyanızın adını dosyam.php olarak değiştirmeniz sitenizin o sayfasına dışarıdan gelen bağlantıları etkileceği gibi arama motoru rütbelerinizi de olumsuz olarak etkileyecektir. Peki ne yapabilirsiniz?

<strong>.html</strong> uzantılı sayfalarda PHP'yi çalıştırmanız için <strong>.htaccess</strong> dosyanıza bir satır komut eklemeniz yeterli olacaktır. Bu dosya bir çok FTP programı tarafından gizlenebilir. Dosyayı görebilmek için kullandığınız <strong>FTP</strong> programının ayarlarından gizli dosyaları göstermesi için gerekli işlemleri yapın. Daha sonra <strong>.html</strong> uzantılı dosyalarınızda PHP çalıştırabilmek için aşağıdaki satırı ekleyin:
<pre class="line-numbers"><code class="language-apacheconf">AddType application/x-httpd-php .html</code></pre>
Bu sayede çok daha farklı uzantılarında çalışmasını sağlayabilirsiniz. Mesela dosya adınızı dosyam.tr olarak değiştirdiğinizde yukarıdaki kodun sonuna .tr eklemeniz yeterli olacaktır. Artık hem .html hem de .tr uzantılı dosyalarda PHP kodlarını çalıştırabilirsiniz.
<pre class="line-numbers"><code class="language-apacheconf">AddType application/x-httpd-php .html .tr</code></pre>
Bu uzantı sayısını aynı mantıkla arttırabilirsiniz.
Uzantı değiştirme işleminizin sadece bir dosyanız için geçerli olmasını istiyorsanız aşağıdaki gibi düzenleyin ilgili satırı:
<pre class="line-numbers"><code class="language-apacheconf">AddType application/x-httpd-php .tr</code></pre>
Bu satır sayesinde sadece dosyam.tr sayfası için PHP kodlarının çalıştırılmasına müsaade etmiş olursunuz. dosyamiki.tr dosyasında PHP kodlarınız çalışmamaya devam edecektir. Umarım faydalı bir makale olmuştur, Kolay gelsin,