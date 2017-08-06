---
ID: 60
post_title: 'jQuery ile URL&#8217;deki Parametreleri Değerleri ile Birlikte Alma'
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/jquery-ile-url-parametre-ve-degerlerini-cekin-60.html
published: true
post_date: 2010-07-16 07:46:19
---
Bir çoğumuz bir proje üstünde çalışırken PHP ile oluşturulmuş linklerdeki parametre ve değerleri çekmek isteriz. Bunun için Roshambo'nun snipplr'da paylaştığı JavaScript kodu işimizi görecektir.
<pre class="line-numbers"><code class="language-javascript">function getUrlVars()
{
    var vars = [], hash;
    var hashes = window.location.href.slice(window.location.href.indexOf('?') + 1).split('&amp;');
    for(var i = 0; i &lt; hashes.length; i++)
    {
        hash = hashes[i].split('=');
        vars.push(hash[0]);
        vars[hash[0]] = hash[1];
    }
    return vars;
}</code></pre>
Bu fonksiyon URL parametreleriyle değerlerini bir dizi halinde getirir. Örneğin şu link için deneyelim: <em>http://www.example.com/?me=myValue&amp;name2=SomeOtherValue</em> adresi için <code>getUrlVars()</code> çağırdığımızda aşağıdaki diziye ulaşırız:
<pre class="line-numbers"><code class="language-json">{
    "me" : "myValue",
    "name2" : "SomeOtherValue"
}</code></pre>
İlk parametredeki değeri almak için aşağıki gibi çalıştırın fonksiyonu:
<pre class="line-numbers"><code class="language-javascript">var first = getUrlVars()["me"];

// İkinci parametreyi almak içinse
var second = getUrlVars()["name2"];</code></pre>
Bu kodların jQuery için yoğurulmuş son halide aşağıdaki gibidir:
<pre class="line-numbers"><code class="language-javascript">$.extend({
    getUrlVars: function(){
        var vars = [], hash;
        var hashes = window.location.href.slice(window.location.href.indexOf('?') + 1).split('&amp;');
        for(var i = 0; i &lt; hashes.length; i++)
        {
            hash = hashes[i].split('=');
            vars.push(hash[0]);
            vars[hash[0]] = hash[1];
        }
        return vars;
    },
    getUrlVar: function(name){
        return $.getUrlVars()[name];
    }
});</code></pre>
Yukarıdaki kodu javascript dosyanıza eklerseniz URL parametre ve değerlerini aşağıdaki gibi alabilirsiniz:
<pre class="line-numbers"><code class="language-javascript">// URL Parametrelerini alalım
var allVars = $.getUrlVars();

// URL Parametre değerlerini alalım
var byName = $.getUrlVar('name');</code></pre>

Umarım faydalı olur, kolay gelsin,