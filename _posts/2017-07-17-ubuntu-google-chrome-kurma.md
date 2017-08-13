---
ID: 9308
post_title: 'Ubuntu&#8217;ya Google Chrome Kurma'
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/ubuntu-google-chrome-kurma-9308.html
published: true
post_date: 2017-07-17 20:48:08
---
Ubuntu Google Chrome kurulumu nasıl yapılır? Sizlere bunu göstereceğim bu yazıda.

Çevrenizde Linux kullananları gördünüz ve kullanım şekillerinden ve sağladığı kolaylıklardan o kadar etkilendiniz ki hemen bilgisayarınıza Ubuntu kurmak istediniz ve kurdunuz. (Ubuntu'yu indirmek için <a href="https://www.ubuntu.com/download/desktop">tıklayınız</a>.)

Sizleri bilmiyorum ama artık bende Google Chrome alışkanlığı oluşmuş. Bütün işletim sistemlerinde başarılı bir şekilde çalışması onu tercih etmemin en büyük sebebi. Cep telefonumda, dizüstü bilgisayarımda, tabletimde hep birbiriyle senkronize çalışması çok hoşuma gidiyor. Bu nedenle Google'ı seviyorum.

Google Chrome'u indirmek için şu bağlantıdan faydalanabilirsiniz: <a href="https://www.google.com/chrome/browser/desktop/index.html">google.com/chrome/browser/desktop/index.html</a>

Ubuntu kurulumu bitti ve bilgisayarınızda varsayılan olarak Mozilla Firefox kurulu olduğunu farkettiniz. Hemen Google'a girip Google Chrome diye arattığınız ve <strong>google-chrome-stable_current_amd64.deb</strong> dosyasını indirdiniz. Fakat bir türlü kuramıyorsunuz değil mi? İşte Ubuntu Google Chrome nasıl kurulur okuyun :)
<h3>1. Adım</h3>
CTRL + ALT + T tuş kombinasyonu ile terminali açın.
<h3>2. Adım</h3>
Google Chrome 3. parti yazılım olduğundan Repo'sunu tanımlamamız gerekiyor. Bunun için öncelikle Public Key tanımlıyoruz. Terminale aşağıdaki komutu yapıştırın:
<pre class="prettyprint lang-sh" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo apt-key add -</pre>
<h3>3. Adım</h3>
Bu adımda Chrome repo'sunu tanımlıyoruz:
<pre class="prettyprint lang-sh" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">sudo sh -c 'echo "deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main" &gt;&gt; /etc/apt/sources.list.d/google-chrome.list'</pre>
<h3>4. Adım</h3>
Artık Google Chrome'u kurabiliriz :) Aşağıdaki komut ile kurulumu tamamlıyoruz:
<pre class="prettyprint lang-sh" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">sudo apt-get update 
sudo apt-get install google-chrome-stable</pre>
İşte bu kadar.. Artık Google Chrome kullanmaya başlayabilirsiniz. Bilgisayarınızda Chrome diye aratarak bulabilirsiniz.

Umarım faydalı olur,

Kaynak: <a href="https://www.ubuntuupdates.org/ppa/google_chrome?dist=stable">ubuntuupdates.org/ppa/google_chrome?dist=stable</a>