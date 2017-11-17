# Find the latest file by modified date

find /path -printf '%T+ %p\n' | sort -r | head

# ghost systemd server

/etc/systemd/system/ghost.service
```
✔ Creating systemd service file at /var/www/ghost/system/files/ghost_54-169-190-39.service
Running sudo command: ln -sf /var/www/ghost/system/files/ghost_54-169-190-39.service /lib/systemd/system/ghost_54-169-190-39.service
Running sudo command: systemctl daemon-reload
```
Admin URL
As per the SSL section above, admin.url can be used to specify a different protocol for your admin panel. It can also be used to specify a different hostname (domain name). It cannot be used to affect the path at which the admin panel is served (this is always /ghost/).

"admin": { 
  "url": "http://example.com" 
}
