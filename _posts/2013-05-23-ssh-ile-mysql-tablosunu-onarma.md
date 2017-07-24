---
ID: 1717
post_title: SSH ile MySQL Tablosunu Onarma
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/linux/ssh-ile-mysql-tablosunu-onarma-1717.html
published: true
post_date: 2013-05-23 21:42:20
---
Merhaba arkadaşlar,

Uzun zamandır makale yazamıyordum. Yoğunluğumdan dolayı bir türlü fırsat bulamadım. Bugün sizlere <strong>phpMyAdmin </strong>olmadan veritabanı tablolarınızı nasıl onaracağınızı göstereceğim.
<h3>1- SSH İle Sunucuya Bağlanın</h3>
Sunucumuzda işlem yapmak öncelikle SSH aracılığıyla sunucumuzla bağlantı kurmalıyız. Bunu yapmak için aşağıdaki komutu kullanalım:
<pre class="lang:bash decode:1 ">ssh -l root trkodlama.com</pre>
Daha sonra şifrenizi girmeniz istenecek. Şifrenizi girip devam edin.
<h3>2- MySQL Komut Satırını Çalıştırın</h3>
MySQL'de işlem yapmak için aşağıdaki komutla MySQL Komut Satırını çalıştırın:
<pre class="lang:bash decode:1 ">mysql</pre>
Bu komutu gönderdiğiniz anda aşağıdaki şekilde bir çıktı alacaksınız:
<blockquote>Welcome to the MySQL monitor.  Commands end with ; or \g.

Your MySQL connection id is 2

Server version: x.x.xx-community MySQL Community Server (GPL)

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql&gt;</blockquote>
<h3>3- Veritabanını Seçin</h3>
İşlem yapacağınız ilgili veritabanını seçmemiz gerekiyor. Bunun için aşağıdaki komutu kullanacağız:
<pre class="lang:bash decode:1 ">mysql&amp;gt; USE veritabani_adi</pre>
Bu komutu gönderdiğiniz anda şu yazıyı görmelisiniz:
<blockquote>Database changed</blockquote>
Şu anda artık <strong>veritabani_adi </strong>veritabanındasınız ve bu veritabanıyla istediğiniz işlemi gerçekleştirebilirsiniz.
<h3>4- Tabloyu Onarın</h3>
Artık tek ihtiyacımız olan tablo adını bilmek. Aşağıdaki komut ile istediğimiz tabloyu onarabiliriz. Bu işlem tablonun boyutuna bağlı olarak uzun sürebilir.
<pre class="lang:bash decode:1 ">mysql&amp;gt; REPAIR TABLE &lt;code&gt;tablo1&lt;/code&gt;, &lt;code&gt;tablo2&lt;/code&gt;;</pre>
Şu anda onarma işleminiz tamamlanmış bulunmaktadır.

<span style="color: #ff0000;">İpucu:</span> Eğer tablo adını unuttuysanız ilgili veritabanındaki bütün tabloları aşağıdaki komut ile sıralayabilirsiniz:
<pre class="lang:bash decode:1 ">mysql&amp;gt; SHOW TABLES FROM veritabani_adi</pre>
Umarım işinize yarayacak bir yazı olmuştur. Kolay gelsin,