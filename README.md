# se-fruits-tips
Tips journey along the way

# Recon

## enum
```.*\.example\.com$```

```sublist3r -d example.com```

```amass enum -passive -d example.com```

```cat example.urls | httprobe -t 1000```

```w3techs```

```ffuf -u https://FUZZ.example.com/ -w /usr/share/wordlists/dirb/common/txt -p 1 -fc 301```

```host domain```

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
