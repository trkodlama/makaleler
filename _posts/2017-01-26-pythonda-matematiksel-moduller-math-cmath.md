---
ID: 6416
post_title: 'Python&#8217;da Matematiksel Modüller: Math ve Cmath'
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/pythonda-matematiksel-moduller-math-cmath-6416.html
published: true
post_date: 2017-01-26 07:45:11
---
Kodlama yaparken sık sık matematiksel işlemlerden(en azından ben, genellikle hesap-kitap otomasyonları hazırlıyorum da) faydalanırız. Diğer programlama dilleri gibi Python'da da basit hesaplama operatörleri vardır. Çarpma için <pre class="class:prettyprint lang-python data-start-line:1 data-visibility:visible data-highlight: data-caption: decode:1 " >*</pre>, modül alma için <pre class="class:prettyprint lang-python data-start-line:1 data-visibility:visible data-highlight: data-caption: decode:1 " >%</pre> ve yuvarlama için <pre class="class:prettyprint lang-python data-start-line:1 data-visibility:visible data-highlight: data-caption: decode:1 " >//</pre> kullanılır.

Periyodik hareket çalışması veya elektrik devrelerini taklit etmek gibi belirli görevleri yerine getirmek için bir program yazıyorsanız, karmaşık sayılar kadar trigonometrik işlevlerle çalışmanız gerekecektir. Bu işlevleri doğrudan kullanamazsınız, ancak önce iki matematiksel modül ekleyerek bunlara erişebilirsiniz. Bu modüller  <a href="https://docs.python.org/3/library/math.html" target="_blank" rel="external">math</a> ve <a href="https://docs.python.org/3/library/cmath.html" target="_blank" rel="external">cmath</a> dir.

İlki, gerçek sayılar için hiperbolik, trigonometrik ve logaritmik işlevlere erişmenizi sağlarken, ikincisi karmaşık sayılarla çalışmanıza izin verir. Bu yazıda, bu modüllerin sunduğu tüm önemli işlevleri gözden geçireceğim. Açıkça belirtilmediği sürece, döndürülen tüm değerler yüzdür.
<h2>Aritmetik Fonksiyonlar</h2>
Bu fonksiyonlar yuvarlama ve mutlak değer alma gibi bir dizi işlem gerçekleştirirler. <pre class="class:prettyprint lang-python data-start-line:1 data-visibility:visible data-highlight: data-caption: decode:1 " >ceil(x)</pre> fonksiyonu x'den büyük veya eşit en küçük tam sayıyı verir. Benzer şekilde  <pre class="class:prettyprint lang-python data-start-line:1 data-visibility:visible data-highlight: data-caption: decode:1 " >floor(x)</pre> fonksiyonu ise x'den küçük veya eşit en büyük tam sayıyı verir. <pre class="class:prettyprint lang-python data-start-line:1 data-visibility:visible data-highlight: data-caption: decode:1 " >fabs(x)</pre> ise x'in mutlak değerini verir.

Ayrıca <pre class="class:prettyprint lang-python data-start-line:1 data-visibility:visible data-highlight: data-caption: decode:1 " >factorial(x)</pre> fonksiyonu ile bir sayının faktöriyelini alabilirsiniz. Bir faktöriyel, bir tamsayının ve ondan daha küçük olan tüm pozitif tamsayıların çarpımıdır. Kombinasyonlar ve permütasyonlar ile uğraşırken yoğun şekilde kullanılır. Sinüs ve kosinüs fonksiyonlarının değerini hesaplamak için de kullanılabilir.
<pre class="prettyprint lang-python" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">import math
 
def sinus(x):
 
    carpan = 1
    sonuc = 0
     
    for i in range(1,20,2):
        sonuc += carpan*pow(x,i)/math.factorial(i)
        carpan *= -1
         
    return sonuc
     
 
