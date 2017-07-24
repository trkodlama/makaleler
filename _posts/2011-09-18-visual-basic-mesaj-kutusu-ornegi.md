---
ID: 266
post_title: Visual Basic Mesaj Kutusu Örneği
author: prodigy
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/visual-basic-mesaj-kutusu-ornegi-266.html
published: true
post_date: 2011-09-18 02:15:09
---
Visual Basic dilinin gerek temellerini vererek gerekse nesnelerin ne işe yaradığını belirterek kafanızda bir altyapı oluşturmayı amaçladım. Bu bilgiler doğrultusunda basitten başlayarak birkaç örnek yapacağız. Sandığınızdan kolay ve zevkli olduğunu anlayacak ve bana hak vereceksiniz.

İlk olarak Commandbutton nesnesini yani button kullanacağız. Formu kendinize göre yükseklik, en, genişlik gibi özellikleri belirlemekte özgürsünüz. En çok zevk alacağınız noktalardan biride tasarımdır.

Command tuşuna basıldığında basit bir mesaj kutusu gösterelim. Bunun için:

- Forma 1 adet ebatlarını ve yerini kendiniz belirleyeceğiniz şekilde Command (button) oluşturun. Caption bölümüne yani tuşun başlığını "Mesajın nedir ?" metnini yazın. Genelde isim olarak karıştırabilirsiniz. Bu metni "Name" ayarına değil "Caption" ayarına yazmaya dikkat edelim.

- Tuşu oluşturduk ve ebatlarını yerini belirledikten sonra forma isim verme vs. gibi işlemleri tamamen kullanıcıya yani size bırakıyorum.

- Command tuşunun "Click" olayına yani tıklandığında ne yapılmasını istediğiniz olaya bir satır kod yazacağız. Bu olay için Command yani tuşa mouse ile klasör veya dosya açar gibi çift tıklamanız yeterlidir.

- Karşınıza gelecek olan kod bölümünde en yukarıda şöyle yazması gerekir "Private Sub Command1_Click()". Arada bir satır boşluk ve ardından şu yazmalıdır "End Sub". Burada Click olayı açılırken Private Sub kullanılmış. Her veya fonksiyon tanımladıktan sonra mutlaka "End Sub" veya "End Function" vs. gibi olayınıza ve işleminize göre bir son getirmelisiniz. Zaten siz getirmesenizde otomatik olarak gelecektir.

- Private Sub ve End Sub satırları arasındaki boş yere hiçbirşey silmeden ve değiştirmeden aşağıdaki kodu yazın.

<pre class="lang:vb decode:1 " >Private Sub Command1_Click()
MsgBox &amp;quot;Ben mesaj kutucuğuyum&amp;quot;
End Sub</pre>

- Bu kodu girdikten sonra projenizde yani Visual Basic ekranının en üstünde ikinci sırada bir toolbar vardır. Bu toolbarda play, pause, stop isimlerini karşılayan mavi resimler vardır. Projeniz çalışmadığından sadece play yani çalıştırma tuşu aktiftir. Eğer stop tuşuna basarsanız proje kapanır, pause tuşuna basarsanız projeniz duraklar.

- Play yani çalıştır tuşuna bastığınızda projeniz çalışacak ve karşınıza oluşturduğunuz form gelecektir. Formunuzda başlığını belirlediğiniz Command yani bir tuş bulunması gerekir. Bu tuşa tıklamanızı istiyorum. Tıkladığınızda başlığı "Project1" olan herhangi bir resim olmayan (information resmi, error resmi, uyarı resmi, soru resmi olmayan) bir mesaj kutucuğu çıkacak ve mesajın içeriğinde ise "Ben mesaj kutucuğuyum" metni yazacaktır.

- Bu örnekte kullandığımız msgbox, küçük yazsanızda MsgBox olarak değişecektir. Çünkü bu bir fonksiyondur. Tanımlandığı için nasıl ismi belirlenmişse siz nasıl yazarsanız yazın belirlenmiş fonksiyon ismi olarak belirecektir. Örneğin msgbox'un MsgBox olması.

- Hazır fonksiyonumuz yani msgbox fonksiyonunun basit bir halinin bulunduğu bir örnekti. Başlığını, Hangi buttonların olacağını (Evet, Hayır, İptal vb.) ve mesaj resimlerini iki satır kod yazarak gerçekleştirebilirsiniz. Bunun için değişken tanımlayacağız ve tipini, içerisine metin atayacağımız için "String" olarak belirleyecek ve değişkenimize değer atayacağız.

