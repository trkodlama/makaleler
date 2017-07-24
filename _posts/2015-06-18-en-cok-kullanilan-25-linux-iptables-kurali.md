---
ID: 5827
post_title: >
  En Çok Kullanılan 17 Linux IPTables
  Kuralı
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/en-cok-kullanilan-25-linux-iptables-kurali-5827.html
published: true
post_date: 2015-06-18 04:37:48
---
İlk sefer bakanlar için veya yeni yeni kurcalamaya başlayanlar için IPTables kuralları karışık gelebilir.

Bu makalede, genellikle ihtiyaç duyacağınız 17 pratik IPTables kuralını sizlerle paylaşıyorum. Sizde rahatlıkla kopyala/yapıştır yaparak faydalanabilirsiniz.

Aşağıdaki örneklerin kimisi temsili değerler göz önüne alınarak hazırlanmıştır. Siz kendi ihtiyaçlarınız doğrultusunda düzenleyiniz lütfen.

<h3>1. IPTables Kurallarını Silme</h3>

Yeni kurallarınızı oluşturmadan önce bütün IPTables kurallarınızı temizlemek en doğrusu olacaktır. Bu sayede çakışma vs. olmayacaktır. Bunun için <strong>flush</strong> komutunu kullanacağız.

<pre class="lang:bash decode:1 " >iptables -F</pre>

veya

<pre class="lang:bash decode:1 " >iptables --flush</pre>

<h3>2. Varsayılan Zincir Politikasını Ayarlama</h3>

Aslında bu başlık biraz google translate oldu. Orjinali <strong>Default Chain Policy</strong>.

Varsayılan zincir politikası <strong>ACCEPT</strong>'tir.

<pre class="lang:bash decode:1 " >iptables -P INPUT DROP
 iptables -P FORWARD DROP
 iptables -P OUTPUT DROP</pre>

<strong>INPUT</strong> ve <strong>OUTPUT</strong>'un ikisini de <strong>DROP</strong> olarak ayarlarsanız her güvenlik duvarı kuralında ikisini de tanımlamak zorundasınız. Gelen ve giden bağlantılar...

Aşağıdaki örneklerin hepsinde INPUT ve OUTPUT ayrı ayrı tanımlanmıştır.

<h3>3. IP Adresi Engelleme</h3>

Belirli bir IP adresinin sunucunuza erişmesini istemiyorsanız onu engelleyebilirsiniz. Sunucunuzdaki hiç bir web adresine erişimi kalmayacaktır bu sayede. "x.x.x.x" kısmını düzenlemelisiniz.

<pre class="lang:bash decode:1 " >BLOCK_THIS_IP=&amp;quot;x.x.x.x&amp;quot;
 iptables -A INPUT -s &amp;quot;$BLOCK_THIS_IP&amp;quot; -j DROP</pre>

Log dosyalarınızda şüpheli eylemler gerçekleştiren IP adreslerini engellemek isteyebilirsiniz. İsterseniz kalıcı isterseniz geçici..

Ayrıca bu IP adresi için eth0 üzerindeki TCP trafiğini de engelleyebilirsiniz.

<pre class="lang:bash decode:1 " >iptables -A INPUT -i eth0 -s &amp;quot;$BLOCK_THIS_IP&amp;quot; -j DROP
 iptables -A INPUT -i eth0 -p tcp -s &amp;quot;$BLOCK_THIS_IP&amp;quot; -j DROP</pre>

<h3>4. Bütün SSH Bağlantılarına İzin Ver</h3>

Aşağıdaki kural SSH bağlantısı kurmak isteyen eth0'dan herkesi kabul edecektir. Aslında 22 portunu açıyoruz.

<pre class="lang:bash decode:1 " >iptables -A INPUT -i eth0 -p tcp --dport 22 -m state --state NEW,ESTABLISHED -j ACCEPT
 iptables -A OUTPUT -o eth0 -p tcp --sport 22 -m state --state ESTABLISHED -j ACCEPT</pre>