sinus(math.pi/2) # ciktisi 1.0 olacaktır
sinus(math.pi/4) # ciktisi 0.7071067811865475 olacaktır</pre>
<strong><em>math</em></strong><em> </em>modülünde bulunan bir diğer faydalı fonksiyon ise <pre class="class:prettyprint lang-python data-start-line:1 data-visibility:visible data-highlight: data-caption: decode:1 " >gcd(x,y)</pre> fonksiyonudur. Bu fonksiyon en büyük ortak böleni yani EBOB i verecektir. <em>x</em> ve <em>y</em> eğer sıfırdan farklı iki tam sayı ise bu fonksiyon bu iki tamsayıyı bölen en büyük tam sayıyı verecektir. Bu fonksiyonu kullanarak aşağıdaki formül yardımıyla en küçük ortak katı yani EKOK u da rahatlıkla bulabilirsiniz:
<pre class="prettyprint lang-text" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">gcd(a, b) x lcm(a, b) = a x b</pre>
Python'un sunduğu aritmetik işlemlerden bir kaçını şöyle sıralayabiliriz:
<pre class="prettyprint lang-python" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">import math
 
math.ceil(1.001)    # ciktisi 2
math.floor(1.001)   # ciktisi 1
math.factorial(10)  # ciktisi 3628800
math.gcd(10,125)    # ciktisi 5
 
math.trunc(1.001)   # ciktisi 1
math.trunc(1.999)   # ciktisi 1</pre>
<h2>Trigonometrik Fonksiyonlar</h2>
Bu fonksiyonlar bir üçgenin açılarını kenar uzunluklarıyla ilişkilendirirler. Üçgen çalışmalar, ses, ışık ve manyetik dalgalar gibi periyodik olayların modellenmesinde trigonometrik fonksiyonlar kullanılır. Pythonda trigonometrik fonksiyonları kullanırken açı olarak <strong>radyan</strong> kullanmanız gerektiğini de unutmayın.

<pre class="class:prettyprint lang-python data-start-line:1 data-visibility:visible data-highlight: data-caption: decode:1 " >sin(x)</pre>, <pre class="class:prettyprint lang-python data-start-line:1 data-visibility:visible data-highlight: data-caption: decode:1 " >cos(x)</pre> ve <pre class="class:prettyprint lang-python data-start-line:1 data-visibility:visible data-highlight: data-caption: decode:1 " >tan(x)</pre> fonksiyonlarını kullanarak hesaplamaları rahatlıkla yapabilirsiniz. Fakat <pre class="class:prettyprint lang-python data-start-line:1 data-visibility:visible data-highlight: data-caption: decode:1 " >cosec(x)</pre>, <pre class="class:prettyprint lang-python data-start-line:1 data-visibility:visible data-highlight: data-caption: decode:1 " >sec(x)</pre> ve <pre class="class:prettyprint lang-python data-start-line:1 data-visibility:visible data-highlight: data-caption: decode:1 " >cot(x)</pre> için ne yazık ki direk hesaplama yapan bir fonksiyon bulunmamaktadır.

Ayrıca trigonometrik fonksiyonların terslerini sağlıyor bize. Ters trigonometrik fonksiyonlarımız şu şekildedir: <pre class="class:prettyprint lang-python data-start-line:1 data-visibility:visible data-highlight: data-caption: decode:1 " >asin(x)</pre>, <pre class="class:prettyprint lang-python data-start-line:1 data-visibility:visible data-highlight: data-caption: decode:1 " >acos(x)</pre> ve <pre class="class:prettyprint lang-python data-start-line:1 data-visibility:visible data-highlight: data-caption: decode:1 " >atan(x)</pre>

Pisagor teoremine aşina mısınız? Pisagor, hipotenüsün karesinin diğer iki kenarın karelerinin toplamına eşit olduğunu belirtmektedir. Hipotenüs aynı zamanda dik açılı üçgenin en büyük tarafıdır. Matematik modülü hipotenüs uzunluğunu hesaplamak için <pre class="class:prettyprint lang-python data-start-line:1 data-visibility:visible data-highlight: data-caption: decode:1 " >hypot(a,b)</pre> fonksiyonuna sahiptir.
<pre class="prettyprint lang-python" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">import math
 
