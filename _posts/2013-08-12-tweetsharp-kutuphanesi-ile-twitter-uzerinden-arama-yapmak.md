---
ID: 2290
post_title: >
  TweetSharp Kütüphanesi İle Twitter
  Üzerinden Arama Yapmak
author: Yiğit Can TÜRE
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/tweetsharp-kutuphanesi-ile-twitter-uzerinden-arama-yapmak-2290.html
published: true
post_date: 2013-08-12 19:23:03
---
TweetSharp Kütüphanesi ile twitter üzerinden arama yapmak için ilk önce  <a title="twitter developers" href="https://dev.twitter.com/" target="_blank">dev.twitter.com</a> adresine twitter adresimiz ile giriş yapıyoruz. Daha sonra resimdeki adımları izliyoruz.

<a href="http://www.trkodlama.com/wp-content/uploads/2013/08/tweetsharp1.png"><img class="size-medium wp-image-2291 aligncenter" src="http://www.trkodlama.com/wp-content/uploads/2013/08/tweetsharp1-300x189.png" alt="tweetsharp1" width="300" height="189" /></a>

Developer Rules Of The Road belgesini onayladığımızı belirtiyor ardından CAPTCHA ile insan olduğumuzu belirtiyoruz ve Create your Twitter application butonuna tıklıyoruz.
Resimde benim Uygulama adım ve website url formatım yanlış şekilde verilmişti. Uygulama adında noktalama işaretleri ve "Twitter" kullanmak yasak. Url belirtirken de http:// etiketini koymayı unutmuyoruz.
Şimdi bize gerekli bir kaç işlem daha kaldı. onları da resim üzerinden halledelim;

<a href="http://www.trkodlama.com/wp-content/uploads/2013/08/tweetsharp2.png"><img class="size-medium wp-image-2292 aligncenter" src="http://www.trkodlama.com/wp-content/uploads/2013/08/tweetsharp2-300x235.png" alt="tweetsharp2" width="300" height="235" /></a>

<strong>Adım 1:</strong> Settings Sekmesine Geçiyoruz.
<strong>Adım 2: </strong>Application Type kısmındaki Access'i Read and Write olarak belirliyoruz <strong>*</strong>
<strong>Adım 3:</strong> Update this Twitter application's settings butonuna tıklayarak değişiklikleri kaydediyoruz.
<strong>Adım 4:</strong> Details Sekmesine geri dönüyoruz.
<strong>Adım 5:</strong> En alttaki Create my access token butonuna tıklıyoruz.
<strong>Adım 6:</strong> Bize gerekli olan Consumer key ve secret
<strong>Adım 7: </strong>Access token ve token secret.

İşlemimiz için ön hazırlık tamam. Şimdi <strong>Visual Studio</strong> ile yeni <strong>WindowsFormsApplication</strong> açıyoruz.<strong> C#</strong> dilini kullanıyorum ben.
<strong>Solution Explorer</strong>da yer alan <strong>References</strong>'e sağ tıklayıp <strong>Manage NuGet Packages</strong> diyoruz. <strong>Search</strong> kısmına <strong>TweetSharp</strong> yazıp aratıyoruz ve <strong>TweetSharp</strong>'ı projemize dahil ediyoruz.
İşlem başarıyla sonuçlandığında <strong>References</strong> klasörünün altında<strong> TweetSharp</strong> gözükecektir.

Form tasarımımıza bir göz atalım. Yapacağımız işlem aradığımız kelime ya da kişi  ile ilgili tweetleri çekip göstermek bunun için 1 tane textbox, 1 adet buton , 2 adet radio buton, ve bir list box kullanağız. Tasarım şu şekilde oluşturdum;

<a href="http://www.trkodlama.com/wp-content/uploads/2013/08/tweetsharp3.png"><img class="size-medium wp-image-2293 aligncenter" src="http://www.trkodlama.com/wp-content/uploads/2013/08/tweetsharp3-300x176.png" alt="tweetsharp3" width="300" height="176" /></a>

Ben kontrollerin isimlerini unutmamak için düzenledim. txtAra,btnAra,rbtnHashtag,rbtnHuman,lstTweets şeklinde gayet neyin ne olduğu belli . Kod kısmına geçelim şimdi de;

