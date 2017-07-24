---
ID: 281
post_title: 'C++ Ders 2: Değişkenler ve Veri Türleri'
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/c-ders-2-degiskenler-ve-veri-turleri-281.html
published: true
post_date: 2012-02-03 02:36:18
---
Merhaba arkadaşlar,

Önceki dersimizde "Merhaba Dünya" uygulamasını yazdık beraber. Fakat bununla beraber aklınızda bir soru oluştur. Sadece ekrana "Merhaba Dünya" yazdırmak için satırlarca kod yazdık, bunu derledik ve sonra çalıştırdık. Halbuki bunu elinizle 5 saniyede yazabilirdiniz. Fakat programlama sadece bununla sınırlı değil. İyi bir program yazdığınızda bir çok işinizi daha rahat, güvenilir ve hızlı bir şekilde gerçekleştirebilirsiniz. Fakat iyi bir program yazmadan önce değişkenler hakkında bilgi sahibi olmalısınız.

Şimdi aklınızda 5 sayısını tutun, daha sonra 2 sayısını da tutun. Şu anda hafızanızda iki farklı sayı var Şimdi sizden ilk tuttuğunuz sayıya 1 eklemenizi istiyorum. Daha sonra aklınızdaki sayılar 6(5+1) ve 2 olacaktır. Şimdi ise bu değerleri birbirinden çıkarın ve sonuç olarak 4'ü elde edin.

Siz bu işlemleri tamamen aklınızdan yaptınız. Aynı işlemler C++ ile aşağıdaki gibi yapılabilirdi:

<pre class="lang:cpp decode:1 " >a = 5;
b = 2;
a = a + 1;
sonuc = a - b;</pre>

Açıkca gördüğünüz gibi çok basit bir işlemdi, çünkü çok basit iki sayı kullandık. Fakat düşünün ki bilgisayarınız milyonlarca sayıyı aklında tutuyor ve bunların hepsiyle birden matematiksel işlemler yapabiliyor.

Kesin elde edilmiş bir değer bir değişkene atayarak bunu hafızanın bir kısmında saklayabiliriz.

Her değişken bir tanımlayıcıya ihtiyaç duyar, diğer değişkenlerden ayırt edilmek için. Örneğin, önceki kodda değişken tanımlayıcılarımız a,b ve sonuc'du. Bu değişkenleri istediğimiz şekilde daha uzun biçimlerde tanımlayabilirdik. Fakat değişken tanımlayıcılarınında bir kuralları var. Şimdi onlara biraz göz atalım.

<strong>Tanımlayıcılar</strong>
Doğru bir tanımlayıcı bir veya daha fazla harf, rakam veya alttan tire(_) karakterini içerir. Boşluk veya diğer noktalama işaretleri tanımlayıcının bir parçası olamaz. Sadece harfler, rakamlar ve alttan tire geçerli karakterlerdendir. Ayrıca değişken tanımlayıcıları her zaman harf ile başlamak zorundadırlar. Ayrıca alttan tire(_) ile de başlayabilirler fakat bu tanımlamalarda değişken derleyici programın bir değişkeni ile çakışabilir bu nedenle alttan tire ile başlayarak değişken tanımlamak pek önerilmemektedir. Hiç bir şekilde rakamla başlayamaz.

Ayrıca dikkat etmeniz gereken bir kural daha var ki hep dikkatlerden kaçar. Derleyicinin veya C++'ın kendi tanımlayıcılarını kullanmamaya dikkat edin. Bunlar zaten kullanılmış tanımlayıcılardır. Bu tanımlayıcılar:
asm, auto, bool, break, case, catch, char, class, const, const_cast, continue, default, delete, do, double, dynamic_cast, else, enum, explicit, export, extern, false, float, for, friend, goto, if, inline, int, long, mutable, namespace, new, operator, private, protected, public, register, reinterpret_cast, return, short, signed, sizeof, static, static_cast, struct, switch, template, this, throw, true, try, typedef, typeid, typename, union, unsigned, using, virtual, void, volatile, wchar_t, while, and, and_eq, bitand, bitor, compl, not, not_eq, or, or_eq, xor, xor_eq

<strong>Çok Önemli:</strong> C++ harf duyarlı bir dildir. Bu küçük harflerle yazılmış bir değişken tanımlayıcınız büyük harflerle yazılmış olandan farklıdır. Önceki örnekte sonuc ile bize 4 sonucunu verecekken Sesult ile bize herhangi bir sonuç vermez çünkü böyle bir değişken tanımlı değil.

<strong>Temel veri türlü</strong>
Programla yaparken bazı değişkenleri bilgisayarın hafızasında saklamamız gerekebilir ve bilgisayar bizim ne tür bir veriyi saklamak istediğimizi öğrenmelidir ki hafızasında ona göre bir yer açsın. Çünkü, basit bir rakamın veya bir harfin veya büyük bir sayının hafızada tutacağı yerler çok farklıdır.

