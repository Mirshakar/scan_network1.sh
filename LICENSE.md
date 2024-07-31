#!/bin/bash

# Tarmoq manzili
network="192.168.100.0/24"

# Tarmoqdagi barcha IP manzillarni olish
ips=$(nmap -sn $network | grep 'Nmap scan report for' | awk '{print $5}')

# Har bir IP manzil uchun ochiq portlarni tekshirish
for ip in $ips; do
    echo "Skanerlash: $ip"
    nmap -p- $ip
done
