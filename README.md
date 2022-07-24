# Scouting Site
The purpose of the repository, to provide a template for every type of scouting unit to give ability to have a landing page and a unit's _business card_.

Supported unit types:
- [ ] Pack

The site is hosted by [GitHub](https://github.io) with [GitHub Pages](https://docs.github.com/en/pages) service.

One site can be associated only with one **GitHub** repository. Therefore, this repository should be forked or copied. The forked or copied repository must be public (unless, the repository your account is under *GitHub Enterprise*).

## The site's domain name
The site's domain name should be nice and self explaining. It is recommended to have it in the way:  
`[unit type][unit number][city]-[state].org`  
Scouting is a non-profit organization, therefore the top level domain `.org` is the most appropriate.

Domain name can be created and managed by any _registrar_ or _DNS provider_. The easiest experience was with [Google](https://domains.google.com/), but any trusted can be used.  
_**No hosting required!**_.

Example of the result domain [pack630allen-tx.org](https://pack630allen-tx.org)

In case, the unit cannot afford to pay for domain name and there is no sponsor for this default domain can be used. However, in this case it will be better to have a dedicated user on **GitHub** for this. For example, in my case the full URL/address of the site will be  
[https://ivankostyuk.github.io/scouting_site](https://ivankostyuk.github.io/scouting_site)  
The URL/address above does not give any clue what it is about. The workaround, to create a complete copy of repository (not a fork) and give it a name like it was constructed for domain, e.g. `pack630allen-tx.org`.  
[https://ivankostyuk.github.io/pack630allen-tx.org/](https://ivankostyuk.github.io/pack630allen-tx.org/)


## Associate repository with domain
This is called _[custom domain](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/about-custom-domains-and-github-pages)_ by **GitHub**.  
Avoid using `www` (it is outdated for very long time). The domain which was created is called _**Apex domain**_.

Go to the domain _registrar_ or _DNS provider_. Find **DNS** records (look for `DNS`). Locate records for the domain and create/update them in this way

| Host name | Type | TTL | Data |
| --- | --- | --- | --- |
| `[domain]` | A | `[use the smallest allowed for now]` | 185.199.108.153 |
| `[domain]` | AAAA | `[use the smallest allowed for now]` | 2606:50c0:8000::153 |
| www | CNAME | `[use the smallest allowed for now]` | `[domain]` |

The last record is to support internet users who still uses the prefix `www` to access websites.

**GitHub** recommends adding all 4 IP addresses for `A` and `AAAA` records. If the _registrar_ or `DNS provider` allow addition of more than one record per a type or extra records for a type then add all for  
- `A`
```
185.199.108.153
185.199.109.153
185.199.110.153
185.199.111.153
```
- `AAAA`
```
2606:50c0:8000::153
2606:50c0:8001::153
2606:50c0:8002::153
2606:50c0:8003::153
```

Example of how it will look.
| Host name | Type | TTL | Data |
| --- | --- | --- | --- |
| pack630allen-tx.org | A | 10 minutes | 185.199.108.153<br>185.199.109.153<br>185.199.110.153<br>185.199.111.153 |
| pack630allen-tx.org | AAAA | 10 minutes | 2606:50c0:8000::153<br>2606:50c0:8001::153<br>2606:50c0:8002::153<br>2606:50c0:8003::153 |
| www | CNAME | 10 minutes | pack630allen-tx.org |


The second part of configuration should be done on repository side. Go to repository **Settings** (gear/cogwheel). Go to **Pages**. Type or paste the domain name into the field **Custom domain** and press the button **Save**. Check the option **Enforce HTTPS** (the scout is trustworthy).

## Publish site
Go to repository **Settings** (gear/cogwheel). Go to **Pages**. Under **Source** select the branch and directory which should be used for publishing.