---
ID: 173
post_title: HTML4 Tablo Kullanımı
author: prodigy
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/web-tasarim-2/html/html-bilgileri-2-173.html
published: true
post_date: 2011-04-30 18:47:36
---
Bu dersimizde sizlere asp ile tablo, sütun, blok oluşturmayı öğreteceğim. Bunlar ilerde sizlerin çok kullanacağı temel bilgilerdendir. Eğer bunları öğrenmez veya tam öğrenemezseniz asp kullanmayı bilseniz bile bunu sayfaya yansıtamaz ve görsellik/ tasarım adına hiçbirşeyi yapamazsınız.

Tablo nedir ? Tablo web sitenizi oluşturmak için ana hatları ile arayüzü belirlemeye yarar. Tablo oluşturmadan ne sütun ne de blok oluşturabilirsiniz. Önce basit bir tablo oluşturalım.

Örnek :
<pre class="prettyprint lang-html" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;table border="1" height="100" width="100"&gt;
    &lt;tr&gt;
        &lt;td&gt;Örnek bir tablo, sütun ve blok&lt;/td&gt;
    &lt;/tr&gt;
&lt;/table&gt;</pre>
- Yukarda "border" tablonun çerçevesini, "height" uzunluğunu, "width" ise enini belirliyor. Bunları "&lt;tr&gt;" veya "&lt;td&gt;" yani blok ve sütun içinde girebilirsiniz. Yani sütunun ve blokun boyunu, enini örnek tablodaki gibi belirleyebilirsiniz. Örnek verecek olursak..
<pre class="prettyprint lang-html" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;table border="1" height="200" width="200"&gt;
    &lt;tr&gt;
        &lt;td width="100"&gt;Örnek tablo, blok ve sütundur. Bu sütunun eni 100'dür&lt;/td&gt;
        &lt;td width="100"&gt;Örnek tablo, blok ve sütundur. Bu sütunun eni 100'dür&lt;/td&gt;
    &lt;/tr&gt;
&lt;/table&gt;</pre>
- Burada 200 birimlik bir tablo ve içerisinde 1 blok, 2 sütun (100 birimlik, tablo 2 eş sütuna bölünmüş) göreceksiniz. Sütunlar blokla beraber kullanılır. Bir blokta hiç sütun kullanmayabilirsiniz. Yani "&lt;td&gt;" ve "&lt;/td&gt;" kısımlarını çıkarabilir sadece bloka veri koydurabilirsiniz. Bu sadece bloku 1 parça olarak gösterecek ve herhangi bir bloku bölme/sütunlama yapmayacaktır.

- Sütunların enini ve boyunu değiştirdik. Blokların enini ve boyunu değiştirmemiz de mümkün. "height" ve "width"'i kullanarak blokun görsel yönden ayarlarını yapmak mümkün. Örnek verecek olursak eğer :
<pre class="prettyprint lang-html" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;table border="1" height="200" width="200"&gt;
    &lt;tr width="100" height="100"&gt;
        &lt;td&gt;Örnek tablo, blok ve sütundur. Bu blokun eni 100'dür&lt;/td&gt;
    &lt;/tr&gt;
    &lt;tr width="100" height="100"&gt;
        &lt;td&gt;Örnek tablo, blok ve sütundur. Bu blokun eni 100'dür&lt;/td&gt;
    &lt;/tr&gt;
