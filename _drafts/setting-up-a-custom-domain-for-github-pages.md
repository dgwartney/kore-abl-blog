---
title: "Setting Up a Custom Domain for GitHub Pages"
date: 2026-06-16 10:52:41 -0700
categories: [Announcements]
tags: [github-pages, dns, deployment]
---

GitHub Pages works great out of the box at `dgwartney.github.io/kore-abl-blog`, but a custom domain makes the blog feel more permanent and is straightforward to configure.

## Subdomain vs. Apex Domain

The two options are:

- **Subdomain** — `blog.yourdomain.com` — easiest, requires one CNAME record
- **Apex domain** — `yourdomain.com` — requires four A records pointing to GitHub's IPs

A subdomain is recommended unless you specifically want the blog at the root of your domain.

## Step 1: Add a DNS Record

For a subdomain, add a CNAME record with your DNS provider:

| Type | Host | Value |
|------|------|-------|
| `CNAME` | `blog` | `dgwartney.github.io` |

For an apex domain, add these four A records instead:

| Type | Host | Value |
|------|------|-------|
| `A` | `@` | `185.199.108.153` |
| `A` | `@` | `185.199.109.153` |
| `A` | `@` | `185.199.110.153` |
| `A` | `@` | `185.199.111.153` |

DNS propagation typically takes a few minutes but can take up to 24 hours.

## Step 2: Configure the Domain on GitHub

```bash
gh api repos/dgwartney/kore-abl-blog/pages \
  --method PUT \
  -f cname=blog.yourdomain.com
```

## Step 3: Update `_config.yml`

```yaml
url: "https://blog.yourdomain.com"
baseurl: ""   # clear this — no subdirectory path needed with a custom domain
```

Commit and push — the GitHub Actions workflow redeploys automatically.

## Step 4: Enable HTTPS

Once DNS propagates, go to **Settings → Pages** in the GitHub repo and check **Enforce HTTPS**. GitHub provisions a free Let's Encrypt certificate automatically.

That's it — the blog will be live at your custom domain with a valid SSL cert.
