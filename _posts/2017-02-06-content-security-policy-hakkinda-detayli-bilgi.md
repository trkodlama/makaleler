---
ID: 6522
post_title: >
  Content Security Policy Hakkında
  Detaylı Bilgi
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/content-security-policy-hakkinda-detayli-bilgi-6522.html
published: true
post_date: 2017-02-06 03:07:03
---
<em>Yeni</em> <pre class="class:prettyprint lang-text data-start-line:1 data-visibility:visible data-highlight: data-caption: decode:1 " >Content-Security-Policy</pre> HTTP yanıt başlığı(response header) modern tarayıcılarda yaşabileceğiniz XSS saldırılarını azaltmayı amaçlamaktadır.

Direktiflerden önce hangi tarayıcıların bu başlığı destekleyip desteklemediğini inceleylim.
<h2>Tarayıcı Destekleri</h2>
<table class="table table-bordered table-responsive">
<thead>
<tr>
<th>Header</th>
<th><i class="fa fa-chrome"></i><span class="hidden-xs"> Chrome</span></th>
<th><i class="fa fa-firefox"></i><span class="hidden-xs"> FireFox</span></th>
<th><i class="fa fa-safari"></i><span class="hidden-xs"> Safari</span></th>
<th><i class="fa fa-internet-explorer"></i><span class="hidden-xs"> IE</span></th>
<th><i class="fa fa-edge"></i><span class="hidden-xs"> Edge</span></th>
</tr>
</thead>
<tbody>
<tr>
<td><pre class="decode:1 " >Content-Security-Policy</pre> <span class="label label-success">CSP Level 2</span></td>
<td>40+ Ocak <small>2015</small></td>
<td>31+ <small title="36+ is missing the plugin-types and child-src directives"><em>Kısmen</em>
Temmuz 2014</small></td>
<td>-</td>
<td>-</td>
<td>-</td>
</tr>
<tr>
<td><pre class="decode:1 " >Content-Security-Policy</pre> <span class="label label-success">CSP 1.0</span></td>
<td>25+</td>
<td>23+</td>
<td>7+</td>
<td>-</td>
<td>Edge 12 build 10240+</td>
</tr>
<tr>
<td><pre class="decode:1 " >X-Content-Security-Policy</pre> <span class="label label-warning">Kullanımdan kaldırıldı</span></td>
<td></td>
<td>4+</td>
<td>-</td>
<td>10+ <small title="only sandbox directive is partiall supported"><em>Kısıtlı</em></small></td>
<td>12+ <small title="only sandbox directive is partiall supported"><em>Kısıtlı</em></small></td>
</tr>
<tr>
<td><pre class="decode:1 " >X-Webkit-CSP</pre> <span class="label label-warning">Kullanımdan Kaldırıldı</span></td>
<td>14+</td>
<td>-</td>
<td>6+</td>
<td>-</td>
<td>-</td>
</tr>
</tbody>
</table>
Kaynaklar <a href="http://caniuse.com/contentsecuritypolicy">caniuse.com/contentsecuritypolicy</a>, <a href="http://caniuse.com/contentsecuritypolicy2">caniuse.com/contentsecuritypolicy2</a> ve <a href="https://hacks.mozilla.org/2013/05/content-security-policy-1-0-lands-in-firefox-aurora/">hacks.mozilla.org/2013/05/content-security-policy-1-0-lands-in-firefox-aurora/</a>

Tarayıcınızın CSP başlığını destekleyip desteklemediğiniz şu adresten kontrol edebilirsiniz: <a href="https://content-security-policy.com/browser-test/">content-security-policy.com/browser-test/</a>

Dikkat: Content-Security-Policy başlığı ile X-Content-Security-Policy veya X-Webkit-CSP başlığının beraber kullanılması tarayıcı bazı anormal durumlara yol açabiliyor. Kullanmayın.
<h2>Direktifler</h2>
Content-Security-Policy başlığı aşağıda tanımlanan direktiflerden biri veya bir kaçı ile birden oluşturulabilir. Birden fazla direktif noktalı virgül ; kullanarak ayrılmalıdır.

