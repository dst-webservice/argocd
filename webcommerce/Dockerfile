FROM bitnami/wordpress-nginx:latest

USER root

# Installer unzip et curl (nécessaire pour télécharger WooCommerce)
RUN install_packages unzip curl

# Télécharger et installer WooCommerce dans le dossier plugins WordPress
RUN curl -L -o /tmp/woocommerce.zip https://downloads.wordpress.org/plugin/woocommerce.latest-stable.zip && \
    unzip /tmp/woocommerce.zip -d /opt/bitnami/wordpress/wp-content/plugins && \
    rm -f /tmp/woocommerce.zip

# Repasser en utilisateur non-root pour sécurité
USER 1001
