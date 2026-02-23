# 🕷️ Secret Hunter 🕸️
A bCheck for Burpsuite that aids in discovering keys in responses.

Happy hunting. 

~x0ptimal

`secret-hunter.bcheck` scans HTTP responses for **267 regex patterns** covering potential secret leakage, exposed credentials, internal metadata, and sensitive artifacts.

### Cloud Credentials & Tokens
- AWS: access keys, secret keys, S3 URLs/buckets, IoT endpoints/keys, AppSync-style keys.
- GCP: service account markers, project/client metadata, private key blocks, bucket URLs.
- Azure: access/client/tenant/subscription identifiers, blob storage/account URLs, function-style keys.
- Alibaba/Aliyun, DigitalOcean, Linode, Oracle Cloud, IBM Cloud, Cloudflare patterns.

### API Keys & Service Secrets
- OpenAI (`sk-...`), Hugging Face (`hf_...`), Stripe (`pk_live`, `sk_live`, `whsec_...`), PayPal variants.
- Twilio, Shopify, Datadog, Mailchimp, Segment, Mixpanel, New Relic, Razorpay, Adyen.
- Auth0, Okta, OneLogin, OAuth client/access/secret token patterns.
- Generic API key/token/secret/password proximity patterns.

### VCS / CI-CD / Package Secrets
- GitHub tokens (`ghp_`, `gho_`, `ghu_`), GitLab PAT/runner tokens, Bitbucket patterns.
- CircleCI/Travis/Jenkins token-like patterns and exposed CI references.
- npm/yarn auth tokens, `.npmrc` token forms, artifact env token patterns.

### Webhooks & Messaging Secrets
- Slack webhook URLs and bot token formats.
- Microsoft Teams webhook URL formats.
- Discord bot/token/client-secret patterns.
- Telegram bot token patterns.
- Generic webhook URL patterns.

### Database & Connection Secrets
- PostgreSQL, MySQL, MongoDB URI patterns.
- DB password assignments (`DB_PASSWORD`, JSON config keys).
- Generic credential-in-URL patterns.

### Cryptographic Material
- RSA/EC/DSA/OpenSSH/PGP/private key PEM headers.
- Encrypted private key blocks, JWT secret-like assignments, encryption key patterns.
- Firebase/GCP private key structures.

### JWT / Auth Artifacts
- Bearer JWTs and JWT-like triple-segment tokens.
- JWT in auth context (`authorization`, `access_token`, etc.).
- Session/CSRF/XSRF token-like values.

### Exposed Files, Endpoints & Runtime Artifacts
- `.env`, `.git`, backup/debug/log file extensions.
- Admin/dashboard/portal path patterns.
- API docs/GraphQL/debug endpoint indicators.
- Stack traces, debug logging flags, runtime env references (`process.env.*`).
- Local sensitive path patterns (`/tmp`, `/private`, `/secrets`, etc.).

### Infrastructure / DevOps Artifacts
- Kubernetes/kubeconfig/admin config/token indicators.
- Terraform state sensitivity markers.
- Ansible vault header patterns.
- Docker registry/auth config exposure patterns.

### Mobile / IoT / Blockchain / Misc
- Android/iOS key patterns (Google Maps/Firebase/APNS style).
- Firmware/update URL indicators.
- IoT key/token proximity patterns.
- Ethereum/Bitcoin and blockchain API-key-like formats.
- License key/serial number-like patterns.
- Base64 blobs and hash-like strings (MD5/SHA1/SHA256-style).

### Important Note
- This check intentionally includes some broad/high-noise regexes to catch unknown secret formats.
- Expect false positives; validate findings before triage/escalation.
