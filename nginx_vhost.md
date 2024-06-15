# Introduction
When using the Nginx web server, server blocks can be used to encapsulate configuration details and host more than one domain on a single server.
In this guide, we’ll discuss how to configure server blocks in Nginx on an Ubuntu 20.04 server.
## This the basic how to create nginx virtual host
```
sudo vim /etc/nginx/sites-available/example.com
```
```
server {
        listen 80; #ipv4
        listen [::]:80; #ipv6 (you can skip if non-use)

        root /var/www/html;
        index index.html index.htm index.nginx-debian.html;

        server_name _;

        location / {
                try_files $uri $uri/ =404;
        }
}
```
## Note*
Replace server_name with your actuall domain name.

## Make symbolic links from this files to the sites-enabled
```
sudo ln -s /etc/nginx/sites-available/example.com /etc/nginx/sites-enabled/
```

## Check nginx sysntax 
You should check the syntax first before nginx reload or restart service.
### nginx -t
The output success should be:
```
nginx: the configuration file /etc/nginx/nginx.conf syntax is ok
nginx: configuration file /etc/nginx/nginx.conf test is successful
```

After that you can reload or restart service to take effect.
```
sudo systemctl reload nginx.service
sudo systemctl restart nginx.service
```
