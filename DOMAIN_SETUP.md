# Domain Setup

Canonical domain: `belindawanglab.com`

The simplest setup is:

1. Publish this site to a GitHub repository.
2. Turn on GitHub Pages for that repository.
3. Add `belindawanglab.com` as the custom domain in GitHub Pages settings.
4. Add DNS records for `belindawanglab.com` and `www.belindawanglab.com` at the domain provider.
5. Turn on Enforce HTTPS in GitHub Pages after GitHub finishes the DNS check.

## Recommended GitHub Repository

Use the lab-owned GitHub account/organization `BelindaWangLab`, and create this repository:

`BelindaWangLab.github.io`

That would give the site a clean fallback URL:

`https://belindawanglab.github.io`

GitHub Pages will also work with `belindawanglab.com`; the DNS target for `www` should be the owner Pages domain, not the repository path.

## GitHub Pages Settings

After the repository exists on GitHub:

1. Go to the repository on GitHub.
2. Open Settings.
3. Open Pages.
4. Under Build and deployment, choose GitHub Actions.
5. Save.
6. Under Custom domain, enter `belindawanglab.com`.
7. Save and wait for DNS checks.
8. Turn on Enforce HTTPS when GitHub makes the checkbox available.

This folder includes `.github/workflows/pages.yml`, so GitHub Actions will build and deploy the Jekyll site when changes are pushed to `main`. The `CNAME` file in this folder records the intended domain, but the repository Pages setting is still the authoritative place to set the custom domain.

## DNS Records For GitHub Pages

At your DNS provider, create these records for the apex/root domain:

| Type | Name | Value |
| --- | --- | --- |
| A | `@` | `185.199.108.153` |
| A | `@` | `185.199.109.153` |
| A | `@` | `185.199.110.153` |
| A | `@` | `185.199.111.153` |
| AAAA | `@` | `2606:50c0:8000::153` |
| AAAA | `@` | `2606:50c0:8001::153` |
| AAAA | `@` | `2606:50c0:8002::153` |
| AAAA | `@` | `2606:50c0:8003::153` |

Also create this record for `www`:

| Type | Name | Value |
| --- | --- | --- |
| CNAME | `www` | `belindawanglab.github.io` |

This assumes the repository is `BelindaWangLab/BelindaWangLab.github.io`.

Do not create wildcard records such as `*.belindawanglab.com`.

## Verify

After DNS has had time to update, run:

```bash
dig belindawanglab.com +noall +answer -t A
dig belindawanglab.com +noall +answer -t AAAA
dig www.belindawanglab.com +nostats +nocomments +nocmd
```

The apex records should point to the GitHub Pages IP addresses above, and `www.belindawanglab.com` should point to the GitHub Pages domain.