<h3>5. SSH'a Sadece Kısmi Bir Ağdan Erişime İzin Verme</h3>

Aşağıdaki komut sadece 192.168.100.X IP'li kullanıcılara SSH erişimini açacaktır.

<pre class="lang:bash decode:1 " >iptables -A INPUT -i eth0 -p tcp -s 192.168.100.0/24 --dport 22 -m state --state NEW,ESTABLISHED -j ACCEPT
 iptables -A OUTPUT -o eth0 -p tcp --sport 22 -m state --state ESTABLISHED -j ACCEPT</pre>

<h3>6. Gelen HTTP ve HTTPS Sorgularına İzin Ver</h3>

Aşağıdaki komut web trafiğine izin verecektir. Yani 80 portunu açacak. HTTP

<pre class="lang:bash decode:1 " >iptables -A INPUT -i eth0 -p tcp --dport 80 -m state --state NEW,ESTABLISHED -j ACCEPT
 iptables -A OUTPUT -o eth0 -p tcp --sport 80 -m state --state ESTABLISHED -j ACCEPT</pre>

Aşağıdaki komut sayesinde ise 443 portu açılacak ve bu da HTTPS.

<pre class="lang:bash decode:1 " >iptables -A INPUT -i eth0 -p tcp --dport 443 -m state --state NEW,ESTABLISHED -j ACCEPT
 iptables -A OUTPUT -o eth0 -p tcp --sport 443 -m state --state ESTABLISHED -j ACCEPT</pre>

<h3>7. MultiPort'u Kullanarak Birden Fazla Kuralı Birleştirme</h3>

Her port için ayrı ayrı kural yazmaktansa bütün portları <strong>MultiPort</strong> kullanarak tek kural ile yazabiliriz. Aşağıdaki kural ile HTTP, HTTPS ve SSH'a erişime izin veriyoruz.

<pre class="lang:bash decode:1 " >iptables -A INPUT -i eth0 -p tcp -m multiport --dports 22,80,443 -m state --state NEW,ESTABLISHED -j ACCEPT
 iptables -A OUTPUT -o eth0 -p tcp -m multiport --sports 22,80,443 -m state --state ESTABLISHED -j ACCEPT</pre>

<h3>8. Giden SSH'a İzin Verme</h3>

Sunucunuzdan başka bir sunucuya bağlanmanıza olanak sağlar.

<pre class="lang:bash decode:1 " >iptables -A OUTPUT -o eth0 -p tcp --dport 22 -m state --state NEW,ESTABLISHED -j ACCEPT
 iptables -A INPUT -i eth0 -p tcp --sport 22 -m state --state ESTABLISHED -j ACCEPT</pre>

Gelen SSH'dan farklı olduğunu incelerseniz görebilirsiniz.

<h3>9. Sadece Kısmi Bir Ağa (Giden)SSH İle Bağlanma</h3>

Aşağıdaki kural ile sunucunuzdan 192.168.100.0/24 ağındaki bir IP adresine bağlantı sağlayabilirsiniz.

<pre class="lang:bash decode:1 " >iptables -A OUTPUT -o eth0 -p tcp -d 192.168.100.0/24 --dport 22 -m state --state NEW,ESTABLISHED -j ACCEPT
iptables -A INPUT -i eth0 -p tcp --sport 22 -m state --state ESTABLISHED -j ACCEPT</pre>

<h3>10. Giden HTTPS'ye İzin Verme</h3>

Sunucunuzdan https adreslerine istek yapabilmenizi sağlar. <strong>wget</strong> vs. ile dosya indirmek istediğinizde oldukça işinize yarayacaktır.

<pre class="lang:bash decode:1 " >iptables -A OUTPUT -o eth0 -p tcp --dport 443 -m state --state NEW,ESTABLISHED -j ACCEPT
 iptables -A INPUT -i eth0 -p tcp --sport 443 -m state --state ESTABLISHED -j ACCEPT</pre>

Not: HTTP için 443 portunu 80 olarak güncelleyin.

<h3>11. Sunucunuza Ping Yapılmasına İzin Verme</h3>

