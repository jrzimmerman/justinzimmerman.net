+++
author = "Justin Zimmerman"
date = "2015-10-15T09:48:08-04:00"
description = "Creating a static page on a Digital Ocean droplet."
keywords = ["NGINX", "Digital Ocean"]
tags = ["NGINX", "Digital Ocean"]
title = "Create a Static Page on a Digital Ocean Droplet"
topics = ["NGINX", "Digital Ocean"]
type = "post"

+++

I currently use Digital Ocean to host my ghost blog. This has a been a very fun adventure, allowing me to learn the "ins and outs" of linux server administration.

##### What if we want to add a new static page?
Using a ghost blog is very easy and simple, but what if we want to add our projects to our site?

This takes a little bit of work.

After we copy our files onto our server, we want open the Ghost nginx file using:
`nano /etc/nginx/sites-enabled/ghost`

The file should look like this:

```
    server {
      listen 80 default_server;
      listen [::]:80 default_server ipv6only=on;

      server_name justinzimmerman.net; # Replace with your domain

      root /usr/share/nginx/html;
      index index.html index.htm;

      client_max_body_size 10G;

      location / {
          proxy_pass http://localhost:2368;
          proxy_set_header X-Forwarded-For   $proxy_add_x_forwarded_for;
          proxy_set_header Host $http_host;
          proxy_set_header X-Forwarded-Proto     $scheme;
          proxy_buffering off;
      }
    }
```

Add this block after the location / block:

```
    location /chatbuilder/ {
            alias /var/www/ChatBuilder/;
      }
```

We have just created an alias to a folder on the file system.

##### Completed file

```
    server {
      listen 80 default_server;
      listen [::]:80 default_server ipv6only=on;

      server_name justinzimmerman.net; # Replace with your domain

      root /usr/share/nginx/html;
      index index.html index.htm;

      client_max_body_size 10G;

      location / {
          proxy_pass http://localhost:2368;
          proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
          proxy_set_header Host $http_host;
          proxy_set_header X-Forwarded-Proto $scheme;
          proxy_buffering off;
      }

      location /chatbuilder/ {
          alias /var/www/ChatBuilder/;
      }
    }
```

##### Restart nginx and ghost

```
    sudo service nginx restart
    sudo service ghost restart
```

Thanks for reading! I hope this helps you set up your new static page.