Bu tablo hazırlanırken şu adresteki belgeden faydalanılmıştır:
<table class="table table-bordered table-responsive">
<thead>
<tr>
<th width="150">Direktif</th>
<th width="250">Örnek Değer</th>
<th>Açıklama</th>
</tr>
</thead>
<tbody>
<tr>
<td><pre class="decode:1 " >default-src</pre></td>
<td><pre class="decode:1 " >'self' cdn.ornek.com</pre></td>
<td> <pre class="decode:1 " >default-src</pre> direktifi JavaScript, Resimler, CSS, Font, AJAX sorguları, html5 medyaları vs. için varsayılan politikadır.Örnek değerleri sayfanın aşağısında göreceksiniz.

<span class="label label-success">CSP Level 1</span> <span class="label label-default" title="Chrome 25+ - February 2013"><i class="fa fa-chrome"></i> 25+</span> <span class="label label-default" title="Firefox 23+ - August 2013"><i class="fa fa-firefox"></i> 23+</span> <span class="label label-default" title="Safari 7+ - October 2013"><i class="fa fa-safari"></i> 7+</span> <span class="label label-default" title="IE Edge 12.10240+ - July 2015"><i class="fa fa-edge"></i> 12+</span></td>
</tr>
<tr>
<td><pre class="decode:1 " >script-src</pre></td>
<td><pre class="decode:1 " >'self' js.ornek.com</pre></td>
<td>Geçerli JavaScript kaynakları tanımlar.

<span class="label label-success">CSP Level 1</span> <span class="label label-default" title="Chrome 25+ - February 2013"><i class="fa fa-chrome"></i> 25+</span> <span class="label label-default" title="Firefox 23+ - August 2013"><i class="fa fa-firefox"></i> 23+</span> <span class="label label-default" title="Safari 7+ - October 2013"><i class="fa fa-safari"></i> 7+</span> <span class="label label-default" title="IE Edge 12.10240+ - July 2015"><i class="fa fa-edge"></i> 12+</span></td>
</tr>
<tr>
<td><pre class="decode:1 " >style-src</pre></td>
<td><pre class="decode:1 " >'self' css.ornek.com</pre></td>
<td>Geçerli CSS kaynaklarını tanımlar.

<span class="label label-success">CSP Level 1</span> <span class="label label-default" title="Chrome 25+ - February 2013"><i class="fa fa-chrome"></i> 25+</span> <span class="label label-default" title="Firefox 23+ - August 2013"><i class="fa fa-firefox"></i> 23+</span> <span class="label label-default" title="Safari"><i class="fa fa-safari"></i> 7+</span> <span class="label label-default" title="IE Edge 12.10240+ - July 2015"><i class="fa fa-edge"></i> 12+</span></td>
</tr>
<tr>
<td><pre class="decode:1 " >img-src</pre></td>
<td><pre class="decode:1 " >'self' img.ornek.com</pre></td>
<td>Geçerli resim kaynaklarını tanımlar.

<span class="label label-success">CSP Level 1</span> <span class="label label-default" title="Chrome 25+ - February 2013"><i class="fa fa-chrome"></i> 25+</span> <span class="label label-default" title="Firefox 23+ - August 2013"><i class="fa fa-firefox"></i> 23+</span> <span class="label label-default" title="Safari 7+ - October 2013"><i class="fa fa-safari"></i> 7+</span> <span class="label label-default" title="IE Edge 12.10240+ - July 2015"><i class="fa fa-edge"></i> 12+</span></td>
</tr>
<tr>
<td><pre class="decode:1 " >connect-src</pre></td>
<td><pre class="decode:1 " >'self'</pre></td>
<td> <pre class="decode:1 " >XMLHttpRequest</pre> (AJAX), <pre class="decode:1 " >WebSocket</pre> veya <pre class="decode:1 " >EventSource</pre> için tanımlanır. Eğer izin verilmeyen kaynaktan bu sorgular yapılırsa tarayıcıdan  <pre class="decode:1 " >400</pre> HTTP kodu döner.

