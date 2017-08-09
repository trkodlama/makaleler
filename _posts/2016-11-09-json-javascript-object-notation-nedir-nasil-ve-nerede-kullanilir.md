---
ID: 9968
post_title: >
  JSON (JavaScript Object Notation) Nedir,
  Nasıl ve Nerede Kullanılır?
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/json-javascript-object-notation-nedir-nasil-ve-nerede-kullanilir-9968.html
published: true
post_date: 2016-11-09 13:51:12
---
JSON veri formatı nedir,nasıl kullanılır, nerelerde kullanılır, XML ve JSON arasındaki farklar nelerdir, JSON nesne (object) dizi (array) örnekleri ve özel karakterleri nelerdir? Hepsine değineceğiz..
<h2>JSON Nedir?</h2>
Json, Javascript uygulamaları için oluşturulmuş bir veri formatıdır. <strong>J</strong>avascript <strong>O</strong>bject <strong>N</strong>otation’ın kısaltmasıdır. Json’ın çıkış amacı veri transferlerinde verilerin XML’den daha az yer kaplamasını sağlamaktır. Şu an sadece Javascript uygulamalarında değil, yazılım geliştirmede kullanılan bir çok teknolojide Json formatındaki veriler tercih edilmektedir. Java uygulamaları .Net uygulamaları PHP uygulamaları Web servis uygulamaları Mobil uygulamaların veri transferleri gibi bir çok noktada veriler Json formatında kullanılmaktadır.
<h3>JSON Veri Formatı</h3>
Json türündeki veriler iki parçadan oluşur: key (anahtar) ve value (değer). Anahtar’da nesnenin hangi özelliğinin olduğu (koddaki değişken ismi gibi düşünülebilir) tanımlanırken değerde ise anahtar özelliğinin değeri (değişkenin değeri) tanımlanır. Nesnelerdeki anahtar ve değerler <strong>string</strong> türünde tanımlanır. Aşağıda basit bir json nesnesi örneği bulunmaktadır.
<pre class="line-numbers"><code class="language-json">{
   "Ad": "Veysel Uğur",
   "Soyad": "Kızmaz"
}</code></pre>
Yukarıdaki örnekte 2 tane anahtar ve 2 tane değer vardır: "Ad" anahtarının değeri "Veysel Uğur" , "Soyad" anahtarını değeri ise "Kızmaz" olarak tanımlanmıştır.

Nesne içerisinde istediğiniz kadar anahtar – değer (key-value) ikilisi tanımlayabilirsiniz.
<pre class="line-numbers"><code class="language-json">{
    "Ad": "Veysel Uğur",
    "Soyad": "Kızmaz",
    "Bolum": "Bilgisayar Muhendisligi",
    "Sehir": "Ankara",
    "Telefon": "05000000000"
}</code></pre>
<h3>JSON Nesne(Object) Yapısı</h3>
Her Json nesnesi süslü parantez ile başlar ve içinde sonsuz sayıda key-value ikilileri bulunabilir. Json.org sitesinde bu durumu anlatan güzel bir grafik mevcut:

<img class="aligncenter size-full wp-image-9969" src="https://www.trkodlama.com/wp-content/uploads/2017/08/json_object.gif" alt="json object" width="598" height="113" />

Her Json nesnesi süslü parantez içinde tanımlanır. Nesne içinde anahtar (grafikte <em>string</em>) ve değer (grafikte<em> value</em>) tanımlamaları, araya iki nokta üst üste karakteri gelecek şekilde tanımlanır. Nesne içindeki her key-value ikilisinden sonra virgül karakteri kullanılır. Nesnenin tanımlaması bittikten sonra süslü parantez kapatılır.

<strong>Örnek 1:</strong> 1 key-value’ya sahip Json nesnesi: “Ad” anahtarının değeri : “Veysel Uğur”.
<pre class="line-numbers"><code class="language-json">{
   "Ad": "Veysel Uğur"
}</code></pre>
<strong>Örnek 2:</strong> 2 key-value’ya sahip Json nesnesi: “Ad” anahtarının değeri: “Veysel Uğur” , “Soyad” anahtarının değeri “Kızmaz”
<pre class="line-numbers"><code class="language-json">{
   "Ad": "Veysel Uğur",
   "Soyad": "Kızmaz"
}</code></pre>
<h3>JSON Dizi(Array) Yapısı</h3>
Her Json dizisi köşeli parantez ile başlar ve içinde sonsuz sayıda değer bulunabilir. Dizilerde key-value ikilileri yoktur. Sadece <strong>string</strong> değer alabileceği gibi <strong>Json nesnesi</strong> de tanımlanabilir. Json.org sitesinde bu durumu anlatan güzel bir grafik mevcut:

<img class="aligncenter size-full wp-image-9970" src="https://www.trkodlama.com/wp-content/uploads/2017/08/json_array.gif" alt="json array" width="598" height="113" />

Her JSON dizisi köşeli parantez içinde tanımlanır. Dizi içindeki tüm değerler aralarında virgül karakteri gelecek şekilde tanımlanır. Dizinin tanımlaması bittikten sonra köşeli parantez kapatılır.

