---
ID: 483
post_title: >
  WordPress Aramasında Sayfalarınız
  Görünmesin
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/wordpress-aramasinda-sayfalariniz-gorunmesin-483.html
published: true
post_date: 2012-06-12 02:14:37
---
Merhaba arkadaşlar,

Bu konu ile ilgili açılmış çok fazla başlık gördüm. Wordpress aramalarında sadece yazdıklarım aransın, sayfalarım aranmasın şeklinde istekler var. Bu isteklere verilen cevaplar yeterli bir cevap değil.
<h3>Neden Yeterli Değil?</h3>
Verilen cevaplar sistemde mantıksal bir çalışma hatasına sebep oluyor. Cevap şu şekilde:
<blockquote>Arama listeleme sayfanızda while altına tek satır kod ekliyorsunuz. Eğer döngüde çıkan bir sayfa ise <strong>continue</strong> ile döngünün başına atıyor.</blockquote>
Fakat arama sorgunuz da sadece sayfalar mevcut ama size bu sayfalar gizleniyor. Bu nedenle "Sonuç bulunamadı" yazısı da görünmüyor. Çıplak bir arama sayfası geliyor ve bozuk bir izlenim uyandırıyor.
<h3>Çözüm Ne?</h3>
Çözümü oldukça basit. Kullandığınız temada arama formunun oluşturulduğu yeri bulun. Genelde şöyle bir şeydir:

<pre class="lang:html decode:1 " >&amp;lt;form method=&amp;quot;get&amp;quot; id=&amp;quot;searchform&amp;quot; action=&amp;quot;&amp;lt;?php bloginfo('home'); ?&amp;gt;/&amp;quot;&amp;gt;
     &amp;lt;input type=&amp;quot;text&amp;quot; value=&amp;quot;&amp;lt;?php echo $search_text; ?&amp;gt;&amp;quot; name=&amp;quot;s&amp;quot; id=&amp;quot;s&amp;quot;  /&amp;gt;
     &amp;lt;input type=&amp;quot;submit&amp;quot; value=&amp;quot;Ara&amp;quot; /&amp;gt;
&amp;lt;/form&amp;gt;</pre>

Burada yapmanız gereken hidden bir input türünde post_type="post" parametresini de arama formuna eklemektir.

<pre class="lang:html decode:1 " >&amp;lt;input type=&amp;quot;hidden&amp;quot; name=&amp;quot;post_type&amp;quot; value=&amp;quot;post&amp;quot; /&amp;gt;</pre>

Bu tek satırlık kodu formunuzun içine ekleyin. Bu sayede sadece blog postlarında arama yapılacaktır. Formunuzun son hali şöyle olacaktır:

<pre class="lang:html decode:1 " >&amp;lt;form method=&amp;quot;get&amp;quot; id=&amp;quot;searchform&amp;quot; action=&amp;quot;&amp;lt;?php bloginfo('home'); ?&amp;gt;/&amp;quot;&amp;gt;
     &amp;lt;input type=&amp;quot;text&amp;quot; value=&amp;quot;&amp;lt;?php echo $search_text; ?&amp;gt;&amp;quot; name=&amp;quot;s&amp;quot; id=&amp;quot;s&amp;quot;  /&amp;gt;
     &amp;lt;input type=&amp;quot;hidden&amp;quot; name=&amp;quot;post_type&amp;quot; value=&amp;quot;post&amp;quot; /&amp;gt;
     &amp;lt;input type=&amp;quot;submit&amp;quot; value=&amp;quot;Ara&amp;quot; /&amp;gt;
&amp;lt;/form&amp;gt;</pre>

Umarım işinize yarar ve faydalı bir yazı olmuştur.

Kolay gelsin