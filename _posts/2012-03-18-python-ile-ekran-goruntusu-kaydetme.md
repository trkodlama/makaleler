---
ID: 371
post_title: Python ile ekran görüntüsü kaydetme
author: Shibby Tersakyan
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/python/python-ile-ekran-goruntusu-kaydetme-371.html
published: true
post_date: 2012-03-18 16:19:11
---
Merhaba,

Bu yazımda Python araçlarını kullanarak ufak bir kod yardımıyla ekran görüntüsü almayı göstereceğim.
<pre class="prettyprint lang-python" data-start-line="1" data-visibility="visible" data-highlight="" data-caption=""># coding=utf-8
import gtk.gdk
import datetime

## Tarih ve saati now değişkenine atıyoruz.
now = datetime.datetime.now()
now = str(now)

w = gtk.gdk.get_default_root_window()
sz = w.get_size()
print "Ekran çözünürlüğü: %d x %d" % sz
#Ekran görüntüsü yakalanıyor.
pb = gtk.gdk.Pixbuf(gtk.gdk.COLORSPACE_RGB,False,8,sz[0],sz[1])
pb = pb.get_from_drawable(w,w.get_colormap(),0,0,0,0,sz[0],sz[1])
if (pb != None):
    # Ekran görüntüsünü dosyaya kaydediyoruz.
    pb.save(now+"_screenshot.png","png")
    print "Ekran görüntüsü "+now+".png olarak kaydedildi."
else:
    print "Ekran görüntüsü kaydedilemedi."</pre>
Ekran görüntünüz, görüntünün alındığı tarih ve saat ile birlikte py dosyanızın çalıştırıldığı konuma kaydedilecektir. Bu betiği crontab yardımıyla belli aralıklarla çalıştırarak ekran görüntünüzün alınmasını sağlayabilirsiniz.

Not: Sadece Linux ortamında denenmiştir. GTK aracını kullandığı için Windows'ta çalışacağını düşünmüyorum ancak deneyenler olursa bildirirlerse sevinirim.