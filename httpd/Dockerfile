FROM httpd:2.4-alpine3.19

COPY ./httpd.conf /usr/local/apache2/conf/httpd.conf

COPY ./index.html /usr/local/apache2/htdocs/.

CMD ["httpd-foreground"]