<strong>Örnek 1: </strong>1 <em>string değere</em> sahip Json dizisi
<pre class="line-numbers"><code class="language-json">[
    "Veysel Uğur"
]</code></pre>
<strong>Örnek 2:</strong> 2 <em>string değere</em> sahip Json dizisi
<pre class="line-numbers"><code class="language-json">[
    "Veysel Uğur",
    "Kızmaz"
]</code></pre>
<strong>Örnek 3: </strong>1 <em>Json nesnesine</em> sahip Json dizisi
<pre class="line-numbers"><code class="language-json">[
    {
        "Ad": "Veysel Uğur",
        "Soyad": "Kızmaz",
        "Bolum": "Bilgisayar Muhendisligi",
        "Sehir": "Ankara",
        "Telefon": "05000000000"
    }
]</code></pre>
<strong>Örnek 4:</strong> 2 <em>Json nesnesine</em> sahip Json dizisi
<pre class="line-numbers"><code class="language-json">[
    {
        "Ad": "Veysel Uğur",
        "Soyad": "Kızmaz",
        "Bolum": "Bilgisayar Muhendisligi",
        "Sehir": "Ankara",
        "Telefon": "05000000000"
    },
    {
        "Ad": "Neslihan",
        "Soyad": "Yağmur",
        "Bolum": "Tıp Fakültesi",
        "Sehir": "Malatya",
        "Telefon": "05000000001"
    }
]</code></pre>
<strong>Örnek 5: </strong>2 <em>Json nesnesi</em> ve 1 <em>string</em> <em>değere</em> sahip Json dizisi
<pre class="line-numbers"><code class="language-json">[
    {
        "Ad": "Veysel Uğur",
        "Soyad": "Kızmaz",
        "Bolum": "Bilgisayar Muhendisligi",
        "Okul": "Gazi Üniversitesi",
        "Sehir": "Ankara",
        "Telefon": "05000000000"
    },
    "Asp.Net MVC 5",
    "Uygulamalarla Asp.Net 4.5"
]</code></pre>
<h3>JSON Değerlerinin Alabileceği Veriler</h3>
Json değerlerinin <strong>string</strong> veri türünde yazıldığını yukarıda belirtmiştim. Json nesnelerinin içinde değerler (value) farklı türden veriler de alabilirler: “dizi”, “boolean veri (true, false)”, “null”, “Json Nesnesi”. Json değerlerinin esnek yapısı uygulama geliştirme aşamasında büyük kolaylıklar sağlayacaktır.

Örneğin yazar bilgilerinin bulunduğu <strong>Yazar</strong> ve yazarın kitaplarının bulunduğu <strong>Kitap</strong> türünde iki sınıfımız olsun. Bir yazarın birden fazla kitabı olabileceği için <em>Yazar</em> nesnesinin içinde birden fazla <em>Kitap</em> tanımlanmasına olanak sağlamalıyız. Aşağıda <em>Yazar</em> ve <em>Kitap</em> isimli C# sınıflarını tanımladım.
<pre class="line-numbers"><code class="language-csharp">public class Yazar
{
    public string Ad { get; set; }
    public string Soyad { get; set; }
    public List&lt;Kitap&gt; Kitaplar { get; set; }
}
public class Kitap
{
    public string Ad { get; set; }
    public int BaskiSayisi { get; set; }
}</code></pre>
<em>Yazar</em> sınıfı türünden bir nesne tanımalyalım. Tanımladığımız yazarın 2 tane de kitabı olsun.
<pre class="line-numbers"><code class="language-csharp">Yazar yazarVeyselUgurKizmaz = new Yazar
{
    Ad = "Veysel Uğur",
    Soyad = "Kızmaz",
    Kitaplar = new List&lt;Kitap&gt;
    {
        new Kitap
        {
            Ad = "Uygulamalarla Asp.Net 4.5",
            BaskiSayisi = 5
        },
        new Kitap{
            Ad = "Asp.Net MVC 5",
            BaskiSayisi = 2
        }
    }
};</code></pre>
Yukarıda C# kodlaması ile tanımladığımız veriyi Json ile tanımlayalım:
<pre class="line-numbers"><code class="language-json">{
    "Ad": "Veysel Uğur",
    "Soyad": "Kizmaz",
    "Kitaplar": [
        {
            "Ad": "UygulamalarlaAsp.Net4.5",
            "BaskiSayisi": "5"
        },
        {
            "Ad": "Asp.NetMVC5",
            "BaskiSayisi": "2"
        }
    ]
}</code></pre>
<ol>
 	<li>İlk satırda nesnenin başlangıç süslü parantezini tanımladık.</li>
 	<li>“Ad” ve “Soyad” özelliklerini ve değerlerini 2. ve 3. satırda tanımladık.</li>
 	<li>4. satırda “Kitaplar” özelliğinde (anahtarında) kitap dizisi tanımladık. Dizinin içine 2 tane eleman ekledik (yazarın kitapları). Her elemanın “Ad” ve “BaskiSayisi” özelliklerine (anahtarlarına) değerlerini tanımladık.</li>
 	<li>Dizi tanımlamasını bitirdikten sonra son satırda süslü parantez ile nesneyi sonlandırdık.</li>
</ol>
Böylelikle C# ile oluşturduğumuz nesnenin aynısını Json formatında da oluşturmuş olduk.
<h3>JSON Değerlerinde Kullanılamayan (Özel) Karakterler</h3>
Json formatında bir nesne ya da dizi oluştururken bazı karakterlerin kullanımı için karakterin başına “\” eklenmesi gerekir. Bunlar Json.org sitesindeki güzel bir grafik ile anlatılmıştır:

<img class="aligncenter size-full wp-image-9971" src="https://www.trkodlama.com/wp-content/uploads/2017/08/json_string.gif" alt="json string" width="598" height="413" />