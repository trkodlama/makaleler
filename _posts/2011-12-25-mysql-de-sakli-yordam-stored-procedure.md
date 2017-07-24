---
ID: 270
post_title: 'MySQL de Saklı Yordam &#8211; Stored Procedure'
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/mysql-de-sakli-yordam-stored-procedure-270.html
published: true
post_date: 2011-12-25 02:22:46
---
Stored procedure tanım olarak; veritabanında saklı bulunan bildirimsel SQL kodlarının daha sonra bir program, tetikleyici ya da bir başka saklı yordam tarafından katalog olarak çağırılmasını kolaylaştıran bir yapıdır.

Stored Procedure recursive ve kendi kendini çağıran bir yordamdır. Hemen her RDMBS(Relational database management system) recursive stored procedure destekler.Fakat veriyona bağlı olarak MySQL desteklemiyor olabilir. Recursive stored procedure kullanmak için MySQL versiyonunuzu kontrol etmek, yükseltmek zorunda kalabilirsiniz.

<strong>MySQL'de Stored Procedure</strong>

MySQL topluluklar, kuruluş ve şirketler ve web yazılımcıları tarafından yaygın olarak kullanılan bir veritabanı çözümüdür. Fakat ilk versiyonları itibariyle Stored Procedure, trigger gibi özellikleri desteklememektedir. MySQL 5.0 sürümünden bu yana, veritabanı motoruna esneklik ve güçlülük katacak bu özellikleri açık kaynak kodlu yapısına eklenmiştir. Yani stored procedure ile ilgili örnekler üzerinde çalışacak, yazılımınızda destekleyici olarak kullanacaksanız MySQL 5.0+ bir sürümün kurulu olduğundan emin olmalıyız.

<strong>Stored Procedure Avantajları</strong>

Saklı yordam uygulamalarınızın performansını arttırır.
Oluşturulduktan sonra, saklı yordam veritabanının sorguya bağlı sonuçlarını derlenmiş olarak saklar. Bu sayede sonuçlar derlenmemiş SQL sorgularından daha hızlı bir şekilde çekilebilir.

Saklı yordam sayesinde uygulama ve veritabanı sunucusu arasında trafik yoğunluğu da azalır. Birden çok derlenmemiş SQL komutunun çağırılması yerine, saklı yordam ile derlenmiş sonuçların geri çağırılması sağlanır. Böylelikle çokca sql kodu tekrar tekrar derlenmek yerine, saklı yordamın isminin çağırılması ile zaten derlenmiş kütüphane yapısı sonuçları hızlıca elde edilebilir.

Saklı yordam yeniden kullanılabilirdir ve erişmek isteyen her dil için şeffaftır. Bu sayede programcılar ek yazılımlara, fonksiyonlara gerek duymadan MySQL saklı yordamlarına hızlıca erişebilirler.

Saklı yordam güvenlidir. Saklı yordam sayesinde tablo yetkileri haricinde, saklı yordam özel yetkilerini kullanılarak veritabanı yöneticilerinin spesifik prosedürlere erişimi sağlanabilir. Böylelikle korunan bir tablonun bir kısmı için derlenmiş bir saklı yordam, yetkiler ile kimilerine görünür kılınıp, tablonun güvenliği sabitleştirilebilir.

Bu avantajların yanında saklı yordamın aşağıdaki gibi bazı dezavantajları da vardır.

<strong>Stored Procedures Dezavantajları</strong>

Saklı yordamlar ram ve işlemciye bağlı olarak veritabanı sunucusunda aşırı yüklenmelere sebep olabilir.
Veritabanı sunucusu için uygun tasarlanmamış, karmaşık bir iş mantığını gerçekleştirmek için hatalı olarak kullanıldığında sorun teşkil edebilir.

Saklı yordam sadece bildirimsel SQL içerir. Bu sebeple karmaşık bir iş mantığı için prosedürler yazmak Java, C++, C# tarzı uygulama katmanlarına nazaran bihayli zordur.

Diğer hemen hemen tüm RDMBS'lerde ve ayrıca MySQL'de saklı yordam için hata ayıklama yapılamıyor. Bu sorun için bazı geçici çözümler geliştirilmiş olsa da çok iyi oldukları söylenemez.

Saklı yordam yazmak tüm geliştiricilerin sahip olduğu temel yeteneklerin üzerinde bir yeteneğe ihtiyaç duyar. Karmaşık süreçler için fazlasıyla karmaşık yapıda prosedürler oluşturmak içi konu hakkında fazla bilgiye sahip olmak ve temel prosedürleri iyi bilmek gerekir.

Saklı yordamın yukarıda belirtildiği gibi avantajları ve dezavantajları vardır. Bu nedenle uygulama geliştirirken, saklı yordam kullanıp kullanmama konusunda bir denge sağlamak gerekir. Daha sonra bu konu ile ilgili pratik örneklere değinmeye çalışacağım.

Kolay gelsin,