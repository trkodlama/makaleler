---
ID: 149
post_title: 'C++ Ders 1: Bir programın yapısı'
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/c-ders-1-bir-programin-yapisi-149.html
published: true
post_date: 2011-04-13 17:52:36
---
Merhaba arkadaşlar,

Hep beraber C++ dilini öğrenelim dedim ve kendim öğrenirken sizlere de yazmak istedim. Umarım faydalı olur. Bu dersimizde C++'ın genel olarak yapısını inceleyeceğiz. Bende Sizinle beraber öğreniyorum bu dili.. Şimdiden hayırlı olsun, fakat ders paylaşım sıklığı hakkında size net bir bilgi ne yazık ki veremiyorum. Bazen gecikmeler yaşanabilir. Başlayalım..

Bir programlama dilini öğrenmenin en iyi yolu bir program yazmaktır. İşte burada ilk programımızı yazalım:
<pre class="prettyprint lang-c_cpp" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">// C++ ile yazdığımız ilk programımız  
  
#include &lt;iostream&gt;
using namespace std;  
  
int main()  
{  
    cout&lt;&lt;"Merhaba Dünya!";
    return 0;  
}</pre>
<blockquote>Merhaba Dünya!</blockquote>
İlk sütun(soldaki) ilk programımızın kaynak kodunu göstermektedir. İkincisi ise(sağdaki) programımız derlenip çalıştırıldıktan sonraki sonucu göstermektedir.

Bir programı düzenleyip derlemek bilgisayarınızın sistemine göre değişiklik gösterebilir. Kullandığınız geliştirme arayüzüne veya onun sürümüne bağlı olarak değişiklik gösterebilir.