<span class="label label-success">CSP Level 1</span> <span class="label label-default" title="Chrome 25+ - February 2013"><i class="fa fa-chrome"></i> 25+</span> <span class="label label-default" title="Firefox 23+ - August 2013"><i class="fa fa-firefox"></i> 23+</span> <span class="label label-default" title="Safari 7+ - October 2013"><i class="fa fa-safari"></i> 7+</span> <span class="label label-default" title="IE Edge 12.10240+ - July 2015"><i class="fa fa-edge"></i> 12+</span></td>
</tr>
<tr>
<td><pre class="decode:1 " >font-src</pre></td>
<td><pre class="decode:1 " >font.ornek.com</pre></td>
<td>Geçerli yazı tipi kaynaklarını tanımlar.

<span class="label label-success">CSP Level 1</span> <span class="label label-default" title="Chrome 25+ - February 2013"><i class="fa fa-chrome"></i> 25+</span> <span class="label label-default" title="Firefox 23+ - August 2013"><i class="fa fa-firefox"></i> 23+</span> <span class="label label-default" title="Safari 7+ - October 2013"><i class="fa fa-safari"></i> 7+</span> <span class="label label-default" title="IE Edge 12.10240+ - July 2015"><i class="fa fa-edge"></i> 12+</span></td>
</tr>
<tr>
<td><pre class="decode:1 " >object-src</pre></td>
<td><pre class="decode:1 " >'self'</pre></td>
<td><pre class="decode:1 " >&lt;object&gt;</pre>, <pre class="decode:1 " >&lt;embed&gt;</pre> veya <pre class="decode:1 " >&lt;applet&gt;</pre> için geçerli kaynakları tanımlar.

<span class="label label-success">CSP Level 1</span> <span class="label label-default" title="Chrome 25+ - February 2013"><i class="fa fa-chrome"></i> 25+</span> <span class="label label-default" title="Firefox 23+ - August 2013"><i class="fa fa-firefox"></i> 23+</span> <span class="label label-default" title="Safari 7+ - October 2013"><i class="fa fa-safari"></i> 7+</span> <span class="label label-default" title="IE Edge 12.10240+ - July 2015"><i class="fa fa-edge"></i> 12+</span></td>
</tr>
<tr>
<td><pre class="decode:1 " >media-src</pre></td>
<td><pre class="decode:1 " >media.ornek.com</pre></td>
<td>HTML5'in <pre class="decode:1 " >&lt;audio&gt;</pre>, <pre class="decode:1 " >&lt;video&gt;</pre> etiketleri gibi geçerli ses ve görüntü kaynaklarını tanımlar.

<span class="label label-success">CSP Level 1</span> <span class="label label-default" title="Chrome 25+ - February 2013"><i class="fa fa-chrome"></i> 25+</span> <span class="label label-default" title="Firefox 23+ - August 2013"><i class="fa fa-firefox"></i> 23+</span> <span class="label label-default" title="Safari 7+ - October 2013"><i class="fa fa-safari"></i> 7+</span> <span class="label label-default" title="IE Edge 12.10240+ - July 2015"><i class="fa fa-edge"></i> 12+</span></td>
</tr>
<tr>
<td><pre class="decode:1 " >frame-src </pre></td>
<td><pre class="decode:1 " >'self'</pre></td>
<td>Geçerli çerçeve kaynağını tanımlar. Artık  <pre class="decode:1 " >child-src</pre>  kullanılıyor, bu yöntem kullanımdan kaldırıldı.

<span class="label label-warning">Kullanımdan kaldırıldı.</span></td>
</tr>
<tr>
<td><pre class="decode:1 " >sandbox</pre></td>
<td><pre class="decode:1 " >allow-forms allow-scripts</pre></td>
<td>Sandbox modu sayesinde bir çok etkinliği kısıtlayabilirsiniz. Popupları engeller, formları durdurur, javascriptleri çalıştırmaz vs. vs.

