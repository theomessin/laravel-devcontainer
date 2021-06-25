# From official php image.
FROM php:8.0-cli-alpine
# Create a user group and account under id 1000.
RUN addgroup -g 1000 -S user && adduser -u 1000 -D user -G user
# Install quality-of-life packages.
RUN apk add --no-cache bash curl git vim
# Install composer for php deps.
RUN apk add --no-cache composer
# Install postgres pdo driver.
RUN apk add --no-cache postgresql-dev && docker-php-ext-install pdo_pgsql
# Install redis driver.
RUN mkdir -p /usr/src/php/ext/redis; \
    curl -fsSL --ipv4 https://github.com/phpredis/phpredis/archive/5.3.4.tar.gz | tar xvz -C "/usr/src/php/ext/redis" --strip 1; \
    docker-php-ext-install redis
# Install nodejs and npm for frontend.
RUN apk add --no-cache nodejs npm
# Prevent container from exiting early.
CMD ["sleep", "infinity"]
