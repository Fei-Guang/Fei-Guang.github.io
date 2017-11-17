# Find the latest file by modified date

find /path -printf '%T+ %p\n' | sort -r | head

# ghost systemd server

/etc/systemd/system/ghost.service
