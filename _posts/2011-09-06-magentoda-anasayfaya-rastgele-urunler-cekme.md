---
ID: 248
post_title: 'Magento&#8217;da Anasayfaya Rastgele Ürünler Çekme'
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/magentoda-anasayfaya-rastgele-urunler-cekme-248.html
published: true
post_date: 2011-09-06 01:25:17
---
Merhaba arkadaşlar,

Bugünkü makalemde sizlere Magento e-ticaret sistemi ile ilgili bir yöntemi anlatıyorum. Daha doğrusu nasıl yapılacağını gösteriyorum. Magento anasayfasında belirli kategorilerden nasıl rastgele ürün çekebileceğinizi anlatacağım.

Öncelikle <a href="http://togl.me/0Cd" target="_blank">Magentocommerce</a>'den Magento'nun son sürümünü indirin.

Şimdi yavaş yavaş başlayalım. Öncelikle <strong>anasayfa_rastgele.phtml</strong> adlı bir dosya oluşturalım. Bu dosyayı<strong>/app/design/frontend/base/default/template/catalog/product</strong> içine kaydediyoruz bu dosyayı. Bu dosyanın içeriği şu şekilde olsun:

<pre class="lang:php decode:1 " >&amp;lt;?php
/**
 * TR Kodlama
 * @author oralunal
 * @copyright 2011
 * @link http://www.trkodlama.com
 */
?&amp;gt;
&amp;lt;?php
/**
 * Product list template
 *
 * @see Mage_Catalog_Block_Product_List
 */
?&amp;gt;
&amp;lt;?php
    $_productCollection=$this-&amp;gt;getLoadedProductCollection();
    $_helper = $this-&amp;gt;helper('catalog/output');