Yukarıdaki program bir programlama dilini öğrenmeye yeni başlayanlar için alışılmış bir yazıyı yani "Merhaba Dünya!" yazısının ekrana basılmasını sağlar. Bu C++ ile yazılabilecek en basit programdır fakat bu program bile bütün C++ programlarında kullanılan temel bileşenlere sahip. Şimdi satır satır yazdığımız kodları inceleyelim:
<pre class="prettyprint lang-c_cpp" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">// C++ ile yazdığımız ilk programımız</pre>
Bu bir yorum satırıdır. Çift slaş(//) işareti ile başlayan satırlar yorum olarak algılanır ve programın çalışmasında hiç bir etkisi yoktur. Programlamayı yaparken programlarımızın, fonksiyonlarımızın ne işe yaradıklarını bu satırlar ile rahatlıkça anlayabiliriz.
<pre class="prettyprint lang-c_cpp" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">#include &lt;iostream&gt;</pre>
Diyez işareti(#) ile başlayan satırlar önişlemci için talimatları içerir. Bunlar ifadelerden oluşan basit kod satırları değildir ama derleyicinin önişlemcisi için birer göstergedir. #include talimatı önişlemciye iostream standar dosyasını eklemesini söyler. Bu dosya(iostream) basit ve standart giriş-çıkış kütüphanelerinin tanımlandığı dosyadır ve bunu dosyalarımıza ekleriz çünkü programımızda kullanacağımız bir takım işlemler bu dosya da tanımlanır.
<pre class="prettyprint lang-c_cpp" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">using namespace std;</pre>
C++ kütüphanesi bütün elemanları namespace denilen ve std adında tanımlanmıştır. Bu satır çok sık kullanılır ve bu derslerde de birçok kaynak kodda kullanılacaktır.
<pre class="prettyprint lang-c_cpp" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">int main()</pre>
Bu satır ana fonksiyonun tanımlandığı yerin başlangıcıdır. Ana fonksiyon C++ programlarında işleyişi yöneten fonksiyon diyebiliriz. Program çalıştırıldığın bu fonksiyon dikkate alınır. Bundan başka farklı bir isimle önce yada sonra başka bir fonksiyon yazılması sorun değil. Önemli olan main() fonksiyonunun tanımlanıp tanımlanmadığıdır. Her C++ programı main() fonksiyonuna sahip olmalıdır. main kelimesini bir çift parantez takip eder. Bunun sebebi fonksiyonların tanımından kaynaklanmaktadır. Parantezlerden sonra küme parantezi dediğimiz işaretleri görürüz({}). Fonksiyonlar bu iki işaret arasında tanımlanır.
<pre class="prettyprint lang-c_cpp" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">cout&lt;&lt;"Merhaba Dünya!";</pre>
Bu satır C++'daki kod demecidir. Kod demeci tek satırlık veya bir kaç satırlık ifadelerden oluşabilir.

cout ekrana çıktı almamızı sağlayan bir komuttur. Sayfanın başında eklediğimiz iostream dosyasında tanımlanmıştır.

Dikkat edin kod demeci noktalı virgül(;) ile bitiyor. C++ programlarımızda bütün ifadelerimizin sonuna bu işareti koymalıyız. Bu derleyiciye o satırın, kodlama ifadesinin sonu olduğunu belirtiyor ve söz dizimi(syntax) hatalarının genellik çoğunluğu bu işaretin unutlmasından kaynaklanmaktadır.
<pre class="prettyprint lang-c_cpp" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">return 0;</pre>
return ifadesi ana fonksiyonun bitmesini sağlar. Return belki farklı bir sayısal ifade ilede bitebilirdi ama biz sıfır ile bitirdi.

C++ programımızda her kodlama ifademizi alt alta yazmak zorunda değiliz. Yani:
<pre class="prettyprint lang-c_cpp" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">// C++ ile yazdığımız ilk programımız  
  
#include &lt;iostream&gt;
using namespace std;  
  
int main()  
{  
    cout&lt;&lt;"Merhaba Dünya!";
    return 0;  
}</pre>
Yerine
<pre class="prettyprint lang-c_cpp" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">int main() { cout&lt;&lt;"Merhaba Dünya!"; return 0; }</pre>
Şeklinde de yazabilirdir. Bu program iki şekilde de birebir aynı şekilde çalışacaktır.

C++'da ifadeler arasında ayrım noktalı virgül(;) ile yapılmaktadır, bu sayede her ifadenin ayrı bir işlemi gerçekleştirdiğini derleyiciye bildirmiş oluyoruz. Programımızda kullandığımız her ifadeyi ayrı satıra veya hepsini bir satıra yazabiliriz. Fakat daha sonra dönüp kontrol edeceğiniz zaman tek satır olarak yazdıklarınız büyük bir sıkıntı oluşturabilir. Fakat ayrı ayrı yazmak hem şematik hem de incelemesi daha kolay bir hale getirir kodlarınız.

Şimdi ilk programımıza bir satır daha ekleyelim:
<pre class="prettyprint lang-c_cpp" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">// C++ ile yazdığımız ilk programımız  
  
#include &lt;iostream&gt;
using namespace std;  
  
int main()  
{  
    cout&lt;&lt;"Merhaba Dünya!";
    cout&lt;&lt;"Bu ilk C++ programımız";
    return 0;  
}</pre>
<blockquote>Merhaba Dünya! Bu ilk C++ programımız</blockquote>
Bu işlemde iki tane cout kullandık ve iki ayrı satırda. Tekrar etmek gerekirse farklı satırları ayırmak için boşluk kullanmamız okunabilirliği muhteşem arttırdı. Yani main fonksiyonumuz şu şekilde de yazılabilirdi:
<pre class="prettyprint lang-c_cpp" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">int main(){ cout&lt;&lt;"Merhaba Dünya"; cout&lt;&lt;"Bu ilk C++ programımız"; return 0; }</pre>
Ayrıca daha anlaşılabilir olduğunu düşünürsek kodlarımızı daha fazla satırlara da ayırabiliriz:
<pre class="prettyprint lang-c_cpp" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">// C++ ile yazdığımız ilk programımız  
  
#include &lt;iostream&gt;
using namespace std;  
  
int main()  
{  
    cout&lt;&lt;
        "Merhaba Dünya!";
    cout&lt;&lt;  
        "Bu ilk C++ programımız";
    return 0;  
}</pre>
Ve sonuç önceki örnek ile birebir aynı olacaktır.

Önişlemci talimatları(# ile başlayanlar) bu kuralın dışındadır. Ve asla noktalı virgül(;) ile bitmezler.

<strong>Yorumlar</strong>

Yorumlar derleyicinin görmezden geldiği satırlardır. Siz kod bloğunuz hakkında bilgi vermekten başka hiçbir işe yaramazlar. Programcıya sadece bilgi vermek için yine programcı tarafından eklenir. C++ iki farklı yorum satırını desteklemektedir:
<pre class="prettyprint lang-c_cpp" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">// Tek satırlı yorum  
/* Çok satırlı yorum */</pre>
İlk satırdaki çift slaş(//) hazırlanmış olan yorum satırı sadece tek satır için geçerli olur. İkincisinde ise /* işareti ile */ işareti arasında yer alan bütün yazılar yorum olarak algılanır.

Şimdi en son hazırladığımız programımıza yorum satırlarını ekleyelim:
<pre class="prettyprint lang-c_cpp" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">/* C++ ile yazdığımız ilk programımız 
    artık birden fazla yorum satırı ile beraber */  
  
#include &lt;iostream&gt;
using namespace std;  
  
int main()  
{  
    cout&lt;&lt;"Merhaba Dünya!"; // Merhaba Dünya! yazdırır  
    cout&lt;&lt;"Bu ilk C++ programımız"; // Bu ilk C++ programımız yazdırır  
    return 0;  
}</pre>
<blockquote>Merhaba Dünya! Bu ilk C++ programımız</blockquote>
İlk dersimiz bu kadar arkadaşlar. Herkese iyi günler dilerim, kolay gelsin.