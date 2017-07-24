---
ID: 6459
post_title: >
  mysqlcheck ile Veritabanı Optimize Etme
  ve Onarma
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/mysql/mysqlcheck-ile-veritabani-optimize-etme-onarma-6459.html
published: true
post_date: 2017-01-30 08:38:58
---
Bu yazıda MySQL ve MariaDB veritabanı tablolarını kontrol eden, analiz eden, onaran ve optimize eden komut satırı aracı <strong>mysqlcheck</strong>‘den bahsedeceğim. Kısım kısım kullanımını inceleyelim.
<h2>Veritabanındaki Bir Tabloyu Kontrol Etme</h2>
<em>blog </em>veritabanındaki <em>yazilar </em>tablosunu kontrol etmek için aşağıdaki komut kullanılır:
<pre class="prettyprint lang-sh" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">$ mysqlcheck -c blog yazilar
blog.yazilar                         OK # Bu da çıktısı</pre>
Eğer veritabanınız şifre ile korunuyorsa <code class="prettyprint lang-sh" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">-u root -p</code> kısmını komutunuzun sonuna ekleyin:
<pre class="prettyprint lang-sh" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">$ mysqlcheck -c blog yazilar -u root -p
Enter password:
blog.yazilar                         OK</pre>
<h2>Veritabanındaki Bir Tabloyu Analiz Etme</h2>
Aşağıdaki komut ile blog veritabanındaki yazılar tablosunu analiz edebilirsiniz:
<pre class="prettyprint lang-sh" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">$ mysqlcheck -a blog yazilar
blog.yazilar                         OK</pre>
Eğer MySQL veya MariDB sunucunuz uzak bir sunucuda çalışıyorsa komutunuzun sonuna <code class="prettyprint lang-sh" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">-h</code> ekleyerek uzak sunucu adresini girin:
<pre class="prettyprint lang-sh" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">$ mysqlcheck -a blog yazilar -h uzaksunucu.com
blog.yazilar                         OK</pre>
<h2>Bütün Veritabanlarındaki Bütün Tabloları Analiz Etme</h2>
<pre class="prettyprint lang-sh" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">$ mysqlcheck -o --all-databases
blog.kullanicilar
note     : Table does not support optimize, doing recreate + analyze instead
status   : OK
mysql.time_zone_transition_type                    Table is already up to date
</pre>
Bu komutun çıktısında yazan <code class="prettyprint lang-sh" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">Table does not support optimize, doing recreate + analyze instead</code> bu ifadeden şunu anlamalıyız. Optimize etmeye çalıştığımız tablonun depolama motoru InnoDB imiş. InnoDB tabloyu optimize etmeye çalıştığınızda yeni bir tablo oluşturulur, optimize ettiğiniz tablonun bütün satırları yeni tabloya kopyalanır, eski tablo silinir ve yeni tablonun ismi yeniden eskisi ile aynı olacak şekilde güncellenir ve en sonunda ANALYZE komutu çalıştırılır tabloda.

<code class="prettyprint lang-sh" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">Table is already up to date</code> çıktısı ile de tablonun durumunun güncel olduğunu ve işlem yapmaya gerek olmadığını belirtir.
<h2>Birden Fazla Veritabanını Onarma</h2>
Aşağıdaki komut ile hem <em>blog</em> hemde <em>blog2</em> tablosunu aynı anda onarabilirsiniz:
<pre class="prettyprint lang-sh" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">$ mysqlcheck -r --databases blog blog2</pre>
Eğer bu komutu çalıştırdığınızda <code class="prettyprint lang-sh" data-start-line="1" data-visibility="visible" data-highlight="" data-caption=""> note : The storage engine for the table doesn't support repair</code> uyarısını görürseniz anlayın ki ilgili tablonun da depolama motoru InnoDB’dir.
<h2>Bütün Veritabanlarını Optimize Edip Onarma</h2>
Aşağıdaki komut sunucunuzda ki bütün veritabanlarını kontrol edecektir ve bozulmuş olan varsa otomatik olarak onaracaktır. :
<pre class="prettyprint lang-sh" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">$ mysqlcheck --auto-repair -o --all-databases</pre>
Umarım işinize yarar, sorularınızı yorum olarak sorabilirsiniz,