?&amp;gt;
&amp;lt;?php if(!$_productCollection-&amp;gt;count()): ?&amp;gt;
&amp;lt;p class=&amp;quot;note-msg&amp;quot;&amp;gt;&amp;lt;?php echo $this-&amp;gt;__('There are no products matching the selection.') ?&amp;gt;&amp;lt;/p&amp;gt;
&amp;lt;?php else: ?&amp;gt;
&amp;lt;div class=&amp;quot;category-products&amp;quot;&amp;gt;

    &amp;lt;?php $_collectionSize = $_productCollection-&amp;gt;count() ?&amp;gt;
    &amp;lt;?php $_columnCount = 4; //TR Kodlama - www.trkodlama.com $this-&amp;gt;getColumnCount(); ?&amp;gt;
    &amp;lt;?php
        // TR Kodlama - www.trkodlama.com
        $urunler = $_productCollection-&amp;gt;getItems();
        shuffle($urunler);
        $say = 1;
        $max_say = 4;
        // TR Kodlama - www.trkodlama.com
    ?&amp;gt;
    &amp;lt;?php $i=0; foreach ($urunler as $_product): ?&amp;gt;
        &amp;lt;?php if ($i++%$_columnCount==0): ?&amp;gt;
        &amp;lt;ul class=&amp;quot;products-grid&amp;quot;&amp;gt;
        &amp;lt;?php endif ?&amp;gt;
            &amp;lt;li class=&amp;quot;item&amp;lt;?php if(($i-1)%$_columnCount==0): ?&amp;gt; first&amp;lt;?php elseif($i%$_columnCount==0): ?&amp;gt; last&amp;lt;?php endif; ?&amp;gt;&amp;quot;&amp;gt;
                &amp;lt;a href=&amp;quot;&amp;lt;?php echo $_product-&amp;gt;getProductUrl() ?&amp;gt;&amp;quot; title=&amp;quot;&amp;lt;?php echo $this-&amp;gt;stripTags($this-&amp;gt;getImageLabel($_product, 'small_image'), null, true) ?&amp;gt;&amp;quot; class=&amp;quot;product-image&amp;quot;&amp;gt;&amp;lt;img src=&amp;quot;&amp;lt;?php echo $this-&amp;gt;helper('catalog/image')-&amp;gt;init($_product, 'small_image')-&amp;gt;resize(170); ?&amp;gt;&amp;quot; width=&amp;quot;170&amp;quot; height=&amp;quot;170&amp;quot; alt=&amp;quot;&amp;lt;?php echo $this-&amp;gt;stripTags($this-&amp;gt;getImageLabel($_product, 'small_image'), null, true) ?&amp;gt;&amp;quot; /&amp;gt;&amp;lt;/a&amp;gt;
                &amp;lt;h2 class=&amp;quot;product-name&amp;quot;&amp;gt;&amp;lt;a href=&amp;quot;&amp;lt;?php echo $_product-&amp;gt;getProductUrl() ?&amp;gt;&amp;quot; title=&amp;quot;&amp;lt;?php echo $this-&amp;gt;stripTags($_product-&amp;gt;getName(), null, true) ?&amp;gt;&amp;quot;&amp;gt;&amp;lt;?php echo $_helper-&amp;gt;productAttribute($_product, $_product-&amp;gt;getName(), 'name') ?&amp;gt;&amp;lt;/a&amp;gt;&amp;lt;/h2&amp;gt;
                &amp;lt;?php if($_product-&amp;gt;getRatingSummary()): ?&amp;gt;
                &amp;lt;?php echo $this-&amp;gt;getReviewsSummaryHtml($_product, 'short') ?&amp;gt;
                &amp;lt;?php endif; ?&amp;gt;
                &amp;lt;?php echo $this-&amp;gt;getPriceHtml($_product, true) ?&amp;gt;
                &amp;lt;div class=&amp;quot;actions&amp;quot;&amp;gt;
                    &amp;lt;?php if($_product-&amp;gt;isSaleable()): ?&amp;gt;
                        &amp;lt;button type=&amp;quot;button&amp;quot; title=&amp;quot;&amp;lt;?php echo $this-&amp;gt;__('Add to Cart') ?&amp;gt;&amp;quot; class=&amp;quot;button btn-cart&amp;quot; onclick=&amp;quot;setLocation('&amp;lt;?php echo $this-&amp;gt;getAddToCartUrl($_product) ?&amp;gt;')&amp;quot;&amp;gt;&amp;lt;span&amp;gt;&amp;lt;span&amp;gt;&amp;lt;?php echo $this-&amp;gt;__('Add to Cart') ?&amp;gt;&amp;lt;/span&amp;gt;&amp;lt;/span&amp;gt;&amp;lt;/button&amp;gt;
                    &amp;lt;?php else: ?&amp;gt;
                        &amp;lt;p class=&amp;quot;availability out-of-stock&amp;quot;&amp;gt;&amp;lt;span&amp;gt;&amp;lt;?php echo $this-&amp;gt;__('Out of stock') ?&amp;gt;&amp;lt;/span&amp;gt;&amp;lt;/p&amp;gt;
                    &amp;lt;?php endif; ?&amp;gt;
                    &amp;lt;ul class=&amp;quot;add-to-links&amp;quot;&amp;gt;
                        &amp;lt;?php if ($this-&amp;gt;helper('wishlist')-&amp;gt;isAllow()) : ?&amp;gt;
                            &amp;lt;li&amp;gt;&amp;lt;a href=&amp;quot;&amp;lt;?php echo $this-&amp;gt;helper('wishlist')-&amp;gt;getAddUrl($_product) ?&amp;gt;&amp;quot; class=&amp;quot;link-wishlist&amp;quot;&amp;gt;&amp;lt;?php echo $this-&amp;gt;__('Add to Wishlist') ?&amp;gt;&amp;lt;/a&amp;gt;&amp;lt;/li&amp;gt;
                        &amp;lt;?php endif; ?&amp;gt;
                        &amp;lt;?php if($_compareUrl=$this-&amp;gt;getAddToCompareUrl($_product)): ?&amp;gt;
                            &amp;lt;li&amp;gt;&amp;lt;span class=&amp;quot;separator&amp;quot;&amp;gt;|&amp;lt;/span&amp;gt; &amp;lt;a href=&amp;quot;&amp;lt;?php echo $_compareUrl ?&amp;gt;&amp;quot; class=&amp;quot;link-compare&amp;quot;&amp;gt;&amp;lt;?php echo $this-&amp;gt;__('Add to Compare') ?&amp;gt;&amp;lt;/a&amp;gt;&amp;lt;/li&amp;gt;
                        &amp;lt;?php endif; ?&amp;gt;
                    &amp;lt;/ul&amp;gt;
                &amp;lt;/div&amp;gt;
            &amp;lt;/li&amp;gt;
        &amp;lt;?php if ($i%$_columnCount==0 || $i==$_collectionSize): ?&amp;gt;
        &amp;lt;/ul&amp;gt;
        &amp;lt;?php endif ?&amp;gt;
        &amp;lt;?php
        // TR Kodlama - www.trkodlama.com
        if($say == $max_say){break;}
        else{$say++;}
        // TR Kodlama - www.trkodlama.com
        ?&amp;gt;
        &amp;lt;?php endforeach ?&amp;gt;
        &amp;lt;script type=&amp;quot;text/javascript&amp;quot;&amp;gt;decorateGeneric($$('ul.products-grid'), ['odd','even','first','last'])&amp;lt;/script&amp;gt;

&amp;lt;/div&amp;gt;
&amp;lt;?php endif; ?&amp;gt;</pre>

Bu sayfayı kaydedin. Daha sonra magento yönetici panelinden CMS menüsünün altından Sayfalar(Pages) linkine tıklayın. Burada Anasayfanızın açıldığı sayfayı bulun ve onu açın. Gelen sayfada soldaki menüden İçerik(Contents) linkine tıklayın. Artık bu sayfa içinde:

<pre class="lang:html decode:1 " >{{block type=&amp;quot;catalog/product_list&amp;quot; category_id=&amp;quot;36&amp;quot; template=&amp;quot;catalog/product/anasayfa_rastgele.phtml&amp;quot;}}</pre>

yazdığınızda belirlediğiniz kategoriden rastgele ürün çekimi yapabileceksiniz. Kategori numarasını değiştirerek bu kodu tekrar tekrar kullanabilirsiniz:

<pre class="lang:html decode:1 " >{{block type=&amp;quot;catalog/product_list&amp;quot; category_id=&amp;quot;36&amp;quot; template=&amp;quot;catalog/product/anasayfa_rastgele.phtml&amp;quot;}}
{{block type=&amp;quot;catalog/product_list&amp;quot; category_id=&amp;quot;4&amp;quot; template=&amp;quot;catalog/product/anasayfa_rastgele.phtml&amp;quot;}}
{{block type=&amp;quot;catalog/product_list&amp;quot; category_id=&amp;quot;86&amp;quot; template=&amp;quot;catalog/product/anasayfa_rastgele.phtml&amp;quot;}}</pre>

Umarım anlatabilmişimdir. Herkese kolay gelsin