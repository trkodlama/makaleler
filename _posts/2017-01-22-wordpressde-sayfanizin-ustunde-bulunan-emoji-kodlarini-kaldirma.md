---
ID: 6308
post_title: 'WordPress&#8217;de Sayfanızın Üstünde Bulunan Emoji Kodlarını Kaldırma'
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/wordpressde-sayfanizin-ustunde-bulunan-emoji-kodlarini-kaldirma-6308.html
published: true
post_date: 2017-01-22 19:19:00
---
Hızlıca giriş yapıp sonuçlanacak ipucu niteliğinde bir yazı bu. WordPress 4.2 ile beraber sayfalarınızın üstüne şu kodları ekliyor WordPress:
<pre class="prettyprint lang-javascript" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">window._wpemojiSettings = {"baseUrl":"http:\/\/s.w.org\/images\/core\/emoji\/72x72\/","ext":".png","source":{"concatemoji":"http:\/\/wordpress-adresiniz.com\/wp-includes\/js\/wp-emoji-release.min.js?ver=4.2.1"}};
    !function(a,b,c){function d(a){var c=b.createElement("canvas"),d=c.getContext&amp;&amp;c.getContext("2d");return d&amp;&amp;d.fillText?(d.textBaseline="top",d.font="600 32px Arial","flag"===a?(d.fillText(String.fromCharCode(55356,56812,55356,56807),0,0),c.toDataURL().length&gt;3e3):(d.fillText(String.fromCharCode(55357,56835),0,0),0!==d.getImageData(16,16,1,1).data[0])):!1}function e(a){var c=b.createElement("script");c.src=a,c.type="text/javascript",b.getElementsByTagName("head")[0].appendChild(c)}var f;c.supports={simple:d("simple"),flag:d("flag")},c.supports.simple&amp;&amp;c.supports.flag||(f=c.source||{},f.concatemoji?e(f.concatemoji):f.wpemoji&amp;&amp;f.twemoji&amp;&amp;(e(f.twemoji),e(f.wpemoji)))}(window,document,window._wpemojiSettings);</pre>
<pre class="prettyprint lang-css" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">img.wp-smiley,
img.emoji {
    display: inline !important;
    border: none !important;
    box-shadow: none !important;
    height: 1em !important;
    width: 1em !important;
    margin: 0 .07em !important;
    vertical-align: -0.1em !important;
    background: none !important;
    padding: 0 !important;
}</pre>
Emoji ikonlarını kullanmak istemiyorsak bunların yüklenmesinin önüne geçmek için kullandığının temanın <strong>functions.php</strong> dosyasını açın ve aşağıdaki kodları ekleyin dosyaya:
<pre class="prettyprint lang-php" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="functions.php">&lt;?php
// WP EMOJI'leri kaldırır
// www.trkodlama.com
remove_action('wp_head', 'print_emoji_detection_script', 7);
remove_action('wp_print_styles', 'print_emoji_styles');

remove_action( 'admin_print_scripts', 'print_emoji_detection_script' );
remove_action( 'admin_print_styles', 'print_emoji_styles' );
?&gt;</pre>
Faydalı olur umarım, kolay gelsin,