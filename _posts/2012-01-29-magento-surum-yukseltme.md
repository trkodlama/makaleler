---
ID: 279
post_title: Magento Sürüm Yükseltme
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/magento-surum-yukseltme-279.html
published: true
post_date: 2012-01-29 02:33:48
---
Merhaba arkadaşlar,

Bu makalemde her yaptığınız işlemde korkulu rüyanız olan Magento'yu nasıl son sürüme güncelleyeceğinizi anlatıyorum..

Öncelikle Magento Connect Manager adresine gidin. Alan adınızın domain.com olduğunu sayarsak ve Magento'yu da direkt olarak domain.com'a kurduğunuzu düşünürsek Magento Connect Manager'a http://www.domain.com/downloader adresinden ulaşabilirsin. Karşınıza bir giriş ekranı gelecektir. Bu ekrana admin giriş bilgilerinizi girip giriş yapıyorsunuz.

Daha sonra "<strong>Check for Upgrades</strong>" butonuna basın.. Güncellemesi bulunanların arka planı sarı renkli olmak üzere bir liste çıkacak karşınıza. Bu listede bir option list göreceksiniz. Burda şu sürüme güncelle, reinstall ve uninstall seçenekleri mevcut. Burdan en son sürüme güncellemesini seçiyorsunuz bütün hepsi için.. Bunu tek tek yapıyorsunuz. Ayrıca bu tablonun üst sağ köşesinde bulunan "Clear all sessions after successfull install or upgrade" kutucuğunu işaretleyin. Daha sonrada "<strong>Commit Changes</strong>" butonuna tıklayın. Güncelleme işleminiz gerçekleşti..

Bu adımlar çok yorucu olduysa daha kısa bir yöntem mevcut. Yine aynı sayfada "<strong>Paste extension key to install</strong>" kutucuğuna "<strong>community/Mage_All_Latest</strong>" yazın. Karşınıza farklı bir tablo gelecek. Bu tablonun hemen altında ise "<strong>Proceed</strong>" butonu mevcut. Bu butona tıklıyoruz ve yüklememizi gerçekleştiriyoruz. Fakat bu işlemin sonunda web sitenizin ana dizininde "<strong>maintenance.flag</strong>" isimli bir dosya oluşur. Siz bu dosyayı bir FTP programı aracılığıyla silmedikten sonra sitenize erişemezsiniz.

Güncellemede bazı paketlerde problemler oluşabilir. Bu problemleri şu şekilde kontrol edebilirsiniz. İlk anlattığım adımı tekrarlarsınız, eğer arka planı sarı olan bir paket yoksa kurulumunuz başarılı ile gerçekleşmiş demektir. Artık tek yapmanız gereken yönetici paneline giderek önbelleğ tazelemek ve indeksleri yenilemek olacaktır. Eğer bu iki işlemi yapmazsanız güncellemeden sonra bazı sayfalara erişmeden hata alabilirsiniz.

<strong>Dikkat: </strong>Bu güncelleme ile mevcut modifikasyonlarınızın tamamı etkilenme riski altındadır. Magento dosyalarında yaptığınız bütün değişiklikleri yeniden yapmak zorunda kalabilirsiniz.

Eğer Magento Connect Manager ile güncellemede problem yaşarsanız bu sefer imdadınıza SSH yetişiyor. Eğer SSH paneline erişiminiz yoksa bunun için Cronjob'u kullanabilirsiniz. Bunu nasıl yapacağınızı internette araştırın lütfen.

SSH ile Magento'nuzun kurulu olduğu dizine gelin ve aşağıdaki komutu çalıştırın:

[sourcecode]./mage install http://connect20.magentocommerce.com/community Mage_All_Latest --force[/sourcecode]

Eğer bu komutu çalıştırdığınız zaman <strong>./mage: Permission denied</strong> şeklinde bir uyarı alırsanız aşağıdaki komutu çalıştırın daha sonra tekrar yukarıdaki komutu çalıştırmayı deneyin:

[sourcecode]chmod 550 mage[/sourcecode]

<strong>Dikkat:</strong> Lütfen bu işlemleri yapmadan Magento kurulumunuzu veritabanı dahil yedeklemeyi unutmayın. Yedekleme işlemleri uzun ve zahmentli işlemler fakat bir problemle karşılaşırsanız Magento'nuzu geri getirmek size pahalıya mal olabilir.