Sandbox direktifi için boş değer girerseniz aşağıdaki listenin tümünü girmiş sayılırsınız veyahut sadece seçtiklerinizin de çalışmasın sağlayabilirsiniz: <pre class="decode:1 " >allow-forms</pre> <pre class="decode:1 " >allow-same-origin</pre> <pre class="decode:1 " >allow-scripts</pre> <pre class="decode:1 " >allow-popups</pre>, <pre class="decode:1 " >allow-modals</pre>, <pre class="decode:1 " >allow-orientation-lock</pre>, <pre class="decode:1 " >allow-pointer-lock</pre>, <pre class="decode:1 " >allow-presentation</pre>, <pre class="decode:1 " >allow-popups-to-escape-sandbox</pre> ve <pre class="decode:1 " >allow-top-navigation</pre>

<span class="label label-success">CSP Level 1</span> <span class="label label-default" title="Chrome 25+ - February 2013"><i class="fa fa-chrome"></i> 25+</span> <span class="label label-default" title="Firefox 50+"><i class="fa fa-firefox"></i> 50+</span> <span class="label label-default" title="Safari 7+ - October 2013"><i class="fa fa-safari"></i> 7+</span> <span class="label label-default" title="IE Edge 12.10240+ - July 2015"><i class="fa fa-edge"></i> 12+</span></td>
</tr>
<tr>
<td><pre class="decode:1 " >report-uri</pre></td>
<td><pre class="decode:1 " >/report-uri</pre></td>
<td>Tarayıcıya belirttiğiniz adrese direktiflerinizle ilgili hataların POST edilmesini sağlar.  <pre class="decode:1 " >-Report-Only</pre> ekleyerek herhangi bir şeyi bloklamadan sadece belirttiğiniz adrese rapor gönderir..

<span class="label label-success">CSP Level 1</span> <span class="label label-default" title="Chrome 25+ - February 2013"><i class="fa fa-chrome"></i> 25+</span> <span class="label label-default" title="Firefox 23+ - August 2013"><i class="fa fa-firefox"></i> 23+</span> <span class="label label-default" title="Safari 7+ - October 2013"><i class="fa fa-safari"></i> 7+</span> <span class="label label-default" title="IE Edge 12.10240+ - July 2015"><i class="fa fa-edge"></i> 12+</span></td>
</tr>
<tr>
<td><pre class="decode:1 " >child-src</pre></td>
<td><pre class="decode:1 " >'self'</pre></td>
<td><pre class="decode:1 " >&lt;frame&gt;</pre> ve<pre class="decode:1 " >&lt;iframe&gt;</pre> için geçerli kaynakları tanımlar.

<span class="label label-success">CSP Level 2</span> <span class="label label-default" title="Chrome 40+ - January 2015"><i class="fa fa-chrome"></i> 40+</span> <span class="label label-default" title="Firefox 45+ - March 2016"><i class="fa fa-firefox"></i> 45+</span></td>
</tr>
<tr>
<td><pre class="decode:1 " >form-action</pre></td>
<td><pre class="decode:1 " >'self'</pre></td>
<td>HTML <pre class="decode:1 " >&lt;form&gt;</pre> işlemi için geçerli kaynakları tanımlar.

<span class="label label-success">CSP Level 2</span> <span class="label label-default" title="Chrome 40+ - January 2015"><i class="fa fa-chrome"></i> 40+</span> <span class="label label-default" title="Firefox 36+ - February 2015 "><i class="fa fa-firefox"></i> 36+</span></td>
</tr>
<tr>
<td><pre class="decode:1 " >frame-ancestors</pre></td>
<td><pre class="decode:1 " >'none'</pre></td>
<td><pre class="decode:1 " >&lt;frame&gt;</pre> <pre class="decode:1 " >&lt;iframe&gt;</pre> <pre class="decode:1 " >&lt;object&gt;</pre> <pre class="decode:1 " >&lt;embed&gt;</pre> <pre class="decode:1 " >&lt;applet&gt;</pre> dökümanınıza ekleyebileceğiniz bu etiketlerin kaynaklarını tanımlar. Bu direktifi  <pre class="decode:1 " >'none'</pre> olarak ayarlamak şuna da eşit sayılır <pre class="decode:1 " >X-Frame-Options: DENY</pre>

