---
ID: 262
post_title: Visual Basic Temel Bilgiler
author: prodigy
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/visual-basic-temel-bilgiler-262.html
published: true
post_date: 2011-09-17 02:11:54
---
Visual Basic basit ve zengin bir programlama dilidir. En başta tasarımdan başlayalım. Bu iş tamamen size kalmış. Visual Basic bu konuda sizere yardımcı olmak için sadece formunuz ile ilgili bir kısım ayarlar vermiş. Bu ayarları kullanarak birbirinden güzel formlar oluşturabilirsiniz. Kodlamadan sonra en önemli etken tasarım yani göze hitaptır.

Visual Basic formunda "Caption" ayarı formunuzun başlığının yazıldığı ayardır. Bu ayarı değiştirebilirsiniz. Yeni bir Visual Basic projesi açtığınızda otomatik olarak forma "Form1" ismi verilir. Formun ikonunu değiştirmek isterseniz "Icon" ayarından belirlediğiniz ikonu bilgisayarınızdan seçebilirsiniz. Formdaki "Backcolor" ayarı ise formun arka rengini belirleyen ayardır. İstediğiniz gibi değiştirebilirsiniz. Formdaki bir başka ayar ise "Visible" ayarıdır. Bu ayar formun projeniz çalıştığında gözüküp gözükmemesi ile ilgilidir. Eğer Visible değeri "True" ise gözükür, "False" ise formunuz gözükmez. Aynı şey nesneler içinde geçerlidir.

Yukarıda verdiğimiz ufak tefek form ayarlarından sonra kalan bölümler örneklerden de anlaşılacağı gibi orta düzey İngilizce bilen birinin bu terimlerin anlamından o ayarın ne olduğunu anlayabilmesi olanaklıdır. Visual Basic için İngilizce bilmeniz gerekmektedir ki sıkıntı çekmeyesiniz ve kodları anlayabilesiniz.

Kodlarımızda kod tasarrufu ve hız açısından önemli olan değişkenleri kullanacağız. Bütün programlarda kullanılan "Değişkenler" projemizin vazgeçilmezleri arasında. Eğer hız istiyorsanuz bunu uygulamanız şarttır.

Geçelim değişkenlerimize. Değişkenleri tanımlarken onların hangi tür bir değişken olduğunu tanımlamak mümkün. Şöyle ki eğer bir metni bir değişkene atayacaksak kullanmamız gereken "String" tipidir. Örnek olarak "Dim değişken As String" yazarsanız değişken isimli değişkeninize metin atamanız gerekir. Sayı atayacak iseniz string tipi yerine "Integer" tipini kullanmanız gerekmktedir. Örnek verecek olursak "Dim sayi as Integer". Bu örnekte sayı isimli değişkenimiz –32768 ile +32767 arasında bir sayı olmalıdır. Eğer bu sayı aralığında değil ve daha büyük ise değişkenimizin tipi "Long" olmalıdır. Long daha büyük bir aralıktaki sayılar için kullanılacak olan bir veri tipidir. Örnek verecek olursak "Dim uzun As Long". Burda kullandığımız long veri tipi +2,147,483,647 ile -2,147,483,648 değerleri arasındadır. Eğer küsüratlı bir sayı ise tam sayı değilse kullanacağımız tip "Single" olmalıdır. Örnek verecek olursak "Dim kusurat As Single". Burda kullanılan single veri tipi negatif sayılar için -3.402823E38 ile –1.401298E-45 , pozitif sayılar için 1.401298E-45 ile 3.402823E38 değerleri arasındadır. Eğer kullanacağınız değişkende en büyük veri tipini istiyorsanız "Double" tipini kullanmalısınız. Örnek verecek olursak "Dim buyuk As Double". Bu örnekte kullandığımız double veri tipi pozitif sayılar için 4.94065645841247E-324 ile 1.797693134862232E308, negatif sayılar için ise -1.797693134862232E308 ile -4.94065645841247E-324 değerleri arasındadır.

Değişkenlerimize kullanacağımız diğer bir veri tipi ise "Boolean" tipidir. Bu veri tipi diğerlerine oranla ne sayısal ne de metin içerebilir. Bu veri tipi sadece "True" yada "False" olarak cevap verir ve kendi içinde işlem yaptırılabilir. True = Doğru, False = Yanlış'tır.

Eğer bir formdan diğer formdaki nesneyi kullanmak istiyorsanız, kullanacağınız formda kodun en başına nesnenin bulunduğu formu, ardından "." koyup daha sonra kullanacağınız nesneyi ve ardından gerçekleştirmek istediğiniz işlemi yapmalısınız. Eğer kullanacağınız nesne formunuz üzerinde ise başına formun ismini yazmasınızda işleminiz gerçekleşecektir.

Nesneleri eklemek veya silmek için "Project/Components" bölümüne gelmeli, *.ocx dosya tipinde bulduğunuz ya da yazdığınız nesneler varsa "Browse" seçeneği ile ekleyebilir ve kullanmak istemediğiniz nesnelerin işaretini (tikini) kaldırabilirsiniz.

Kodlamada kullanacağınız ve zorlanabileceğiniz diğer bölüm ise Windows Apisi kullanmak ve çağırmaktır. Bu apilerin ne işe yaradığını bilmek ve ne gibi işlemler gerçekleştirdiğini bilmeniz gerekmektedir. Örnek verecek olursak "Private Declare Function SystemParametersInfo Lib "user32" Alias "SystemParametersInfoA" (ByVal uAction As Long, ByVal uParam As Long, ByVal lpvParam As Any, ByVal fuWinIni As Long) As Long" verebiliriz. Bu apileri içeren tüm kodlar her bilgisayarda çalışabilir. Ama bazı projeleriniz çalışmayabilir. Çünkü Visual Basic ile gelen nesneyi kullanmanızdan kaynaklanıyordur. Eğer o nesne dosyasını çalıştırdığınız proje ile aynı klasöre atarsanız hata almayacaksınız.

Diğer derslerde görüşmek üzere. Hızlı olarak hazırladım en ince ayrıntısına kadar girmeye uğraştım. Umarım başarılı bir makale olmuştur. Kolay gelsin.

(Makale 2010 yılında tarafımdan hazırlanmıştır).