FROM php:8.1-fpm

# Installer NGINX, curl, unzip, wget, etc.
RUN apt-get update && apt-get install -y nginx curl unzip wget mariadb-client && \
    docker-php-ext-install mysqli

# Télécharger WordPress
RUN mkdir -p /var/www/html && \
    curl -o /tmp/wordpress.tar.gz https://wordpress.org/latest.tar.gz && \
    tar -xvzf /tmp/wordpress.tar.gz -C /var/www/html --strip-components=1 && \
    rm /tmp/wordpress.tar.gz

# Télécharger WooCommerce
RUN mkdir -p /var/www/html/wp-content/plugins && \
    curl -o /tmp/woocommerce.zip https://downloads.wordpress.org/plugin/woocommerce.8.6.1.zip && \
    unzip /tmp/woocommerce.zip -d /var/www/html/wp-content/plugins && \
    rm /tmp/woocommerce.zip

# Copier la config NGINX personnalisée
COPY nginx.conf /etc/nginx/nginx.conf

# Exposer le port 80
EXPOSE 80

# Script pour lancer NGINX + PHP-FPM ensemble
CMD service nginx start && php-fpm