<span class="label label-success">CSP Level 2</span> <span class="label label-default" title="Chrome 39+ - November 2014"><i class="fa fa-chrome"></i> 39+</span> <span class="label label-default" title="Firefox 33+ - October 2014"><i class="fa fa-firefox"></i> 33+</span></td>
</tr>
<tr>
<td><pre class="decode:1 " >plugin-types</pre></td>
<td><pre class="decode:1 " >'application/pdf'</pre></td>
<td><pre class="decode:1 " >&lt;object&gt;</pre> ve <pre class="decode:1 " >&lt;embed&gt;</pre> ile dökümanınıza ekleyebileceğiniz MIME tiplerini limitler. Örneğin  <pre class="decode:1 " >&lt;applet&gt;</pre> eklemek istiyorsanız şunu kullanmalısınız <pre class="decode:1 " >application/x-java-applet</pre>.

<span class="label label-success">CSP Level 2</span> <span class="label label-default" title="Chrome 40+ - January 2015"><i class="fa fa-chrome"></i> 40+</span></td>
</tr>
</tbody>
</table>
&nbsp;
<h2>Kaynak Listesi Örnekleri</h2>
Yukarıda paylaşmış olduğum direktiflerden sonu <strong>-src</strong> ile biten direktifler Kaynak Listesi denilen benzer değerler alırlar. 'none' dışında bütün kaynaklar birbirleriyle beraber kullanılabilir.
<table class="table table-bordered table-responsive">
<thead>
<tr>
<th>Kaynak Değeri</th>
<th>Örnek</th>
<th>Açıklama</th>
</tr>
</thead>
<tbody>
<tr>
<td><pre class="decode:1 " >*</pre></td>
<td><pre class="decode:1 " >img-src *</pre></td>
<td>Yıldız işareti data: blob: filesystem: şeması dışındaki bütün URL'leri kabul eder.</td>
</tr>
<tr>
<td><pre class="decode:1 " >'none'</pre></td>
<td><pre class="decode:1 " >object-src 'none'</pre></td>
<td>Hiç bir kaynaktan içerik kabul etme.</td>
</tr>
<tr>
<td><pre class="decode:1 " >'self'</pre></td>
<td><pre class="decode:1 " >script-src 'self'</pre></td>
<td>Aynı alan adın, ip vs.'den içerik yüklemesine izin verir.</td>
</tr>
<tr>
<td><pre class="decode:1 " >data:</pre></td>
<td><pre class="decode:1 " >img-src 'self' data:</pre></td>
<td>data: şemasından resim yüklenmesine izin verir(base64 şifrelenmiş resimler)</td>
</tr>
<tr>
<td><pre class="decode:1 " >domain.ornek.com</pre></td>
<td><pre class="decode:1 " >img-src domain.ornek.com</pre></td>
<td>İçerikler sadece belirtilen domain'den indirilir</td>
</tr>
<tr>
<td><pre class="decode:1 " >*.ornek.com</pre></td>
<td><pre class="decode:1 " >img-src *.ornek.com</pre></td>
<td>Bütün alt alan isimlerine izin verir <pre class="decode:1 " >example.com</pre></td>
</tr>
<tr>
<td><pre class="decode:1 " >https://cdn.com</pre></td>
<td><pre class="decode:1 " >img-src https://cdn.com</pre></td>
<td>Belirtilen domain'e HTTPS protokolü kullanmak şartıyla izin verir.</td>
</tr>
<tr>
<td><pre class="decode:1 " >https:</pre></td>
<td><pre class="decode:1 " >img-src https:</pre></td>
<td>HTTPS olsun hangi domain olursa olsun :)</td>
</tr>
<tr>
<td><pre class="decode:1 " >'unsafe-inline'</pre></td>
<td><pre class="decode:1 " >script-src 'unsafe-inline'</pre></td>
<td>Style, onlick vs. gibi inline kodlama dediğimiz olaya izin verir.</td>
</tr>
<tr>
<td><pre class="decode:1 " >'unsafe-eval'</pre></td>
<td><pre class="decode:1 " >script-src 'unsafe-eval'</pre></td>
<td>Dinamik JavaScript kod çalıştırıcısına izin verir <pre class="decode:1 " >eval()</pre></td>
</tr>
</tbody>
</table>
<h2>Content-Security-Policy Örnekleri</h2>
Aşağıda bir kaç örnek Content-Security-Policy örnekleri mevcuttur.
<h3>Aynı Domain'den Olan Herşeyi Kabul Et</h3>
<pre class="prettyprint lang-text" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">default-src 'self';</pre>
<h3>JavaScript'i Aynı Domain'se Kabul Et</h3>
<pre class="prettyprint lang-text" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">script-src 'self';</pre>
<h3>Google Analytics'i, Google AJAX CDN'sini ve Aynı Domain'den JavaScript'i Kabul Et</h3>
<pre class="prettyprint lang-text" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">script-src 'self' www.google-analytics.com ajax.googleapis.com;</pre>
<h3>Acemi Politikası</h3>
Yeni başlayanların kullanabileceği bir politika, kural olabilir bu. Aynı domain'den resimlere, scriptlere, css ve AJAX'a izin verir. Ve object, media ve frame gibi diğer nesneleri kullanılamaz hale getirir.
<pre class="prettyprint lang-text" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">default-src 'none'; script-src 'self'; connect-src 'self'; img-src 'self'; style-src 'self';</pre>
<h2>Content-Security-Policy Hata Mesajları</h2>
Chrome'da geliştirici araçlarında Content-Security-Policy kurallarını ihlal ettiğinizde şu hatayı görürsünüz:
<blockquote>Refused to load the script 'script-uri' because it violates the following Content Security Policy directive: "your CSP directive".</blockquote>
Firefox'da ise web geliştirici araçlarında aynı durumda bu hatayı görürsünüz:
<blockquote>Content Security Policy: A violation occurred for a report-only CSP policy ("An attempt to execute inline scripts has been blocked"). The behavior was allowed, and a CSP report was sent.</blockquote>
<h2>Sunucu Taraflı Ayarlama</h2>
Sunucu taraflı kodlamalarda kullandığınız web sunucusu HTTP başlıkları göndermenize olanak sağlar. Aşağıda Apache ve Nginx için bu işin yolu yordamı gösterilmiştir.
<h3>Apache'de Content-Security-Policy Başlığı Ayarlama</h3>
Aşağıdaki kodu Apache konfigürasyon dosyanızda VirtualHost'unuzun olduğu bölüme (httpd.conf) veya .htaccess dosyanıza ekleyebilirsiniz:
<pre class="prettyprint lang-apache_conf" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">Header set Content-Security-Policy "default-src 'self';"</pre>
<h3>Nginx'de Content-Security-Policy Başlığı Ayarlama</h3>
Aşağıdaki kodu server{} bloğunuzun arasına ekleyin:
<pre class="prettyprint lang-text" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">add_header Content-Security-Policy "default-src 'self';";</pre>
<h3>IIS'de Content-Security-Policy Başlığı</h3>
<pre class="prettyprint lang-xml" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;system.webServer&gt;
  &lt;httpProtocol&gt;
    &lt;customHeaders&gt;
      &lt;add name="Content-Security-Policy" value="default-src 'self';" /&gt;
    &lt;/customHeaders&gt;
  &lt;/httpProtocol&gt;
&lt;/system.webServer&gt;</pre>
<h2>Kaynaklar</h2>
<ul>
 	<li>Çeviri: <a href="https://content-security-policy.com">content-security-policy.com</a></li>
 	<li><a href="http://www.w3.org/TR/CSP1/">w3.org/TR/CSP1/</a></li>
 	<li><a href="http://www.w3.org/TR/CSP2/">w3.org/TR/CSP2/</a></li>
 	<li><a href="https://content-security-policy.com/presentations/">content-security-policy.com/presentations/</a></li>
 	<li><a href="https://hacks.mozilla.org/2016/02/implementing-content-security-policy/">hacks.mozilla.org/2016/02/implementing-content-security-policy/</a></li>
 	<li><a href="https://developer.mozilla.org/en-US/docs/Web/Security/CSP/CSP_policy_directives">developer.mozilla.org/en-US/docs/Web/Security/CSP/CSP_policy_directives</a></li>
</ul>