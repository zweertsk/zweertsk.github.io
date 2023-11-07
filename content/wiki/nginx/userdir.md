+++
title = 'User directory html pages'
summary = 'Serve user directory html pages with nginx'
date = 2023-11-07T17:40:01+01:00
draft = false
+++

```nginx
# example.com/~user

server {
    listen 80;
    listen [::]:80;

    server_name ~^(?<user>[a-zA-Z0-9-]+)\.example\.com$; #user.example.com

    location / {
        alias /home/$user/public_html/;
        index index.html index.htm;
        autoindex on;

        error_page 404 /home/$user/public_html/404.html;
        error_page 500 502 503 504 /home/$user/public_html/50x.html;
    }
}
```
```nginx


server {
    listen 80;
    listen [::]:80;

    server_name example.com www.example.com; #(www.)example.com/~user

    root /var/www/example.com

    location ~ ^/~(.+?)(/.*)?$ {
        alias /home/$1/public_html$2;
        index index.html index.htm;
        autoindex on;

        error_page 404 /home/$1/public_html/404.html;
        error_page 500 502 503 504 /home/$1/public_html/50x.html;
    }
}
```
