---
ID: 5793
post_title: Genel Kurulum Değerlendirmesi
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/genel-kurulum-degerlendirmesi-5793.html
published: true
post_date: 2011-05-28 03:43:44
---
Kuruluma başlamadan önce PHP'yi ne amaçla kullanacağınızı bilmeniz faydalı olur. Kullanım amaçları <a href="http://www.trkodlama.com/yazili-dersler/php-yazili-dersler/php-kilavuzu/php-neler-yapabilir-5768.html">PHP ile ne yapılabilir?</a> bölümünde anlatıldığı üzere 3 bölümde incelenebilir:

<ul>
    <li>Genel Ağ siteleri ve uygulamaları (Sunucu taraflı)</li>
    <li>Komut satırı uygulamaları</li>
    <li>Masaüstü uygulamaları</li>
</ul>

İlk ve en önemli amaç için üç şeye ihtiyacınız bulunmaktadır: PHP'nin kendisi, bir HTTP Sunucusu ve bir tarayıcı. Muhtemelen bir tarayıcınız zaten vardır. Kullanmakta olduğunuz işletim sistemine bağlı olarak bir HTTP Sunucunuz da olabilir (Linux ve MacOS üzerinde Apache, Windows üzerinde IIS gibi). Yoksa, bir firmadan site barındırma hizmeti alabilirsiniz. Böylece herşeyi kendiniz ayarlamak zorunda kalmazsınız. Sadece PHP betiklerinizi yazmakla ilgilenir ve onları kiraladığınız alana yükleyip tarayıcınızla sonuçları görürsünüz.

Sunucuyu ve PHP’yi kendiniz yapılandıracaksanız, PHP’yi sunucuya bağlamak için iki seçeneğiniz olacak. Bir çok sunucunun PHP için (SAPI de denilen) bir modülü vardır. Apache, Microsoft Internet Information Server, Netscape and iPlanet sunucuları bu tür sunuculardandır. Bir çok sunucunun da Microsoft modül arayüzü, ISAPI için desteği vardır (OmniHTTPd gibi). Eğer sunucunuzda PHP için modül desteği yoksa sunucunuz ne türde olursa olsun onu bir CGI veya FastCGI işlemcisi olarak kullanabilirsiniz. Yani, sunucuya gelen tüm PHP dosyası isteklerini işleme sokmak için PHP’nin CGI çalıştırılabilirini kullanmak üzere sunucunuzu yapılandırabilirsiniz.

PHP'yi komut satırı betikleri yazmak için kullanmayı düşünüyorsanız (özdevinimli olarak resim üreten veya komut satırından aktardığınız değiştirgelerle metin dosyalarını işleyen betikler gibi), bir komut satırı betik yorumlayıcısına ihtiyacınız var demektir. Bu konuda daha fazla bigi edinmek için Komut satırı PHP uygulamalarının yazılması bölümüne bakınız. Bu durumda ne sunucuya ne de tarayıcıya ihtiyacınız olur.

PHP ile PHP-GTK eklentisini kullanarak masaüstü uygulamaları da yazabilirsiniz. Herhangi bir HTML çıktı üretilmediği için Genel Ağ sayfaları yazmaktan tamamen farklı bir yaklaşıma sahiptir. Bu araçlarla sadece pencereleri ve nesneleri yönetirsiniz. PHP-GTK hakkında daha ayrıntılı bilgi edinmek için lütfen » bu eklentinin kendi sitesini ziyaret ediniz. PHP-GTK, resmi PHP dağıtımlarıyla gelmez.

Bu noktadan itibaren belgede, daha çok Unix ve Windows üzerinde çalışan modüllü HTTP sunucuları ve CGI çalıştırılabilirlerinin yapılandırılması üzerinde durulacaktır. Ayrıca, komut satırı çalıştırılabiliri hakkında da bilgi bulabileceksiniz.

PHP'nin kaynak kodu ve Windows için çalıştırılabilir sürümleri » http://www.php.net/downloads.php adresinden temin edilebilir. Dağıtımları indirmek için yakınınızdaki » yansıları kullanmanızı öneririz.