math.sin(math.pi/4)    # ciktisi 0.7071067811865476
math.cos(math.pi)      # ciktisi -1.0
math.tan(math.pi/6)    # ciktisi 0.5773502691896257
math.hypot(12,5)       # ciktisi 13.0
 
math.atan(0.5773502691896257) # ciktisi 0.5235987755982988
math.asin(0.7071067811865476) # ciktisi 0.7853981633974484</pre>
<h2>Hiperbolik Fonksiyonlar</h2>
Hiperbolik fonksiyonlar, daire yerine bir hiperbola dayanan trigonometrik fonksiyonların analogudur. Trigonometride (cos b , sin b ) noktası bir birim çemberin noktalarını temsil eder. Hiperbolik fonksiyonlar da ise (cosh b , sinh b ) noktası bir eşkenar hiperbolün sağ yarısını oluşturan noktaları temsil etmektedir.

Trigonometrik fonksiyonlarda olduğu benzer fonksiyonlar hiperbolik fonksiyonlar için de geçerlidir: <pre class="class:prettyprint lang-python data-start-line:1 data-visibility:visible data-highlight: data-caption: decode:1 " >sinh(x)</pre>, <pre class="class:prettyprint lang-python data-start-line:1 data-visibility:visible data-highlight: data-caption: decode:1 " >cosh(x)</pre>, <pre class="class:prettyprint lang-python data-start-line:1 data-visibility:visible data-highlight: data-caption: decode:1 " >tanh(x)</pre>, <pre class="class:prettyprint lang-python data-start-line:1 data-visibility:visible data-highlight: data-caption: decode:1 " >asinh(x)</pre>, <pre class="class:prettyprint lang-python data-start-line:1 data-visibility:visible data-highlight: data-caption: decode:1 " >acosh(x)</pre> ve <pre class="class:prettyprint lang-python data-start-line:1 data-visibility:visible data-highlight: data-caption: decode:1 " >atanh(x)</pre>
<pre class="prettyprint lang-php" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">import math
 
math.sinh(math.pi)    # ciktisi 11.548739357257746
math.cosh(math.pi)    # ciktisi 11.591953275521519
math.cosh(math.pi)    # ciktisi 0.99627207622075
 
math.asinh(11.548739357257746)   # ciktisi 3.141592653589793
math.acosh(11.591953275521519)   # ciktisi 3.141592653589793
math.atanh(0.99627207622075)     # ciktisi 3.141592653589798</pre>
<h2>Üstel ve Logaritmik Fonksiyonlar</h2>
Muhtemelen program geliştirirken trigonometrik veya hiperbolikten ziyade üstel ve logaritmik fonksiyonlarla uğraşacaksınız. Neyse ki, matematik  modülü bize logaritma hesaplamak için bir çok fonksiyon sağlıyor.

Logaritma a tabanında x değerini bulmak için <pre class="class:prettyprint lang-python data-start-line:1 data-visibility:visible data-highlight: data-caption: decode:1 " >log(x, a)</pre> kullanmanız yeterli olacaktır. Eğer taban değerini boş bırakırsanız x'in logaritması <em>e</em> tabanına göre alınacaktır. Burada <strong><em>e</em></strong>, değeri 2.71828182... olan matematiksel sabit bir sayıyı ifade etmektedir. Bu ifadeyi <pre class="class:prettyprint lang-python data-start-line:1 data-visibility:visible data-highlight: data-caption: decode:1 " >math.e</pre> yazarak kullanabilirsiniz. Ayrıca pi sayısını da <pre class="class:prettyprint lang-python data-start-line:1 data-visibility:visible data-highlight: data-caption: decode:1 " >math.pi</pre> yazarak kullanabilirsiniz.

