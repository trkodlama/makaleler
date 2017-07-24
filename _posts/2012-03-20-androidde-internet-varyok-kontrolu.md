---
ID: 385
post_title: 'Android&#8217;de internet var/yok kontrolü'
author: Shibby Tersakyan
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/android/androidde-internet-varyok-kontrolu-385.html
published: true
post_date: 2012-03-20 05:17:01
---
Merhabalar,

Kimi zaman uygulamalarımızda internetten veri çekmemiz gerekir. Eğer telefonun internet bağlantısı yoksa, veri çekmeye çalışırken uygulama hata verip kapanabilir. Bu da son kullanıcının hoşuna gitmeyen bir durum olur. Bunun yerine önce internetin olup olmadığını kontrol edip, daha sonra işlemi yaptırmak daha iyi olacaktır. Öncelikle internet durumunu okuyabilmemiz için aşağıdaki izni manifest dosyanıza ekleyin.
<pre class="prettyprint lang-xml" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">&lt;uses-permission android:name="android.permission.ACCESS_NETWORK_STATE"/&gt;</pre>
İzni ekledikten sonra fonksiyonumuzu ilgili sınıfımıza ekleyebiliriz.
<pre class="prettyprint lang-java" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">public boolean isConn(){
    connectivity = (ConnectivityManager) getSystemService(Context.CONNECTIVITY_SERVICE);
    if(connectivity.getActiveNetworkInfo()!=null){
        if(connectivity.getActiveNetworkInfo().isConnected ()) return true;
    }

    return false;
}
</pre>
Kodun kullanımı ise oldukça basit. Gerektiği yerde fonksiyonu çağırın yeter.
<pre class="prettyprint lang-java" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">if(isConn()){
    // Bağlantı var
}else{
    //Bağlantı yok
}</pre>
Kolay gelsin.