&lt;/table&gt;</pre>
- Burada 2 adet blok oluşturduk. Bu blokların her biri 100 birim eninde ve 100 birim genişliğinde. Kodları *.html dosyası olarak kaydedip tarayıcınızla çalıştırdığınızda tablonun 2 bloktan oluştuğunu görebilirsiniz. Bu blokların içerisinde 1'er adet sütun var. Dilerseniz bunları 2'şer sütun veya istediğiniz kadar sütun şeklinde göstertebilirsiniz. Size 2'şer sütunlu olanını da göstereyim haydi
<pre class="prettyprint lang-html" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;table border="1" height="200" width="200"&gt;
    &lt;tr width="100" height="100"&gt;
        &lt;td width="50"&gt;Bu blokun eni 100'dür ve sütunlar 50 birimdir&lt;/td&gt;
        &lt;td width="50"&gt;Bu blokun eni 100'dür ve sütunlar 50 birimdir&lt;/td&gt;
    &lt;/tr&gt;
    &lt;tr width="100" height="100"&gt;
        &lt;td width="50"&gt;Bu blokun eni 100'dür ve sütunlar 50 birimdir&lt;/td&gt;
        &lt;td width="50"&gt;Bu blokun eni 100'dür ve sütunlar 50 birimdir&lt;/td&gt;
    &lt;/tr&gt;
    &lt;/table&gt;</pre>
- Şimdi tablo, blok ve sütun oluşturmayı öğrendiğimize göre sırada bunları görsel olarak iyileştirme yani süsleme/şekillendirme var. Bunları nasıl yapacağız sorularını şimdiden duyar gibiyim. Acele etmeyin geliyoruz yavaş yavaş. Önce tablonun arka plan rengini belirleyelim. Beyaz değilde kırmızı olsun. Örnek aşağıda hemen gözatalım
<pre class="prettyprint lang-html" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;table bgcolor="red" border="1" height="100" width="100"&gt;
    &lt;tr&gt;
        &lt;td&gt;Bu bir bgcolor örneğidir&lt;/td&gt;
    &lt;/tr&gt;
&lt;/table&gt;</pre>
- Yukarıda "height" ve "width"'e ek olarak "bgcolor" özelliğini ekledik. Bu özellik sayesinde tablomuzun içerisine renk verebiliyoruz. Ben kırmızı rengini seçtim. Sizler ise daha farklı renkler deneyebilirsiniz. "red" yerine "blue", "green" vb. yazabilirsiniz. Ama genel olarak daha fazla renk istiyorsanız, html'de renk kodlarından yararlanmalısınız. Örnek olarak "#FFFFFF" başına işareti gelecek şekilde renge ait kod numarasını giriyoruz. "FFFFFF" 6 haneli, bu beyaz renk kodudur öte yandan "#000000" ise siyah renk kodudur. Eğer dreamweaver gibi web tasarım programları kullanıyorsanız size ufak bir ekranda renkler ve üzerine geldiğiniz rengin kodu çıkacaktır. Rengi mouse ile tıkladığınız takdirde "bgcolor" kısmına renk kodunu otomatik olarak girecektir.

- Tablomuz değilde sütunumuz ya da blok'a renk vermek istiyorsan "bgcolor" özelliğini blok veya sütun için girmemiz gerekecek. Şimi size bir örnek yazalım
<pre class="prettyprint lang-html" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;table border="1" height="100" width="100"&gt;
    &lt;tr&gt;
        &lt;td bgcolor="blue" width="50"&gt;Bu bir backcolor örneğidir&lt;/td&gt;
        &lt;td bgcolor="green" width="50"&gt;Bu bir backcolor örneğidir&lt;/td&gt;
    &lt;/tr&gt;
&lt;/table&gt;</pre>
- Örnekteki 2 sütuna farklı renkler verdim. Baştakine mavi sondakine ise yeşil renk. Bu sütunları renklendirdi. "bgcolor" kullanarak bloklarınıza da renk verdirebilirsiniz.

- Bir başka komut/özellik ise "style"'dir. "style" sayesinde css ayarları vermeniz mümkün. Tabii css işinizi kolaylaştırmak için var "style" hakkında hiçbirşeye değinmiyorum çünkü css'ye geçtiğimizde css komutlarını/özelliklerini "style"'da kullanabileceksiniz.

