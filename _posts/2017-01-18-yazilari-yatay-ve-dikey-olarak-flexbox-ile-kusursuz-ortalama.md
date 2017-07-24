---
ID: 6210
post_title: >
  Yazıları Yatay ve Dikey Olarak Flexbox
  ile Kusursuz Ortalama
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/web-tasarim-2/yazilari-yatay-ve-dikey-olarak-flexbox-ile-kusursuz-ortalama-6210.html
published: true
post_date: 2017-01-18 11:16:08
---
"Yazılarınızı yatay olarak ortalamanın kusurlusu kusursuzu olmaz, zaten yıllardır ortalıyoruz gayet güzelce." dediğinizi duyar gibiyim. Evet haklısınız da. Yatay olarak ortalama zaten hep kolaydı. Peki ya yazılarınızı değişken yükseliğe sahip alanlarda dikey olarak ortalamadan ne haber? Bu durum karşınıza her çıktığında eminim ki problem olmuştur. Bu makaleyle beraber yazılarınızı dikey olarak Flexbox ile ortalamanın ne kadar kolay olduğunu göstereceğim.
<h2>Eski Usul Ortalama</h2>
Flexbox ile ortalamaya geçmeden önce daha evvel bunu nasıl yaptığımı anlatmak istiyorum. Bir resim düşünün ve bu resmin üzerinde 3 satır slogan veya yazı düşünün. Düşünmeyelim hazırlayalım hatta.

Öncelikle şu şekilde bir HTML bloğumuz olsun:
<pre class="prettyprint lang-html" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;div class="slogan"&gt;
    &lt;div class="slogan-yazisi"&gt;
        &lt;h1&gt;Flexbox Sloganımız&lt;/h1&gt;
        &lt;h3&gt;Tamamen Ortalanmış&lt;/h3&gt;
        &lt;h6&gt;Kaç satır olduğunun önemi olmaksızın ortalanmış hemde.&lt;/h6&gt;
    &lt;/div&gt;
&lt;/div&gt;</pre>
Şimdi bir de başlangıç CSS'imiz olsun. Yani basit bir tasarımımız olsun. Fakat herhangi bir ortalama, kaydırma vs. olmadan:
<pre class="prettyprint lang-css" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">html, body{
    margin: 0;
    padding: 0;
    font-family: Helvetica, Arial, sans-serif;
}

h1{ font-size: 60px; }
h3{
    font-size: 32px;
    font-weight: normal;
    text-transform: uppercase;
    letter-spacing: 4px;
}
h6{ font-size: 22px; }

.slogan h1, .slogan h3, .slogan h6{
    margin: 0;
    text-shadow: 2px 2px 6px #000;
}

.slogan{
    color: white;
    background: url('https://s3-us-west-2.amazonaws.com/s.cdpn.io/409269/banner-flowers.jpg') top left/cover no-repeat;
    height: 300px;
}</pre>
Bu çalışmanın canlı önizlemesini <a href="http://codepen.io/oralunal/pen/ggLyWY/" target="_blank">buraya</a> tıklayarak görüntüleyebilirsiniz. Ekran çıktınız şu şekilde olacaktır:

<img class="aligncenter size-large wp-image-6211" src="http://www.trkodlama.com/wp-content/uploads/2017/01/flexbox-1-1024x257.png" alt="" width="670" height="168" />

Öncelikle yazımızı yatay olarak ortalayalım:
<pre class="prettyprint lang-css" data-start-line="1" data-visibility="visible" data-highlight="19" data-caption="">html, body{
    margin: 0;
    padding: 0;
    font-family: Helvetica, Arial, sans-serif;
}

h1{ font-size: 60px; }
h3{
    font-size: 32px;
    font-weight: normal;
    text-transform: uppercase;
    letter-spacing: 4px;
}
h6{ font-size: 22px; }

.slogan h1, .slogan h3, .slogan h6{
    margin: 0;
    text-shadow: 2px 2px 6px #000;
    text-align: center;
}

