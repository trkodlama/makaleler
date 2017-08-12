---
ID: 9984
post_title: >
  Unity Gelişmiş Input Sistemi (Mobil
  Destekli)
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/unity-gelismis-input-sistemi-mobil-destekli-9984.html
published: true
post_date: 2017-08-12 12:43:46
---
Hepinize yeniden merhabalar,

Son zamanlarda <strong>Input.GetAxis</strong> kullanan kodların <strong>Android</strong> cihazlarda nasıl çalıştırılabileceği ile ilgili çeşitli sorular alıyordum. Ben de bu konuda basit bir çözüm üretmeye çalıştım ve ortaya <strong>SimpleInput</strong> adını verdiğim bir sistem çıktı.

SimpleInput sistemi ile UI butonlarına dokunarak, dokunmatik ekranda parmağınızı sürükleyerek, joystick kullanarak veya klavye tuşlarını kullanarak Input.GetAxis’i simüle edebiliyorsunuz. Dilerseniz de biraz kod yardımıyla kendi input yöntemlerinizi de sisteme tanıtabiliyorsunuz.

Unitypackage linki: <a href="https://www.dropbox.com/s/wopvkfsuenw8wus/SimpleInput.unitypackage?dl=0">https://www.dropbox.com/s/wopvkfsuenw8wus/SimpleInput.unitypackage?dl=0</a> (<a href="https://drive.google.com/uc?id=0BwLax4zOZiIQWk82ZXlsX0NLems&amp;export=download">Alternatif link</a>)

Detaylar için yazının devamını okuyabilirsiniz…

Sistemin işleyişi Input.GetAxis’e çok benziyor. Öyle ki çoğu zaman kodlarınızdaki Input.GetAxis’leri <strong>SimpleInput.GetAxis</strong>‘e ve Input.GetAxisRaw’ları da <strong>SimpleInput.GetAxisRaw</strong>‘a çevirmek yeterli olacaktır. Bunun dışında tek yapmanız gereken, bu fonksiyonlara parametre olarak girdiğiniz axis’lerin (“Horizontal”, “Vertical”, “Mouse X” vs.) değerlerini nasıl alacaklarını belirlemek olacak: ekrandaki butonlarla mı, joystick’le mi yoksa dokunmatik ekranla mı gibi…

Paketle birlikte 4 tane hazır input scripti gelmekte: <em>SimpleInputButon</em>, <em>SimpleInputDokunmatikEkran</em>, <em>SimpleInputKlavye</em> ve <em>SimpleInputRealAxis</em>.
<h3>SimpleInputButon</h3>
<img class="aligncenter size-full wp-image-9985" src="https://www.trkodlama.com/wp-content/uploads/2017/08/simpleinputbuton.png" alt="" width="346" height="78" />

Herhangi bir UI elemanına verebilirsiniz. Butona basılı tutulduğu sürece, girilen <strong>Axis</strong>‘in değeri <strong>Deger</strong> olur. Örneğin Input.GetAxis(“Vertical”)’ı ekrandaki yukarı-aşağı butonlarıyla simüle etmek istiyorsanız önce Input.GetAxis(“Vertical”)’ı <strong>SimpleInput.GetAxis(“Vertical”)</strong>‘a çevirmeli, ardından yukarı yön butonuna SimpleInputButon component’i verip Axis’ini “<em>Vertical</em>” (tırnaksız), Deger’ini 1 yapmalı ve son olarak aşağı yön butonuna da SimpleInputButon component’i verip Axis’ini “<em>Vertical</em>“, Deger’ini -1 yapmalısınız.
<h3>SimpleInputDokunmatikEkran</h3>
<img class="aligncenter size-full wp-image-9987" src="https://www.trkodlama.com/wp-content/uploads/2017/08/simpleinputdokunmatikekran1.png" alt="" width="327" height="110" />

Dokunmatik ekranda parmak sürükleyerek input almaya yarar. Örneğin “<em>Mouse X</em>” ve “<em>Mouse Y</em>” axis’lerini simüle etmek için idealdir. Bu durumda sahnenizdeki herhangi bir objeye SimpleInputDokunmatikEkran component’i verip “<strong>X Axis</strong>“ini “<em>Mouse X</em>” ve “<strong>Y Axis</strong>“ini de “<em>Mouse Y</em>” yapmanız yeterlidir. Eğer “<strong>Ui Yoksay</strong>” seçeneğini işaretlerseniz ekrana dokunan herhangi bir parmak input verebilirken işaretlemezseniz de o zaman sadece ekrandaki boş bir yere tıklayan (bir UI elemanının üzerine tıklamayan) parmaklar input verebilir.
<h3>SimpleInputKlavye</h3>
<img class="aligncenter size-full wp-image-9988" src="https://www.trkodlama.com/wp-content/uploads/2017/08/simpleinputklavye.png" alt="" width="331" height="185" />

