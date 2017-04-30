FROM nginx:latest

COPY nginx.conf /etc/nginx/nginx.conf
COPY wordpress.conf /etc/nginx/global/wordpress.conf
COPY restrictions.conf /etc/nginx/global/restrictions.conf

COPY landing.conf /etc/nginx/sites-available/landing.conf
COPY django.conf /etc/nginx/sites-available/django.conf

RUN mkdir -p /etc/nginx/sites-enabled/ &&\
      ln -s /etc/nginx/sites-available/landing.conf /etc/nginx/sites-enabled/landing.conf &&\
      ln -s /etc/nginx/sites-available/django.conf /etc/nginx/sites-enabled/django.conf
