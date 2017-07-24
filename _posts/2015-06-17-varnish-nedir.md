---
ID: 5816
post_title: Varnish Nedir?
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/varnish/varnish-nedir-5816.html
published: true
post_date: 2015-06-17 06:52:11
---
Varnish bir <a href="http://www.trkodlama.com/makaleler/ters-vekil-sunucusureverse-proxy-server-nedir-5812.html">HTTP hızlandırıcı</a>dır(<a href="http://www.trkodlama.com/makaleler/ters-vekil-sunucusureverse-proxy-server-nedir-5812.html">Ters Vekil Sunucusu</a>, <a href="http://www.trkodlama.com/makaleler/ters-vekil-sunucusureverse-proxy-server-nedir-5812.html">Reverse Proxy Server</a>). Ziyaretçileri her ziyarette tekrar oluşturulan dinamik sayfalar yerine önbelleğine alınmış statik sayfalara yönlendirir ve sitenin hızlı bir şekilde açılmasını sağlar. Varnish’in en güzel özelliklerinden bir tanesi ise ne zaman içeriği dinamik olarak oluşturulmasını sağlayacağını bilmesidir. Bu durumda sadece gerek olduğu zaman sayfalar dinamik olarak oluşturulur.

Varnish basitçe, yapılan istekleri, belli kurallar ile cache'leyip istemciye dönen, genelde web sunucuların önünde konumlandırılan bir araç. İstekler Varnish'e geliyor, Varnish önbelleğinde varsa isteği buradan dönüyor, eğer yoksa sunucudan derleniyor. Varnish’in hızlı olmasının en büyük sebebi proxy için disk kullanmadan sadece ram kullanması ve log tutmak için yine disk kullanmamasıdır.

Örnek vermek gerekirse oluşan markup çıktısı her ne kadar ~20KB civarında olsa da, o 20KB'ı oluşturmak için, her istekte 5-10 MB RAM ve işlemci boşa harcanıyor. Ve siteye aynı anda 10.000 kullanıcı gelirse, 70-80 GB RAM'e ihtiyacınız oluyor! Toplamda ~20KB RAM işinizi görecekken 70-80 GB'lık bir sunucu bulmanız, yükü ona göre dağıtmanız ve bu sunucuları maintain etmeniz, en önemlisi bu sunuculara "para ödemeniz" gerekiyor. Varnish işte tam burada yardımınıza yetişiyor.
<h4>Daha aydınlatıcı olması için test edelim...</h4>
PHP ile basitçe 50ms'de dönen bir kod yazalım:

<img class="aligncenter size-full wp-image-5820" src="http://www.trkodlama.com/wp-content/uploads/2015/06/varns3.png" alt="varns3" width="878" height="190" />

Şimdi apache üzerinde, mod_php ile çalışan bu adrese, anlık 100, toplam 5000 istek gönderelim:

<img class="aligncenter size-full wp-image-5818" src="http://www.trkodlama.com/wp-content/uploads/2015/06/varns.png" alt="varns" width="876" height="1332" />

5000 isteğin tamamlanması 3.304 saniye sürmüş. Bu da saniyede toplam 1513 isteğe cevap verebilmişiz demek. Bir de Varnish ile deneyelim:

<img class="aligncenter size-full wp-image-5819" src="http://www.trkodlama.com/wp-content/uploads/2015/06/varns2.png" alt="varns2" width="874" height="1338" />

Bu sefer, 5000 istek, 0.307 saniyede döndü! Ve saniyede 16309.86 isteğe cevap verebilen bir sunucumuz oldu. Süper değil mi? 10 kattan daha fazla kazancımız oldu. Bu da kabaca, 10 tane sunucunun işini tek sunucuda yapabiliyoruz demek. <a href="https://www.cloudbunny.net/knowledgebase/351/LitespeedplusVarnish-Nedir-Ne-e-Yarar-Avantajlar-Nedir.html" target="_blank" rel="noopener">cloudbunny</a>