.slogan{
    color: white;
    background: url('https://s3-us-west-2.amazonaws.com/s.cdpn.io/409269/banner-flowers.jpg') top left/cover no-repeat;
    height: 300px;
}</pre>
Bu işin kolay kısmıydı. <code class="prettyprint lang-css" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">text-align: center;</code> ile anında yazımızı ortaladık. Dikey olarak ortalamaya gelince eğer yazımız tek satır olsaydı <code class="prettyprint lang-css" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">line-height: 300px;</code> yaparak içinde bulunduğu divin yüksekliğinde line-height tanımlayarak yazımızı dikey olarak ortalayabilirdik. Peki bu şekilde 3 başlık etiketi varsa şayet içinde paragraf varsa ne yapıyoruz? Tabii ki <strong>slogan-yazisi</strong> alanına <strong>padding-top</strong> ekliyoruz ve görsel olarak okey verdiğimiz değeri yazıyoruz. Yani CSS'imiz şu şekilde olacak:
<pre class="prettyprint lang-css" data-start-line="1" data-visibility="visible" data-highlight="19,28-30" data-caption="">html, body{
    margin: 0;
    padding: 0;
    font-family: Helvetica, Arial, sans-serif;
}

h1{ font-size: 60px; }
h3{
    font-size: 32px;
    font-weight: normal;
    text-transform: uppercase;
    letter-spacing: 4px;
}
h6{ font-size: 22px; }

.slogan h1, .slogan h3, .slogan h6{
    margin: 0;
    text-shadow: 2px 2px 6px #000;
    text-align: center;
}

.slogan{
    color: white;
    background: url('https://s3-us-west-2.amazonaws.com/s.cdpn.io/409269/banner-flowers.jpg') top left/cover no-repeat;
    height: 300px;
}

.slogan-yazisi{
    padding-top: 60px;
}</pre>
Codepen'de canlı olarak görüntülemek için <a href="http://codepen.io/oralunal/pen/bgBJve" target="_blank">buraya</a> tıklayınız. Ekran görüntüsü şu şekilde olacaktır:

<img class="aligncenter size-large wp-image-6214" src="http://www.trkodlama.com/wp-content/uploads/2017/01/flexbox-2-1024x258.png" alt="" width="670" height="169" />
<h2>Yeni Usul Ortalamak İsteseydik Flexbox ile Nasıl Yapacaktık?</h2>
HTML bloğumuz aynen kalmak üzere <strong>Flexbox</strong> ile ortalama yapmak için öncelikle <strong>.slogan</strong> elementine <code class="prettyprint lang-css" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">display: flex;</code> ekleyeceğiz. Ve daha sonra <strong>justify-content</strong> ve <strong>align-items</strong> kullanarak yatay ve dikey olarak ortalamış olacağız.

Justify-content:center ile yazımızı yatayda ortalarken <strong>align-items: center</strong> ile yazımızı <strong>dikeyde ortalıyoruz</strong>.
<pre class="prettyprint lang-css" data-start-line="1" data-visibility="visible" data-highlight="19,26-28" data-caption="">html, body{
    margin: 0;
    padding: 0;
    font-family: Helvetica, Arial, sans-serif;
}

h1{ font-size: 60px; }
h3{
    font-size: 32px;
    font-weight: normal;
    text-transform: uppercase;
    letter-spacing: 4px;
}
h6{ font-size: 22px; }

.slogan h1, .slogan h3, .slogan h6{
    margin: 0;
    text-shadow: 2px 2px 6px #000;
    text-align: center;
}

.slogan{
    color: white;
    background: url('https://s3-us-west-2.amazonaws.com/s.cdpn.io/409269/banner-flowers.jpg') top left/cover no-repeat;
    height: 300px;
    display: flex;
    justify-content: center;
    align-items: center;
}</pre>
Codepen'de bu çalışmayı görüntülemek için <a href="http://codepen.io/oralunal/pen/OWbGaN" target="_blank">buraya</a> tıklayınız. Ekran çıktısı aşağıdaki gibi olacaktır:

<img class="aligncenter size-large wp-image-6215" src="http://www.trkodlama.com/wp-content/uploads/2017/01/flexbox-3-1024x259.png" alt="" width="670" height="169" />

Flexbox yeni teknoloji olmakla beraber eski tarayıcılarda desteklenmemektedir. Flexbox destekleyen tarayıcıları görmek için <a href="http://www.w3schools.com/css/css3_flexbox.asp" target="_blank">buraya</a> tıklayınız. Daha derin bilgi için Fatih abinin hazırladığı <a href="http://fatihhayrioglu.com/yenilenmis-flex-modulu/" target="_blank">kaynağı</a> inceleyebilirsiniz.

Faydalı olması dileğiyle, kolay gelsin