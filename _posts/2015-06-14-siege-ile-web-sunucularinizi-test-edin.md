---
ID: 5805
post_title: >
  Siege ile Web Sunucularınızı Test
  Edin
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/siege-ile-web-sunucularinizi-test-edin-5805.html
published: true
post_date: 2015-06-14 20:05:38
---
<strong>Siege</strong> web sunucularınıza ağır yük bindirildiğinde ne gibi bir durumla karşılaşacağınızı görmenize olanak sağlayan HTTP yük test etme ve kıyaslama programıdır. Transfer edilen veriyi, sunucu cevap süresini, işlem hızı, çıktı ve eşzamanlılık değerlerini hesaplar. Siege üç işlem modu sunuyor: internet simülasyonu, brute force ve regresyon(regression, türkçe karşılığını bilemedim).

Bu rehber Debian veya Ubuntu sistemler için hazırlanmıştır.

<h2>Siege'i İndirin ve Ayarlarını Yapın</h2>

<ol>
    <li>Sisteminizi güncelleştirin. Bunu her yeni yazılımdan önce yapmanızı tavsiye ediyorum.

[text]sudo apt-get update &amp;&amp; sudo apt-get upgrade --show-upgraded[/text]

</li>
    <li>Siege'nin son versiyonunu indirin(3.1.0 şu anda), <strong><a href="https://www.joedog.org/siege-home/" target="_blank">Siege'nin websitesi</a></strong>nden de her zaman indirebilirsiniz.

[text]wget http://download.joedog.org/siege/siege-latest.tar.gz[/text]

</li>
    <li>Dosyaları çıkartın:

[text]tar -zxvf siege-latest.tar.gz[/text]

</li>
    <li>Siege dizinine gelin:

[text]cd siege-*/[/text]

</li>
    <li>Eğer GNU Compiler Collection(gcc) kurulu değilse şimdi onu kurun. Eğer kuruluysa bu adımı atlayın:

[text]sudo apt-get install build-essential[/text]

</li>
    <li>Configure yapın ve kurulumu tamamlayın:

[text]./configure
make
sudo make install[/text]

</li>
    <li>Bir ayar dosyası oluşturun:

[text]siege.config[/text]

</li>
    <li><em><strong>.siegerc</strong> </em>dosyasını bulun ve açın.</li>
    <li>Siege'nin Tavsiye edilen kalıcı bağlantı sayısı 25'dir. Ayar dosyamızı da böyle yazalım. Loglarımızın kaydedileceği yeri tanımlayalım. Aşağıdaki ayar dosyasında gerekli yerleri kendi isteklerinize göre ayarlayın:<strong>.siegerc dosyasının bir kısmı:</strong>

[text]...

#
# Variable declarations. You can set variables here
# for use in the directives below. Example:
# PROXY = proxy.joedog.org
# Reference variables inside ${} or $(), example:
# proxy-host = ${PROXY}
# You can also reference ENVIRONMENT variables without
# actually declaring them, example:
logfile = $(HOME)/siege.log

...

#
# Default number of simulated  concurrent users
# ex: concurrent = 25
#
concurrent = 25

#
# Default duration of the siege.  The right hand argument has
# a modifier which specifies the time units, H=hours, M=minutes,
# and S=seconds. If a modifier is not specified, then minutes
# are assumed.
# ex: time = 50M
#
time = 1M[/text]

</li>
</ol>

<strong>Siege</strong> kurulumu bitti. Artık kullanmak için hazırsınız.

<h2>Siege'i Çalıştırın</h2>

Siege'i varsayılan ayarlarla çalıştırmak için aşağıdaki komutu kullanıyoruz. Biz bu örnekte <strong>www.trkodlama.com</strong> adresini çalıştıracağız:

[text]siege www.trkodlama.com[/text]

Siege size şöyle bir çıktı verecektir:

[text]** SIEGE 2.70
** Preparing 25 concurrent users for battle.
The server is now under siege...
Lifting the server siege...      done.
Transactions:		        2913 hits
Availability:		      100.00 %
Elapsed time:		       59.51 secs
Data transferred:	        0.41 MB
Response time:		        0.00 secs
Transaction rate:	       48.95 trans/sec
Throughput:		        0.01 MB/sec
Concurrency:		        0.04
Successful transactions:        2913
Failed transactions:	           0
Longest transaction:	        0.01
Shortest transaction:	        0.00

FILE: /var/log/siege.log
You can disable this annoying message by editing
the .siegerc file in your home directory; change
the directive 'show-logfile' to false.[/text]

Eğer bir bağlantı hatası yoksa ve <strong>availability</strong> satırı 100.00% şeklindeyse yapılan testi sunucunuzun başarı ile geçtiğini anlayabilirsiniz.

<h2>Siege Komutları</h2>

Siege ayar dosyanızdan farklı ayarlarla çalışmanız için bazı komutlarımız var:

<ul>
    <li><strong>-c [num]: </strong>Kalıcı bağlantı sayısını ayarlar. Bir çok web sitesinin genelden 200ün altındadır bu değer.</li>
    <li><strong>-t [num]: </strong>Siege'i çalıştırdığınızda süre limitini ayarlar. saniyeler için <strong>s</strong>, dakikalar için <strong>m</strong> ve saatler için <strong>h</strong> kullanılır. Bu ayarda aralarda boşluk olmaması önemlidir. Yani -<strong>t10s</strong> doğru bir kullanımken <strong>-</strong><strong>t 10s</strong> yanlıştır.</li>
    <li><strong>-d [num]: </strong>Siege kullanıcıları için gecikmeyi ayarlar. Bu gecikme süresi 1 ile ayarlanan sayı arasındadır. Varsayılan değer <strong>3</strong>'tür.</li>
    <li><strong>-l:</strong> Bir kayıt dosyası oluşturulmasını sağlar.</li>
    <li><strong>-C:</strong> Siege'in o anki ayarlarını görüntüler.</li>
    <li><strong>-V:</strong> Siege'in versiyonunu yazdırır.</li>
    <li><strong>-h:</strong> Yardım dökümanını gösterir.</li>
</ul>

<h3>Daha Fazla Bilgi?</h3>

Daha fazla bilgiye mi ihtiyaç var? Daha fazla bilgi için <strong><a href="http://www.joedog.org/siege-home" target="_blank">Siege sitesi</a></strong>ni ziyaret edebilirsiniz. Umarım işinize yarar :)

&nbsp;