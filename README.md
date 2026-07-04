# ⚡ Vipor Deploy Forge

**Production-grade Windows deployment scripts, assembled in your browser.**

Toggle the modules you need — domain join, winget app installs, debloat, Windows Update, French language pack, Wi-Fi, RDP, power hardening — and watch a fully logged, verified PowerShell deployment script build itself in real time.

🔗 **Live tool:** https://forge.vipor.ca *(or your GitHub Pages URL)*

Built by [Vipor AI Solutions](https://ai.vipor.ca) · Montréal 🇨🇦 · Bilingual EN/FR

---

## ✨ Features

- **10 battle-tested modules** — serial-based computer rename, winget installs with per-app verification, AppX debloat, PSWindowsUpdate loop, domain join, fr-CA language pack, Wi-Fi profile, power config, RDP, and an RMM-friendly pass/fail report with exit codes
- **Real deployment-grade output** — `#Requires -RunAsAdministrator`, transcript logging to `C:\Logs`, per-step try/catch with a `SUCCESS/FAILED` summary table, idempotent checks (skips what's already done)
- **Encrypted embedded secrets** — domain join credentials and Wi-Fi passphrases can be AES-256-CBC encrypted *in your browser* for unattended runs; plaintext never enters the script and never leaves your machine
- **Separate key file mode** — ship `Deploy-Machine.ps1` and `Deploy-Machine.key` independently so the script alone is useless ciphertext
- **100% client-side** — a single static HTML file; no backend, no signup, no telemetry
- **Bilingual** — full English / Français toggle

## 🔐 Security model (read this)

Embedded secrets are encrypted with a random 256-bit AES key generated locally in your browser (WebCrypto). Be honest with yourself about the threat model:

| Mode | Protects against | Does NOT protect against |
|---|---|---|
| Runtime prompt (default) | Everything — nothing is stored | — |
| Embedded secret + separate `.key` file | Anyone who obtains only the script | Anyone who obtains both files |
| Embedded secret + embedded key | Casual reading, log scraping | Anyone who obtains the script |

Treat generated scripts containing secrets like credentials. For unattended domain joins at scale, prefer Windows Autopilot / offline domain join.

> ⚠️ Scripts are provided as-is. Always test in a lab before touching production.

## 🚀 Run locally

Just open `index.html`. That's the whole app.

> Note: the secret-encryption feature requires a secure context (HTTPS, `localhost`, or `file://`).

## 📦 Deploy

Any static host works: GitHub Pages (workflow included in `.github/workflows/pages.yml` — deploys automatically on push to `main`), Cloudflare Pages, Netlify, etc.

## 🤝 Need this at Intune / Autopilot scale?

Vipor AI Solutions builds custom deployment automation, Entra ID integrations, and AI-powered IT workflows.
**→ [ai.vipor.ca](https://ai.vipor.ca)**

## 📄 License

MIT — see [LICENSE](LICENSE).
