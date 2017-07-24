---
ID: 6416
post_title: 'Python&#8217;da Matematiksel Modüller: Math ve Cmath'
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/python/pythonda-matematiksel-moduller-math-cmath-6416.html
published: true
post_date: 2017-01-26 07:45:11
---
Kodlama yaparken sık sık matematiksel işlemlerden(en azından ben, genellikle hesap-kitap otomasyonları hazırlıyorum da) faydalanırız. Diğer programlama dilleri gibi Python'da da basit hesaplama operatörleri vardır. Çarpma için <code class="prettyprint lang-python" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">*</code>, modül alma için <code class="prettyprint lang-python" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">%</code> ve yuvarlama için <code class="prettyprint lang-python" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">//</code> kullanılır.

Periyodik hareket çalışması veya elektrik devrelerini taklit etmek gibi belirli görevleri yerine getirmek için bir program yazıyorsanız, karmaşık sayılar kadar trigonometrik işlevlerle çalışmanız gerekecektir. Bu işlevleri doğrudan kullanamazsınız, ancak önce iki matematiksel modül ekleyerek bunlara erişebilirsiniz. Bu modüller  <a href="https://docs.python.org/3/library/math.html" target="_blank" rel="external">math</a> ve <a href="https://docs.python.org/3/library/cmath.html" target="_blank" rel="external">cmath</a> dir.

İlki, gerçek sayılar için hiperbolik, trigonometrik ve logaritmik işlevlere erişmenizi sağlarken, ikincisi karmaşık sayılarla çalışmanıza izin verir. Bu yazıda, bu modüllerin sunduğu tüm önemli işlevleri gözden geçireceğim. Açıkça belirtilmediği sürece, döndürülen tüm değerler yüzdür.
<h2>Aritmetik Fonksiyonlar</h2>
Bu fonksiyonlar yuvarlama ve mutlak değer alma gibi bir dizi işlem gerçekleştirirler. <code class="prettyprint lang-python" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">ceil(x)</code> fonksiyonu x'den büyük veya eşit en küçük tam sayıyı verir. Benzer şekilde  <code class="prettyprint lang-python" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">floor(x)</code> fonksiyonu ise x'den küçük veya eşit en büyük tam sayıyı verir. <code class="prettyprint lang-python" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">fabs(x)</code> ise x'in mutlak değerini verir.

Ayrıca <code class="prettyprint lang-python" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">factorial(x)</code> fonksiyonu ile bir sayının faktöriyelini alabilirsiniz. Bir faktöriyel, bir tamsayının ve ondan daha küçük olan tüm pozitif tamsayıların çarpımıdır. Kombinasyonlar ve permütasyonlar ile uğraşırken yoğun şekilde kullanılır. Sinüs ve kosinüs fonksiyonlarının değerini hesaplamak için de kullanılabilir.
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
<strong><em>math</em></strong><em> </em>modülünde bulunan bir diğer faydalı fonksiyon ise <code class="prettyprint lang-python" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">gcd(x,y)</code> fonksiyonudur. Bu fonksiyon en büyük ortak böleni yani EBOB i verecektir. <em>x</em> ve <em>y</em> eğer sıfırdan farklı iki tam sayı ise bu fonksiyon bu iki tamsayıyı bölen en büyük tam sayıyı verecektir. Bu fonksiyonu kullanarak aşağıdaki formül yardımıyla en küçük ortak katı yani EKOK u da rahatlıkla bulabilirsiniz:
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

<code class="prettyprint lang-python" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">sin(x)</code>, <code class="prettyprint lang-python" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">cos(x)</code> ve <code class="prettyprint lang-python" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">tan(x)</code> fonksiyonlarını kullanarak hesaplamaları rahatlıkla yapabilirsiniz. Fakat <code class="prettyprint lang-python" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">cosec(x)</code>, <code class="prettyprint lang-python" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">sec(x)</code> ve <code class="prettyprint lang-python" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">cot(x)</code> için ne yazık ki direk hesaplama yapan bir fonksiyon bulunmamaktadır.

Ayrıca trigonometrik fonksiyonların terslerini sağlıyor bize. Ters trigonometrik fonksiyonlarımız şu şekildedir: <code class="prettyprint lang-python" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">asin(x)</code>, <code class="prettyprint lang-python" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">acos(x)</code> ve <code class="prettyprint lang-python" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">atan(x)</code>

Pisagor teoremine aşina mısınız? Pisagor, hipotenüsün karesinin diğer iki kenarın karelerinin toplamına eşit olduğunu belirtmektedir. Hipotenüs aynı zamanda dik açılı üçgenin en büyük tarafıdır. Matematik modülü hipotenüs uzunluğunu hesaplamak için <code class="prettyprint lang-python" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">hypot(a,b)</code> fonksiyonuna sahiptir.
<pre class="prettyprint lang-python" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">import math
 
math.sin(math.pi/4)    # ciktisi 0.7071067811865476
math.cos(math.pi)      # ciktisi -1.0
math.tan(math.pi/6)    # ciktisi 0.5773502691896257
math.hypot(12,5)       # ciktisi 13.0
 
