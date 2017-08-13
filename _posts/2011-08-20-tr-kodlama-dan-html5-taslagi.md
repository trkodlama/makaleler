---
ID: 230
post_title: 'TR Kodlama&#8217;dan HTML5 Taslağı'
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/web-tasarim-2/tr-kodlama-dan-html5-taslagi-230.html
published: true
post_date: 2011-08-20 00:23:03
---
Merhaba arkadaşlar,

Daha önce sizlere HTML5 hakkında kısa bir bilgi vermiştim. Bugün de sizlere hazır bir HTML5 taslağı veriyorum. Bu taslak sayesinde birçok işlemden anında feragat edebileceksiniz.

Aşağıdaki HTML5 Taslağı sayesinde yeni bir sayfa oluşturduğunuzda içini doldurmak için ekstra zaman kaybetmeyeceksiniz. Aşağıdaki taslak üzerinden html tasarımınıza rahatlıkla başlayabilirsiniz. Kullanılan etiketler hakkında kısa açıklamalarda da bulundum.

İşte HTML5 taslağı:

<pre class="lang:xhtml decode:true prettyprint lang-html  ">&lt;!DOCTYPE HTML&gt;
&lt;html lang="tr"&gt;
    &lt;head&gt;
        &lt;meta charset="utf-8" /&gt;
        &lt;title&gt;www.trkodlama.com&lt;/title&gt;
        &lt;script src="http://ajax.googleapis.com/ajax/libs/jquery/1.6.2/jquery.min.js"&gt;&lt;/script&gt;
        &lt;script src="http://html5shim.googlecode.com/svn/trunk/html5.js"&gt;&lt;/script&gt;
        &lt;link rel="stylesheet" href="stil.css" /&gt;
        &lt;meta name="generator" content="http://www.trkodlama.com"&gt;
    &lt;/head&gt;
    &lt;body&gt;
        &lt;section&gt;
        &lt;!-- section etiketi sayfanızı bölümlendirmeye yarar --&gt;
            &lt;header&gt;
            &lt;!-- header etiketi sayfalarınızın başlık kısımlarını belirtir --&gt;
                &lt;nav&gt;
                &lt;!-- nav etiketi menülerinizin bulunduğu kısmı belirtir --&gt;
                &lt;/nav&gt;
            &lt;/header&gt;
        &lt;/section&gt;
        &lt;section&gt;
            &lt;article&gt;
            &lt;!-- article etiketi yazı alanlarını belirtmek için kullanılır --&gt;
            &lt;p&gt;TR Kodlama &lt;/p&gt;
            &lt;p&gt;Güncel Programlama Makaleleri&lt;/p&gt;
            &lt;figure&gt;
            &lt;!-- figure etiketi resim eklemenizi sağlar --&gt;
                &lt;img src="resim.png" /&gt;
                &lt;figcaption&gt;Deneme resim&lt;/figcaption&gt;
                &lt;!-- figcaption etiketi resime açıklama eklemek için kullanılır --&gt;
            &lt;/figure&gt;
        
            &lt;small&gt;Küçük yazım&lt;/small&gt;&lt;!-- small etiketi yazıyı herhangi bir stil belirtmeden küçük yazdırmanızı sağlar --&gt;
            &lt;mark&gt;Vurgulu www.trkodlama.com&lt;/mark&gt;&lt;!-- mark etiketi yazılarınızı vurgulu yazmanızı sağlar --&gt;
            
        &lt;/article&gt;
        &lt;/section&gt;
        &lt;section&gt;
            &lt;aside&gt;
            &lt;!-- aside etiketi sağ ve sol bloklarınızı belirlemede kullanabilirsiniz --&gt;
            &lt;p&gt;TR Kodlama Forumu&lt;/p&gt;
            &lt;p&gt;Programlama Destek Forumu&lt;/p&gt;
            &lt;/aside&gt;
        &lt;/section&gt;
        &lt;section&gt;
        &lt;footer&gt;
        &lt;!-- footer etiketi sitelerinizin alt kısmıdır. nav etiketini burda da kullanabilirsiniz. --&gt;
            &lt;p&gt;http://www.trkodlama.com&lt;/p&gt;
        &lt;/footer&gt;
        &lt;/section&gt;
    &lt;/body&gt;
&lt;/html&gt;</pre>

Bu framework'ün çalışan demosuna <strong><a href="http://www.trkodlama.com/demo/html5_framework/index.html" target="_blank" rel="noopener">buraya tıklayarak</a></strong> ulaşabilirsiniz.

Umarım işinize yarar, kolay gelsin,