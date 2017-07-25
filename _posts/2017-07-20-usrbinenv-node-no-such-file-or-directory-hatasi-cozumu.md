---
ID: 9319
post_title: '&#8220;/usr/bin/env: ‘node’: No such file or directory&#8221; Hatası ve Çözümü'
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/usrbinenv-node-no-such-file-or-directory-hatasi-cozumu-9319.html
published: true
post_date: 2017-07-20 21:11:58
---
Uzun zamandır Ubuntu kullanmayınca epey paslanmışım haliyle. Az önce bir problem yaşadım. <strong>uglifyjs</strong> kullanmak istedim fakat o da ne! Kurulumu bir türlü tamamlayamadım. Uglifyjs'i Node.JS aracılığıyla rahatlıkla edinebilirsiniz. Peki node.js nedir? Kısaca ona değinelim.
<blockquote>
<h3>node.js Nedir?</h3>
<b>NodeJS</b>, Chrome web tarayıcısının da üzerinde çalıştığı gibi, V8 javascript motoru üzerinde çalışan, event-driven, nonblocking I/O modeli kullanan, ölçeklenebilir uygulamalar geliştirmek için dizayn edilmiş bir platformdur.</blockquote>
node.js'in ne olduğu hakkında kısaca bir fikir sahip olduğunuzu düşünüyorum. Eğer yeterince açıklayıcı olmadıysa, ki olmaması aslında gayet normal, kaynaklar listesindeki 1. nolu kaynağı görüntüleyin.

Gelelim Uglifyjs konusunda. Symfony framework'ü ile TR Kodlama'yı baştan hazırlıyorum. WordPress'i tamamen arkamda bırakmak istiyorum. Bunun temel nedeni ise WordPress'in kalıplarına sıkışarak iş yapmaya çalışmak oldukça zor! Dilediğim eklemeleri ve yahut değişiklikleri ha deyince yapamamak oldukça canımı sıkıyor. Onca işimin gücümün arasında birde WP-Core'u anlamaya çalışırsam vay halime... Uglifyjs ve uglifycss Symfony Assetics ile beraber kullanacağınız iki adet yazılımdır. Bu yazılımlar isimlerindende anlaşılacak gibi JS ve CSS dosyalarınızı çirkinleştirir. JS ve CSS dosyalarınızı birleştirir ve sıkıştırır. Development modundayken orjinal halini görürken Production modundayken birleştirir ve sıkıştırır.

Neyse terminal ekranında <pre class="class:prettyprint lang-sh data-start-line:1 data-visibility:visible data-highlight: data-caption: decode:1 " >uglifyjs --help</pre> komutunu girdiğimde devamlı şu hata ile karşılaştım:
<pre class="prettyprint lang-sh" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">/usr/bin/env: ‘node’: No such file or directory</pre>
Bu durumun üstesinden gelmek için <em><strong>nodejs-legacy</strong></em> kurmak gerekiyormuş. Onu da hemen şu komutla kuruyoruz:
<pre class="prettyprint lang-sh" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">apt install nodejs-legacy</pre>
Umarım bir probleminiz çözülmüştür. Faydalı olduysam ne mutlu :)
<h4>Kaynaklar</h4>
<ol>
 	<li>http://dergi.bmo.org.tr/teknoloji/nodejs-nedir</li>
 	<li>https://symfony.com/doc/current/assetic/uglifyjs.html</li>
 	<li>https://github.com/animetosho/Nyuu/issues/14</li>
</ol>