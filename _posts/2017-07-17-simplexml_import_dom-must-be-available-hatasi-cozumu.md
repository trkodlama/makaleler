---
ID: 9311
post_title: '&#8220;simplexml_import_dom() must be available&#8221; Hatası ve Çözümü'
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/simplexml_import_dom-must-be-available-hatasi-cozumu-9311.html
published: true
post_date: 2017-07-17 21:19:09
---
<strong>Symfony</strong> ile yeni bir proje oluştururken bu hata ile karşılaştım. PHP7 kurdum, sonra symfony kurdum. Daha sonra <code>symfony new projeminadi</code> komutunu çalıştırdığımda bu hata ile karşılaştım:
<blockquote>Preparing project...

✕ Symfony 3.3.4 was successfully installed but your system doesn't meet its
technical requirements! Fix the following issues before executing
your Symfony application:

* simplexml_import_dom() must be available
> Install and enable the SimpleXML extension.

After fixing these issues, re-check Symfony requirements executing this command:

php projeminadi/bin/symfony_requirements

Then, you can:

* Change your current directory to /home/oralunal/projeminadi

* Configure your application in app/config/parameters.yml file.

* Run your application:
1. Execute the php bin/console server:start command.
2. Browse to the http://localhost:8000 URL.

* Read the documentation at http://symfony.com/doc</blockquote>
<h2>simplexml_import_dom() must be available Hatasının Çözümü</h2>
Hatayı almanızın sebebi PHP-XML'in kurulu olmamasıdır. Hatanın çözümü de oldukça basittir. PHP-XML kurmanız yeterli olacaktır:
<pre class="command-line" data-user="root" data-host="trkodlama"><code class="language-bash">sudo apt-get install php-xml</code></pre>
Umarım faydalı olur arkadaşlar,

Kaynak: <a href="http://www.phpfriend.com/how-to-install-symfony-2-8-under-ubuntu-16-04/">phpfriend.com/how-to-install-symfony-2-8-under-ubuntu-16-04/</a>