Aşağıdaki tabloda C++'da yer alan temel veri türleri ve bunların aralıklarını göreceksiniz:
<table width="100%">
<tbody>
<tr>
<th>Ad</th>
<th>Açıklama</th>
<th>Boyut</th>
<th>Aralık</th>
</tr>
<tr>
<td>char</td>
<td>Karakter veya küçük tamsayı</td>
<td>1byte</td>
<td>işaretli: -128 de 127 ye
işaretsiz: 0 dan 255 e</td>
</tr>
<tr>
<td>short int (short)</td>
<td>Kısa tamsayı</td>
<td>2bytes</td>
<td>işaretli: -32768 de 32767 ye
işaretsiz: 0 dan 65535 e</td>
</tr>
<tr>
<td>int</td>
<td>Tamsayı</td>
<td>4bytes</td>
<td>işaretli: -2147483648 den 2147483647 ye
işaretsiz: 0 dan 4294967295 e</td>
</tr>
<tr>
<td>long int (long)</td>
<td>Uzun tamsayı</td>
<td>4bytes</td>
<td>işaretli: -2147483648 den 2147483647 ye
işaretsiz: 0 dan 4294967295 e</td>
</tr>
<tr>
<td>bool</td>
<td>Boolean - Bu sadece TRUE veya FALSE olabilir</td>
<td>1byte</td>
<td>true veya false</td>
</tr>
<tr>
<td>float</td>
<td>Ondalıklı sayılar</td>
<td>4bytes</td>
<td>+/- 3.4e +/- 38 (~7 basamak)</td>
</tr>
<tr>
<td>double</td>
<td>Hassas ondalıklı sayılar</td>
<td>8bytes</td>
<td>+/- 1.7e +/- 308 (~15 basamak)</td>
</tr>
<tr>
<td>long double</td>
<td>Uzun hassas ondalıklı sayılar</td>
<td>8bytes</td>
<td>+/- 1.7e +/- 308 (~15 karakter)</td>
</tr>
<tr>
<td>wchar_t</td>
<td>Geniş karakter</td>
<td>2 veya 4 bytes</td>
<td>1 geniş karakter</td>
</tr>
</tbody>
</table>
<strong>Değişlerin tanımlanması</strong>
C++'da değişken kullanmak istiyorsak öncelikle bu değişkenin türünü tanımlamamız gerekmektedir. Örnek:

<pre class="lang:cpp decode:1 " >int a;
float ondaliklisayi;</pre>

Bunlar iki tane geçerli değişken tanımlamasıdır. İlk a tanımlayıcısı ile bir tamsayı değişkeni tanımlamaktadır. İkincisi ise ondaliklisayi tanımlayıcısı ile bir rasyonel tamsayı değişkeni tanımlamaktadır.

Aynı türde birden fazla değişken tanımlamak isterseniz değişken türünü yazdıktan sonra diğer değişken adlarını virgülle ayırarak aynı satırda tanımlamayı yapabilirsiniz.

<pre class="lang:cpp decode:1 " >int a, b, c;</pre>

Bu şekilde a, b ve c değişkenlerinin birer tamsayı olduğunu tanımladınız. Aşağıdaki çalışma şekliyle aynı şekilde çalışır:

<pre class="lang:cpp decode:1 " >int a;
int b;
int c;</pre>

Tamsayı değişkenlerde işaretli ve işaretsizin anlamını merak edenler vardır. Yukarıdaki tabloda anlaşılmamış olabilir. İşaretli dediğimiz türlerde tanımlanan değişkenler negatif(eksi) değerler alabilir. Eğer veri türünü belirlerken işaretli veya işaretsiz olduğunuz belirlemezsek bir çok derleyici program varsayılan olarak işaretli olarak kabul eder ve o şekilde işleme sokar belirlediğini veri türünü.

shot int ve long int veri türleri yerine daha kısa olması amacıyla sadece short ve long kullanabilirsiniz:

<pre class="lang:cpp decode:1 " >short Yil;
short int Yil;</pre>

Şimdi değişken tanımlama bir program yazılırken nasıl görünüyormuş bir bakalım:

<pre class="lang:cpp decode:1 " >// değişkenlerle işlemler
#include &amp;amp;lt;iostream&amp;amp;gt;
using namespace std;

int main ()
{
 // değişkenleri tanımlama
 int a, b;
 int sonuc;

// islemler:
 a = 5;
 b = 2;
 a = a + 1;
 sonuc= a - b;

// sonuc'u ekrana basalım:
 cout &amp;lt;&amp;lt; sonuc;

// programı sonlandıralım;
 return 0;
}</pre>

<strong>Değişkenlerin tanımlanması</strong>
Değişkenleri biraz daha farklı biçimlerde tanımlayabiliriz. Bir değişkeni tanımladığımız onun herhangi bir değerli olmaz. Fakat değişkeni tanımladığınız anda ona bir de değer vermek isteyebilirsiniz. C++'da bunu yapabilmeniz için iki yöntem var:

<em>tur tanimlayici = deger;</em> buna örnek olarak <strong>int a = 0;</strong> veya
<em>tur tanimlayici(deger);</em> buna örnek olaraksa <strong>int a(0);</strong> verilebilir. Şimdi bunlarla ilgili bir örnek verelim hemen:

<pre class="lang:cpp decode:1 " >#include &amp;lt;iostream&amp;gt;
using namespace std;

int main ()
{
 int a=5; // değer = 5
 int b(2); // değer = 2
 int sonuc; // değer tanımlanmamış

a = a + 3;
 sonuc= a - b;
 cout &amp;lt;&amp;lt; sonuc;

return 0;
}</pre>
<blockquote>6</blockquote>
<strong>Katarlara giriş</strong>
Değişkenler nümerik olmayan verileri de saklayabilirler ki bunlar katar olarak tanımlanan bir birden fazla alfanümerik karakterin yanyana gelmesiyle oluşmuş dizelerdir. Hemen basit bir örnek yapalım:

<pre class="lang:cpp decode:1 " >#include &amp;lt;iostream&amp;gt;
#include &amp;lt;string&amp;gt;
using namespace std;

int main ()
{
 string katar = &amp;quot;ilk c&uuml;mlem&amp;quot;;
 cout &amp;lt;&amp;lt; katar;
 return 0;
}</pre>
<blockquote>ilk cümlem</blockquote>
Değişkenler ve veri türleri ile benim anlatacaklarım bu kadar. Saat sabah 6:10. Bu nedenle hatalarım olabilir. Lütfen kusuruma bakmayın.
Umarım faydalı olur, kolay gelsin