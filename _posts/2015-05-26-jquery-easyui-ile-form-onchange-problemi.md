---
ID: 5790
post_title: jQuery Easyui ile Form Onchange Problemi
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/web-tasarim-2/jquery-easyui-ile-form-onchange-problemi-5790.html
published: true
post_date: 2015-05-26 03:34:17
---
<a href="https://www.jeasyui.com/">jQuery EasyUI</a> kullananlar yaşamıştır diye düşünüyorum. <em>Öncelikle belirtmekte fayda var, bu makale 2015 yılına ait, en son jQuery EasyUI üzerinde denenmemiştir.</em> jQuery easyUI ile <code>textbox</code>, <code>datebox</code>, <code>numberbox</code> ve <code>combobox</code> fonksiyonlarına sahibiz. Bu fonksiyonlar inputlara bazı modern özellikler ekliyor. Olay şurada başlıyor, inputlarımızı EasyUI ile daha işlevsel hale getirdiğimizde form onchange olayı yakalanmıyor. Yani şöyle ki aşağıdaki gibi başlayan bir formumuz olduğunu düşünün ve form inputlarında değişiklik yaptığımızda <code>degisimYapildi()</code> fonksiyonunun çalışmasını istiyoruz. Fakat çalışmıyor! İşte çözümü bu makalede!
<pre class="line-numbers"><code class="language-html">&lt;form action="#" id="trkodlamaForm" onChange="degisimYapildi()"&gt;</code></pre>
jQuery EasyUI inputları bu onchange eventini yakalayamıyor.. onChange özelliğinden faydalanmak için jQuery EasyUI kütüphanemizi HTML'inize eklediğiniz satırdan sonra aşağıdaki JavaScript kodunu eklerseniz probleminiz çözülecektir:
<pre class="line-numbers"><code class="language-javascript">(function($){
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

})(jQuery);</code></pre>
Umarım faydalı olur, iyi geceler,