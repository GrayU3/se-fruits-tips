# se-fruits-tips
Tips journey along the way

# Recon

## enum
```
.*\.example\.com$
sublist3r -d example.com
subfinder -d example.com -all -recursive -o subfinder.txt
amass enum -passive -d example.com | cut -d']' -f 2 | awk '{print $1}' | sort -u > amass.txt
amass enum -active -d example.com | cut -d']' -f 2 | awk '{print $1}' | sort -u > amass.txt
curl -s https://crt.sh\?q\=\domain.com\&output\=json | jq -r '.[].name_value' | grep -Po '(\w+\.\w+\.\w+)$' >crtsh.txt
cat example.urls | httprobe -t 1000
dnsx -l crtsh.txt -silent -o live_subs.txt
cat *.txt | sort -u > final.txt
ffuf -u https://FUZZ.example.com/ -w /usr/share/wordlists/dirb/common/txt -p 1 -fc 301
host domain-name
curl -s "https://www.virustotal.com/vtapi/v2/domain/report?domain=<DOMAIN>&apikey=[api-key]" | jq -r '.. | .ip_address? // empty' | grep -Eo '([0-9]{1,3}\.){3}[0-9]{1,3}'
curl -s "https://www.virustotal.com/vtapi/v2/domain/report?domain=<DOMAIN>&apikey=[api-key]" | jq -r '.. | .ip_address? // empty' | grep -Eo '([0-9]{1,3}\.){3}[0-9]{1,3}' | sort -u | httpx-toolkit -sc
```

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

```
nmap -A -F -T1/2 ipaddress -v
cat urls.txt | hakrawler -u > urls3.txt
getallurls example.com | sort -u | grep "="
cat allurls.txt | grep '=' | urldedupe | tee output.txt
cat allurls.txt | grep -E '\?[^=]+=.+$' | tee output.txt
cat allurls.txt | grep -E "\.xls|\.xml|\.xlsx|\.json|\.pdf|\.sql|\.doc|\.docx|\.pptx|\.txt|\.zip|\.tar\.gz|\.tgz|\.bak|\.7z|\.rar|\.log|\.cache|\.secret|\.db|\.backup|\.yml|\.gz|\.config|\.csv|\.yaml|\.md|\.md5"
cat allurls.txt | grep -E "\.(xls|xml|xlsx|json|pdf|sql|doc|docx|pptx|txt|zip|tar\.gz|tgz|bak|7z|rar|log|cache|secret|db|backup|yml|gz|config|csv|yaml|md|md5|tar|xz|7zip|p12|pem|key|crt|csr|sh|pl|py|java|class|jar|war|ear|sqlitedb|sqlite3|dbf|db3|accdb|mdb|sqlcipher|gitignore|env|ini|conf|properties|plist|cfg)$"
site:*.example.com (ext:doc OR ext:docx OR ext:odt OR ext:pdf OR ext:rtf OR ext:ppt OR ext:pptx OR ext:csv OR ext:xls OR ext:xlsx OR ext:txt OR ext:xml OR ext:json OR ext:zip OR ext:rar OR ext:md OR ext:log OR ext:bak OR ext:conf OR ext:sql)

subfinder -dL subdomains.txt -all -silent | httpx-toolkit -td -sc -silent | grep -Ei 'asp|php|jsp|jspx|aspx'   <!-- SQLi discovery -->
echo http://site.com | gau | uro | grep -E ".php|.asp|.aspx|.jspx|.jsp" | grep -E '\?[^=]+=.+$'

echo https://example.com/ | gau | gf xss | uro | Gxss | kxss | tee xss_output.txt  <!-- XSS ? -->
cat xss_output.txt | grep -oP '^URL: \K\S+' | sed 's/=.*/=/' | sort -u > final.txt
```
