---
ID: 5949
post_title: >
  CSF Güvenlik Duvarı Yüklü
  Sunucularda FTP Pasif Mod Bağlantı
  Problemi
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/csf-guvenlik-duvari-yuklu-sunucularda-ftp-pasif-mod-baglanti-problemi-5949.html
published: true
post_date: 2016-12-21 16:08:07
---
<a href="https://configserver.com" target="_blank">CSF</a> web sunucunuzda rahatlıkla kullanabileceğiniz; WHM'de bulunan kullanıcı arayüzü sayesinde kullanımı ve ayarlaması oldukça basit olan bir güvenlik duvarı uygulamasıdır.

Fakat CSF yüklü sunucularda FTP Pasif Mod'da çalışmasına engel olabilen bazı durumlar mevcut. Bunu CSF readme dosyasında şu şekilde tanımlamış:
<blockquote>13. A note about FTP Connection Issues
######################################

It is important when using an SPI firewall to ensure FTP client applications are configured to use Passive (PASV) mode connections to the server.

On servers running Monolithic kernels (e.g. VPS Virtuozzo/OpenVZ and custom built kernels) ip_conntrack and ip_conntrack_ftp iptables kernel modules may not be available or fully functional. If this happens, FTP passive mode (PASV) won't work. In such circumstances you will have to open a hole in your firewall and configure the FTP server to use that same hole.

For example, with pure-ftpd you could add the port range 30000:35000 to TCP_IN
and add the following line to /etc/pure-ftpd.conf and then restart pure-ftpd:
PassivePortRange   30000 35000

For example, with proftpd you could add the port range 30000:35000 to TCP_IN
and add the following line to /etc/proftpd.conf and then restart proftpd:
PassivePorts   30000 35000

FTP over SSL/TLS will usually fail when using an SPI firewall. This is because of the way the FTP protocol established a connection between client and server. iptables fails to establish a related connection when using FTP over SSL because the FTP control connection is encrypted and so cannot track the relationship between the connection and the allocation of an ephemeral port.

If you need to use FTP over SSL, you will have to open up a passive port block in both csf and your FTP server configuration (see above).

Perversely, this makes your firewall less secure, while trying to make FTP connections more secure.</blockquote>
<h2>FTP Nedir? FTP Aktif Mod ve Pasif Mod Nedir? (<a href="http://www.hostingsozluk.com/hosting-terimleri/ftp/" target="_blank">kaynak</a>)</h2>
FTP, İngilizce “File Transfer Protocol”’un kısaltmasıdır. Türkçe’ye “Dosya Transfer Protokolü” olarak çevrilebilir. Amacı, TCP/IP üzerinden dosya transferi yapılmasını sağlamaktır. FTP de tıpkı HTTP gibi bir Layer 7 (OSI katmanında) protokolüdür ve standart portu 20 ve 21’dir.

FTP’nin “aktif” ve “pasif” şeklinde iki modu vardır.

FTP Aktif mod: Bu modda FTP komutları 21. porttan, tüm veri aktarımları ise 20. port üzerinden gerçekleştirilir. Çok belirgin ve saldırıya açık bir metod olduğundan, günümüzde FTP Aktif mod çok nadir kullanılmakta, yerine; aktif modun yarattığı güvenlik zaaflarını gidermek için geliştirilmiş olan FTP Pasif mod kullanılmaktadır.

FTP Pasif mod: Pasif mod da, tıpkı aktif modda gibi FTP kontrol komutları 21. port üzerinden gönderilir ancak, veri aktarımları; FTP sunucusunun açtığı son port ve FTP istemcisinin açtığı son port arasında gerçekleşir. Veri aktarımı yapılan portlar bilinmediğinden, güvenlik duvarı problemleri ve sniffing gibi sorunları en aza indirgemeyi amaçlamaktadır.

Bir FTP sunucusuna bağlanmak için bir FTP istemcisine ihtiyaç duyarsınız. Bu FTP istemcisi, günümüzün en çok kullanılan istemcilerinden bir tanesi olan FileZilla olabileceği gibi, artık birçok metin editörünün de FTP desteği bulunmaktadır. Hatta birçok web tarayıcısı bile, FTP istemcisi olarak çalışabilmektedir ve bunun sebebi de HTTP ve FTP protokollerinin benzer olmalarıdır.
<h2>Sonuca Gelelim</h2>
Uzun lafın kısası bazı sunucularda CSF, FTP Pasif Mod portlarını bloklayabilir. Bunun için kullandığınız ftp uygulamasının ayar dosyasında Pasif Mod Port aralığını tanımlayıp aynı aralığı TCP_IN kuralında izinli hale getirmelisiniz.
<h3>ProFTP Ayarları</h3>
ProFTP ayar dosyasını açın. Dosya konumu şu şekildedir: <em><strong>/etc/proftpd.conf</strong></em> . <strong>PassivePorts</strong> kuralını 30000 35000 olacak şekilde güncelleyin:

[text]PassivePorts   30000 35000[/text]

<h3>Pure-FTPD Ayarları</h3>
Pure-FTPD ayar dosyasını açın. Dosya konumu şu şekildedir: <em><strong>/etc/pure-ftpd.conf</strong></em>.<strong>PassivePortRange </strong>kuralını 30000 35000 olacak şekilde güncelleyin:

[text]PassivePortRange   30000 35000[/text]

<h3>FTP Ayarları Bitti! Şimdi CSF'de Bu Port Aralığına İzin Verelim</h3>
CSF ayar dosyasını açın. Dosya konumu şu şekildedir: <em><strong>/etc/csf/csf.conf</strong></em>. <strong>TCP_IN</strong> kuralına 30000:35000 ekleyeceğiz. Temsili olarak şu şekilde olmalıdır:

[text]TCP_IN = &quot;20,21,22,...,30000:35000&quot;[/text]

Yaşadığım bir sıkıntıydı fakat bu şekilde rahatlıkla çözebilirsiniz. Kolay gelsin dilerim,

&nbsp;