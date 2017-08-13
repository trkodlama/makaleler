---
ID: 2265
post_title: 'Unity3d  ile C# Scripts Kullanarak Obje Hareket Ettirme'
author: Yiğit Can TÜRE
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/unity3d-ile-c-scripts-kullanarak-obje-hareket-ettirme-2265.html
published: true
post_date: 2013-08-06 22:08:32
---
Unity3d şu an yaygın olarak kullanılan oyun motorlarından sadece bir tanesi. Unity ile windows,mac,linux, android, ios.. aklınıza ne geliyorsa destekleyen oyunlar yapabiliyoruz. Şimdi yapacağımız örnekte sadece bir Cube objesini yön tuşları ya da w,a,s,d tuşları ile hareket ettirmeyi öğreneceğiz.

<strong>İlk önce Boş bir unity3d projesi oluşturalım. Boş'dan kasıt hiç bir paket eklemeyelim projemize.</strong>

Karşımıza böyle bir ekran gelecek.

<a href="http://www.trkodlama.com/wp-content/uploads/2013/08/unityekran.png"><img class="size-medium wp-image-2269 aligncenter" src="http://www.trkodlama.com/wp-content/uploads/2013/08/unityekran.png" alt="unityekran" width="300" height="174" /></a>

(Not standart olarak bu şekilde düzenlenmiş olarak gelmeyebilir. Fakat aynı pencereler yer alacaktır ekranınızda.)

<strong>Şimdi yukarıdan GameObject -&gt; Create Other -&gt; Cube diyelim.</strong> Yukarıdaki menüde göreceksiniz GameObject sekmesini.

<a href="http://www.trkodlama.com/wp-content/uploads/2013/08/Unity2.png"><img class="size-medium wp-image-2270 aligncenter" src="http://www.trkodlama.com/wp-content/uploads/2013/08/Unity2.png" alt="Unity2" width="300" height="91" /></a>

Resimde görüldüğü gibi Cube seçiliyken Transform altında yer alan Position'dan orjin değerini veriyoruz küpümüze.
Küpü oluşturmuş olduk. Şimdi asıl amacımıza geçelim ;
<strong>Küp bizim karakterimiz olacak. Biz de onu hareket ettireceğiz şimdi.</strong>

<a href="http://www.trkodlama.com/wp-content/uploads/2013/08/Unity3.png"><img class="size-medium wp-image-2271 aligncenter" src="http://www.trkodlama.com/wp-content/uploads/2013/08/Unity3.png" alt="Unity3" width="300" height="201" /></a>

Resimde görüldüğü gibi Project sekmemizde yer alan Assets klasörüne sağ tıklayıp Create &gt; Folder diyoruz . Klasörümüze Scripts adını verelim ki projemiz karışık bir hal almasın.
<strong>Şimdi de yeni oluşturduğumuz Scripts klasörüne sağ tıklayıp</strong> Create &gt; C# Scripts diyoruz. C# Script adına da <strong>Hareketler </strong>diyelim.

<strong> Hareketler.cs </strong>dosyamıza çift tıkladığımızda Unity3d'nin içinde yer alan MonoDevelop programı çalışacaktır. Bu Visual Studio gibi derleme programıdır. İsterseniz bu ayarları değiştirebilirsiniz. Başka bir uygulama ile de Scriptlerinizi açabilirsiniz.

<a href="http://www.trkodlama.com/wp-content/uploads/2013/08/Unity4.png"><img class="size-medium wp-image-2272 aligncenter" src="http://www.trkodlama.com/wp-content/uploads/2013/08/Unity4.png" alt="Unity4" width="300" height="264" /></a>

Update ve Start fonksiyonu işlevlerinden çok kısa içerisinde bahsettim. Biraz kod yazıp <strong>kendimize gelelim</strong>.

<a href="http://www.trkodlama.com/wp-content/uploads/2013/08/Unity5.png"><img class="size-medium wp-image-2273 aligncenter" src="http://www.trkodlama.com/wp-content/uploads/2013/08/Unity5.png" alt="Unity5" width="300" height="220" /></a>

<strong>transform :</strong> nesnemizin hareket değerlerini tutan özelliktir. Bunu private bir değişkene atadık.Bize kolaylık olsun,akılda kalsın diye.
<strong>position :</strong>pozisyonu;
<pre class="prettyprint lang-csharp" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">hareket.position = new Vector3(0,0,0);</pre>
burada Cube'e<strong> start pozisyonu </strong>verdik. Eğer hareket değişkenimize transformu vermeseydik;
<pre class="prettyprint lang-csharp" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">transform.position = new Vector3(0,0,0);</pre>
bu şekilde de yapabilirdik.

