# Domain configuration

Primary website: https://zilinyang.com/

Domain registration and renewal remain with GoDaddy. Cloudflare manages DNS on the Free plan. GitHub Pages hosts the website from the `main` branch, repository root.

## Setup status — 2026-11-12

Setup is complete. GitHub has verified ownership of `zilinyang.com`, and its certificate is approved for both `zilinyang.com` and `www.zilinyang.com` (observed expiration: 2027-02-10). GitHub Enforce HTTPS is enabled.

Cloudflare is active on the Free plan. The four apex A records and the www CNAME are proxied. All seven mail and service verification records remain DNS-only. Cloudflare Universal SSL is Active, Full (Strict) is configured, Always Use HTTPS is enabled, and the WWW redirect rule is deployed.

Verified: HTTPS certificate validation on all four GitHub Pages origin addresses, browser loading of the HTTPS homepage and portrait, Cloudflare TLS 1.3 at its Singapore edge, HTTP-to-HTTPS redirects, WWW-to-apex redirects with path and query-string preservation, and redirection of `yang-zilin.github.io` to the primary domain. CSS and portrait assets return HTTP 200.

The original certificate request stalled in state `new`. After the DNS records propagated and ownership verification succeeded, removing and re-adding the GitHub custom domain restarted provisioning successfully. The resulting GitHub-generated CNAME commits were pulled into the local working copy.

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

All five website records are proxied through Cloudflare. Use Full (Strict) encryption. During any future certificate or hosting migration, keep records DNS-only until the origin and edge certificates are ready; do not weaken certificate validation to hide an origin error.

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
- Cloudflare rule `WWW to primary domain` redirects `https://www.zilinyang.com/*` to `https://zilinyang.com/${1}` with HTTP 301 and query-string preservation. The website records are proxied, so this rule handles live traffic.
- Cloudflare's minimum TLS version is 1.2; TLS 1.3 remains enabled.
- GitHub Pages Enforce HTTPS is enabled. GitHub Pages redirects its default `yang-zilin.github.io` hostname to the custom domain.

Do not configure GoDaddy URL forwarding, wildcard DNS, or a redirect from the apex domain back to `www`: these conflict with the primary-domain setup.

## Verification

Check the apex page, portrait asset, HTTP-to-HTTPS redirect, www-to-apex redirect, default GitHub hostname, and preservation of URL paths and query strings after any hosting or DNS change. Keep the GitHub ownership TXT record after verification.
