---
ID: 152
post_title: 'LaTeX&#8217;de Yazıyı Renklendirme'
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/latex/latexde-yaziyi-renklendirme-152.html
published: true
post_date: 2011-04-22 18:01:57
---
Merhaba arkadaşlar,
Bu makalede LaTeX'de yazdığınız yazıları nasıl renklendireceğinizi anlatıyorum.. Umarım hepiniz için faydalı olur. Bunu yazmamdaki en büyük etken Osmangazi Üniversitesi Matematik ve Bilgisayar Bilimleri'nde okuyan arkadaşlarıma yardımcı olmak..
<h2>Paketi Ekleme</h2>
LaTeX'de yazıyı renklendirmek için pakete ihtiyacımız var.. Bunun için
<pre class="prettyprint lang-javascript" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">usepackage{color}</pre>
Kodunu documentclass'dan hemen sonra ekliyoruz.
<h2>Yazıyı Renklendirme</h2>
Yazdığınız yazıyı renklendirmenin en basit yolu aşağıdaki şekilde yapılır:
<pre class="prettyprint lang-latex" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">textcolor{renk}{yazı}</pre>
Burada {yazı} kısmına yazdıklarınız {renk} kısmında belirttiğiniz renk ile renklendirilecektir. Aynı zamanda bunu şu şekilde de yapabilirsiniz:
<pre class="prettyprint lang-latex" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">{color{renk} yazı}</pre>
Ayrıca bütün sayfanın arkaplanını da şu şekilde değiştirebilirsiniz:
<pre class="prettyprint lang-latex" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">pagecolor{renk}</pre>
Detaylı örnekleri aşağıda yazacağım..

LaTeX'de önceden tanımlanmış birkaç ana renk bulunur.. Bunlar: white, black, red, green, blue, cyan, magenta, yellow. Yukarıda gördüğünüz kodlarda renk alanlarına bu renk isimlerinden birini yazdığınız anda yazılar ilgili renkle renklendirilmiş olacaktır.

Fakat siz standartın dışında bir renk belirlemek isterseniz bunu LaTeX derleyicisine tanımlamanız gerekir. Bu tanımlama işleminde RGB denilen metod kullanılır.
<h2>RGB Nedir?</h2>
RGB'nin açılımı Red Green ve Blue'dur.. Yani Kırmızı Yeşil Mavi. Bunlar yeni belirleyeceğiniz rengin tonlarını belirlersiniz. Yani Kırmızılık şu kadar olsun. Mavilik şu kadar ve yeşillik de şu kadar olsun. RGB'nin standart yazılışı kırmızılık,yesillik,mavilik şeklindedir. Ve verdiğiniz değerler 0 ile 255 arasında olmak zorundadır. Mesela Beyazın RGB kodu 255,255,255 dir. Kırmızının ki 255, 0, 0 dır. Mavinin ki 0,0,255 dir. Dilediğiniz bir renk için bunları nasıl elde ederim diyorsanız bilgisayarınızda Paint'i açın. Özel Renk Tanımla'ma bölümüne gidin. Ve bir tane renk seçin. Kutucuklarda R(Red), G(Green), B(Blue) şeklinde ifadeler vardır. Bunlar bizim bahsettiğimiz RGB işte. Buradan edinebilirsiniz.

Peki bu renkleri nasıl kullanacağız LaTeX'de. O da şöyle:
<pre class="prettyprint lang-latex" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">definecolor{renkadi} {RGB}{ozellikleri}</pre>
Örnek yapalım hemen. 255, 222, 111 rengini tanımlayalım:
<pre class="prettyprint lang-latex" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">definecolor{bizimrengimiz}{RGB}{255,222,111}</pre>
Artık "bizimrengimiz" diye bir renk oluşturduk. Şimdi bütün bir örnek yapalım ve sonucunu görelim:
<pre class="prettyprint lang-latex" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">documentclass{article}
usepackage{color}
begin{document}

    definecolor{renkbir}{RGB}{255,222,111}
    definecolor{renkiki}{RGB}{0,222,111}
    definecolor{renkuc}{RGB}{140,80,255}

    begin{center}
        textcolor{renkbir}{Eskisehir} textcolor{renkiki}{Osmangazi} textcolor{renkuc}{Universitesi}
    end{center}

end{document}</pre>
Burada begin{center} ve end{center} kullanarak yazımızı ortaladık. Daha sonra definecolor ile üç tane renk belirledik. Bunlar renbir(255,222,111), renkiki(0,222,111) ve renkuc{140,80,255}. Bu renklerle daha sonra yazılarımızı renklendirdik. Yukarıdaki kodun PDF çıktısı aşağıdaki gibi olacaktır:
<p style="text-align: center;"><span style="color: #ff9900;">Eskisehir</span> <span style="color: #99cc00;">Osmangazi</span> <span style="color: #993366;">Universitesi</span></p>
LaTeX'de renklendirme bu kadar basit işte. Sorularınızı forumumuzdan veya yorum olarak aşağıdaki formdan iletebilirsiniz.
Kolay gelsin,