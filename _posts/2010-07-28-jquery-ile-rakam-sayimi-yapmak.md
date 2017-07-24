---
ID: 66
post_title: jQuery ile Rakam Sayımı Yapmak
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/jquery-ile-rakam-sayimi-yapmak-66.html
published: true
post_date: 2010-07-28 07:54:25
---
Merhaba arkadaşlar,
Bugünlü makalemde jQuery ile nasıl rakam sayımı yapabileceğimizi öğreneceğiz. Rakam sayımından kastımın ne olduğunu da hemen kısaca açıklayayım. Mesela geri sayım yapacağız. Başlangıç değerimiz 500 bitiş değerimiz 158. Sayfa açıldığında 500'den geriye sizin belirlediğiniz aralıklarla saymaya başlar. Aynı işlemi birkaç değişiklike 158'den 500'e kadar şeklinde de artacak şekilde uygulayabiliriz.
Öncelikle sayfamıza vazgeçilmez olan jquery kütüphanesi ekleyelim:
[sourcecode lang="html"]&lt;script src=&quot;http://ajax.googleapis.com/ajax/libs/jquery/1.4.2/jquery.min.js&quot;&gt;&lt;/script&gt;[/sourcecode]
Şimdi öncelikle ilk yazağım kodda "0"dan başlayarak "500"e kadar saydıralım:
[sourcecode lang="html"]&lt;script type=&quot;text/javascript&quot;&gt;
    var maks = 500;// php ile yazdırın bu değeri
    $(function(){
     ileriSayim();
    });
    function ileriSayim() {
     var deger = parseInt($('#sayac').html());
     $('#sayac').text(deger+1);
     // Üst ve alt satırdaki +1'i arttırarak sayacın kaçarlı sayılacağını belirtiyoruz
     if (deger+1 != maks) {
      setTimeout('ileriSayim()',50);
     }
     if(deger&lt;=maks){
       $('#sayac').text(maks);
     }
    }
&lt;/script&gt;

// Bu kısmı sayacın görünmesini istediğiniz yere yazın
&lt;div id=&quot;sayac&quot;&gt;0&lt;/div&gt;[/sourcecode]
Aynı şekilde bu sayaş kodun da bir kaç değişiklik yaparak 500'den 0'a doğru saydıralım:
[sourcecode lang="html"]&lt;script type=&quot;text/javascript&quot;&gt;
    var min= 0;// php ile yazdırın bu değeri

    $(function(){
     geriSayim();
    });
    function geriSayim() {
     var deger = parseInt($('#sayac').html());
     $('#sayac').text(deger-1);
     // Üst ve alt satırdaki -1'i azaltarak sayacın kaçarlı sayılacağını belirtiyoruz
     if (deger-1 != min) {
      setTimeout('geriSayim()',50);
     }
     if(deger&gt;=maks){
       $('#sayac').text(min);
     }
    }
&lt;/script&gt;

// Bu kısmı sayacın görünmesini istediğiniz yere yazın
&lt;div id=&quot;sayac&quot;&gt;500&lt;/div&gt;[/sourcecode]
Umarım faydalı ve anlaşılır bir çalışma olmuştur.