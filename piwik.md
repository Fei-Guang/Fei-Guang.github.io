# Configuring Piwik accessed via an Nginx reverse proxy

public Nginx server configured as
```
location ^~ /piwik/ {
                proxy_set_header Host $host;
                proxy_set_header X-Real-IP $remote_addr;
                proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
                proxy_set_header X-Forwarded-Host $host;
                proxy_pass http://192.168.79.4/piwik/;

}
```


config.ini.php config on piwi nginx site
```
[General]
proxy_client_headers[] = "HTTP_X_FORWARDED_FOR"
proxy_client_headers[] = "X-Real-IP"
proxy_host_headers[] = "HTTP_X_FORWARDED_HOST"
proxy_ips[] = "192.168.79.4"
trusted_hosts[] = "192.168.79.4"
trusted_hosts[] = "<public-domain-server>"
```

# Configure GeoIP (PECL) With Piwik

check php version 
    curl http://localhost/info.php
PHP Version 7.0.17
    sudo apt-get install php-geoip php-dev libgeoip-dev