- Öğrenmeniz gerek diğer bir özellik "bordercolor" özelliğidir. Bu özellik ile oluşturduğunuz tablonun "border" değeri 0'dan farklıysa, çerçeve yani border'in rengini belirlemek mümkün. "bordercolor" özelliği ile dilediğiniz renkte çerçeve oluşturabilirsiniz. Renk kodları html'de hep aynıdır değişmez, "#renkkodu" şeklinde kullanılır, bu daha doğrudur.
<pre class="prettyprint lang-html" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;table border="1" height="100" width="100" bordercolor="red"&gt;
    &lt;tr&gt;
        &lt;td&gt;Bu bir bordercolor örneğidir&lt;/td&gt;
    &lt;/tr&gt;
&lt;/table&gt;</pre>
- Tablomuzun "border" değeri 0'dan farklı 1'dir. Böylece çerçevenin rengini değiştirebileceğim. Ben kırmızı yaptım. Sizde deneyip kırmızı olduğunu görebilirsiniz. Farklı renkler kullanmanız mümkün.

- Tablomuza ek bir başka özellik olarak "align"'i kullanabiliriz. Tablomuzun konumunu belirlememizde bize yardımcı olacaktır. Sağa yaslama, sola yaslama ve ortalama gibi biçimleri mevcut. Sağa yaslamak isterseniz "align="Right"", sola yaslamak isterseniz "align="Left"" ve ortalamak isterseniz "align="Center"" yapmanız yeterli olacaktır. Örneğimizi inceleyelim
<pre class="prettyprint lang-html" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;table border="1" height="100" width="100" align="center"&gt;
    &lt;tr&gt;
        &lt;td&gt;Bu bir align örneğidir&lt;/td&gt;
    &lt;/tr&gt;
&lt;/table&gt;</pre>
- Yukardaki örnekte tablomuzun ortaladık. Peki sütunumuzu veya blokları ortalayamaz mıyız ? Tabii ki bunlarda mümkün. Sütunu ortalarsanız içindeki veriler ortalanacaktır, blok ortalandığında ise sütunlarda ortalanacağından bloktaki tüm veriler ortada hizalanacaktır. Örneğe bakalım
<pre class="prettyprint lang-html" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;table border="1" height="100" width="100"&gt;
    &lt;tr align="center"&gt;
        &lt;td&gt;Bu bir align örneğidir&lt;/td&gt;
    &lt;/tr&gt;
&lt;/table&gt;</pre>
- Burda blok ortaladık ama eğer 2 sütun oluşturup birini ortalayıp diğerini ortalamadan aradaki farkı görmek isterseniz size bu örneğide gösterelim.
<pre class="prettyprint lang-html" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;table border="1" height="100" width="100"&gt;
    &lt;tr&gt;
        &lt;td width="50" align="center"&gt;Bu bir align örneğidir&lt;/td&gt;
        &lt;td width="50"&gt;Bu bir align örneğidir&lt;/td&gt;
    &lt;/tr&gt;
&lt;/table&gt;</pre>
- Örnekte ilk sütun ortalandı ve içindeki verilerde ortalandı ama ikinci sütunda ortalama yapmadığımızdan sola yaslanmış bir hal aldı. Şimdi her iki sütunuda ortalayalım.
<pre class="prettyprint lang-html" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;table border="1" height="100" width="100"&gt;
    &lt;tr&gt;
        &lt;td width="50" align="center"&gt;Bu bir align örneğidir&lt;/td&gt;
        &lt;td width="50" align="center"&gt;Bu bir align örneğidir&lt;/td&gt;
    &lt;/tr&gt;
&lt;/table&gt;</pre>
*Not: Unutmayınız, tablosuz blok ve bloksuz sütun olmaz!

- İşte bu kadar basit. 2 sütunda ortalandı. Ne kadar kolay değil mi ?

Şimdilik size aktarmam gerektiğini düşündüklerim bunlar. Diğer derslerde gene beraber asp yolunda ilerlemek üzere hoşçakalın.