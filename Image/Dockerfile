FROM webdevops/php-nginx:8.2-alpine

# Environment variables
ENV WEB_DOCUMENT_ROOT=/app/public
ENV PHP_DISMOD=bz2,calendar,exif,ffi,intl,gettext,ldap,mysqli,imap,pdo_pgsql,pgsql,soap,sockets,sysvmsg,sysvsm,sysvshm,shmop,xsl,zip,gd,apcu,vips,yaml,imagick,mongodb,amqp

# Set working directory
WORKDIR /app

# Copy composer files
COPY composer.json composer.lock /app/

# Copy all files
COPY . .

# Install dependencies
RUN composer install --no-interaction --optimize-autoloader --no-dev

# Run post-install commands and set permissions
RUN php artisan optimize && \
    php artisan horizon:publish && \
    chown -R application:application .

# Copy configuration files (assuming they change less frequently than app code)
COPY docker/php-nginx /opt/docker/
