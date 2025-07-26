# se-fruits-tips
Tips journey along the way

URL - regex
LEVEL 1 - http://example.com atau https://example.com

```^https?:\/\/example\.com$```

Penjelasan:

```^``` dan ```$``` memastikan seluruh string cocok.

```https?``` cocok untuk ```http``` dan ```https```

```example\.com``` adalah domain utama

LEVEL 2 - api.example.com, www.example.com, dsb.

```^https?:\/\/[\w-]+\.example\.com$```

Penjelasan:

```[\w-]+``` = satu subdomain (seperti ```api```, ```www```)

```\.``` = titik literal

Jadi cocok hanya satu subdomain

LEVEL 3 - api.example.com, deep.api.example.com, v1.deep.api.example.com, dsb

```^https?:\/\/(?:[\w-]+\.)+example\.com$```

Penjelasan:

```(?:...)``` = non-capturing group

```[\w-]+\.``` = satu subdomain dengan titik

```+``` artinya bisa ada lebih dari satu subdomain

Jadi cocok untuk:

```api.example.com```

```sub.api.example.com```

```deep.sub.api.example.com```
