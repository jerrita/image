# My php application template

nginx + php-fpm

Cause of some bugs in containerd, you'd better use port greater than 1024.
I default expose 8000 for web and 9000 for php-cgi

## Usage
Copy your conf to /etc/nginx/sites-enabled
And your web application to /www
