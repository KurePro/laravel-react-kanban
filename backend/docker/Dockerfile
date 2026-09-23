FROM php:8.5-cli

# PostgreSQL用のパッケージとPHP拡張機能をインストール
RUN apt-get update && apt-get install -y \
    libpq-dev \
    unzip \
    git \
    && docker-php-ext-install pdo_pgsql

# Composer（PHPのパッケージ管理ツール）をインストール
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

# Set working directory
WORKDIR /var/www/html