Klavye tuşları ile input alabilmeye yarar. <strong>Tus</strong>‘ta belirlenen klavye tuşuna basılı tutulduğu sürece <strong>Axis</strong>‘in değeri <strong>Deger</strong> olur.
<h3>SimpleInputRealAxis</h3>
<img class="aligncenter size-full wp-image-9989" src="https://www.trkodlama.com/wp-content/uploads/2017/08/simpleinputrealaxis1.png" alt="" width="331" height="180" />

Input.GetAxis ile kullandığınız axis’leri direkt SimpleInput’ta da kullanabilmenizi sağlar. Örneğin normalde klavyenin sol-sağ tuşları ve A-D tuşları Input.GetAxis(“Horizontal”)’a etki eder; eğer siz bu klavye input’una SimpleInput’tan da erişebilmek istiyorsanız bu component'in <strong>Axisler</strong>'ine "<em>Horizontal</em>"ı (tırnaksız) ekleyebilirsiniz.
<h3>SimpleInputJoystick (Bonus)</h3>
Bu component yukarıda paylaştığım <em>unitypackage</em> ile otomatik olarak gelmiyor çünkü bu kodun compile olabilmesi için projede, <a href="https://yasirkula.com/2016/06/17/unity-ui-dokunmatik-ekran-joystick-kullanimi-multi-touch-destekli/">daha önceki bir dersimde paylaştığım JoystickUI component’inin olması</a> gerekiyor. Joystick’in <strong>Vector2</strong> türündeki <strong>sonuc</strong> değişkeninin <strong>x</strong> ve <strong>y</strong> değerleri sırasıyla “<em>X Axis</em>” ve “<em>Y Axis</em>“e değer olarak gitmekte.

Bu script unitypackage ile gelmediği için, eğer kullanacaksanız projeye elle eklemeniz lazım:
<pre class="line-numbers"><code class="language-csharp">using UnityEngine;
 
public class SimpleInputJoystick : MonoBehaviour
{
    public JoystickUI joystick;
 
    [SerializeField]
    private string xAxis = "Mouse X";
    [SerializeField]
    private string yAxis = "Mouse Y";
 
    private SimpleInputAxis xInput = null;
    private SimpleInputAxis yInput = null;
 
    void Awake()
    {
        if( xAxis != null &amp;&amp; xAxis.Length &gt; 0 )
            xInput = new SimpleInputAxis( xAxis );
 
        if( yAxis != null &amp;&amp; yAxis.Length &gt; 0 )
            yInput = new SimpleInputAxis( yAxis );
    }
 
    void OnEnable()
    {
        if( xInput != null )
            xInput.AxisEkle();
 
        if( yInput != null )
            yInput.AxisEkle();
    }
 
    void OnDisable()
    {
        if( xInput != null )
            xInput.AxisCikar();
 
        if( yInput != null )
            yInput.AxisCikar();
    }
 
    void Update()
    {
        Vector2 joystickSonuc = joystick.sonuc;
 
        xInput.deger = joystickSonuc.x;
        yInput.deger = joystickSonuc.y;
    }
}</code></pre>
Bu kod vasıtasıyla aslında nasıl kendi input metotlarınızı sisteme tanıtabileceğinizi de görmüş oluyorsunuz. Yapmanız gerekenler kabaca şöyle:
<ul>
 	<li><strong>SimpleInputAxis</strong> türünde bir değişken oluşturmak</li>
 	<li><strong>Awake</strong> fonksiyonunda bu değişkeni<strong> new SimpleInputAxis(“axis ismi”);</strong> şeklinde initialize etmek</li>
 	<li><strong>OnEnable</strong> fonksiyonunda değişkenin <strong>AxisEkle</strong> fonksiyonunu çağırmak</li>
 	<li><strong>OnDisable</strong> fonksiyonunda değişkenin <strong>AxisCikar</strong> fonksiyonunu çağırmak</li>
 	<li>Gerektiği zaman (<em>Update</em> fonksiyonunda veya uygun gördüğünüz başka bir yerde) değişkenin <strong>deger</strong>‘ini güncellemek</li>
</ul>
Örneğin <strong>SimpleInputJoystick</strong> scripti, “<em>Mouse X</em>” axis’ine <strong>joystick.sonuc.x</strong>‘i ve “<em>Mouse Y</em>” axis’ine de <strong>joystick.sonuc.y</strong>‘yi değer olarak atmakta.

Umarım faydalı olur. Çok sıkıntı yaşarsanız belki çok basit bir örnek proje de paylaşabilirim. Daha sonra görüşmek dileğiyle!