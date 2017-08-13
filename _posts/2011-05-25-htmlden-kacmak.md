---
ID: 5764
post_title: 'HTML&#8217;den Kaçmak'
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/htmlden-kacmak-5764.html
published: true
post_date: 2011-05-25 12:37:56
---
PHP bir dosyayı çözümlerken, hangi bölümü yorumlayıp hangi bölümü yorumlamadan geçeceğine açılış ve kapanış etiketlerine bakarak karar verir. PHP'nin bu şekilde çalışıyor olması, PHP'nin çesitli türde birçok belgenin içine gömülebilmesini sağlar, çünkü PHP başlangıç ve bitiş etiketlerinin dışında kalan her şey PHP çözümleyicisi tarafından gözardı edilir. Çoğu zaman, bu örnekte olduğu gibi PHP'nin HTML içine gömülmüş olduğunu göreceksiniz.
<pre class="prettyprint lang-php" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;p&gt;Bu bölüm gözardı edilecektir.&lt;/p&gt;
&lt;?php echo 'Bu bölüm PHP tarafından çözümlenecektir.'; ?&gt;
&lt;p&gt;Bu bölüm de gözardı edilecektir.&lt;/p&gt;</pre>
Daha gelişmiş yapılar da kullanmanız mümkündür:
<h2>Örnek 1 - Gelişmiş önceleme</h2>
<pre class="prettyprint lang-php" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;?php
if ($ifade) {
    ?&gt;
    &lt;strong&gt;Bu önerme doğrudur.&lt;/strong&gt;
    &lt;?php
} else {
    ?&gt;
    &lt;strong&gt;Bu önerme yanlıştır.&lt;/strong&gt;
    &lt;?php
}
?&gt;</pre>
Bu beklendiği gibi çalışacaktır, çünkü PHP, ?&gt; kapanış etiketi ile karşılaştığında, tekrar bir açılış etiketi ile karşılaşana kadar bulduğu herşeyi (kapanış etiketinden sonraki satırsonu karakteri hariç - bkz, deyim ayırma) çıktılayacaktır. Buradaki örnek oldukça basit, ancak büyük metin bloklarını görüntülemek istediğimizde PHP'yi çözümleme kipinden çıkartmak çoğu zaman tüm metni echo ya da print ile görüntülemekten daha verimlidir.
PHP ile kullanılabilecek dört farklı açılış ve kapanış etiketi çifti vardır. Bunlardan ikisi, &lt;?php ?&gt; ve &lt;script language="php"&gt; &lt;/script&gt; her zaman kullanılabilir durumdadır. Diğer ikisi, kısa etiketler ve ASP tarzı etiketler olup <span style="text-decoration: underline;">php.ini</span> yapılandırma dosyası içersinden açılıp kapatılabilirler. Bazı kişiler kısa etiketleri ve ASP tarzı etiketleri daha kullanışlı bulmaktadır, ancak bu ikisi daha az taşınabilir olduklarından genellikle tavsiye edilmemektedir.
<blockquote><strong>Bilginize</strong>:
Bir diğer önemli nokta, PHP'yi XML ya da XHTML içine gömmek istiyorsanız standartlarla uyumlu kalabilmek için &lt;?php ?&gt; etiketlerini kullanmanız gerektiğidir.</blockquote>
<h2>Örnek 2 - PHP Açılış ve Kapanış Etiketleri</h2>
<pre class="prettyprint lang-php" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">1.  &lt;?php echo 'XHTML ya da XML belgeleri sunacaksanız, böyle yapın'; ?&gt;

2.  &lt;script language="php"&gt;
        echo 'bazı düzenleyiciler (FrontPage gibi) işlem
             yönergelerini sevmezler';
    &lt;/script&gt;

3.  &lt;? echo 'Bu en basit, SGML işlem yönergesidir'; ?&gt;
    &lt;?= ifade ?&gt; Bu "&lt;? echo ifade ?&gt;" için bir kısayoldur.

4.  &lt;% echo 'İsterseniz ASP tarzı etiketler kullanabilirsiniz'; %&gt;
    &lt;%= $degisken; # Bu "&lt;% echo . . ." %&gt; için bir kısayoldur.</pre>
Bir ve iki numaralı örneklerde gözüken etiketler her zaman kullanılabilirler. Bu ikisinden birincisi en geniş kullanıma sahip olanı ve en çok tercih edilenidir.

Kısa etiketler (üçüncü gibi) yalnızca php.ini içersinde short_open_tag yapılandırma yönergesiyle etkinleştirilmişlerse ya da PHP, --enable-short-tags derleme seçeneği ile yapılandırılmışsa kullanılabilirler.

ASP tarzı etiketler (dördüncü örnek) php.ini dosyasında asp_tags yapılandırma yönergesiyle etkinleştirilmişlerse kullanılabilirler.
<blockquote><strong>Bilginize:</strong>
Geliştirdiğiniz uygulamaları ya da kütüphaneleri başkalarına dağıtacaksanız ya da bu uygulamaları denetiminizde olmayan PHP sunucularına kuracaksanız kısa etiketleri kullanmaktan kaçınmalısınız, çünkü hedef sunucu kısa etiketleri desteklemiyor olabilir. Kodlarınızın taşınabilir ve yeniden dağıtılabilir olması için, alışkanlıkla kısa etiketleri kullanmadığınızdan emin olun.</blockquote>
<blockquote><strong>Bilginize:</strong>
PHP 5.2 ve öncesinde, çözümleyici, bir dosya içindeki tek şey olarak &lt;?php başlangıç etiketine izin vermezdi. PHP 5.3'ten itibaren izin verilmektedir.</blockquote>