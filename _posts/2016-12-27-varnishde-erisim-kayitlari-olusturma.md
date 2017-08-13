---
ID: 5967
post_title: 'Varnish&#8217;de Erişim Kayıtları Oluşturma'
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/varnishde-erisim-kayitlari-olusturma-5967.html
published: true
post_date: 2016-12-27 11:28:35
---
Merhaba arkadaşlar,

Yakınlarda sunucuma bütün websitelerimin önünde ilk çalışacak Varnish Cache kurdum. Bu cümle biraz dengesiz oldu; açıklamam gerekirse tarayıcıdan sunucuma istek gönderildiğinde ilk olarak Apache'ye değil Varnish'e gidiyor istek. İyi haber performansı gözle görülür bir şekilde arttırdı Varnish.

Bugün bütün gece sunucumdaki <strong>WordPress</strong>'lerden birine <strong>Brute-Force</strong> denilen yöntem ile giriş denemeleri gerçekleştirildi. Hızlı farkettim ve girişe bir süre kapattım fakat problem şuydu ki saldırganın IP'sini yakalamıyorum. Sebebi ise apache erişim kayıtlarında(access logs)  IP olarak sunucumun IP'si görünüyordu. Bunun sebebi ise Apache'ye isteği gönderen kullanıcı değil Varnish'di.

<strong>Varnish</strong>'i kurduğunda otomatik olarak erişim kayıtları vermediğini farkettim biraz araştırınca. Fakat biraz daha araştırınca aynı <strong>Apache</strong> gibi <strong>Varnish</strong>'in de bu kayıtları oluşturabildiğini öğrendim.

Aşağıdaki komut ile <strong>/var/log/varnish/access.log</strong> isimli dosya da bütün sitelerinize gelen erişimleri tek dosyada görebilirsiniz:

[text]varnishncsa -a -w /var/log/varnish/access.log -D -P /var/run/varnishncsa.pid[/text]

Umarım işinize yaramıştır, kolay gelsin,