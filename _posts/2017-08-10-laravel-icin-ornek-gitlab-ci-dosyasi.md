---
ID: 9979
post_title: Laravel için Örnek GitLab CI Dosyası
author: Shibby Tersakyan
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/laravel-icin-ornek-gitlab-ci-dosyasi-9979.html
published: true
post_date: 2017-08-10 07:41:19
---
Uzun süre GitLab'deki projelerimde <strong>unit test</strong>leri otomatik çalıştırmayı beceremedim. GitLab’de bununla ilgili bir örnek bulamadım. Çeşitli forumlarda örnek konfigürasyonlar paylaşılmış ama google’da ilk sırada çıkan <a href="https://laracasts.com/discuss/channels/testing/laravel-ci-testing-with-gitlab">konfigürasyonda</a> testin tamamlanması 10 dakikayı buluyordu.

En sonunda daha derli toplu güzel bir <a href="https://laracasts.com/discuss/channels/testing/laravel-ci-testing-with-gitlab/replies/307623">repo</a> buldum.

Laravel’e özel bir docker image kullanıyor ve bende testin tamamlanması 2 dakika filan sürüyor.

GitLab ve Laravel için CI(Pipeline) konfigürasyonu arayanlara sevgilerimle. Umarım yardımcı olur.

Benim konfigürasyonum:
<pre class="line-numbers"><code class="language-yaml">before_script:
  - mv /root/composer.phar .
  - php -v
  - git --version
  - ls -lah
  - php composer.phar self-update
  - php composer.phar install --no-interaction --prefer-dist --optimize-autoloader
  - cp .env.gitlab .env
  - php artisan key:generate
  - php artisan config:cache
  - php artisan migrate --force
  - php artisan db:seed

variables:
  MYSQL_DATABASE: laravel
  MYSQL_ROOT_PASSWORD: secret

phpunit:php-laravel-env:mysql5.7:
  image: woohuiren/php-laravel-env:latest
  services:
    - mysql:5.7
  script:
    - php vendor/bin/phpunit --coverage-text --colors=never</code></pre>