---
ID: 5969
post_title: 'CentOS 6&#8217;da Varnish 2&#8217;den Varnish 4.0&#8217;a Yükseltme ve Varnish 4.0 Kurulumu'
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/centos-6da-varnish-2den-varnish-4-0a-yukseltme-ve-varnish-4-0-kurulumu-5969.html
published: true
post_date: 2016-12-28 03:30:58
---
Merhaba arkadaşlar,

Varnish 2'den Varnish 4'e direkt olarak "yum update" çalıştırdığınızda geçiş yapamıyorsunuz. Bunun sebebi varnish 2 ile 4'ün söz diziminde meydana gelen değişikliktir. Evrensel bir sıkıntı yaşanmaması için EPEL'de sadece Varnish 2 sürümünü kurabiliyorsunuz. Aynı zamanda Varnish 2.0'dan Varnish 4.1'e geçerken de hatalarla karşılaştım; bu nedenle 4.0 kurdum. 4.0'dan 4.1'e yükseltmeyi denemedim henüz.

Öncelikle
<pre class="prettyprint lang-sh" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">yum update</pre>
ile EPEL de dahil bir güncelleme yapalım. Eğer EPEL kurulu değilse şu şekilde kurabilirsiniz:
<pre class="prettyprint lang-sh" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">yum install epel-release</pre>
Daha sonra Varnish 4.0 RPM'ini kuralım. 2 farklı RPM mevcut, birisi EL6 için diğeri isi EL7 içindir.

EL6 için Varnish 4.0 RPM ve Varnish kurulumu:
<pre class="prettyprint lang-sh" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">rpm --nosignature -i https://repo.varnish-cache.org/redhat/varnish-4.0.el6.rpm
yum install varnish</pre>
Eğer 4.0'a güncelleme yapacaksanız:
<pre class="prettyprint lang-sh" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">rpm --nosignature -i https://repo.varnish-cache.org/redhat/varnish-4.0.el6.rpm
yum update varnish</pre>
EL7 için Varnish 4.0 RPM ve Varnish Kurulumu
<pre class="prettyprint lang-sh" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">rpm --nosignature -i https://repo.varnish-cache.org/redhat/varnish-4.0.el7.rpm
yum install varnish</pre>
Eğer 4.0'a güncelleme yapacaksanız:
<pre class="prettyprint lang-sh" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">rpm --nosignature -i https://repo.varnish-cache.org/redhat/varnish-4.0.el7.rpm
yum update varnish</pre>
İşinize yaraması dileğiyle,