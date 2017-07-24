---
ID: 38
post_title: Web Sitenize IE 6 İle Girilmesin
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/web-sitenize-ie-6-ile-girilmesin-38.html
published: true
post_date: 2009-06-12 07:21:50
---
Web tasarımı yapan herkesi fazladan uğraştıran ilkel tarayıcı IE 6 ile sitenize girilmesini rahatlıkla engelleyebilirsiniz.
Web tasarımcılar iyi bilirler ki hazırladıkları şablonlar IE'nin son sürümlerinde, Firefox ve diğer tarayıcılarda sorunsuz çalışırken IE 6 her zaman problemler çıkarır ve tasarımcıların bu problemleri düzeltmek için her zaman daha fazla çalışmalarına sebep olur. Bu da hem zaman kaybı hem de çok sıkıcı bir iştir.
Aşağıdaki kodu sayfalarınızın en üstüne ekleyerek sitenize IE 6 ile girişi engelleyebilirsiniz.
[sourcecode lang="php"]&lt;?php  
$kontrol = $_SERVER[&quot;HTTP_USER_AGENT&quot;]; // Kullanıcının tarayıcı bilgisini çekiyoruz.  
$kontrol = substr($kontrol,0,33); // Tarayıcı bilgisinin ilk 33 karakterini çekiyoruz  
if($kontrol == &quot;Mozilla/4.0 (compatible; MSIE 6.0&quot;){   
   // Tarayıcı bilgisinin ilk 33 karakteri Mozilla/4.0 (compatible; MSIE 6.0 ise  
   //ie6.html sayfasına yönlendiriyoruz kullanıcıyı.  
   header(&quot;Location:ie6.html);    
   die();  
}  
?&gt;[/sourcecode]