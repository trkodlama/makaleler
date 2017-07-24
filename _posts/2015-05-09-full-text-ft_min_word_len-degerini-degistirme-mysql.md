---
ID: 5758
post_title: 'Full Text ft_min_word_len Değerini Değiştirme &#8211; MySQL'
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/full-text-ft_min_word_len-degerini-degistirme-mysql-5758.html
published: true
post_date: 2015-05-09 00:22:58
---
MySQL full text kelimeleri 4 veya daha fazla karaktere sahip olmasına göre indeksler. Yani "PHP" kelimesini arattığınızda size hiçbir sonuç vermez. Bu yazımızda daha düşük karakterlerde indeksleme nasıl yapabileceğinizi göstereceğim.

/etc/my.cnf'de bulunun MySQL ayar dosyanızı açın ve 3 harfli olarak indekslemeyi açmak için [mysqld] bölümüne aşağıdaki satırı ekleyin:

<pre class="lang:sql decode:1 " >ft_min_word_len = 3</pre>

Eğer ft_min_word_len daha önceden eklenmişse değerini değiştirin.

Değişiklikleri yaptıktan sonra MySQL sunucusunu yeniden başlatın. Bu değeri bir sorgu ile değiştirmek malesef mümkün değildir. (örn. "SET ft_min_word_len = 3" sorgusunu çalıştırmayı denerseniz şu hatayı alırsınız: "#1193 - Unknown system variable 'ft_min_word_len'").

Artık ft_min_word_len değerini güncellediniz. Artık tablonuza yeni eklediğiniz veya güncellediğiniz satırlar istediğiniz gibi indekslenecekler fakat hiç dokunulmamış olan satırlar hala eski uzunluğa göre indekslenmiş olacak kalır. Bunun içinde tablonuzu bir kere onarmanız yeterlidir:

<pre class="lang:sql decode:1 " >REPAIR TABLE tablom QUICK;</pre>

Bahsedilen bazı yorumlar var ki onarmanın hem yavaş hemde tam olarak başarıyla sonuçlanmadığını söyleyenler var. Onarmak yerine fulltext index'ini kaldırıp yeniden eklemeyi hem daha hızlı hemde daha kesin sonuçlandığını söylüyorlar. Fakat ekleyip kaldırma süresinde sitenizde MySQL hataları alma ihtimaliniz olduğundan bunu yaparken sitenizi kapatmanızı öneririm.

Umarım iş görücü olmuştur, kolay gelsin,