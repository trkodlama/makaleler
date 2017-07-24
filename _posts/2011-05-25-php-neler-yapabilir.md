---
ID: 5768
post_title: PHP neler yapabilir?
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/php-neler-yapabilir-5768.html
published: true
post_date: 2011-05-25 12:49:32
---
Her şeyi. PHP temel olarak sunucu-taraflı programlamaya odaklanmıştır, bu nedenle CGI uygulamalarının yaptığı her şeyi, örneğin formdan veri toplama, devingen sayfa içeriği oluşturma, ya da çerez alıp gönderme gibi işlemleri yapabilirsiniz. Ancak PHP bunlardan çok daha fazlasını yapabilecek yetenektedir.

PHP betiklerinin kullanıldığı başlıca üç alan vardır.

<ul>
    <li>Sunucu-taraflı programlama. Bu PHP için en geleneksel ve en temel olan alandır. Sunucu-taraflı programlama için üç şeye sahip olmanız gerekir. PHP çözümleyici (CGI ya da sunucu modülü), bir HTTP sunucusu ve bir tarayıcı. PHP programlamada deneyimliyseniz tüm bunları evinizdeki makinede çalıştırabilirsiniz. Yapılandırma ve Kurulum bölümünden bununla ilgili daha fazla bilgiye ulaşabilirsiniz.</li>
    <li>Komut satırı uygulamaları. Bir PHP uygulamasını komut satırından hiçbir sunucu ya da tarayıcı uygulama kullanmadan çalıştırabilirsiniz. Burada tek ihtiyacınız olan PHP çözümleyicidir. Bu tür kullanım cron üzerinden (Windows eşdeğeri görev yöneticisi) düzenli çalıştırılan işlemler ya da basit metin işleme görevleri için idealdir. PHP'nin komut satırında kullanımı bölümünde daha ayrıntılı bilgiye ulaşaşabilirsiniz.</li>
    <li>Masaüstü uygulamalarının yazımı. PHP için görsel uygulamaların yazılabileceği en iyi dil diyemeyiz, ancak PHP'yi iyi biliyorsanız ve PHP'nin birtakım ileri seviye özelliklerini kendi istemci taraflı uygulamalarınızda kullanmak istiyorsanız, PHP-GTK eklentisini bu tip programlar yazmak için kullanabilirsiniz. Bu şekilde platformdan bağımsız uygulamalar yazma şansına da kavuşacaksınız. PHP-GTK, PHP için bir eklentidir ve ana dağıtımda yer almaz. PHP-GTK ilginizi çektiyse, » kendi sitesini ziyaret edebilirsiniz.
PHP bütün büyük işletim sistemlerinde, Linux, birçok Unix türevi (HP-UX, Solaris, OpenBSD vb.), Microsoft Windows, Mac OS X, RISC OS dahil olmak üzere çok çeşitli platformlarda çalışabilir. PHP benzer biçimde bugün yaygın biçimde kullanılan HTTP sunucularının büyük kısmını destekler. Bunlara Apache, IIS ve daha birçok sunucuyu örnek gösterebiliriz. Bunlara FastCGI PHP çalıştırılabilirini kullanan lighttpd ve nginx gibi sunucular da dahildir. PHP modül olarak kullanılabildiği gibi bir CGI işleyici olarak da çalıştırılabilir.</li>
</ul>

Sonuç olarak, PHP ile işletim sistemi ve HTTP sunucusu seçme özgürlüğüne sahipsiniz. Dahası, hangi programlama yöntemini kullanacağınıza, işlevsel yaklaşımı mı yoksa nesne yönelimli yaklaşımı mı yoksa her ikisini birden mi kullanacağınıza kendiniz karar verebilirsiniz.

PHP'nin yetenekleri yalnızca HTML çıktı üretmekle sınırlı değildir. PHP'nin yetenekleri arasında resim çıktısı üretebilme, PDF oluşturabilme ve hatta Flash filmleri oluşturabilme (libswf ve Ming kullanarak) bulunmaktadır. Aynı şekilde XHTML ya da XML gibi her tür metin tabanlı dosyayı oluşturabilmeniz mümkündür. PHP bu dosyaları özdevinimli olarak oluşturabilir ve ekrana yazdırmanın yanında sizin için dosya sisteminde saklayabilir, böylece devingen içeriğiniz için sunucu-taraflı bir depo sistemini kullanımınıza sunabilir.

PHP'nin en güçlü ve en çok üstünde durulan özelliklerinden biri, sahip olduğu geniş ve gelişmiş veritabanı desteğidir. Veritabanlarına özgü eklentilerden birini (örn. mysql) kullanarak veya PDO gibi bir soyutlama katmanı kullanarak PHP ile veritabanı bağlantılı site sayfaları oluşturmak ya da ODBC eklentisi üzerinden bu standardı destekleyen bir bağlantı açmak son derece basittir. Diğer veritabanları için cURL eklentisi veya soketler (CouchDB gibi) kullanılabilir.

PHP, farklı hizmetlerle LDAP, IMAP, SNMP, NNTP, POP3, HTTP, COM (Windows için) ve daha sayısız protokol aracılığıyla iletişim kurabilecek bir altyapıya da sahiptir. Hazır modüllerin haricinde ham ağ soketleri açıp bu soketler üzerinden istediğiniz bütün protokollerle çalışabilirsiniz. PHP, WDDX üzerinden sanal olarak sanal doku üzerinde hangi dilde yazılmış olursa olsun tüm uygulamalarla haberleşebilir. Ayrıca Java nesnelerinin oluşturulabilmesi ve şeffaf biçimde PHP nesneleri olarak kullanılabilmeleri önemli bir diğer özelliktir.

PHP oldukça faydalı belge işleme özelliklerine sahiptir. Bu yelpaze Genişletilmiş POSIX ya da Perl düzenli ifade komutlarından (PCRE) XML dosyalarını okumaya ve çözümlemeye kadar uzanır. PHP tüm XML uzantılarını libxml2 tabanında tek bir standartta toplamış ve SimpleXML ile XMLReader ve XMLWriter desteğini de bünyesine katarak sunduğu imkan yelpazesini genişletmiştir.

Alfabetik olarak ve sınıflandırılarak belgelenmiş daha pek çok ilginç eklenti vardır. Bunlara ek olarak » XDebug gibi PHP kılavuzu içinde belgelenmiş ya da belgelenmemiş PECL eklentileri de mevcuttur.

Sizin de görebildiğiniz gibi bu sayfa PHP'nin sunabileceği bütün özellikleri ve faydaları anlatabilmek için yeterli değil. Yapılandırma ve Kurulum bölümünde ve İşlev başvuru kılavuzunda listelenen eklentilerin başlangıç bölümlerindeki açıklamalardan her bir eklenti için daha fazla bilgiye ulaşabilirsiniz.