<strong>Öncelikle bir TwitterService oluşturuyoruz. </strong>
<pre class="prettyprint lang-csharp" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">TwitterService servis;
public Form1()
{
    InitializeComponent();
    servis = new TwitterService(ConsumerKey, ConsumerSecret,AccessToken,AccessTokenSecret);
}
</pre>
Projeye hazırlanma aşamasında dev.twitter.com üzerinden aldığımız Key ve Secret değerlerini giriyoruz. Code bloğunda görüldüğü gibi.TwitterService kullanmak için TweetSharp kütüphanesini namespacelerimize eklemeyi unutmuyoruz tabiki.

<strong>Şimdi arama butonumuza gelelim;</strong>
<pre class="prettyprint lang-csharp" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">private void btnAra_Click(object sender, EventArgs e)
{
    lstTweets.Items.Clear();
    if (txtAra.Text != String.Empty)
    {
        if (rbtnHashtag.Checked)
        {
            string aranan = "#" + txtAra.Text;
            var AramaAyari = new SearchOptions { Q = aranan, Count = 25 };
            var Ara = servis.Search(AramaAyari);
            foreach (var i in Ara.Statuses)
            {
                var Tweets = String.Format("{0} diyor ki: '{1}'", i.User.ScreenName, i.Text);
                lstTweets.Items.Add(Tweets);
            }

        }
        else if (rbtnHuman.Checked)
        {
            string aranan = txtAra.Text;
            var AramaAyari = new SearchForUserOptions { Q = aranan, Count = 25 };
            var Ara = servis.SearchForUser(AramaAyari);
            foreach (var i in Ara)
            {
                var Kullanıcılar = String.Format("{0} kullanıcısının;{1} takipçişi ve {2} tweeti bulunmakta ", i.ScreenName, i.FollowersCount, i.StatusesCount);
                lstTweets.Items.Add(Kullanıcılar);
            }
        }
        else
        {
            MessageBox.Show("Ne ile arama yapacağınızı seçin lütfen", "Hata", MessageBoxButtons.OK, MessageBoxIcon.Error);
        }
    }
    else
    {
        MessageBox.Show("Arayacağın kelimeyi yazmayı unuttun herhalde?", "Hata", MessageBoxButtons.OK, MessageBoxIcon.Error);
    }
}</pre>
İlk önce ListBoxımız içini boşaltıyoruz. Daha sonra Textboxımızın dolu olduğuna emin olduğumuzda hangi radiobuton seçilmiş ona bakıyoruz. Bunlar basit olan işlemlerdi. Birazda kütüphane fonksiyonundan neler ile uğraşmışız ona değinelim.

<strong>SearchOptions : </strong>Adı üzerinde arama ayarları. 8 tane parametre alabiliyor. Biz sadece Q ve Count parametrelerini kullandık. Q anahtarımız aradığımız kelimeyi yazdığımız yer diyelim. Count da kaç adet tweet çekicek isek onun sayısı. Ben 25 tweet/Kullanıcı yeterli diye düşündüm ve 25 değerini verdim.
<strong>servis.Search(SearchOptions) : </strong>Arama ayarlarına göre arama yap dediğimiz kısım. Daha önceden girdiğimiz arama ayarlarına göre arama işlemini gerçekleştiriyor.
<strong>Ara.Statuses :</strong> Bu işlem ile atılan tweetlere erişiyoruz.
<strong>SearchForUserOptions : </strong>SearchOptions ile aynı işlevi görüyor. Fakat kullanıcı arıyor.
servis.SearchForUser(SearchForUserOptions): Arama ayarlarına göre kullanıcı araması yapıyor.
foreach döngülerinin içersindeki <strong>"i"</strong> parametrelerinin içindeki özellikleri ve methodları inceleyiniz.
Ben sadece ;
Hashtag arama için <strong>ScreenName</strong>: Ekran adı, <strong>Text</strong> : Tweet texti kullandım.
Kullanıcı arama için <strong>ScreenName</strong>: Ekran adı, <strong>FollowersCount</strong>: Takipçi sayısı , <strong>StatusesCount</strong> : Tweet sayisi özelliklerini kullandım.

<strong>Uygulamamamızı çalıştıralım ve görelim;</strong>

<a href="http://www.trkodlama.com/wp-content/uploads/2013/08/tweetsharp4.png"><img class="size-medium wp-image-2294 aligncenter" src="http://www.trkodlama.com/wp-content/uploads/2013/08/tweetsharp4-254x300.png" alt="tweetsharp4" width="254" height="300" /></a>

&nbsp;

Umarım bu makale yararlı olmuştur.

(* Başka bir uygulama ile Tweet atma işlemi yapıcak olursak diye Access'i Read and Write olarak belirledik.)