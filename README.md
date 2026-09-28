# Kairali Ayurvedic Group — 2026–27 Rates & Stay Information Emailer

Production-ready, responsive, client-tested HTML emailer announcing 2026–27 rates and stay information for:
1. **Kairali – The Ayurvedic Healing Village, Palakkad, Kerala (KTAHV)** *(Appears FIRST)*
2. **Villa Raag, Agonda Beach, South Goa** *(Appears SECOND)*

---

## 📁 File Structure

```text
├── email.html                   # Primary production-ready email HTML
├── preview.html                 # Interactive preview suite (Desktop 600px, Mobile 375px, Side-by-Side)
├── README.md                    # Documentation & asset replacement instructions
├── assets/
│   ├── logos/
│   │   ├── kairali-logo.png     # Master Kairali Ayurvedic Group logo (health through ayurveda · since 1908)
│   │   ├── ktahv-logo.png       # The Ayurvedic Healing Village full-colour logo
│   │   ├── villa-raag-logo.png  # Villa Raag Yoga Sanctuary logo
│   │   ├── ktahv-logo.svg       # Vector source
│   │   └── villa-raag-logo.svg  # Vector source
│   ├── images/
│   │   ├── ktahv-hero.jpg       # Approved KTAHV facility photography (552px wide display)
│   │   └── villa-raag-hero.jpg  # Approved Villa Raag sanctuary photography (552px wide display)
│   └── icons/                   # Supporting iconography assets
└── images/                      # Workspace source images
```

---

## ⚙️ Central Configuration Section

At the top of [`email.html`](file:///Users/varunkairalimac/Documents/Kairali%20Work/Email%20Templete/New%20Rates/email.html), all document links, asset paths, and contact details are centralized:

```html
<!--
================================================================================
KAIRALI EMAIL CONFIGURATION SETTINGS
================================================================================
[DOCUMENT LINKS]
• ALL_RATES_URL:        https://kairali-documents.vercel.app/?property=all
• KTAHV_RATES_URL:      https://kairali-documents.vercel.app/?property=ahv
• VILLA_RAAG_RATES_URL: https://kairali-documents.vercel.app/?property=villa-raag

[ASSET PATHS]
• KAIRALI_GROUP_LOGO:   assets/logos/kairali-logo.png
• KTAHV_LOGO:           assets/logos/ktahv-logo.png
• VILLA_RAAG_LOGO:      assets/logos/villa-raag-logo.png
• KTAHV_HERO_IMAGE:     assets/images/ktahv-hero.jpg
• VILLA_RAAG_HERO_IMAGE:assets/images/villa-raag-hero.jpg

[CONTACT DETAILS]
• VILLA_RAAG_EMAIL:     info@villaraag.com
• KTAHV_EMAIL:          info@kairali.com
• RESERVATIONS_PHONE:   +91 9555 156 156 (tel:+919555156156)
================================================================================
-->
```

---

## 🔄 How to Update Document URLs

If your rates documents or landing pages move to a custom domain (e.g. `kairali.com/rates/`):

1. **Combined / All Rates Link**:
   Search for `https://kairali-documents.vercel.app/?property=all` in `email.html` and replace with your new URL. (Present in the master header CTA and group logo link).
2. **KTAHV Rates Link**:
   Search for `https://kairali-documents.vercel.app/?property=ahv` in `email.html` and replace with your new URL. (Present in the KTAHV button and hero image link).
3. **Villa Raag Rates Link**:
   Search for `https://kairali-documents.vercel.app/?property=villa-raag` in `email.html` and replace with your new URL. (Present in the Villa Raag button and hero image link).

---

## 🖼️ How to Replace Logos and Images

### 1. Hosted CDN / Web Paths for Deployment
Before sending through an ESP (Mailchimp, Brevo, Sendgrid, Klaviyo, HubSpot, etc.), upload the assets folder to your CDN or server and update the `src=""` attributes:

| Current Local Asset Path | Suggested Production CDN URL | Recommended Display Dimensions |
| :--- | :--- | :--- |
| `assets/logos/kairali-logo.png` | `https://cdn.kairali.com/emails/logos/kairali-logo.png` | `156px` width, auto height |
| `assets/logos/ktahv-logo.png` | `https://cdn.kairali.com/emails/logos/ktahv-logo.png` | `144px` width, auto height |
| `assets/logos/villa-raag-logo.png` | `https://cdn.kairali.com/emails/logos/villa-raag-logo.png` | `200px` width, auto height |
| `assets/images/ktahv-hero.jpg` | `https://cdn.kairali.com/emails/images/ktahv-hero.jpg` | `552px` – `600px` width |
| `assets/images/villa-raag-hero.jpg` | `https://cdn.kairali.com/emails/images/villa-raag-hero.jpg` | `552px` – `600px` width |

### 2. Dropping New Local Files
If you replace files locally, simply overwrite the existing files in `assets/logos/` or `assets/images/` keeping the same filenames.

---

## 📱 Testing & QA

Open [`preview.html`](file:///Users/varunkairalimac/Documents/Kairali%20Work/Email%20Templete/New%20Rates/preview.html) in any modern browser:
- **Desktop (600px)**: Verifies Outlook and desktop webmail rendering.
- **Mobile (375px fluid)**: Verifies touch-target sizes, fluid image scaling, and single-column stacking.
- **Side-by-Side**: Allows simultaneous comparison.
- **Copy Email Code**: 1-click clipboard export for pasting directly into your email delivery tool.

---

## 🛡️ Email Client Compatibility Highlights

- **Outlook (Windows Desktop)**: Full table structure with `mso-line-height-rule: exactly;`, conditional XML namespace tags, and VML `<v:roundrect>` bulletproof pill buttons.
- **Gmail (Web & Mobile)**: Inline styles on every text element; no reliance on external stylesheets for critical layout; styles scoped to prevent clipping.
- **Apple Mail & iOS**: Retina 2x image rendering, fluid `@media` queries down to 320px.
- **Dark Mode Friendly**: Contrasting neutral card borders and backgrounds ensure high readability across both light and dark client themes.