math.atan(0.5773502691896257) # ciktisi 0.5235987755982988
math.asin(0.7071067811865476) # ciktisi 0.7853981633974484</pre>
<h2>Hiperbolik Fonksiyonlar</h2>
Hiperbolik fonksiyonlar, daire yerine bir hiperbola dayanan trigonometrik fonksiyonların analogudur. Trigonometride (cos b , sin b ) noktası bir birim çemberin noktalarını temsil eder. Hiperbolik fonksiyonlar da ise (cosh b , sinh b ) noktası bir eşkenar hiperbolün sağ yarısını oluşturan noktaları temsil etmektedir.

Trigonometrik fonksiyonlarda olduğu benzer fonksiyonlar hiperbolik fonksiyonlar için de geçerlidir: <code class="prettyprint lang-python" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">sinh(x)</code>, <code class="prettyprint lang-python" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">cosh(x)</code>, <code class="prettyprint lang-python" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">tanh(x)</code>, <code class="prettyprint lang-python" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">asinh(x)</code>, <code class="prettyprint lang-python" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">acosh(x)</code> ve <code class="prettyprint lang-python" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">atanh(x)</code>
<pre class="prettyprint lang-php" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">import math
 
math.sinh(math.pi)    # ciktisi 11.548739357257746
math.cosh(math.pi)    # ciktisi 11.591953275521519
math.cosh(math.pi)    # ciktisi 0.99627207622075
 
math.asinh(11.548739357257746)   # ciktisi 3.141592653589793
math.acosh(11.591953275521519)   # ciktisi 3.141592653589793
math.atanh(0.99627207622075)     # ciktisi 3.141592653589798</pre>
<h2>Üstel ve Logaritmik Fonksiyonlar</h2>
Muhtemelen program geliştirirken trigonometrik veya hiperbolikten ziyade üstel ve logaritmik fonksiyonlarla uğraşacaksınız. Neyse ki, matematik  modülü bize logaritma hesaplamak için bir çok fonksiyon sağlıyor.

Logaritma a tabanında x değerini bulmak için <code class="prettyprint lang-python" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">log(x, a)</code> kullanmanız yeterli olacaktır. Eğer taban değerini boş bırakırsanız x'in logaritması <em>e</em> tabanına göre alınacaktır. Burada <strong><em>e</em></strong>, değeri 2.71828182... olan matematiksel sabit bir sayıyı ifade etmektedir. Bu ifadeyi <code class="prettyprint lang-python" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">math.e</code> yazarak kullanabilirsiniz. Ayrıca pi sayısını da <code class="prettyprint lang-python" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">math.pi</code> yazarak kullanabilirsiniz.

2 veya 10 tabanında logaritmik işlemlerde <code class="prettyprint lang-python" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">log2(x)</code> ve <code class="prettyprint lang-python" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">log10(x)</code> in cevapları <code class="prettyprint lang-python" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">log(x,2)</code> ve <code class="prettyprint lang-python" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">log(x,10)</code> a göre gerçeğe daha yakındır. Unutmayın ki bu sadece 2 ve 10 tabanı için böyle özel fonksiyonlar mevcut. <code class="prettyprint lang-python" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">log3(x)</code> gibi bir fonksiyon yoktur. 3 tabanında logaritma almak için <code class="prettyprint lang-python" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">log(x,3)</code> şeklinde standart kullanıma devam etmelisiniz.

<code class="prettyprint lang-python" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">pow(x, y)</code> ile x üzeri y'yi de rahatlıkla hesaplayabilirsiniz. Fakat üst alma için <code class="prettyprint lang-python" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">**</code> ifadesinden de faydalanabilirsiniz.

Karekök almak içinse <code class="prettyprint lang-python" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">sqrt(x)</code> fonksiyonu vardır. Fakat az önce göstermiş olduğum <code class="prettyprint lang-python" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">pow()</code> fonksiyonu ile de karekökü <code class="prettyprint lang-python" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">pow(x, 0.5)</code> şeklinde rahatlıkla alabilirsiniz.
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

r değeri <code class="prettyprint lang-python" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">abs()</code> fonksiyonu ile bulunabilirken fi açısı ise <code class="prettyprint lang-python" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">phase(z)</code> ile rahatlıkla elde edilebilir. Düzlemsel formdaki karmaşık sayıları <code class="prettyprint lang-python" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">polar(z)</code> fonksiyonu ile kutupsal forma çevirebilirseniz. Bu fonksiyon size <code class="prettyprint lang-python" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">(r, fi)</code> şeklinde bir ikili verecektir.

Benzer şekilde kutupsal formdan düzlemsel forma geçmek içinse <code class="prettyprint lang-python" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">rect(r, fi)</code> fonksiyonu kullanılır. Bu fonksiyon ise şöyle bir dönüş sağlayacaktır: <code class="prettyprint lang-python" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">r * (math.cos(fi) + math.sin(fi)*1j</code>
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