<pre class="lang:bash decode:1 " >iptables -A INPUT -p icmp --icmp-type echo-request -j ACCEPT
 iptables -A OUTPUT -p icmp --icmp-type echo-reply -j ACCEPT</pre>

<h3>12. Sunucunuzda Ping Yapabilme</h3>

<pre class="lang:bash decode:1 " >iptables -A OUTPUT -p icmp --icmp-type echo-request -j ACCEPT
 iptables -A INPUT -p icmp --icmp-type echo-reply -j ACCEPT</pre>

<h3>13. MySQL Sunucunuza Kısmi Bir Ağdan Erişime İzin Verme</h3>

MySQL kullanıyoruz sunucu dışından direk erişime izin vermek pek de mantıklı bir hamle değil.

Fakat geliştiriciler laptoplarından veya bilgisayarlarından kullandıkları MySQL yazılımları bağlanmak isteyebilirler. 192.168.100.0/24 ağına MySQL'i açalım.

<pre class="lang:bash decode:1 " >iptables -A INPUT -i eth0 -p tcp -s 192.168.100.0/24 --dport 3306 -m state --state NEW,ESTABLISHED -j ACCEPT
 iptables -A OUTPUT -o eth0 -p tcp --sport 3306 -m state --state ESTABLISHED -j ACCEPT</pre>

<h3>14. Sendmail ve Postfix'e İzin Verme</h3>

Sendmail veya Postfix'e smtp portunu açarak izin veriyoruz.

<pre class="lang:bash decode:1 " >iptables -A INPUT -i eth0 -p tcp --dport 25 -m state --state NEW,ESTABLISHED -j ACCEPT
iptables -A OUTPUT -o eth0 -p tcp --sport 25 -m state --state ESTABLISHED -j ACCEPT</pre>

<h3>15. IMAP ve IMAP2'ye İzin Verme</h3>

<pre class="lang:bash decode:1 " >iptables -A INPUT -i eth0 -p tcp --dport 143 -m state --state NEW,ESTABLISHED -j ACCEPT
iptables -A OUTPUT -o eth0 -p tcp --sport 143 -m state --state ESTABLISHED -j ACCEPT</pre>

IMAPS'e izin vermek içinse:

<pre class="lang:bash decode:1 " >iptables -A INPUT -i eth0 -p tcp --dport 993 -m state --state NEW,ESTABLISHED -j ACCEPT
iptables -A OUTPUT -o eth0 -p tcp --sport 993 -m state --state ESTABLISHED -j ACCEPT</pre>

<h3>16. POP3 ve POP3S'e İzin Verme</h3>

<pre class="lang:bash decode:1 " >iptables -A INPUT -i eth0 -p tcp --dport 110 -m state --state NEW,ESTABLISHED -j ACCEPT
iptables -A OUTPUT -o eth0 -p tcp --sport 110 -m state --state ESTABLISHED -j ACCEPT</pre>

POP3S'e izin vermek içinse

<pre class="lang:bash decode:1 " >iptables -A INPUT -i eth0 -p tcp --dport 995 -m state --state NEW,ESTABLISHED -j ACCEPT
iptables -A OUTPUT -o eth0 -p tcp --sport 995 -m state --state ESTABLISHED -j ACCEPT</pre>

<h3>17. DoS Ataklarını Engelleme</h3>

Aşağıdaki IPTables kuralı web sunucunuzu DoS ataklarını kısmen koruyacaktır.

<pre class="lang:bash decode:1 " >iptables -A INPUT -p tcp --dport 80 -m limit --limit 25/minute --limit-burst 100 -j ACCEPT</pre>

Yukarıdaki örnekte:

-m limit: IPTables'ın limit eklentisini kullanır
--limit 25/minute: Dakikada 25 bağlantı kabul edileceğini belirtir
--limit-burst 100: 100 bağlantı sayısına ulaşıldığında limit/minute kuralını çalıştırır

Umarım işinize yarar, hepinize iyi çalışmalar dilerim,

<h3></h3>