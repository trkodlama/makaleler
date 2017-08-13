---
ID: 6337
post_title: Robots.txt Dosyası ve Kullanımı
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/web-tasarim-2/robots-txt-dosyasi-kullanimi-6337.html
published: true
post_date: 2017-01-23 12:19:07
---
Robots.txt dosyası web sitenizin ana dizininde bulunan (ör: trkodlama.com/robots.txt) ve web sayfalarını indeksleyen botların düzenli olarak girip baktıları sizin yetki dosyanızıdır. Yani indeksleme yapan botlara web sitenize girmeleri için izin verip vermediğinizi bu dosya ile bildirirsiniz.
<h2>1 - Robots.txt dosyası nasıl oluşturulur?</h2>
Herhangi bir metin düzenleyicisi (örneğin, Not Defteri veya WordPad) kullanarak "robots.txt" adında bir dosya oluşturun ve bu dosyayı aşağıda verilen kurallara uygun olarak doldurun. Daha sonra bu dosya sitenizin kök dizinine yüklenmelidir.

robots.txt dosyanızın doğru işleyip işlemediğini denetlemek için, <a href="https://webmaster.yandex.com.tr/robots.xml" target="_blank">robots.txt dosyası analiz aracı</a>'ndan yararlanın.
<h2>2 - "User-agent" direktifi</h2>
Sitenin kök dizininde bulunması gereken robots.txt dosyasını kullanarak, robotların sitenize erişimini yönetebilirsiniz. Robotların çoğu <a href="http://www.robotstxt.org/robotstxt.html" target="_blank">http://www.robotstxt.org/robotstxt.html</a> açıklama standardını destekler.

Robotlar belirli aralıklarla robots.txt dosyanızı kontrol eder. Eğer böyle bir dosya yoksa, metin dosyası değilse veya robotun sorgusuna '200' HTTP kodu döndürülürse, robotun erişiminin kısıtlı olmadığı kabul edilir. Aynı robots.txt dosyasında 'User-agent:' ile başlayan kayıtların olup olmadığı denetlenir; bu kayıtlar arasında robot kendi adını veya '*' alt dizelerini arar (büyük/küçük harfe duyarlı değil) ve '<code class="prettyprint lang-plain_text" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">User-agent: RobotAdı</code>' bulunması durumunda '<code class="prettyprint lang-plain_text" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">User-agent: *</code>' için yönergeler dikkate alınmaz. '<code class="prettyprint lang-plain_text" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">User-agent: RobotAdı</code> ' ve '<code class="prettyprint lang-plain_text" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">User-agent: *</code> ' kayıtları yoksa, robotun erişiminin kısıtlanmadığı kabul edilir. Örnek:
<pre class="prettyprint lang-text" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">User-agent: * # Google Googlebot-Image robotları tarafından kullanılmaz
Allow: /

User-agent: Google # Tüm Google robotları tarafından kullanılır
Disallow: /kodlama # kodlama dizinine erişemez

User-agent: Googlebot-Image # Google Resim robotları tarafından kullanılır
Disallow: /resimler</pre>
<h2>3 - Disallow ve Allow direktiflerinin kullanımı</h2>
Robotun sitenin belirli bölümlerine veya sitenin tümüne erişimini yasaklamak için, '<strong>Disallow</strong>' yönergesini kullanın. Örnekler:
<pre class="prettyprint lang-text" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">User-agent: Google 
Disallow: / # Tüm siteye erişimi engeller

User-agent: Google 
Disallow: /cgi-bin # '/cgi-bin' ile başlayan
                   # sayfalara erişimi engeller</pre>
<span style="text-decoration: underline;"><strong>NOT!</strong></span>

'User-agent' ile 'Disallow'-'Allow' yönergeleri arasında ve aynı şekilde 'Disallow'-'Allow' yönergeleri arasında boş satır sonları <strong>bulunamaz</strong>.

Bunun dışında, standarda uygun olarak, her 'User-agent' yönergesinden önce boş satır sonu eklenmesi önerilir.

'#' işareti açıklamayı belirtmek amacıyla kullanılmaktadır. Bu simgeden sonra ilk satır sonuna kadar olan kısımlar dikkate alınmaz.
Robotun sitenin belirli bölümlerine veya sitenin tümüne erişimine izin vermek için, 'Allow' yönergesini kullanın. Örnekler:
<pre class="prettyprint lang-text" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">User-agent: Google 
Allow: /cgi-bin 
Disallow: /

# '/cgi-bin' ile başlayan 
# sayfalar dışında tümünün indirilmesini yasaklar</pre>
<span style="text-decoration: underline;"><strong>Yönergelerin birlikte kullanımı</strong></span>