<pre class="lang:vb decode:1 " >Private Sub Command1_Click()
Dim message As String
message = MsgBox(&amp;quot;clairvoyant&amp;quot;, vbOkOnly + vbCritical, &amp;quot;Bu bir hata resimli mesajdır&amp;quot;)
End Sub</pre>

- Burada msgbox fonksiyonunu ayrıntılı bir şekilde kullandık. MsgBox'tan sonra parantez açtığınızda projenizde size sarı bir kutucuk yardım edecektir. Her "," kullandığınızda sağdaki açıklama koyu hale gelecektir. En başta kullandığımız "clairvoyant" mesajımızın başlığıdır. vbOkOnly komutunu sade kullanabilirdik. Bu komut mesaj kutusunda sadece Ok yani Tamam tuşunun olacağınız gösterir. Zaten ","'den sonra boşluk bıraktığınızda karşınıza projenizde bir liste açılacaktır. O listeden vbYesNo, vbOkOnly vb. seçebilirsiniz. "+" yazarak bu tuşa ek olarak mesaj kutusunda gözükecek resimi belirlemiş olduk. Bu her zaman belirlenen tuş bölümünden sonra "+" yazılarak kullanılır. burdaki komutumuz vbCritical hata mesajı gibi kırmızı bir daire içerisinde kalın bir "X" işareti yani bildiğimiz hata mesajı resmidir. "+" yazdıktan sonra boşluk bıraktığınızda karşınıza gene bir liste açılacaktır. Burdan vbInformation, vbCritical, vbExclamation, vbQuestion vb. gibi resimleri seçebilirsiniz.

- Dikkat edelim kendi yazdığımız metinleri "" (tırnak) arasına her zaman almalıyız. Eğer bit nesnedeki değer veya sayı ise kullanmamıza gerek yok.

- Projenizi önceki örnekteki gibi çalıştırınız. Tuşa tıkladığınızda resmi, mesaj kutusunun başlığını ve mesajın içeriğini ayarladığımız gibi olduğunu göreceksiniz.

- Örneğimizi daha da geliştirecek olursak, mesela iki tane Textbox oluşturalım biri mesajın başlığını diğeri de mesajın içeriğini belirleyecek. Buttona tıkladığımızda başlık olarak birinci Textbox'a girilen metni gösterecek, mesajın içeriği ise ikinci Textbox'a girilen metni gösterecek.

- Bunun için önce forma 1 adet Command (button), 2 tane de Textbox ekleyeceğiz. İsimleri şöyle olmalı Command1, Text1, Text2. İsterseniz "Name" ayarından değiştirebilirsiniz. İsmi değiştirirseniz kodlamadaki Command1, Text1 ve Text2 nesnelerinin isimlerinide değiştirmelisiniz.

<pre class="lang:vb decode:1 " >Private Sub Command1_Click()
Dim message As String
message = MsgBox(Text1.Text, vbOkOnly + vbExclamation, Text2.Text)
End Sub</pre>

- Yukarıdaki kodda başlık için text1 değerini, içerik için text2 değerini kullandık. Text1.Text kodu ise text1 yani metin kutusunun metnini kullandık. Text1.Text metin kutusunun değeri, metni anlamına geliyor. Böylece kullanıcıya imkan sundunuz. Yani mesaj başlığını ve mesaj içeriğini kullanıcı belirleyecek. Az önceki diğer örnekte ise kullanıcı sadece sizin belirlediğiniz başlıklı ve içerikli mesajı görüyordu. Aradaki fark bu.

- Sadece Text1 kullanırsak yanlış olur, proje sadece o nesneyi yani Text1 nesnesini başlık olarak koymaya kalkar ve hata olur. Dikkat edelim.

- Projeyi çalıştırdığınızda Text1 ve Text2 kutucuğuna değerler girin. Command buttonuna bastığınızda text1 metin kutucu mesaj kutusunun başlığı, text2 kutucuğu ise mesaj kutusunun içeriği olacaktır.

Diğer örneklerimizde görüşmek üzere. Kodları inceleyin ve geliştirmeye çalışın. Kendiniz de örnekler yapabilirsiniz. Püf nokta şudur; bir örnek veya proje yapacaksanız önce bu projenin mantığını çıkarın, mantığı öğrenin ve sonra projeyi kodlamaya, tasarlamaya başlayın.

(Makale 2010 yılında tarafımdan hazırlanmıştır).