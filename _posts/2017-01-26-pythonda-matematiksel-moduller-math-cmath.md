---
ID: 6416
post_title: 'Python’da Matematiksel Modüller: Math ve Cmath'
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/pythonda-matematiksel-moduller-math-cmath-6416.html
published: true
post_date: 2017-01-26 07:45:11
---
Kodlama yaparken sık sık matematiksel işlemlerden(en azından ben, genellikle hesap-kitap otomasyonları hazırlıyorum da) faydalanırız. Diğer programlama dilleri gibi Python'da da basit hesaplama operatörleri vardır. Çarpma için <span class="lang:python decode:true crayon-inline ">*</span> , modül alma için <span class="lang:python decode:true lang-python data-highlight: data-caption: crayon-inline">%</span> ve yuvarlama için <span class="lang:php decode:true lang-python data-highlight: data-caption: crayon-inline">//</span> kullanılır.

Periyodik hareket çalışması veya elektrik devrelerini taklit etmek gibi belirli görevleri yerine getirmek için bir program yazıyorsanız, karmaşık sayılar kadar trigonometrik işlevlerle çalışmanız gerekecektir. Bu işlevleri doğrudan kullanamazsınız, ancak önce iki matematiksel modül ekleyerek bunlara erişebilirsiniz. Bu modüller  <a href="https://docs.python.org/3/library/math.html" target="_blank" rel="external noopener">math</a> ve <a href="https://docs.python.org/3/library/cmath.html" target="_blank" rel="external noopener">cmath</a> dir.

İlki, gerçek sayılar için hiperbolik, trigonometrik ve logaritmik işlevlere erişmenizi sağlarken, ikincisi karmaşık sayılarla çalışmanıza izin verir. Bu yazıda, bu modüllerin sunduğu tüm önemli işlevleri gözden geçireceğim. Açıkça belirtilmediği sürece, döndürülen tüm değerler yüzdür.

<h2>Aritmetik Fonksiyonlar</h2>

Bu fonksiyonlar yuvarlama ve mutlak değer alma gibi bir dizi işlem gerçekleştirirler. <span class="lang:python decode:true lang-python data-highlight: data-caption: crayon-inline">ceil(x)</span> fonksiyonu x'den büyük veya eşit en küçük tam sayıyı verir. Benzer şekilde <span class="lang:python decode:true lang-python data-highlight: data-caption: crayon-inline">floor(x)</span> fonksiyonu ise x'den küçük veya eşit en büyük tam sayıyı verir. <span class="lang:php decode:true lang-python data-highlight: data-caption: crayon-inline">fabs(x)</span> ise x'in mutlak değerini verir.

Ayrıca <span class="lang:python decode:true lang-python data-highlight: data-caption: crayon-inline">factorial(x)</span> fonksiyonu ile bir sayının faktöriyelini alabilirsiniz. Bir faktöriyel, bir tamsayının ve ondan daha küçük olan tüm pozitif tamsayıların çarpımıdır. Kombinasyonlar ve permütasyonlar ile uğraşırken yoğun şekilde kullanılır. Sinüs ve kosinüs fonksiyonlarının değerini hesaplamak için de kullanılabilir.

<pre class="lang:python decode:true prettyprint lang-python">import math
 
def sinus(x):
 
    carpan = 1
    sonuc = 0
     
    for i in range(1,20,2):
        sonuc += carpan*pow(x,i)/math.factorial(i)
        carpan *= -1
         
    return sonuc
     
 
sinus(math.pi/2) # ciktisi 1.0 olacaktır
sinus(math.pi/4) # ciktisi 0.7071067811865475 olacaktır</pre>

<strong><em>math</em></strong><em> </em>modülünde bulunan bir diğer faydalı fonksiyon ise <span class="lang:python decode:true lang-python data-highlight: data-caption: crayon-inline">gcd(x,y)</span> fonksiyonudur. Bu fonksiyon en büyük ortak böleni yani EBOB i verecektir. <em>x</em> ve <em>y</em> eğer sıfırdan farklı iki tam sayı ise bu fonksiyon bu iki tamsayıyı bölen en büyük tam sayıyı verecektir. Bu fonksiyonu kullanarak aşağıdaki formül yardımıyla en küçük ortak katı yani EKOK u da rahatlıkla bulabilirsiniz:

