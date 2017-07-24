---
ID: 5840
post_title: 'CentOS&#8217;da Hostname Değiştirme'
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/centosda-hostname-degistirme-5840.html
published: true
post_date: 2015-06-21 19:14:48
---
Şu sıralar sunucular üzerinden yazı yazıyorum devamlı. Fena halde kafayı takmış durumdayım. Bu yazımda da önemli ve basit bir işlemin nasıl yapılacağını anlatıyorum.Varsayılan olarak hostname'iniz sunucunuz adınız olarak atanır. Cpanel gibi bazı yazılımlar hostname için FQDN(Fully Qualified Domain Name) isterler lisans onaylama sistemlerinden ötürü.

<h2>Peki, Hostname Nasıl Değiştirilir?</h2>

<strong>Hostname</strong>'i 4 adımda değiştirebiliriz. Şanslısınız ki oldukça kolay adımlardır :)

<h3>Sysconfig/Network</h3>

<em><strong>/etc/sysconfig/network</strong></em> dosyasını açın. Bu dosyada <strong>HOSTNAME=</strong> değerini kendinize göre uygun bir FQDN ile düzenleyeceğiz. Yönetici değilseniz komutların başına <strong>sudo</strong> ekleyin lütfen.

<pre class="lang:bash decode:1 " >nano /etc/sysconfig/network</pre>

[text]HOSTNAME=sunucum.domain.com[/text]

<h3>Hosts Dosyası</h3>

Sunucunuzun IP adresiyle ilişkilendirilmiş olan hostumuzu güncellemeliyiz. (<strong>/etc/hosts</strong> konumunda bulunur)

<a href="http://www.trkodlama.com/wp-content/uploads/2015/06/hosts.png"><img class="aligncenter size-full wp-image-5842" src="http://www.trkodlama.com/wp-content/uploads/2015/06/hosts.png" alt="hosts" width="636" height="235" /></a>

<h3>'Hostname' Komutu</h3>

'hostname' komutu ile komut satırının bildiği bütün hostname'leri güncelleyebilirsiniz. Fakat sistemdeki bütün hostname değerlerini güncellemediğini bilmelisiniz. Bu yüzden bir değişiklik anında tek tek kontrol etmelisiniz.

<a href="http://www.trkodlama.com/wp-content/uploads/2015/06/hostname.png"><img class="aligncenter size-full wp-image-5843" src="http://www.trkodlama.com/wp-content/uploads/2015/06/hostname.png" alt="hostname" width="620" height="167" /></a>

&nbsp;

<h3>Network Servisini Yeniden Başlatma Vakti</h3>

Bu aşamada ayarlarımızı kaydettik, ayarlarımızın yürülüğe girmesi için tek yapmamız gereken network servisini yeniden başlatma ;)

<pre class="lang:bash decode:1 " >service network restart</pre>

veya

<pre class="lang:bash decode:1 " ></pre>/etc/init.d/network restart<pre class="lang:bash decode:1 " ></pre>

İyi tatiller,

&nbsp;