Sitenin belirli bir sayfası için birkaç yönerge uygun düşüyorsa, seçili User-agent bloğunda ilk sırada görünen yönerge seçilir. Örnekler:
<pre class="prettyprint lang-text" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">User-agent: Google 
Allow: /cgi-bin 
Disallow: / 

# '/cgi-bin' ile başlayan 
# sayfalar dışında tümünün indirilmesini yasaklar

#### ARADAKİ FARKA BAKIN

User-agent: Google 
Disallow: / 
Allow: /cgi-bin 

# tüm sitenin indirilmesini yasaklar</pre>
<strong>Parametreler olmadan Allow-Disallow yönergeleri</strong>

Yönergelerin parametreleri olmadığında aşağıdaki gibi yorumlanır:
<pre class="prettyprint lang-text" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">User-agent: BotAdı 
Disallow: # Allow: / ile aynı şekilde

User-agent: BotAdı 
Allow: # dikkate robot</pre>
<h2>4 - "*" ve "$" gibi özel sembollerin kullanımı</h2>
Allow-Disallow yönergelerinin yolları belirtilirken '*' ve '$' özel karakterleri kullanılabilir ve belirli normal ifadeler bu şekilde verilebilir. '*' özel karakteri, herhangi bir karakter (boş karakter dahil) dizisini ifade eder. Örnekler:
<pre class="prettyprint lang-text" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">User-agent: BotAdı 
Disallow: /cgi-bin/*.aspx # '/cgi-bin/example.aspx' 
                          # ve '/cgi-bin/private/test.aspx' öğelerini yasaklar 
Disallow: /*private # hem '/private',
                    # hem de '/cgi-bin/private' öğesini yasaklar</pre>
<strong>"$" özel karakteri</strong>

Varsayılan olarak, robots.txt dosyasında tanımlanan her kuralın sonuna '*' eklenir. Örneğin:
<pre class="prettyprint lang-text" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">User-agent: BotAdı 
Disallow: /cgi-bin* # '/cgi-bin' ile başlayan 
                    # sayfalara erişimi engeller 
Disallow: /cgi-bin  # aynısı</pre>
Kuralın sonundaki '*' karakterini kaldırmak için, '$' özel karakteri kullanılabilir. Örneğin:
<pre class="prettyprint lang-text" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">User-agent: BotAdı 
Disallow: /example$ # '/example' öğesini yasaklar, 
                    # ancak '/example.html' öğesini yasaklamaz
                    
User-agent: BotAdı 
Disallow: /example # hem '/example', 
                   # hem de '/example.html' öğesini yasaklar
                   
User-agent: BotAdı 
Disallow: /example$ # yalnızca '/example' öğesini yasaklar 
Disallow: /example*$ # 'Disallow: /example' ile aynı 
                     #hem /example.html hem de /example öğesini yasaklar</pre>
<h2>5 - Sitemap direktifi</h2>
Siteniz için sitemaps.xml biçiminde yapı açıklaması kullanıyorsanız ve robotun bunu bilmesini istiyorsanız, sitemaps.xml dosyasının yolunu 'Sitemap' yönerge parametresi olarak belirtin (birkaç dosya varsa, tümünü belirtin). Örnekler:
<pre class="prettyprint lang-text" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">User-agent: BotAdı
Allow: / 

Sitemap: http://www.trkodlama.com/post-sitemap.xml
Sitemap: http://www.trkodlama.com/topic-sitemap.xml</pre>
veya
<pre class="prettyprint lang-text" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">User-agent: BotAdı Allow: / 
User-agent: * Disallow: /

Sitemap: http://www.trkodlama.com/post-sitemap.xml
Sitemap: http://www.trkodlama.com/topic-sitemap.xml</pre>
Robot sitemaps.xml dosyasının yolunu aklında tutar, dosyaları işler ve sonuçları bir sonraki indirme oturumu oluşturulurken kullanır.
<h2>6 - Host Direktifi</h2>
Sitenizde aynalar varsa, özel bir ayna oluşturma robotu bunu belirler ve sitenizin ayna grubunu oluşturur. Aramada yalnızca birincil ayna yer alır. robots.txt dosyasında 'Host' yönergesini kullanarak ve yönerge parametresi olarak da birincil aynanın adını tanımlayarak, tüm aynalar için birincil aynayı belirtebilirsiniz. 'Host' yönergesi belirtilen birincil aynanın seçilmesini garanti etmemekle birlikte, karar verilirken kullanılan algoritma bunu yüksek öncelikli olarak değerlendirir. Örnek:
<pre class="prettyprint lang-text" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">#Sitenin birincil aynası www.birincil-ayna.com ise, ayna grubundaki tüm siteler için
#robots.txt dosyası şöyle görünür:

User-Agent: * 
Disallow: /forum 
Disallow: /cgi-bin 
Host: www.birincil-ayna.com</pre>
<strong>Önemli:</strong> robots.txt dosyasını işlerken standarda tam olarak uymayan robotlarla uyumluluğu sağlamak amacıyla, 'User-Agent' kaydı ile başlayan gruba, 'Disallow'('Allow') yönergesinden hemen sonra 'Host' yönergesinin eklenmesi gerekir. İki nokta üst üste ayrılan etki alanı adı ve bağlantı noktası numarası (varsayılan olarak 80), 'Host' yönergesinin bağımsız değişkenlerini oluşturur.
<pre class="prettyprint lang-text" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">#Doğru şekilde oluşturulmuş robots.txt dosyası örneği 
#Bu dosyanın işlenmesi sırasında Host yönergesi dikkate alınır

User-Agent: * 
Disallow: 
Host: www.trkodlama.com</pre>
Yine de, Host yönergesi bölümler arası bir yönerge olması nedeniyle, belirtildiği robots.txt dosyasındaki yerinden bağımsız olarak robot tarafından kullanılacaktır.

<strong>Önemli:</strong> robots.txt dosyasında yalnızca bir Host yönergesi bulunabilir. Birden fazla yönerge belirtilmesi durumunda, bunların ilki kullanılır.

Örnek:
<pre class="prettyprint lang-text" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">Host: trkodlama.com # kullanılır

User-agent: * 
Disallow: /cgi-bin

User-agent: BotAdı
Disallow: /cgi-bin 
Host: www.trkodlama.com # kullanılmaz</pre>
<strong>Önemli</strong>: Host yönergesinin parametresi, uygun bir ana bilgisayar adı (yani, <a href="http://tools.ietf.org/html/rfc952" target="_blank">RFC 952</a> ile uyumlu ve IP adresi değil) ve kabul edilebilir bir bağlantı noktası numarasından oluşmalıdır. Uygun şekilde oluşturulmamış 'Host:' satırları yoksayılır.
<pre class="prettyprint lang-text" data-start-line="1" data-visibility="visible" data-highlight="" data-caption=""># Yoksayılan Host yönergesi örnekleri

Host: www.trkodlama-.com
Host: www.-trkodlama.com 
Host: www.trkodlama.com:100000 
Host: www.tr_kodlama.com
Host: .tr-kodlama.com:8000 
Host: tr-kodlama.com.
Host: tr..kodlama.com 
Host: www.trkodlama.com/ 
Host: www.trkodlama.com:8080/ 
Host: http://www.trkodlama.com 
Host: 122.122.122.122
Host: www.trkodlama.com,www.digerhost.com 
Host: www.trkodlama.com www.digerhost.com</pre>
Host yönergesinin kullanımıyla ilgili örnekler:
<pre class="prettyprint lang-text" data-start-line="1" data-visibility="visible" data-highlight="" data-caption=""># etkialanı.trkodlama.com adresi 
# www.etkialanı.trkodlama.com için birincil aynaysa,

Host yönergesinin 

# uygun kullanımı şöyledir: 

User-Agent: * 
Disallow: 
Host: etkialanı.trkodlama.com

# etkialanı.trkodlama.com adresi 
# www.etkialanı.trkodlama.com için birincil aynaysa, 

Host yönergesinin 

# yanlış kullanımı şöyledir:

User-Agent: * 
Disallow: 
Host: trkodlama.com</pre>
<h2>7 - Crawl-delay direktifi</h2>
Sunucu aşırı yüklüyse ve indirme isteklerini işlemeye yetişemiyorsa, "Crawl-delay" yönergesini kullanın. Bu yönerge, bir sayfayı indirme işleminin bitmesi ile sonraki sayfayı indirmeye başlama arasında geçmesi gereken en az süreyi (saniye olarak) arama robotuna belirtmeyi sağlar. robots.txt dosyasını işlerken standarda tam olarak uymayan robotlarla uyumluluğu sağlamak amacıyla, "User-Agent" kaydı ile başlayan gruba, "Disallow" ("Allow")yönergesinden hemen sonra "Crawl-delay" yönergesinin eklenmesi gerekir.

Örnekler:
<pre class="prettyprint lang-text" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">User-agent: BotAdı 
Crawl-delay: 2 # 2 saniyelik zaman aşımı belirtir

User-agent: * 
Disallow: /search 
Crawl-delay: 4.5 # 4.5 saniyelik zaman aşımı belirtir</pre>
robots.txt dosyası ile bilmeniz gereken başlıca özellikler bunlardır. Bunların dahası da var. Daha detaylı bilgi almak için <a href="https://yandex.com.tr/support/webmaster/controlling-robot/robots-txt.xml" target="_blank">buraya</a> tıklayınız. Aynı zamanda o sayfadan alıntıdır bu yazıda.

Faydalı olması dileğiyle,