2 veya 10 tabanında logaritmik işlemlerde <pre class="class:prettyprint lang-python data-start-line:1 data-visibility:visible data-highlight: data-caption: decode:1 " >log2(x)</pre> ve <pre class="class:prettyprint lang-python data-start-line:1 data-visibility:visible data-highlight: data-caption: decode:1 " >log10(x)</pre> in cevapları <pre class="class:prettyprint lang-python data-start-line:1 data-visibility:visible data-highlight: data-caption: decode:1 " >log(x,2)</pre> ve <pre class="class:prettyprint lang-python data-start-line:1 data-visibility:visible data-highlight: data-caption: decode:1 " >log(x,10)</pre> a göre gerçeğe daha yakındır. Unutmayın ki bu sadece 2 ve 10 tabanı için böyle özel fonksiyonlar mevcut. <pre class="class:prettyprint lang-python data-start-line:1 data-visibility:visible data-highlight: data-caption: decode:1 " >log3(x)</pre> gibi bir fonksiyon yoktur. 3 tabanında logaritma almak için <pre class="class:prettyprint lang-python data-start-line:1 data-visibility:visible data-highlight: data-caption: decode:1 " >log(x,3)</pre> şeklinde standart kullanıma devam etmelisiniz.

<pre class="class:prettyprint lang-python data-start-line:1 data-visibility:visible data-highlight: data-caption: decode:1 " >pow(x, y)</pre> ile x üzeri y'yi de rahatlıkla hesaplayabilirsiniz. Fakat üst alma için <pre class="class:prettyprint lang-python data-start-line:1 data-visibility:visible data-highlight: data-caption: decode:1 " >**</pre> ifadesinden de faydalanabilirsiniz.

Karekök almak içinse <pre class="class:prettyprint lang-python data-start-line:1 data-visibility:visible data-highlight: data-caption: decode:1 " >sqrt(x)</pre> fonksiyonu vardır. Fakat az önce göstermiş olduğum <pre class="class:prettyprint lang-python data-start-line:1 data-visibility:visible data-highlight: data-caption: decode:1 " >pow()</pre> fonksiyonu ile de karekökü <pre class="class:prettyprint lang-python data-start-line:1 data-visibility:visible data-highlight: data-caption: decode:1 " >pow(x, 0.5)</pre> şeklinde rahatlıkla alabilirsiniz.
<pre class="prettyprint lang-python" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">import math
 
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

r değeri <pre class="class:prettyprint lang-python data-start-line:1 data-visibility:visible data-highlight: data-caption: decode:1 " >abs()</pre> fonksiyonu ile bulunabilirken fi açısı ise <pre class="class:prettyprint lang-python data-start-line:1 data-visibility:visible data-highlight: data-caption: decode:1 " >phase(z)</pre> ile rahatlıkla elde edilebilir. Düzlemsel formdaki karmaşık sayıları <pre class="class:prettyprint lang-python data-start-line:1 data-visibility:visible data-highlight: data-caption: decode:1 " >polar(z)</pre> fonksiyonu ile kutupsal forma çevirebilirseniz. Bu fonksiyon size <pre class="class:prettyprint lang-python data-start-line:1 data-visibility:visible data-highlight: data-caption: decode:1 " >(r, fi)</pre> şeklinde bir ikili verecektir.

Benzer şekilde kutupsal formdan düzlemsel forma geçmek içinse <pre class="class:prettyprint lang-python data-start-line:1 data-visibility:visible data-highlight: data-caption: decode:1 " >rect(r, fi)</pre> fonksiyonu kullanılır. Bu fonksiyon ise şöyle bir dönüş sağlayacaktır: <pre class="class:prettyprint lang-python data-start-line:1 data-visibility:visible data-highlight: data-caption: decode:1 " >r * (math.cos(fi) + math.sin(fi)*1j</pre>
<pre class="prettyprint lang-python" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">import cmath
 
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