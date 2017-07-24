---
ID: 176
post_title: 'LaTeX&#8217;de Slayt Hazırlama'
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/latex/latex-de-slayt-hazirlama-176.html
published: true
post_date: 2011-05-02 18:55:56
---
Merhaba arkadaşlar,

LaTeX'i ben de yeni yeni öğreniyorum. Fakat zevkli bir dil.. Neyse lafı hiç uzatmayalım. Bu yazıda LaTeX'de nasıl slayt yapılacağını anlatıyorum.
LaTeX'de varsayılan sayfa düzeni "portrait" dir. Fakat bu bazen problem olabilir özellikle slaytlarda. Bunun için biz sayfa düzeni olarak "landscape" kullanacağız. Bunu yapmak geometry paketine ihtiyaç duyacağız.
<pre class="prettyprint lang-latex" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">documentclass[landscape]{slides}
usepackage[landscape]{geometry}</pre>
documentclass'ımızı "landscape" sayfa düzenli slayt olarak belirlemiş olduk. LaTeX'de slaytlar şu şekilde hazırlanır:
<pre class="prettyprint lang-latex" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">begin{document}
    begin{slide}
    Burası 1...
    end{slide}
    begin{slide}
    Burası 2...
    end{slide}
end{document}</pre>
Şimdi slaydımızın içeriğini belirleyelim ve hazırlamaya başlayalım. <a title="Lorem Ipsum Nedir?" href="http://www.trkodlama.com/makaleler/lorem-ipsum-nedir-99.html">Lorem Ipsum Nedir?</a> yazısını slayt olarak hazırlayalım.

