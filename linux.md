# Find the latest file by modified date

find /path -printf '%T+ %p\n' | sort -r | head
