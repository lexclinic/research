# How to Set Up GitHub Pages with a Custom Subdomain via Cloudflare

This guide explains how to configure a GitHub Pages site to use a custom subdomain (e.g., `research.lex.clinic`) through Cloudflare, including HTTPS support.

---

## 1. Configure DNS in Cloudflare

1. Log in to Cloudflare and select your domain (e.g., `lex.clinic`).
2. Go to **DNS → Add Record**.
3. Create a **CNAME** record with the following settings:

| Field | Value |
|-------|-------|
| Type | CNAME |
| Name | research |
| Target | lexclinic.github.io |
| Proxy status | DNS only (gray cloud) |
| TTL | Auto |

> ⚠️ Important: Use **DNS only** so GitHub Pages can issue an SSL certificate.  

---

## 2. Set the Custom Domain in GitHub

1. Go to your repository → **Settings → Pages → Custom domain**.
2. Enter `research.lex.clinic` and click **Save**.
3. GitHub will automatically create/update a `CNAME` file in your repository.

---

## 3. Enable HTTPS

1. In GitHub Pages settings, check **Enforce HTTPS**.
2. GitHub will provision an SSL certificate for your subdomain (may take a few minutes to a couple of hours).

---

## 4. Cloudflare SSL Settings

1. Go to **SSL/TLS → Overview** in Cloudflare.
2. Set **SSL/TLS mode** to **Full**.
3. Enable **Always Use HTTPS** for automatic redirection.

> 🔹 **Note:** Do not use Flexible SSL, as it breaks GitHub Pages HTTPS.

---

## 5. Optional: Redirect Root Domain

If you want `lex.clinic` (root) to redirect to `research.lex.clinic`:

1. Go to **Rules → Page Rules → Create Page Rule**.
2. Set **URL:** `https://lex.clinic/*`
3. **Forwarding URL:** 301 Permanent Redirect → `https://research.lex.clinic/$1`

---

## 6. Verify

- Use [DNS Checker](https://dnschecker.org/) to confirm DNS propagation.
- Visit `https://research.lex.clinic` to verify HTTPS is working.

---

## 7. Reference / Chat Guide

This guide was generated based on a live conversation with ChatGPT about configuring GitHub Pages + Cloudflare for `research.lex.clinic`.  
You can reference the original conversation here: [ChatGPT Discussion on GitHub Pages Setup](https://chatgpt.com/share/68c72bf6-69e8-8002-bcee-89f6497efe32)  

---

✅ Your GitHub Pages site should now be fully operational on a custom subdomain with HTTPS.
