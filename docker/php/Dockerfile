#ベースイメージ
FROM php:7.4-fpm

#composer
COPY --from=composer:1.10 /usr/bin/composer /usr/bin/composer

#npm
COPY --from=node:10.22 /usr/local/bin /usr/local/bin
COPY --from=node:10.22 /usr/local/lib /usr/local/lib

#パッケージ管理ツールapt-getの更新と必要パッケージのインストール
RUN apt-get update \
&& apt-get install -y \
git \
zip \
unzip \
zlib1g-dev libpng-dev libjpeg62-turbo-dev \
&& docker-php-ext-install pdo_mysql bcmath \
&& docker-php-ext-configure gd --with-jpeg \
&& docker-php-ext-install -j$(nproc) gd

# 作業ディレクトリ
WORKDIR /var/www/html
