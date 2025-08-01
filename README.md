# se-fruits-tips
Tips journey along the way

# Recon

## enum
```.*\.example\.com$```

```sublist3r -d example.com```

```amass enum -passive -d example.com | cut -d']' -f 2 | awk '{print $1}' | sort -u > amass.txt``` 

```amass enum -active -d example.com | cut -d']' -f 2 | awk '{print $1}' | sort -u > amass.txt```

```
curl -s https://crt.sh\?q\=\domain.com\&output\=json | jq -r '.[].name_value' | grep -Po '(\w+\.\w+\.\w+)$' >crtsh.txt
```

```cat example.urls | httprobe -t 1000```

```dnsx -l crtsh.txt -silent -o live_subs.txt```

```cat *.txt | sort -u > final.txt```

```ffuf -u https://FUZZ.example.com/ -w /usr/share/wordlists/dirb/common/txt -p 1 -fc 301```

```host domain-name```

```nmap -A -F -T1/2 ipaddress -v```

## Note
```
domain.com
├──sub1.domain.com
│  ├──Software
│  │   ├──Recon
│  │   └──etc
│  └──etc
└── sub.subdomain.com
```

## Attack Surface Mapping
Subdomain aktif	?

Port/web server terbuka	?

Login pages, API, upload ?

Hidden endpoints ?

Version fingerprinting	?
