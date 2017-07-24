---
ID: 5971
post_title: 'Varnish 4 Kurulumunda &#8220;VCL compilation failed&#8221; Hatası'
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/varnish/varnish-4-kurulumunda-vcl-compilation-failed-hatasi-5971.html
published: true
post_date: 2016-12-28 05:53:47
---
Merhaba arkadaşlar,

<a href="http://www.trkodlama.com/makaleler/varnish-nedir-5816.html" target="_blank">Varnish</a> 4.0 kurduktan sonra aşağıdaki hatayı alırsanız korkmayın çözümü oldukça basit.
<blockquote>ERROR:
Starting Varnish Cache: Error:
Message from C-compiler:
/bin/sh: /usr/bin/gcc: Permission denied
/bin/sh: line 0: exec: /usr/bin/gcc: cannot execute: Permission denied
Running C-compiler failed, exited with 126

VCL compilation failed</blockquote>
Eğer bu hatayı alırsanız aşağıdaki iki dosyanın iznini 777 ve grubunu <em><strong>compiler </strong></em>olarak güncelleyin. Sorununuz ortadan kalkacaktır.
<ol>
 	<li>/usr/bin/gcc</li>
 	<li>/usr/bin/ld (küçük L)</li>
</ol>
<span style="color: #ff0000;">Not: Bu iki dosyanın iznini 777 yapmanın herhangi bir güvenlik açığına sebep olup olmadığını bilmiyorum. 777 izin vermek her zaman riskli görünmüştür bana. Kendi sorumluluğunuzda gerçekleştirin bu işlemi lütfen.</span>