FROM php:8.2-fpm-alpine

# 必要パッケージ/拡張
RUN apk add --no-cache git unzip libzip-dev oniguruma-dev icu-dev \
  && docker-php-ext-configure zip \
  && docker-php-ext-install pdo_mysql mbstring zip intl

# Composer
COPY --from=composer:2 /usr/bin/composer /usr/bin/composer

WORKDIR /var/www/html

# ビルド時は composer install を実行しない（ボリュームで上書きされるため）
CMD ["php-fpm"]