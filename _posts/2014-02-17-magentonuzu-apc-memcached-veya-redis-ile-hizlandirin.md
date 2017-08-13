---
ID: 5283
post_title: 'Magento&#8217;nuzu APC, Memcached veya Redis ile Hızlandırın'
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/magentonuzu-apc-memcached-veya-redis-ile-hizlandirin-5283.html
published: true
post_date: 2014-02-17 15:29:37
---
Merhaba arkadaşlar,

Bugünkü makalemde sizlere Magento e-ticaret sitenizi <a href="http://pecl.php.net/package/APC" target="_blank">APC</a>, <a href="http://memcached.org/" target="_blank">Memcached</a> ve <a href="http://redis.io/" target="_blank">Redis</a> ile nasıl hızlandıracağınızı anlatacağım. Hepsinin artılarından ve eksilerin bahsedeceğim. Ama öncelikle Magento'nun önbellekleme sistemine bir göz atalım.
<h2>Magento'nun İki-Aşamalı Önbellekleme Sistemi</h2>
Magento varsayılan olarak Zend Framework'ün iki-aşamalı önbellekleme sistemini kullanır.

Basit olarak anlatmak gerekirse önbellek kayıtlarını iki ayrı sistemle kaydedir. APC veya Memcached çok hızlıdır fakat sınırlıdır. Yavaş olan önbelleklemesi is dosya sistemidir.

APC ve Memcached key/value olarak önbellekleme yapar, fakat tagging(önbellek kayıtlarını gruplama) desteği yoktur. Dosya sistemi ve Redis ise tagging desteklidir.
<h2><a href="http://www.trkodlama.com/wp-content/uploads/2014/02/magento_two_level_caching_overview.png"><img class="aligncenter wp-image-5284" src="http://www.trkodlama.com/wp-content/uploads/2014/02/magento_two_level_caching_overview.png" alt="magento_two_level_caching_overview" width="567" height="401" /></a>Magento Önbellek Sistemlerini İnceleyelim</h2>
<h3>Dosya sistemi (var/cache)</h3>
Magento varsayılan olarak önbelleklerini dosya sistemi ile sağlar. Bu önbellekleri var/cache klasörü altında bulabilirsiniz.

Bu önbellekleme sistemi küçük web siteleri için oldukça iyidir. Fakat sunucuya fazla istek göndermeye başladığınız zaman bu önbellekleri okumak gittikçe yavaşlamaya başlar çünkü önbellek kayıtlarının miktarı boyutları artar.

Magento önbellek sistemi tag'ler(etiketler) üzerine kuruludur; bu da önbellek kayıtlarınızın belirli önbellek gruplarına dahil olması demektir.

<strong>Avantajları
</strong>Varsayılan olarak çalışır, herhangi bir kurulum vs. ile uğraşmanıza gerek kalmaz.

<strong>Dezavantajları
</strong>Magento yeni sipariş verildiğinde, yeni ürün eklendiğinde  mağazanızın güncel kalması için ön bellek kayıtlarınız temizler. Fakat Magento bu temizlik sırasında bütün ön bellek gruplarınızdaki ön bellek dosyalarını tek tek açar ve satır satır kontrol eder. Eğer 1000 üründen fazla ürününüz varsa Magento'da kayıtlı bu 50MB'dan büyük ön bellek dosyasına işaret eder. 50MB ön bellek boyutu da 3500 kadar ön bellek dosyasına denk geldiğinde her dosyayı açıp işlemenin ne kadar zahmetli ve zaman alacağını siz düşünün.

<strong>Performansını artırmak için
</strong>1. Normal hard-disk yerine SSD kullanın
2. var/cache dizinini <a href="http://en.wikipedia.org/wiki/Tmpfs" target="_blank">tmpfs</a> içine koyun.
<h3>APC - Alternative PHP Cache (Key/Value)</h3>
<a href="http://pecl.php.net/package/APC" target="_blank">APC</a>, Alternative PHP Cache'in kısaltması olan ve PHP için ücretsiz ve açık kaynak kodlu opcode ön belleklemedir.

<strong>Avantajları
</strong>Çok hızlı bir ön bellekleme sistemidir.

<strong>Dezavantajları
</strong>APC, tagging'i desteklemez. Dosya sistemi ile yavaş ön belleklemeye de devam edersiniz.

<strong>Performansını artırmak için
</strong>1. "apc.shm_size" parametresi ile APC'ye yeterli hafızayı atadığınıza emin olun
2. Aşağıdaki en iyi php.ini ayarlarını uygulayın.

<b>Ayarlama (app/etc/local.xml)</b>
<pre class="prettyprint lang-xml" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;global&gt;
  ...
  &lt;cache&gt;
    &lt;backend&gt;apc&lt;/backend&gt;
      &lt;prefix&gt;mgt_&lt;/prefix&gt;
  &lt;/cache&gt;
  ...
&lt;/global&gt;</pre>
<b>php.ini Ayarları</b>
<pre class="prettyprint lang-text" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">apc.enabled = 1
apc.optimization  = 0
apc.shm_segments = 1
apc.shm_size = 768M
apc.ttl = 48000
apc.user_ttl  = 48000
apc.num_files_hint = 8096
apc.user_entries_hint = 8096
apc.mmap_file_mask = /tmp/apc.XXXXXX
apc.enable_cli = 1
apc.cache_by_default  = 1
apc.max_file_size = 10M
apc.include_once_override = 0</pre>
<h3>Memcached (Key/Value)</h3>
<strong>memcached</strong> yüksek performanslı dağıtılmış hafıza nesnelerini önbellekleyen bir sistemdir. Web uygulamalarında veritabanı yükünü hafifletmek için kullanılır.

