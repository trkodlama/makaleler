---
ID: 244
post_title: >
  Klasördeki Resimleri Gösterme,
  Sayfalama ve Link Verme
author: damatmedya
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/uyelerimizden-klasordeki-resimleri-gosterme-sayfalama-ve-link-verme-244.html
published: true
post_date: 2011-09-05 01:02:32
---
Klasördeki resimleri bir tablo içinde listeleyen ve sayfalayan bir sistem, klasör içindeki bütün resimleri çeker.
Not: Klasördeki bütün dosyaları çektiğinden dolayı klasörde varsa "Thumbs.db" dosyasınıda listeler.
<pre class="prettyprint lang-php" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;table width="750" bgcolor="#f4f4f4" border="0" cellspacing="0" cellpadding="8" align="center"&gt;
	&lt;tr&gt;
		&lt;td valign="top"&gt; 
			&lt;center&gt; 

			&lt;?php 
			// resimleri çekme alanı
			$dizin = "klasoradi/"; // resminizin bulunduğu yolu yazınız örn: " klasor/ "
			$tutucu = opendir($dizin); // dizin aç
			while($dosya = readdir($tutucu)){ 
				if(is_file($dizin.$dosya)) 
					$resim[] = $dosya; 
				} 
				closedir($tutucu); 

				// ön bilgiler 
				$limit = 10; // sayfada gösterilecek resim sayısı
				$sf = @$_GET["sf"]; // get metodu ile sayfa numarasını alma // get başındaki '@' işareti sayfa numarası yok ise hata vermesini önler
				if($sf &lt; 1) $sf = 1; 
				$toplam = count($resim); // toplam resim sayısı

				// bu bilgiler doğrultusunda sayfa ayarları
				$kactan = ($sf-1) * $limit; 
				$kaca = ($kactan+$limit); 
				if($kaca &gt; $toplam) $kaca = $toplam; 

				// $kactan başlayıp $kaca kadar resim basar
				for($i=$kactan; $i &lt; $kaca; $i++){ 
					echo " 
						&lt;a href='".$dizin."/".$resim[$i]."' target='_blank'&gt; 
							&lt;img onContextMenu='return false' src='".$dizin.$resim[$i]."' width='100' height='100' border='0'&gt;&lt;/a&gt; "; 
				} 
				//dizindeki resimleri listeler ve yeni sekmeye link olarak atar
				// onContextMenu='return false' kodu resime sağ tıklamasını engeller

				// birden başlayıp sayfa sayısı kadar link basar
				echo "&lt;br&gt;";
				$lastP = ceil($toplam/$limit); // ceil komutu sayfa numaraları yuvarlamak için kullanılır örn: ceil(0.40) gibi bir değeri 1 olarak alır
				for($i=1; $i &lt;= $lastP; $i++){ 
					if($sf == $i) {
						echo $i." "; // geçerli olan sayfa numarası
					}else{ 
						echo "&lt;a href='index.php?sf=$i'&gt;$i&lt;/a&gt; "; // diğer sayfa numaraları
					}
				}
			?&gt; 

			&lt;/center&gt;
		&lt;/td&gt;
	&lt;/tr&gt;
&lt;/table&gt;</pre>
&nbsp;