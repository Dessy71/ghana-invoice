# InvoiceGH 

> **Free, professional invoice builder — Ghana-first, works worldwide.**
> No sign-up. No subscription. No data leaves your browser.

![InvoiceGH Preview](https://img.shields.io/badge/version-1.0.0-C9A84C?style=flat-square) ![License](https://img.shields.io/badge/license-MIT-green?style=flat-square) ![Status](https://img.shields.io/badge/status-active-brightgreen?style=flat-square) ![Made in Ghana](https://img.shields.io/badge/made%20in-Ghana%20🇬🇭-C9A84C?style=flat-square)

---

## What is InvoiceGH?

InvoiceGH is a browser-based invoice builder designed for Ghanaian freelancers, creatives, and small businesses — with full support for 40+ global currencies. Fill in your details, see a live preview, and export a print-ready invoice in seconds. No account needed. Everything runs in your browser.

---

## Features

- **Live Preview** — See your invoice update in real time as you type
- **Ghana Cedis (₵) by default** — with 40+ currencies across Africa, Americas, Europe, and Asia
- **6 Professional Themes** — Noir, Forest, Gold, Cobalt, Rose, Slate
- **Logo Upload** — Upload your business logo (PNG, JPG, SVG)
- **Project Items** — Add unlimited services/products with quantity and rate
- **Charges & Adjustments** — Discount (%), Tax (%), Shipping, Deposit
- **Payment Details** — Mobile Money, Bank Transfer, Paystack, Flutterwave, PayPal, Stripe, and more
- **Status Stamps** — Draft, Unpaid, Paid — with colour-coded stamps
- **Terms & Notes** — Custom per invoice
- **Signature Lines** — Authorised & Client signature fields
- **Export to HTML** — Download a self-contained file you can print as PDF
- **Print Support** — Direct browser print with print-optimised layout
- **Zoom Controls** — Adjust preview zoom from 40% to 150%
- **Sample Invoice** — One-click demo data to get started fast
- **Works Offline** — No internet connection needed after first load

---

## Tech Stack

| Layer | Technology |
|---|---|
| UI | Vanilla HTML, CSS, JavaScript |
| Fonts | DM Serif Display + DM Sans (Google Fonts) |
| Storage | Browser memory (no backend) |
| Export | Blob API → downloadable HTML |
| Print | CSS `@media print` |

---

## Getting Started

### Option 1 — Just open it

Download `invoice-builder.html` and open it in any modern browser. That's it.

```bash
# No install. No build step. No dependencies.
open invoice-builder.html
```

### Option 2 — Clone and run locally

```bash
git clone https://github.com/YOUR_USERNAME/invoicegh.git
cd invoicegh
# Open with VS Code Live Server or any static file server
```

> ⚠️ **VS Code Live Server note:** Live Server injects a WebSocket `<script>` block at the bottom of the page. This can break the JS if it lands inside the `exportHTML()` template string. Use the provided fixed `exportHTML()` function which builds the HTML as an array join instead of a template literal — this prevents the injection from corrupting the output.

### Option 3 — Deploy to Netlify / Vercel / GitHub Pages

Since this is a single HTML file, deployment is one drag-and-drop:

**Netlify:** Drag the file into [app.netlify.com/drop](https://app.netlify.com/drop)

**GitHub Pages:**
```bash
git init
git add .
git commit -m "initial commit"
git branch -M main
git remote add origin https://github.com/Dessy71/ghana-invoice.git
git push -u origin main
# Then enable Pages in repo Settings → Pages → Deploy from branch: main
```

---

## Project Structure

```
invoicegh/
├── invoice-builder.html   # Main app (self-contained)
├── invoicegh.html      
├── README.md
└── LICENSE
```

> The entire v1 app lives in a single HTML file — CSS, JS, and markup together. This is intentional for portability. The authenticated v2 version uses Firebase and is a separate file.

---

## Currency Support

Ghana Cedi (₵ GHS) is the default. Supported currencies include:

**Africa** — GHS, NGN, KES, ZAR, EGP, ETB, TZS, UGX, RWF, MAD, XOF, XAF, and more

**Americas** — USD, CAD, BRL, ARS, COP, CLP, PEN, JMD

**Europe** — EUR, GBP, CHF, SEK, NOK, DKK, PLN, TRY

**Asia & Oceania** — CNY, JPY, INR, AUD, SGD, AED, SAR, KRW, PHP, and more

---

## Themes

| Theme | Accent Color |
|---|---|
| Noir | `#111111` |
| Forest | `#2C5F2E` |
| Gold | `#8B6914` |
| Cobalt | `#1A3A7A` |
| Rose | `#9B2335` |
| Slate | `#445566` |

---

## Known Issues & Fixes

### Page unresponsive when using VS Code Live Server
**Cause:** Live Server injects a WebSocket `<script>` block at the bottom of the HTML. If this lands inside the `exportHTML()` template literal, the `</script>` tag inside it terminates the main page's script early — killing all JS event handlers.

**Fix:** The `exportHTML()` function now builds the HTML string using `Array.join()` instead of a template literal. This prevents Live Server's injected code from ever appearing inside the string.

### Export file has WebSocket code inside it
Same root cause as above. Fixed in the same way. Always use the latest version of `exportHTML()`.

---

## Roadmap

- [x] Live invoice preview
- [x] 40+ currency support
- [x] 6 colour themes
- [x] Export to HTML / Print to PDF
- [ ] Firebase Auth (Google + Email/Password)
- [ ] Cloud logo storage (Firebase Storage)
- [ ] Invoice CRUD admin panel
- [ ] Auto-generated invoice numbers
- [ ] Paid receipt generation with PAID stamp
- [ ] Supabase migration (open-source backend alternative)
- [ ] Invoice history search and filter
- [ ] Client address book
- [ ] Recurring invoice templates
- [ ] Email invoice directly from the app
- [ ] Mobile responsive layout
- [ ] Multi-language support (Twi, French, Hausa)
- [ ] Invoice analytics dashboard

---

## Contributing

Pull requests are welcome. For major changes, open an issue first to discuss what you'd like to change.

```bash
# Fork the repo
# Create your branch
git checkout -b feature/your-feature-name

# Commit your changes
git commit -m "add: your feature description"

# Push and open a PR
git push origin feature/your-feature-name
```

Please keep the single-file architecture for the v1 offline version. 
---

## License

[MIT](LICENSE) — free to use, modify, and distribute. Credit appreciated but not required.

---

## Author

Built with ♥ in Accra, Ghana 🇬🇭 by #Dessy 

> *InvoiceGH — because every creative deserves a professional invoice.*
