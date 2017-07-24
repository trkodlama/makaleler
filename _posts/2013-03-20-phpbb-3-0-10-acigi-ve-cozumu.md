---
ID: 1512
post_title: phpBB 3.0.10 Açığı ve Çözümü
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/phpbb-3-0-10-acigi-ve-cozumu-1512.html
published: true
post_date: 2013-03-20 09:06:12
---
Merhaba arkadaşlar,

Bugün phpBB forumlarda rastlanan bir hata ile karşılaştım ve bu hatanın çözümünü sizlerle paylaşmak istiyorum. Açık spambot önlemlerinde bulunuyor. Kurulan eklentilerden <strong>"GD 3D Resmi"</strong> seçeneğini seçtiğiniz zaman resimler gözükmüyor.

Bu problemin hata çıktısı şu şekilde gözüküyor:

[text][phpBB Debug] PHP Warning: in file [ROOT]/includes/captcha/captcha_gd_wave.php on line 65: mt_rand() [function.mt-rand]: max(315) is smaller than min(355)
[phpBB Debug] PHP Warning: in file [ROOT]/includes/captcha/captcha_gd_wave.php on line 66: mt_rand() [function.mt-rand]: max(81) is smaller than min(96)
[phpBB Debug] PHP Warning: in file [ROOT]/includes/captcha/captcha_gd_wave.php on line 249: Cannot modify header information - headers already sent by (output started at [ROOT]/includes/functions.php:3876)
[phpBB Debug] PHP Warning: in file [ROOT]/includes/captcha/captcha_gd_wave.php on line 250: Cannot modify header information - headers already sent by (output started at [ROOT]/includes/functions.php:3876)
‰PNG  IHDRh<code>¿£[xIDATxœíÚO‹EÇñ»‡Þìl6Fð =(âÁK&lt; Š7B…‚ƒÉ!ßg_ƒWO¾A%‡xînOf˜jðP;µÕUÕ=õôŸÝüù~N»;³U==U¿~ºª'·nÜ›mŸUJ)¥–Ë'ºÒªÎ¾z2ÊùAK×Yž§7•gùºÍÃuƒ;G/IÚ±´ÖJ)ïm[¢FËEô ›˜CÍ²iU­ÌxŠâŒèšº0´ÖM'g¹|’ÒZŸãÉœ³QU:Ûtr”RóùÁöWowîÝäEqÆÌ„yyà¾°=;š´æUwÐTZïîž÷r'¼ç„£ÇÒ•ö¦¥MU±ÉÜçßg³ÈÛª•jÈ;ó’Ö:}•–k¦…¦_]Y6µ?—ó÷ôÚc+ËÈHHL/£Aéö¥µ.Š3ÕoÿÆö³×S:E“®þäT3¼9f¯Õž¥sýÔ•Ž¾mY¿ÆÚHjá]Ü¢Q%âåÚÆëüà²|ºùM šN~&quot;ïü7K¨A”emðÅ– *5´pÛÈÍ¸ªZ¹¿_¼9l_/ ÉÍëwÌO¦„®œo×¯^½qÌÕEk÷ýÞ8–Î /ªÜÒ'çZ¯¼?º©ýcû4pÓ§j¸þ8) ˜Q^™7XM×ÞDÞ§3C¤9VéUÃ¬ÖÃF›û¡²|šgyÓZ†®úÖ})ªØB’á^c¤wy–’¢ÆÞ ‘&amp;Q“K{Wì/)3áMÖÌúß¦Ï|~°,j´/Fšùl³I9I]¢mTy9•²êæLÛi	ÃÈ«°†­)–ËE–çîUÚÎ±•—ÑRY)i5êb–®t¥WY&gt;­ôÊû{Jœ¥}Æ©ZßXmôÊ×ï§¼íyun¤›ªk}å?.RšÁÉ&amp;ì_l/aYÒ];Ûµn\TJëq–WÑ“Léë™6¹´w¥óÚÛÆà°¼Õ2+z1_,ÑCÊó©¹?21á.¹·T(!Ió</code>ˆ„Q¥M+£¾ú³RÍßn/‚4i05ÜOt%Ü%‘žCÑX„i}QLuZ´N)^”RYž‡™òÚ7I»{:uŽôÔ0ÂìH\ÜjÚ“åyžI¶„‚?CÞ†¢»ùwÜfkT‰n…ŒÚ†wB‘¥º&amp;×º;oUÈ_Ãªuä|œô«wT˜ejýy[–0RÎ§h­4º(6’\§$-¸l‡o\¾˜ÒÎÓ<code>r÷öÏæììï?ÞÝ=ÿ×ß&amp;ÞãIƒÃ0ñ!úŽÓƒ£ÖQÃwÙ²aœxT™ó\™9u±§ædQÕÎÍgˆ‹‹¬Dþ^xZŠ}²L5ÇYswµX[ƒÜ‚yéÖ´Õ˜žnn•åá{×&gt;ªµÎ&amp;wnÞWýž2xôèŸ²&lt;é¡€n©a„ÙÑóˆÄî¼^œ'£êuÐúŒ5ÝÇ©Ø€‹ŽÎ£Õå†ñ-²1Ël¬„_(ËTý³ìï?Þ:Þg÷.])¹f¹UdK¿Ñ‡ÙÖ-L‹bË[,3g/q™ßk?OXš-Ëï}Ño}ÿIú›ÛGg=gã{ú‡aæó¨‘áõå¯_û¹Ú?</code>8+¢9Õ3÷[.¶ÑÒo¨ÓbgÑû[j 3{[R EËÌïpCêiÚùÞÁ «SC)5¹uã^ÊûÂGºÕ„Òg´¼U÷‡¨“Í‚šJñ:rUí=ö¼Uñ{,•RÞöól¶ÓÆF«¦dIÙ ì,ÌŽ”ÂM4û†Œ£H|_d…[/text]

Problemin çözümü için

[phpBB_Dizini]/includes/captcha/captcha_gd_wave.php</strong> dosyasında

<pre class="lang:php decode:1 " >				'x' =&amp;gt; mt_rand($img_x - 5, $img_x - 45),
				'y' =&amp;gt; mt_rand($img_y - 0, $img_y - 15)</pre>

satırlarını bulun ve bu satırları

<pre class="lang:php decode:1 " >				'x' =&amp;gt; mt_rand($img_x - 45, $img_x - 5),
				'y' =&amp;gt; mt_rand($img_y - 15, $img_y - 0),</pre>

bu şekilde değiştirin. Probleminiz giderilmiş olacaktır.