<pre class="lang:python decode:true prettyprint lang-text">gcd(a, b) x lcm(a, b) = a x b</pre>

Python'un sunduğu aritmetik işlemlerden bir kaçını şöyle sıralayabiliriz:

<pre class="lang:python decode:true prettyprint lang-python">import math
 
math.ceil(1.001)    # ciktisi 2
math.floor(1.001)   # ciktisi 1
math.factorial(10)  # ciktisi 3628800
math.gcd(10,125)    # ciktisi 5
 
math.trunc(1.001)   # ciktisi 1
math.trunc(1.999)   # ciktisi 1</pre>

<h2>Trigonometrik Fonksiyonlar</h2>

Bu fonksiyonlar bir üçgenin açılarını kenar uzunluklarıyla ilişkilendirirler. Üçgen çalışmalar, ses, ışık ve manyetik dalgalar gibi periyodik olayların modellenmesinde trigonometrik fonksiyonlar kullanılır. Pythonda trigonometrik fonksiyonları kullanırken açı olarak <strong>radyan</strong> kullanmanız gerektiğini de unutmayın. <span class="lang:python decode:true lang-python data-highlight: data-caption: crayon-inline">sin(x)</span>, <span class="lang:python decode:true lang-python data-highlight: data-caption: crayon-inline">cos(x)</span> ve <span class="lang:python decode:true lang-python data-highlight: data-caption: crayon-inline">tan(x)</span> fonksiyonlarını kullanarak hesaplamaları rahatlıkla yapabilirsiniz. Fakat <span class="lang:python decode:true lang-python data-highlight: data-caption: crayon-inline">cosec(x)</span>, <span class="lang:python decode:true lang-python data-highlight: data-caption: crayon-inline">sec(x)</span> ve <span class="lang:python decode:true lang-python data-highlight: data-caption: crayon-inline">cot(x)</span> için ne yazık ki direk hesaplama yapan bir fonksiyon bulunmamaktadır.

Ayrıca trigonometrik fonksiyonların terslerini sağlıyor bize. Ters trigonometrik fonksiyonlarımız şu şekildedir: <span class="lang:python decode:true lang-python data-highlight: data-caption: crayon-inline">asin(x)</span>, <span class="lang:python decode:true lang-python data-highlight: data-caption: crayon-inline">acos(x)</span> ve <span class="lang:python decode:true lang-python data-highlight: data-caption: crayon-inline">atan(x)</span>

Pisagor teoremine aşina mısınız? Pisagor, hipotenüsün karesinin diğer iki kenarın karelerinin toplamına eşit olduğunu belirtmektedir. Hipotenüs aynı zamanda dik açılı üçgenin en büyük tarafıdır. Matematik modülü hipotenüs uzunluğunu hesaplamak için <span class="lang:python decode:true lang-python data-highlight: data-caption: crayon-inline">hypot(a,b)</span> fonksiyonuna sahiptir.

<pre class="lang:python decode:true prettyprint lang-python">import math
 
math.sin(math.pi/4)    # ciktisi 0.7071067811865476
math.cos(math.pi)      # ciktisi -1.0
math.tan(math.pi/6)    # ciktisi 0.5773502691896257
math.hypot(12,5)       # ciktisi 13.0
 
math.atan(0.5773502691896257) # ciktisi 0.5235987755982988
math.asin(0.7071067811865476) # ciktisi 0.7853981633974484</pre>

<h2>Hiperbolik Fonksiyonlar</h2>

Hiperbolik fonksiyonlar, daire yerine bir hiperbola dayanan trigonometrik fonksiyonların analogudur. Trigonometride (cos b , sin b ) noktası bir birim çemberin noktalarını temsil eder. Hiperbolik fonksiyonlar da ise (cosh b , sinh b ) noktası bir eşkenar hiperbolün sağ yarısını oluşturan noktaları temsil etmektedir.

