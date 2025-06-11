FROM php:8.1

RUN apt update && apt install -y unzip
COPY --from=composer /usr/bin/composer /usr/bin/composer

WORKDIR /app
COPY compose.* ./
RUN php composer install --no-scripts
COPY . .

CMD php artisan serve --host 0.0.0.0