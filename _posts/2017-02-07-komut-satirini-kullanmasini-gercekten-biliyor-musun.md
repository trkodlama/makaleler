---
ID: 6557
post_title: >
  Komut Satırını Kullanmasını
  Gerçekten Biliyor Musun?
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/linux/komut-satirini-kullanmasini-gercekten-biliyor-musun-6557.html
published: true
post_date: 2017-02-07 18:54:30
---
Komut satırını kullanmayı gerçekten biliyor musunuz bilmiyorum ama bunu artık test edebileceksiniz. <strong>Commandline Challenge</strong> uygulaması sayesinde bilgi düzeyinizin ne seviye de olduğunu rahatlıkla keşfedebileceksiniz. Lafı fazla uzatmadan uygulamanın adresini verelim: <a href="https://cmdchallenge.com/">cmdchallenge.com</a>

Bu adrese girdiğiniz sizi bir komut satırı ekranı karşılayacak. Bu ekranda görevler yazacak ve sizden bu görevi yapmanız istenecek. Sayfanın altında yapacağınız görevlere dair bir liste mevcut. Liste şu şekilde:

<a href="https://www.trkodlama.com/wp-content/uploads/2017/02/cmdchallenge1.png" target="_blank"><img class="aligncenter wp-image-6558 size-large" src="https://www.trkodlama.com/wp-content/uploads/2017/02/cmdchallenge1-1024x281.png" width="660" height="181" /></a>

Şimdi her bir görevi tek tek paylaşıyorum ve kullanmanız gereken komutu da anlatıyorum.
<h2>hello_world/ - "hello world" Yazdır</h2>
<pre class="prettyprint lang-sh" data-start-line="1" data-visibility="visible" data-highlight="" data-caption=""># Print "hello world".
# Hint: There are many ways to print text on
# the command line, one way is with the 'echo'
# command.
# 
# Try it below and good luck!
#</pre>
Sizden ekrana "hello world" yazdırmanızı istiyor. Kullanmanız gereken komut <strong>echo</strong> komutudur. Kullanımı aşağıdaki gibidir:
<pre class="prettyprint lang-sh" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">echo "hello world"</pre>
<h2>current_working_directory/ - İçinde bulunduğun dizini yazdır</h2>
<pre class="prettyprint lang-sh" data-start-line="1" data-visibility="visible" data-highlight="" data-caption=""># Print the current working directory.</pre>
Yeni görevimiz bu. İçinde bulunduğumuz klasörün adını istiyor. Bunu bize <strong>$PWD</strong> değişkeni verecektir. <strong>$PWD </strong>değişkeni POSIX uyumlu bütün kabuklarda çalışır. Daha detaylı bilgi için şu adresi ziyaret edebilirsiniz: <a href="http://pubs.opengroup.org/onlinepubs/009695399/utilities/xcu_chap02.html">pubs.opengroup.org/onlinepubs/009695399/utilities/xcu_chap02.html</a>

Cevabımız şu şekilde olacaktır:
<pre class="prettyprint lang-sh" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">echo $PWD</pre>
<h2>list_files/ - Her satırda tek dosya olacak şekilde dosyaları listele</h2>
<pre class="prettyprint lang-sh" data-start-line="1" data-visibility="visible" data-highlight="" data-caption=""># List names of all the files in the current
# directory, one file per line.</pre>
İçinde bulunduğunuz dizindeki dosyaları alt alta listelemeniz isteniyor. Burada kullanacağımız komut <code class="prettyprint lang-sh" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">ls</code>  komutudur. Fakat tek başına <code class="prettyprint lang-sh" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">ls</code>  komutu işimize yaramayacaktır. Çünkü her satıra bir dosya çıktısı vermez. Her satırda bir dosya adı kullanmak istiyorsanız <code class="prettyprint lang-sh" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">ls -1</code>  kullanmalısınız. Detaylı bilgi için: <a href="https://docs.oracle.com/cd/E53394_01/html/E54763/ls-1b.html">docs.oracle.com/cd/E53394_01/html/E54763/ls-1b.html</a>

Cevabını şu olmalı:
<pre class="prettyprint lang-sh" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">ls -1</pre>
<h2>print_file_contents/ - "access.log" dosyasının içeriğini yazdırın</h2>
<pre class="prettyprint lang-sh" data-start-line="1" data-visibility="visible" data-highlight="" data-caption=""># There is a file named "access.log" in the
# current directory. Print the contents.</pre>
İçinde bulunduğunuz dizinde bulunan <strong>acccess.log</strong> dosyasının içeriğini ekrana yazdırmak için <code class="prettyprint lang-sh" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">tail</code>  komutunu kullanıyoruz:
<pre class="prettyprint lang-sh" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">tail access.log</pre>
<h2>last_lines/ - "access.log" dosyasının son 5 satırını yazdırın</h2>
<pre class="prettyprint lang-sh" data-start-line="1" data-visibility="visible" data-highlight="" data-caption=""># Print the last 5 lines of "access.log".</pre>
Bu dosyanın son 5 satırını yazdırmak için yine <code class="prettyprint lang-sh" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">tail</code> komutunu kullanıyoruz fakat bu sefer <code class="prettyprint lang-sh" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">-5</code> diye belirterek:
<pre class="prettyprint lang-sh" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">tail -5 access.log</pre>
<h2>find_string_in_a_file/ - İçinde "GET" yazan satırları yazdırın</h2>
<pre class="prettyprint lang-sh" data-start-line="1" data-visibility="visible" data-highlight="" data-caption=""># There is a file named "access.log" in the
# current working directory. Print all lines
# in this file that contains the string "GET".</pre>
Bizden istediği yine "access.log" dosyamızın içeriğini yazdırmamız fakat bu sefer sadece içinde "GET" yazan satırları yazdıracağız. GET yazısını yakalamak için  <code class="prettyprint lang-sh" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">grep</code> komutunu kullanacağız:
<pre class="prettyprint lang-sh" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">grep GET access.log</pre>
<h2>find_tabs_in_a_file/ - Tab içeren kaç tane satır var</h2>
<pre class="prettyprint lang-sh" data-start-line="1" data-visibility="visible" data-highlight="" data-caption=""># How many lines contain tab characters in
# the file named "file-with-tabs.txt" in the
# current directory.</pre>
Bu görevi yerine getirmek için iki komut kullanıyoruz. İlkinde tab içeren satırları bulup ikincisinde bu satır sayısını sayıyoruz. Yine <code class="prettyprint lang-sh" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">grep</code>  kullanıyoruz ve satırları saymak için <code class="prettyprint lang-sh" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">wc</code>  kullanıyoruz.
<pre class="prettyprint lang-sh" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">grep "$(printf '\t')" file-with-tabs.txt | wc -l</pre>
<h2>search_for_files_containing_string/ - İçinde "500" yazan bütün dosyaları listele</h2>
<pre class="prettyprint lang-sh" data-start-line="1" data-visibility="visible" data-highlight="" data-caption=""># Print all files in the current directory,
# one per line (not the path, just the filename)
# that contain the string "500".</pre>
İçinde bulunduğunuz klasörde "500" terimini içeren dosyaları listelemeniz isteniyor. Bunun çözümü:
<pre class="prettyprint lang-sh" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">grep -lR 500 *</pre>
Aslında bu listenin daha devamı var fakat oldukça uzun bir yazı olacağa benziyor. Bu nedenle bir anda hepsini birden işleme almayacağım. Fakat süreç içerisinde geri kalan görevleri de paylaşacağım.

Sizlerde yorumlar başarılı bir şekilde çözdüğünüz görevleri paylaşabilirsiniz.