Trigonometrik fonksiyonlarda olduğu benzer fonksiyonlar hiperbolik fonksiyonlar için de geçerlidir: <span class="lang:python decode:true lang-python data-highlight: data-caption: crayon-inline">sinh(x)</span>, <span class="lang:python decode:true lang-python data-highlight: data-caption: crayon-inline">cosh(x)</span>, <span class="lang:python decode:true lang-python data-highlight: data-caption: crayon-inline">tanh(x)</span>, <span class="lang:python decode:true lang-python data-highlight: data-caption: crayon-inline">asinh(x)</span>, <span class="lang:python decode:true lang-python data-highlight: data-caption: crayon-inline">acosh(x)</span> ve <span class="lang:python decode:true lang-python data-highlight: data-caption: crayon-inline">atanh(x)</span>

<pre class="lang:python decode:true prettyprint lang-python">import math
 
math.sinh(math.pi)    # ciktisi 11.548739357257746
math.cosh(math.pi)    # ciktisi 11.591953275521519
math.cosh(math.pi)    # ciktisi 0.99627207622075
 
math.asinh(11.548739357257746)   # ciktisi 3.141592653589793
math.acosh(11.591953275521519)   # ciktisi 3.141592653589793
math.atanh(0.99627207622075)     # ciktisi 3.141592653589798</pre>

<h2>Üstel ve Logaritmik Fonksiyonlar</h2>

Muhtemelen program geliştirirken trigonometrik veya hiperbolikten ziyade üstel ve logaritmik fonksiyonlarla uğraşacaksınız. Neyse ki, matematik  modülü bize logaritma hesaplamak için bir çok fonksiyon sağlıyor.

Logaritma a tabanında x değerini bulmak için <span class="lang:python decode:true lang-python data-highlight: data-caption: crayon-inline">log(x, a)</span> kullanmanız yeterli olacaktır. Eğer taban değerini boş bırakırsanız x'in logaritması <em>e</em> tabanına göre alınacaktır. Burada <strong><em>e</em></strong>, değeri 2.71828182... olan matematiksel sabit bir sayıyı ifade etmektedir. Bu ifadeyi <span class="lang:python decode:true lang-python data-highlight: data-caption: crayon-inline">math.e</span> yazarak kullanabilirsiniz. Ayrıca pi sayısını da <span class="lang:python decode:true lang-python data-highlight: data-caption: crayon-inline">math.pi</span> yazarak kullanabilirsiniz.

2 veya 10 tabanında logaritmik işlemlerde <span class="lang:python decode:true lang-python data-highlight: data-caption: crayon-inline">log2(x)</span> ve <span class="lang:python decode:true lang-python data-highlight: data-caption: crayon-inline">log10(x)</span> in cevapları <span class="lang:python decode:true lang-python data-highlight: data-caption: crayon-inline">log(x,2)</span> ve <span class="lang:python decode:true lang-python data-highlight: data-caption: crayon-inline">log(x,10)</span> a göre gerçeğe daha yakındır. Unutmayın ki bu sadece 2 ve 10 tabanı için böyle özel fonksiyonlar mevcut. <span class="lang:python decode:true lang-python data-highlight: data-caption: crayon-inline">log3(x)</span> gibi bir fonksiyon yoktur. 3 tabanında logaritma almak için <span class="lang:python decode:true lang-python data-highlight: data-caption: crayon-inline">log(x,3)</span> şeklinde standart kullanıma devam etmelisiniz. <span class="lang:python decode:true lang-python data-highlight: data-caption: crayon-inline">pow(x, y)</span> ile x üzeri y'yi de rahatlıkla hesaplayabilirsiniz. Fakat üst alma için <span class="lang:python decode:true lang-python data-highlight: data-caption: crayon-inline">**</span> ifadesinden de faydalanabilirsiniz.

Karekök almak içinse <span class="lang:python decode:true lang-python data-highlight: data-caption: crayon-inline">sqrt(x)</span> fonksiyonu vardır. Fakat az önce göstermiş olduğum <span class="lang:python decode:true lang-python data-highlight: data-caption: crayon-inline">pow()</span> fonksiyonu ile de karekökü <span class="lang:python decode:true lang-python data-highlight: data-caption: crayon-inline">pow(x, 0.5)</span> şeklinde rahatlıkla alabilirsiniz.

<pre class="lang:python decode:true prettyprint lang-python">import math
 
