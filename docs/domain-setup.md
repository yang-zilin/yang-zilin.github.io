# Domain configuration

Primary website: https://zilinyang.com/

Domain registration and renewal remain with GoDaddy. Cloudflare manages DNS on the Free plan. GitHub Pages hosts the website from the `main` branch, repository root.

## Nameservers

- `aurora.ns.cloudflare.com`
- `mark.ns.cloudflare.com`

## Website DNS

| Type | Name | Target |
| --- | --- | --- |
| A | @ | 185.199.108.153 |
| A | @ | 185.199.109.153 |
| A | @ | 185.199.110.153 |
| A | @ | 185.199.111.153 |
| CNAME | www | yang-zilin.github.io |

Keep website records DNS-only while GitHub validates the domain and issues its certificate. Enable Cloudflare proxying only after the GitHub origin certificate and Cloudflare Universal SSL certificate are ready. Use Full (Strict) encryption when proxying.

## Preserved service records

| Type | Name | Target / content |
| --- | --- | --- |
| CNAME | secureserver1._domainkey | s1.dkim.zilinyang_com.905.onsecureserver.net |
| CNAME | secureserver2._domainkey | s2.dkim.zilinyang_com.905.onsecureserver.net |
| CNAME | _domainconnect | _domainconnect.gd.domaincontrol.com |
| CNAME | _acme-challenge | zilinyang.com.a2a5947319618a50.dcv.cloudflare.com |
| TXT | @ | v=spf1 include:secureserver.net ~all |
| TXT | _dmarc | v=DMARC1; p=quarantine; adkim=r; aspf=r; rua=mailto:dmarc_rua@onsecureserver.net; |
| TXT | _github-pages-challenge-yang-zilin | da76246c1cadb6727b32150496812b |

Service and verification records must remain DNS-only. The original zone contained no MX records. The public Gmail contact address does not depend on this domain's DNS.

## Primary domain and redirects

- `CNAME` in the repository binds GitHub Pages to `zilinyang.com`.
- The HTML canonical URL is `https://zilinyang.com/`.
- Cloudflare Always Use HTTPS is enabled.
- Cloudflare rule `WWW to primary domain` redirects `https://www.zilinyang.com/*` to `https://zilinyang.com/${1}` with HTTP 301 and query-string preservation. Cloudflare rules require proxied website records.
- Cloudflare's minimum TLS version is 1.2; TLS 1.3 remains enabled.
- Enable GitHub Pages Enforce HTTPS once its certificate is issued. GitHub Pages then redirects its default `yang-zilin.github.io` hostname to the custom domain.

Do not configure GoDaddy URL forwarding, wildcard DNS, or a redirect from the apex domain back to `www`: these conflict with the primary-domain setup.

## Verification

Check the apex page, portrait asset, HTTP-to-HTTPS redirect, www-to-apex redirect, default GitHub hostname, and preservation of URL paths and query strings after any hosting or DNS change. Keep the GitHub ownership TXT record after verification.
