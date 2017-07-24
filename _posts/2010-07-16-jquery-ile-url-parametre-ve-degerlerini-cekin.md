---
ID: 60
post_title: >
  jQuery ile URL Parametre ve Değerlerini
  Çekin
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/jquery-ile-url-parametre-ve-degerlerini-cekin-60.html
published: true
post_date: 2010-07-16 07:46:19
---
Bir çoğumuz bir proje üstünde çalışırken PHP ile oluşturulmuş linklerdeki parametre ve değerleri çekmek isteriz. Bunun için Roshambo'nun snipplr'da paylaştığı JavaScript kodu işimizi görecektir.
[sourcecode lang="js"]function getUrlVars()
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
}[/sourcecode]
Bu fonksiyon URL parametreleriyle değerlerini bir dizi halinde getirir. Örneğin şu link için deneyelim: http://www.example.com/?me=myValue&name2=SomeOtherValue
getUrlVars() çağırdığımızda aşağıdaki diziye ulaşırız::
[sourcecode lang="js"]{
    &quot;me&quot;    : &quot;myValue&quot;,
    &quot;name2&quot; : &quot;SomeOtherValue&quot;
}[/sourcecode]
İlk parametredeki değeri almak için aşağıki gibi çalıştırın fonksiyonu:
[sourcecode lang="js"]var first = getUrlVars()[&quot;me&quot;];

// İkinci parametreyi almak içinse
var second = getUrlVars()[&quot;name2&quot;];[/sourcecode]
Bu kodların jQuery için yoğurulmuş son halide aşağıdaki gibidir:
[sourcecode lang="js"]$.extend({
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
});[/sourcecode]
Yukarıdaki kodu javascript dosyanıza eklerseniz URL parametre ve değerlerini aşağıdaki gibi alabilirsiniz:
[sourcecode lang="js"]// URL Parametrelerini alalım
var allVars = $.getUrlVars();

// URL Parametre değerlerini alalım
var byName = $.getUrlVar('name');[/sourcecode]