math.exp(5)                      # ciktisi 148.4131591025766
math.e**5                        # ciktisi 148.4131591025765
 
math.log(148.41315910257657)     # ciktisi 5.0
math.log(148.41315910257657, 2)  # ciktisi 7.213475204444817
math.log(148.41315910257657, 10) # ciktisi 2.171472409516258
 
math.log(1.0000025)              # ciktisi 2.4999968749105643e-06
math.log1p(0.0000025)            # ciktisi 2.4999968750052084e-06
 
math.pow(12.5, 2.8)              # ciktisi 1178.5500657314767
math.pow(144, 0.5)               # ciktisi 12.0
math.sqrt(144)                   # ciktisi 12.0</pre>

<h2>Karmaşık Sayılar</h2>

Karmaşık sayı, bir gerçel bir de sanal kısımdan oluşan bir nesnedir. x ve y sayıları gerçek olursa karmaşık sayılar şu biçimde gösterilirler:

<blockquote>z=x+<em><strong>i</strong></em>y</blockquote>

Genel olarak karmaşık sayılar için "z" harfi kullanılır. <em><strong>i</strong></em>^2 = -1 özelliğini sağlayan sanal birime <em><strong>i </strong></em>denir. Kimi zaman özellikle elektrik mühendisliğinde <em><strong>i </strong></em>yerine, <em><strong>j</strong></em> kullanılır.

Burada <em>x</em> gerçek kısım iken <em>i</em>y sanal kısmı oluşturuyor. Karmaşık sayılar bu şekilde gösterildiği gibi kutupsal koordinatlar şeklinde de gösterilebilirdi. Yani aynı zamanda <em>r</em> modülünde <em>fi</em> faz açısına sahip olacak şekilde bir kombinasyonla da gösterilebilir.

r değeri <span class="lang:python decode:true lang-python data-highlight: data-caption: crayon-inline">abs()</span> fonksiyonu ile bulunabilirken fi açısı ise <span class="lang:python decode:true lang-python data-highlight: data-caption: crayon-inline">phase(z)</span> ile rahatlıkla elde edilebilir. Düzlemsel formdaki karmaşık sayıları <span class="lang:python decode:true lang-python data-highlight: data-caption: crayon-inline">polar(z)</span> fonksiyonu ile kutupsal forma çevirebilirseniz. Bu fonksiyon size <span class="lang:python decode:true lang-python data-highlight: data-caption: crayon-inline">(r, fi)</span> şeklinde bir ikili verecektir.

Benzer şekilde kutupsal formdan düzlemsel forma geçmek içinse <span class="lang:python decode:true lang-python data-highlight: data-caption: crayon-inline">rect(r, fi)</span> fonksiyonu kullanılır. Bu fonksiyon ise şöyle bir dönüş sağlayacaktır: <span class="lang:python decode:true lang-python data-highlight: data-caption: crayon-inline">r * (math.cos(fi) + math.sin(fi)*1j</span>

<pre class="lang:python decode:true prettyprint lang-python">import cmath
 
cmath.polar(complex(1.0, 1.0))
# ciktisi (1.4142135623730951, 0.7853981633974483)
 
cmath.phase(complex(1.0, 1.0))
# ciktisi 0.7853981633974483
 
abs(complex(1.0, 1.0))
# ciktisi 1.4142135623730951

cmath.sqrt(complex(25.0, 25.0))
# ciktisi (5.49342056733905+2.2754493028111367j)
 
cmath.cos(complex(25.0, 25.0))
# ciktisi (35685729345.58163+4764987221.458499j)</pre>

Karmaşık sayılar sinyal analizi, akışkan dinamiği ve A/C elektrik devrelerinde yoğun bir şekilde kullanılır. Eğer bunlardan biri üzerine çalışıyorsanız <strong><em>cmath</em></strong> kütüphanesi sizi kesinlikle mutlu edecektir.

<h2>Bitti</h2>

Pythonda <em>math</em> ve <em>cmath</em> kütüphanelerinden, kullanım alanlarından ve ilgili fonksiyonların nasıl kullanıldığını güzelce anlatmış olduk.Umarım ki işinize yarar.. Lütfen yorumlarınızı benden esirgemeyin.