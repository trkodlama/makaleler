---
ID: 5790
post_title: jQuery Easyui ile Form Onchange Problemi
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/jquery-easyui-ile-form-onchange-problemi-5790.html
published: true
post_date: 2015-05-26 03:34:17
---
Merhaba arkadaşlar,

jQuery easyUI kullananlar için faydalı olabilecek bir makale olacak bu. jQuery easyUI ile <strong>textbox, datebox, numberbox </strong>ve <b>combobox</b> fonksiyonlarına sahibiz. Bunlar form inputlarımıza kütüphanimizin özelliklerini ekliyor. Fakat bu özellikleri ekledikten sonra

<pre class="lang:html decode:1 " >&amp;lt;form action=&amp;quot;#&amp;quot; id=&amp;quot;trkodlamaForm&amp;quot; onChange=&amp;quot;degisimYapildi()&amp;quot;&amp;gt;</pre>

formumuza örnekteki gibi onChange özelliği eklediğimizde değişikliği yakalayamıyor. Bu da doğal olarak bu özellikten faydalanamamanıza sebep oluyor. onChange özelliğinden faydalanmak için formunuzun üstüne aşağıdaki kodu eklerseniz probleminiz çözülecektir.

<pre class="lang:javascript decode:1 " >(function($){
	var numberbox = $.fn.numberbox.defaults.onChange;
	$.fn.numberbox.defaults.onChange = function(newValue, oldValue){
		$(this).closest('form').trigger('change');
		numberbox.call(this, newValue, oldValue);
	};
	var combobox = $.fn.combobox.defaults.onChange;
	$.fn.combobox.defaults.onChange = function(newValue, oldValue){
		$(this).closest('form').trigger('change');
		combobox.call(this, newValue, oldValue);
	};
	var textbox = $.fn.textbox.defaults.onChange;
	$.fn.textbox.defaults.onChange = function(newValue, oldValue){
		$(this).closest('form').trigger('change');
		textbox.call(this, newValue, oldValue);
	};
	var datebox = $.fn.datebox.defaults.onChange;
	$.fn.datebox.defaults.onChange = function(newValue, oldValue){
		$(this).closest('form').trigger('change');
		datebox.call(this, newValue, oldValue);
	};

})(jQuery);</pre>

Umarım faydalı olur, iyi geceler,