Öncelikle sayfamızın başına eklememiz gereken documentclass ve usepackage komutlarının neler olduğuna bakalım:
<pre class="prettyprint lang-latex" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">documentclass[landscape]{slides}
usepackage[turkish]{babel} %türkçe karakterler için
usepackage[latin5]{inputenc} %türkçe karakterler için
usepackage[T1]{fontenc} %türkçe karakterler için
usepackage{color} %renkli yazabilmek için
usepackage[landscape]{geometry} %sayfa düzenini landscape yapmak için</pre>
Burdan sonra begin{document} ile içeriğimize geçiyoruz. Her bir bölümümüzü begin{slide}....end{slide} arasına yazıyoruz. Bu sayede slaytların nerden nereye geçeceğini belirliyoruz. Hemen başlayalım:
<pre class="prettyprint lang-latex" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">begin{document}
    begin{slide}
        textcolor{blue}{Lorem Ipsum Nedir?}
        begin{itemize}
            item{textbf{Lorem Ipsum}, dizgi ve baskı endüstrisinde kullanılan mıgır metinlerdir. Lorem Ipsum, adı bilinmeyen bir matbaacının bir hurufat numune kitabı oluşturmak üzere bir yazı galerisini alarak karıştırdığı 1500'lerden beri endüstri standardı sahte metinler olarak kullanılmıştır. Beşyüz yıl boyunca varlığını sürdürmekle kalmamış, aynı zamanda pek değişmeden elektronik dizgiye de sıçramıştır. 1960'larda Lorem Ipsum pasajları da içeren Letraset yapraklarının yayınlanması ile ve yakın zamanda Aldus PageMaker gibi Lorem Ipsum sürümleri içeren masaüstü yayıncılık yazılımları ile popüler olmuştur.}
        end{itemize}
    end{slide}

    begin{slide}
        textcolor{blue}{Nereden Gelir?}
        begin{itemize}
            item{Yaygın inancın tersine, Lorem Ipsum rastgele sözcüklerden oluşmaz. Kökleri M.Ö. 45 tarihinden bu yana klasik Latin edebiyatına kadar uzanan 2000 yıllık bir geçmişi vardır. Virginia'daki Hampden-Sydney College'dan Latince profesörü Richard McClintock, bir Lorem Ipsum pasajında geçen ve anlaşılması en güç sözcüklerden biri olan 'consectetur' sözcüğünün klasik edebiyattaki örneklerini incelediğinde kesin bir kaynağa ulaşmıştır. Lorm Ipsum, Çiçero tarafından M.Ö. 45 tarihinde kaleme alınan "de Finibus Bonorum et Malorum" (İyi ve Kötünün Uç Sınırları) eserinin 1.10.32 ve 1.10.33 sayılı bölümlerinden gelmektedir. Bu kitap, ahlak kuramı üzerine bir tezdir ve Rönesans döneminde çok popüler olmuştur. Lorem Ipsum pasajının ilk satırı olan "Lorem ipsum dolor sit amet" 1.10.32 sayılı bölümdeki bir satırdan gelmektedir.}
            item{1500'lerden beri kullanılmakta olan standard Lorem Ipsum metinleri ilgilenenler için yeniden üretilmiştir. Çiçero tarafından yazılan 1.10.32 ve 1.10.33 bölümleri de 1914 H. Rackham çevirisinden alınan İngilizce sürümleri eşliğinde özgün biçiminden yeniden üretilmiştir.}
        end{itemize}
    end{slide}

    begin{slide}
        textcolor{blue}{Neden Kullanırız?}
        begin{itemize}
            item{Yinelenen bir sayfa içeriğinin okuyucunun dikkatini dağıttığı bilinen bir gerçektir. Lorem Ipsum kullanmanın amacı, sürekli 'buraya metin gelecek, buraya metin gelecek' yazmaya kıyasla daha dengeli bir harf dağılımı sağlayarak okunurluğu artırmasıdır. Şu anda birçok masaüstü yayıncılık paketi ve web sayfa düzenleyicisi, varsayılan mıgır metinler olarak Lorem Ipsum kullanmaktadır. Ayrıca arama motorlarında 'lorem ipsum' anahtar sözcükleri ile arama yapıldığında henüz tasarım aşamasında olan çok sayıda site listelenir. Yıllar içinde, bazen kazara, bazen bilinçli olarak (örneğin mizah katılarak), çeşitli sürümleri geliştirilmiştir.}
        end{itemize}
    end{slide}
end{document}</pre>
Yukarıdaki örnekte başlıkları renkli yazdık. Bunu daha önce <a title="LaTeX’de Yazıyı Renklendirme" href="http://www.trkodlama.com/makaleler/latex/latexde-yaziyi-renklendirme-152.html">LaTeX'de Yazıyı Renklendirme</a> yazımızda anlatmıştım. Ayrıca burda yabancı olduğumuz diğer komut ise textbf{} dir. Bu da yazıyı kalın yazmamızı sağlar. Şimdi sizlere son halini verelim:
<pre class="prettyprint lang-latex" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">documentclass[landscape]{slides}
usepackage[turkish]{babel}
usepackage[latin5]{inputenc}
usepackage[T1]{fontenc}
usepackage{color}
usepackage[landscape]{geometry}

begin{document}
    begin{slide}
        textcolor{blue}{Lorem Ipsum Nedir?}
        begin{itemize}
            item{textbf{Lorem Ipsum}, dizgi ve baskı endüstrisinde kullanılan mıgır metinlerdir. Lorem Ipsum, adı bilinmeyen bir matbaacının bir hurufat numune kitabı oluşturmak üzere bir yazı galerisini alarak karıştırdığı 1500'lerden beri endüstri standardı sahte metinler olarak kullanılmıştır. Beşyüz yıl boyunca varlığını sürdürmekle kalmamış, aynı zamanda pek değişmeden elektronik dizgiye de sıçramıştır. 1960'larda Lorem Ipsum pasajları da içeren Letraset yapraklarının yayınlanması ile ve yakın zamanda Aldus PageMaker gibi Lorem Ipsum sürümleri içeren masaüstü yayıncılık yazılımları ile popüler olmuştur.}
        end{itemize}
    end{slide}

    begin{slide}
        textcolor{blue}{Nereden Gelir?}
        begin{itemize}
            item{Yaygın inancın tersine, Lorem Ipsum rastgele sözcüklerden oluşmaz. Kökleri M.Ö. 45 tarihinden bu yana klasik Latin edebiyatına kadar uzanan 2000 yıllık bir geçmişi vardır. Virginia'daki Hampden-Sydney College'dan Latince profesörü Richard McClintock, bir Lorem Ipsum pasajında geçen ve anlaşılması en güç sözcüklerden biri olan 'consectetur' sözcüğünün klasik edebiyattaki örneklerini incelediğinde kesin bir kaynağa ulaşmıştır. Lorm Ipsum, Çiçero tarafından M.Ö. 45 tarihinde kaleme alınan "de Finibus Bonorum et Malorum" (İyi ve Kötünün Uç Sınırları) eserinin 1.10.32 ve 1.10.33 sayılı bölümlerinden gelmektedir. Bu kitap, ahlak kuramı üzerine bir tezdir ve Rönesans döneminde çok popüler olmuştur. Lorem Ipsum pasajının ilk satırı olan "Lorem ipsum dolor sit amet" 1.10.32 sayılı bölümdeki bir satırdan gelmektedir.}
            item{1500'lerden beri kullanılmakta olan standard Lorem Ipsum metinleri ilgilenenler için yeniden üretilmiştir. Çiçero tarafından yazılan 1.10.32 ve 1.10.33 bölümleri de 1914 H. Rackham çevirisinden alınan İngilizce sürümleri eşliğinde özgün biçiminden yeniden üretilmiştir.}
        end{itemize}
    end{slide}

    begin{slide}
        textcolor{blue}{Neden Kullanırız?}
        begin{itemize}
            item{Yinelenen bir sayfa içeriğinin okuyucunun dikkatini dağıttığı bilinen bir gerçektir. Lorem Ipsum kullanmanın amacı, sürekli 'buraya metin gelecek, buraya metin gelecek' yazmaya kıyasla daha dengeli bir harf dağılımı sağlayarak okunurluğu artırmasıdır. Şu anda birçok masaüstü yayıncılık paketi ve web sayfa düzenleyicisi, varsayılan mıgır metinler olarak Lorem Ipsum kullanmaktadır. Ayrıca arama motorlarında 'lorem ipsum' anahtar sözcükleri ile arama yapıldığında henüz tasarım aşamasında olan çok sayıda site listelenir. Yıllar içinde, bazen kazara, bazen bilinçli olarak (örneğin mizah katılarak), çeşitli sürümleri geliştirilmiştir.}
        end{itemize}
    end{slide}
end{document}</pre>
Umarım anlaşılır olmuştur,

Kolay gelsin,