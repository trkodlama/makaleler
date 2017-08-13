---
ID: 159
post_title: 'LaTeX&#8217;de Resim Ekleme'
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/latex-de-resim-ekleme-159.html
published: true
post_date: 2011-04-22 18:30:37
---
Merhaba arkadaşlar,

Önceki yazımda bir yazıyı nasıl renklendireceğimizi anlattım. Şimdi ise LaTeX'de nasıl resim ekleyeceğimizi anlatıyorum. Ve yazımızın sonunda ortalanmış bir resim altına da farklı renklerle yazılmış Eskisehir Osmangazi Universitesi yazalım.
<h2>Paketi Ekleme</h2>
LaTeX'de resim ekleme işlemleri için bir paket eklemeniz gerekiyor. documentclass'dan hemen sonra aşağıdaki satırı ekleyin:
<pre class="prettyprint lang-latex" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">usepackage[pdftex]{graphicx}</pre>
Bu sınıf sayesinde resim ekleyebileceksiniz.
<h2>Resim Ekleme</h2>
Resim eklemek için aşağıdaki kodu kullanıyoruz:
<pre class="prettyprint lang-latex" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">includegraphics{resim}</pre>
{resim} kısmına resim adını yazıyoruz.

Şimdi hemen bir örnek yapalım. Öncelikle <a href="http://www.trkodlama.com/wp-content/uploads/2012/03/ogu.jpg">şu resmi</a> indirin. Daha sonra bu resmi LaTeX dosyanızı kaydedeceğiniz klasörün içine atın. Şimdi yeni oluşturduğunuz tex dosyasının içine aşağıdaki kodu ekleyin:
<pre class="prettyprint lang-latex" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">documentclass{article}
usepackage[pdftex]{graphicx}

begin{document}
begin{center}
includegraphics{ogu.jpg}
end{center}
end{document}</pre>
Şimdi sayfanızı ogu.jpg dosyasıyla aynı klasör olmak şartı ile kaydedin. Sonra PDF olarak görüntüleyin. PDF çıktısı aşağıdaki gibi olacaktır:

<a href="http://www.trkodlama.com/wp-content/uploads/2012/03/ogu.jpg"><img class="aligncenter size-full wp-image-154" title="ogu" src="http://www.trkodlama.com/wp-content/uploads/2012/03/ogu.jpg" alt="" width="200" height="148" /></a>

Şimdi de bu yazının altına renkli halde Eskisehir Osmangazi Universitesi yazalım. Daha önceki yazımızda(<a title="LaTeX’de Yazıyı Renklendirme" href="http://www.trkodlama.com/diger-diller/latexde-yaziyi-renklendirme-152.html">LaTeX'de Yazıyı Renklendirme</a>) yazıyı nasıl renklendireceğinizi anlatmıştım. Renkleri siz kendinize göre düzenlersiniz:
<pre class="prettyprint lang-latex" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">documentclass{article}
usepackage{color}
usepackage[pdftex]{graphicx}

begin{document}

definecolor{renkbir}{RGB}{255,222,111}
definecolor{renkiki}{RGB}{0,222,111}
definecolor{renkuc}{RGB}{140,80,255}

begin{center}
includegraphics{ogu.jpg}
textcolor{renkbir}{Eskisehir} textcolor{renkiki}{Osmangazi} textcolor{renkuc}{Universitesi}
end{center}

end{document}</pre>
Bu kodu derlediğiniz zaman PDF çıktısı aşağıdaki gibi olacaktır:
<p style="text-align: center;"><a href="http://www.trkodlama.com/wp-content/uploads/2012/03/ogu.jpg"><img class="aligncenter size-full wp-image-154" title="ogu" src="http://www.trkodlama.com/wp-content/uploads/2012/03/ogu.jpg" alt="" width="200" height="148" /></a><span style="color: #ff9900;">Eskisehir</span> <span style="color: #99cc00;">Osmangazi</span> <span style="color: #993366;">Universitesi</span></p>
Bu da bizim tam olarak istediğimiz olaydır. Umarım açıklayıcıdır arkadaşlar. Takıldığınız yerleri forumdan veya yorum olarak aşağıdaki formdan sorabilirsiniz. Hepinize kolay gelsin,