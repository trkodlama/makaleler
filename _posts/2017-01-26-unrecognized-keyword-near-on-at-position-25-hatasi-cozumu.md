---
ID: 6443
post_title: 'Unrecognized keyword. (near &#8220;ON&#8221; at position 25) Hatası ve Çözümü'
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/unrecognized-keyword-near-on-at-position-25-hatasi-cozumu-6443.html
published: true
post_date: 2017-01-26 15:22:02
---
WordPress veritabanınızın yedeğini aldınız ve başka bir yere yüklemeye çalışıyorsunuz. PHPMyadmin'de .sql dosyanızı seçtiğiniz, yükle butonuna bastınız. Başarılı olduğunu belirten yeşil kutuyu görmeyi umarken kırmızı bir kutu sizi karşılıyor ve içinde şunlar yazıyor:
<pre class="prettyprint lang-rst" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">Error

Static analysis:

1 errors were found during analysis.

    Unrecognized keyword. (near "ON" at position 25)

SQL query: Edit Edit

SET FOREIGN_KEY_CHECKS = ON;

MySQL said: Documentation
#2006 - MySQL server has gone away</pre>
Hayda, ne alaka şimdi bu hata? Bunun çeşitli sebepleri olabilir fakat hepside memory ve zaman limitlerine dayanıyor. Bu problemi çözmek için PHP.ini dosyanızda aşağıdaki ayarları güncelleyin:
<pre class="prettyprint lang-ini" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">max_execution_time = 600 
max_input_time = 600 
memory_limit = 1024M 
post_max_size = 1024M</pre>
Daha sonra my.cnf dosyanızı yani MySQL dosyanızı güncelleyin:
<pre class="prettyprint lang-ini" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">max_allowed_packet = 1024M</pre>
Artık PHP My Admin'den WordPress'inizi rahatlıkla yükleyebilirsiniz. Yükleme işleminiz bittiğinde bu ayarları eski haline dönüştürmeyi unutmayın.