<strong>Avantajları
</strong>Çok hızlı bir ön bellekleme sistemidir.

<strong style="line-height: 1.5em;">Dezavantajları
</strong>Memcached, tagging'i desteklemez. Dosya sistemi ile yavaş ön belleklemeye de devam edersiniz.

<strong>Gereksinimler
</strong>- Memcached sunucu
- Memcached için olan PHP eklenti

<strong>Ayarlama (app/etc/local.xml)</strong>
<pre class="prettyprint lang-xml" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;global&gt;
...
&lt;cache&gt;
  &lt;backend&gt;memcached&lt;/backend&gt;&lt;!-- apc / memcached / boş=dosya --&gt;
  &lt;memcached&gt;&lt;!-- memcached ön bellekleme --&gt;
    &lt;servers&gt;&lt;!-- birden fazla sunucu eklenebilir --&gt;
      &lt;server&gt;
        &lt;host&gt;&lt;![CDATA[127.0.0.1]]&gt;&lt;/host&gt;
        &lt;port&gt;&lt;![CDATA[11211]]&gt;&lt;/port&gt;
        &lt;persistent&gt;&lt;![CDATA[1]]&gt;&lt;/persistent&gt;
        &lt;/server&gt;
    &lt;/servers&gt;
    &lt;compression&gt;&lt;![CDATA[0]]&gt;&lt;/compression&gt;
    &lt;cache_dir&gt;&lt;![CDATA[]]&gt;&lt;/cache_dir&gt;
    &lt;hashed_directory_level&gt;&lt;![CDATA[]]&gt;&lt;/hashed_directory_level&gt;
    &lt;hashed_directory_umask&gt;&lt;![CDATA[]]&gt;&lt;/hashed_directory_umask&gt;
    &lt;file_name_prefix&gt;&lt;![CDATA[]]&gt;&lt;/file_name_prefix&gt;
  &lt;/memcached&gt;
&lt;/cache&gt;
...
&lt;/global&gt;</pre>
<h3>Redis</h3>
Bu ön bellekleme sistemi sayesinde Redis Sunucusunu merkezi depolama olarak kullanacaksınız. Tagging bu sistemde destekleniyor artık yavaş depolamaya hiç ihtiyacınız kalmayacak. Birden fazla sunucu havuzu ile çalışıyorsanız bu ön bellekleme sistemi tam olarak aradığınız sistem.

<strong>Avantajları
</strong>Tagging desteği olan süper hızlı bir önbellekleme sistemidir.
Günlük ziyareti 500.000 üzerinde olan Magento'da test edilmiş olup sonuç muhteşem ve kusursuz olmuştur.

<b>Gereksinimler
</b>Sunucuda Redis kurulu olmak zorundadır.
PHP Eklentisi olan phpredis kurulu olmalıdır.
Magento eklentisi olan <a href="https://github.com/colinmollenhour/Cm_Cache_Backend_Redis" target="_blank">“Cm_Cache_Backend_Redis”</a> kurulu olmaldır.

<strong>Kurulum</strong>
<ol>
 	<li><a href="http://redis.io/download" target="_blank">Redis</a>'i kurun. (2.4+ gereklidir.)</li>
 	<li><a href="https://github.com/nicolasff/phpredis" target="_blank">phpredis</a>'i kurun.</li>
 	<li><a href="https://github.com/colinmollenhour/Cm_Cache_Backend_Redis" target="_blank">“Cm_Cache_Backend_Redis”</a> Magento eklentisini kurun.</li>
 	<li>app/etc/local.xml dosyasını düzenleyin</li>
</ol>
<pre class="prettyprint lang-xml" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;global&gt;
...
&lt;cache&gt;
  &lt;backend&gt;Cm_Cache_Backend_Redis&lt;/backend&gt;
  &lt;backend_options&gt;
    &lt;server&gt;127.0.0.1&lt;/server&gt;
    &lt;port&gt;6379&lt;/port&gt;
    &lt;persistent&gt;&lt;/persistent&gt;
    &lt;database&gt;0&lt;/database&gt;
    &lt;password&gt;&lt;/password&gt;
    &lt;force_standalone&gt;0&lt;/force_standalone&gt;
    &lt;connect_retries&gt;1&lt;/connect_retries&gt;
    &lt;automatic_cleaning_factor&gt;0&lt;/automatic_cleaning_factor&gt;
    &lt;compress_data&gt;1&lt;/compress_data&gt;
    &lt;compress_tags&gt;1&lt;/compress_tags&gt;
    &lt;compress_threshold&gt;20480&lt;/compress_threshold&gt;
    &lt;compression_lib&gt;gzip&lt;/compression_lib&gt; &lt;!-- Supports gzip, lzf and snappy --&gt;
  &lt;/backend_options&gt;
&lt;/cache&gt;
...
&lt;/global&gt;</pre>
<h2>Sonuç</h2>
Eğer küçük bir web siteniz varsa APC+Dosya Sistemi işinizi rahatlıkla görecektir. Hard-disk yerine SSD kullanıp ve önbellek klasörünüzü de tmpfs içine koyarsanız gayet hızlı olacaktır. Fakat büyük web siteleri için(tek sunuculu, çok sunuculu) en güzel çözüm Redis'dir. Redis'i kurup kullanmanızı öneririm.

Kolay gelsin,