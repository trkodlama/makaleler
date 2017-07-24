---
ID: 195
post_title: PHP ile Alan Adını Alma
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/php-ile-alan-adini-alma-195.html
published: true
post_date: 2011-06-18 19:46:54
---
Merhaba arkadaşlar,
URL'lerin sadece alan adlarını almak istediğiniz zamanlar olabilir. Fakat bazı durumlarda subdomain.domain.tld.tld yapısındaki URL'lerden domain kısmını çekmek zorlaşır.. Aslında zor değildir fakat o yapıyı bulmak zor olabilir Çünkü girilen URL'ler aşağıdaki formatlarda olabilir:
<ul>
	<li>http://www.trkodlama.com</li>
	<li>http://www.trkodlama.com.tr</li>
	<li>http://trkodlama.com</li>
	<li>http://trkodlama.com.tr</li>
	<li>http://sub.trkodlama.com</li>
	<li>http://sub.trkodlama.com.tr</li>
</ul>
Hal böyle olunca işin içinden çıkılmaz bir hal alır.. If else'ler havada uçuşur. Bunun için sizlerle basit ve kullanışlı bir fonksiyon paylaşıyorum:

<pre class="lang:php decode:1 " >function domain($url){
 $tld2 = array('wattle.id.au','emu.id.au','csiro.au','name.tr','conf.au','info.tr','info.au','gov.au','k12.tr','lel.br','ltd.uk','mat.br','jor.br','med.br','net.hk','net.eg','net.cn','net.br','net.au','mus.br','mil.tr','mil.br','net.lu','inf.br','fnd.br','fot.br','fst.br','g12.br','gb.com','gb.net','gen.tr','ggf.br','gob.mx','gov.br','gov.cn','gov.hk','gov.tr','idv.tw','imb.br','ind.br','far.br','net.mx','se.com','rec.br','qsl.br','psi.br','psc.br','pro.br','ppg.br','pol.tr','se.net','slg.br','vet.br','uk.net','uk.com','tur.br','trd.br','tmp.br','tel.tr','srv.br','plc.uk','org.uk','ntr.br','not.br','nom.br','no.com','net.uk','net.tw','net.tr','net.ru','odo.br','oop.br','org.tw','org.tr','org.ru','org.lu','org.hk','org.cn','org.br','org.au','web.tr','eun.eg','zlg.br','cng.br','com.eg','bio.br','agr.br','biz.tr','cnt.br','art.br','com.hk','adv.br','cim.br','com.mx','arq.br','com.ru','com.tr','bmd.br','com.tw','adm.br','ecn.br','edu.br','etc.br','eng.br','esp.br','com.au','com.br','ato.br','com.cn','eti.br','edu.au','bel.tr','edu.tr','asn.au','jl.cn','mo.cn','sh.cn','nm.cn','js.cn','jx.cn','am.br','sc.cn','sn.cn','me.uk','co.jp','ne.jp','sx.cn','ln.cn','co.uk','co.at','sd.cn','tj.cn','cq.cn','qh.cn','gs.cn','gr.jp','dr.tr','ac.jp','hb.cn','ac.cn','gd.cn','pp.ru','xj.cn','xz.cn','yn.cn','av.tr','fm.br','fj.cn','zj.cn','gx.cn','gz.cn','ha.cn','ah.cn','nx.cn','tv.br','tw.cn','bj.cn','id.au','or.at','hn.cn','ad.jp','hl.cn','hk.cn','ac.uk','hi.cn','he.cn','or.jp','name','info','aero','edu','org','int','biz','mil','net','com','ua','st','tw','sg','uk','au','za','yu','ws','at','us','vg','as','va','tv','pt','si','sk','ag','sm','ca','su','al','am','tc','th','tm','ro','tn','to','ru','se','sh','eu','dk','ie','il','de','cz','cy','cx','is','it','jp','ke','kr','la','hu','hm','hk','fi','fj','fo','fr','es','gb','eg','ge','ee','gl','ac','gr','gs','li','lk','cd','nl','no','cc','by','br','nu','nz','bg','be','ba','az','pk','ch','ck','cl','lt','lu','lv','ma','mc','md','mk','mn','ms','mt','mx','dz','cn','pl');
 $url_bolumleri = parse_url($url);
 $Domain = $url_bolumleri[&amp;quot;host&amp;quot;];
 $sayac = 1;
 do {
$tmp_tld = substr($Domain, -strlen(&amp;quot;.&amp;quot;.$tld2[$sayac]));
if ($tmp_tld == &amp;quot;.&amp;quot;.$tld2[$sayac]) {
$tld = ltrim($tld2[$sayac], &amp;quot;.&amp;quot;);
$DomainL = substr($Domain, 0, -(strlen($tld) + 1));
if (strpos($DomainL, &amp;quot;.&amp;quot;) === false) {
$subDomain = &amp;quot;&amp;quot;;
$sonDomain = $DomainL;
} else {
$Domain_bolumleri = explode(&amp;quot;.&amp;quot;, $DomainL);
$sonDomain = array_pop($Domain_bolumleri);
} return $sonDomain;
  }
  $sayac++;
 } while ($sayac &amp;lt; count($tld2));
}</pre>

Kullanımı da oldukça basittir:

<pre class="lang:php decode:1 " >echo domain(&amp;quot;http://subdomain.trkodlama.com.tr&amp;quot;); // Ekran &ccedil;ıktısı: trkodlama</pre>

Umarım faydalı olmuştur, kolay gelsin