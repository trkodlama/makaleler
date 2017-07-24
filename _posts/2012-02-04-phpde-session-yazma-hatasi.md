---
ID: 285
post_title: 'PHP&#8217;de Session Yazma Hatası'
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/web-sunucu/phpde-session-yazma-hatasi-285.html
published: true
post_date: 2012-02-04 02:43:18
---
Merhaba arkadaşlar,

Bugün karşılaştığım bir hatayı ve bunun çözümünü sizlerle paylaşacağım..

Durduk yere error_log dosyamda aşağıdaki hatayı almaya başladım:
<blockquote>PHP Warning: Unknown: open(/var/lib/php/session/sess_57a2e1be3b736579c5af4f9f4acd43f3, O_RDWR) failed: Permission denied (13) in Unknown on line 0, referer: http://xxx.com
PHP Warning: Unknown: Failed to write session data (files). Please verify that the current setting of session.save_path is correct (/var/lib/php/session) in Unknown on line 0, referer: http://xxx.com</blockquote>
Nedenini bilmiyorum bir anda bu hata ortaya çıktı. Bugün bir eklenti kurdum belki de ondandır.. Biraz araştırmalarım sonunda iki satırlık komut ile bu sorunu çözebileceğimi farkettim. Bu sorunu yaşayan arkadaşlar için çözüm aşağıdaki gibi olabilir:
<pre class="prettyprint lang-sh" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">chown apache /var/lib/php/session
chmod 777 /var/lib/php/session</pre>
Bu şekilde tekrar eski haline geliyor ve düzeliyor fakat session klasörünün izinleri çok fazla. Herkesin rahatça erişebileceği bir halde. Daha sonra biraz daha araştırdım ve varsayılan klasör izinlerini elde ettim. O da çalışıyor. Yani kullanmanızı tavsiye ettiğim klasör izinleri için gerekli komut aşağıdaki gibidir:
<pre class="prettyprint lang-sh" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">chown root:psacln /var/lib/php/session
chmod 770 /var/lib/php/session</pre>
Benim tercihim ikincisini kullanmaktan yanadır. Siz hangisini uygun bulursanız onu kullanabilirsiniz. Umarım işinize yarar.

Kolay gelsin,