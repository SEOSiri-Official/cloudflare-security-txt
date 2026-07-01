# cloudflare-security-txt

Easily deploy a fully RFC 9116-compliant vulnerability disclosure policy (`security.txt`) on your domain using Cloudflare Workers.

Built by [SEOSiri](https://www.seosiri.com) · [MIT License](LICENSE)

---

## Why this is necessary

According to the global internet standard **RFC 9116**, websites should host a security policy file at `/.well-known/security.txt` to help security researchers safely report vulnerabilities.

However, many popular blogging, e-commerce, and static CMS platforms (such as Blogger, Shopify, Webflow, or Wix) do not allow users to upload custom files to the root `/.well-known/` directory.

This Cloudflare Worker provides a 100% free, lightweight, and serverless solution to intercept and serve your `security.txt` file directly from Cloudflare's global edge network in under 10ms.

---

## Quick Deployment

### Method 1: Using the Cloudflare Dashboard
1. Create a new blank Worker named `cloudflare-security-txt` in your Cloudflare dashboard.
2. Copy the code from `index.js` and paste it into the Cloudflare code editor, adjusting your business contacts.
3. Click **Deploy**.
4. Go to the Worker's **Triggers/Settings** tab, click **Add Route**, and bind it to your domain:
   `*yourdomain.com/.well-known/security.txt`
5. Set the Failure Mode to **Fail open (proceed)** to ensure your site is completely fail-safe.

### Method 2: Local Development with Wrangler
```bash
# 1. Clone the repository
git clone https://github.com/SEOSiri-Official/cloudflare-security-txt.git
cd cloudflare-security-txt

# 2. Install dependencies
npm install

# 3. Authenticate and deploy
npm run deploy