<strong>Input.GetAxis():</strong> methodu ile hangi yönde değişim göstereceğini belirledik. Yani biz hangi tuşa basıyorsak o eksende hareket etmesini sağladık.
<strong>Vector3 :</strong> Vector3 sınıfı 3 bileşenli vektör tanımlamaya yarar.
Vector3.right ise sağ tarafın vektörünü verir.
<strong>Hiz :</strong>değişkenimiz tanımladığımız objemizin hızı.
<strong>Time.deltaTime :</strong> eş zamanlı diyelim. Frame ile eş zamanlı hızda olması için çarptık.

<strong>hareket.Translate </strong>methodumuz bir vector3 sınıfnın vektörünü istiyordu bizde vector3.right ve vector3.up vektörlerini skalerler ile çarpıp istediği vektöre ulaştık.
<strong>Hızı</strong> public tanımladım oyun içinden ayarlama yapabileyim diye.

<strong>Unity</strong>'e dönelim. <strong>Hareketler.cs</strong> dosyamızı tutup <strong>Cube</strong> objemizin üstüne atalım.

<a href="http://www.trkodlama.com/wp-content/uploads/2013/08/Unity6.png"><img class="size-medium wp-image-2274 aligncenter" src="http://www.trkodlama.com/wp-content/uploads/2013/08/Unity6.png" alt="Unity6" width="251" height="300" /></a>

Daha sonra Cube objemize tıklayalım ve<strong> inspector</strong> ekranında Hareketler(Script) gözüküyor mu bakalım.İşlemi doğru yapmışmıyız kontrolü için.

<a href="http://www.trkodlama.com/wp-content/uploads/2013/08/Unity7.png"><img class="size-medium wp-image-2275 aligncenter" src="http://www.trkodlama.com/wp-content/uploads/2013/08/Unity7-300x170.png" alt="Unity7" width="300" height="170" /></a>

Gördüğünüz gibi public tanimladım demiştim Hiz değişkenimizi . Buradan oynama yapabiliriz Hiz yavaş gelirse. İşlemimiz tamam.
Çalıştıralım oyunumuzu.  (<strong>Ben 16:9 formatında bir ekranda gibi çalıştırıyorum.</strong>)

Sıkıntı yok.<strong> Sağ sol ve yukarı aşağı işlemleri çalışıyor.</strong> Hatta çapraz da gidebiliyoruz. Fakat <strong>Camera açısından çıkıyoruz.</strong> Bunu<strong>engelliyelim </strong>şimdi de;
16:9 oynadığımızda oyunu <strong>x değerimiz -10 , 10 değerleri arasında  gidip geliyor.</strong> Bunu rahatlıkla görebiliyoruz. O zaman biz şunu demeliyiz oyunumuza :
Eğer benim objemin x'i -10'dan küçük bir değer alıyorsa onu x 10 olacak şekilde yönlendir.
Eğer benim objemin x'i 10'dan büyük bir değer alıyorsa onu x -10 olacak şekilde yönlendir.
Açıkca görüldüğü gibi bize iki tane if gerekli bu durumu sağlamamız için. Hemen onları yazalım.
<pre class="lang:c# decode:true prettyprint lang-csharp">if(hareket.position.x &gt; 10){
    hareket.position =new Vector3(-10,hareket.position.y,hareket.position.z);
}
else if (hareket.position.x &lt; -10){
    hareket.position=new Vector3(10,hareket.position.y,hareket.position.z);
}</pre>
Aynı durumu y değerimiz için de yapalım böylece sürekli camera açısında olsun objemiz.

<strong>y değerimiz de -7.5,7.5</strong> arasında değişiyor. Hemen onu da ayarlıyalım
<pre class="lang:c# decode:true prettyprint lang-csharp ">if(hareket.position.y &gt; 7.5f){
    hareket.position=new Vector3(hareket.position.x,-7.5f,hareket.position.z);
}
else if(hareket.position.y &lt; -7.5f){
    hareket.position=new Vector3(hareket.position.x,7.5f,hareket.position.z);
}</pre>
<strong>Böylece hareketin ekranda kalmasını sağladık. Ve nesnemizi w,a,s,d ve ok tuşları ile kontrol edebildik. </strong>

Bu makale buraya kadar umarım yararlı olmuştur.

<strong>Oyunu aşağıdan indirebilir ve deneyebilirsiniz. Anlattığıma ek olarak bir çıkış butonu ve ışık ekledim. </strong>

<a href="http://www.trkodlama.com/wp-content/uploads/demolar/Oyun.rar">Oyun.Rar İndir</a>