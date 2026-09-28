# Kairali Ayurvedic Group — 2026–27 Rates & Stay Information Emailer

Production-ready, executive-level HTML emailer for **Kairali Ayurvedic Group**, designed specifically for direct distribution by the **Director** to esteemed guests, travel partners, and corporate associates.

---

## 🏛️ Design System & Architectural Principles

- **Tone & Register**: Senior executive communication — refined, minimal, calm, and trustworthy. Not a marketing flyer or hotel brochure.
- **Strict Left-Alignment**: All body content, greeting, paragraphs, contact links, and closing share the exact same left content edge.
- **Zero Divider Lines**: Content sections breathe through controlled whitespace alone (no HRs, border lines, or decorative rules).
- **Single Master CTA**: One left-aligned document access button (`VIEW RATES AND DOCUMENTS →`) with subtle 4px rounded corners in Kairali Forest Green (`#006038`).
- **Subtle Compact Footer**: Light warm ivory background (`#FAF8F3`), approximately 60px high, with clean corporate branding.
- **Client Compatibility**: Outlook VML bulletproof button, table-based layout, inline CSS, and responsive media queries.

---

## 🖼️ How to Replace the Kairali Logo

### 1. Logo Asset Location
The emailer references the logo at:
```text
assets/logos/kairali-logo.png
```

### 2. Recommended Dimensions & Format
- **Format**: PNG (transparent background) or High-DPI PNG
- **Display Dimensions in HTML**: `width="138"` and `height="116"`
- **Original Source File Resolution**: Approximately `1090 × 915 px` (retina 2x/3x crispness)

### 3. Option A: In-Place File Replacement (Easiest)
1. Export your updated logo artwork as a transparent PNG.
2. Save or overwrite the file directly at:
   ```bash
   assets/logos/kairali-logo.png
   ```
3. Refresh `preview.html` or `index.html` to confirm the update.

### 4. Option B: Updating the Path in `email.html`
If using a different file name, hosted CDN URL, or path:
1. Open [`email.html`](file:///Users/varunkairalimac/Documents/Kairali%20Work/Email%20Templete/New%20Rates/email.html).
2. Locate the logo block around line 125:
   ```html
   <!-- HEADER / KAIRALI LOGO (CENTERED) -->
   <tr>
     <td align="center" style="padding: 32px 30px 32px 30px; background-color: #FFFFFF;">
       <a href="https://kairali-documents.vercel.app/?property=all" target="_blank" style="text-decoration: none; display: inline-block;">
         <img src="assets/logos/YOUR-NEW-LOGO.png" alt="Kairali Ayurvedic Group" width="138" height="116" border="0" style="display: block; width: 138px; max-width: 138px; height: auto; margin: 0 auto;" />
       </a>
     </td>
   </tr>
   ```
3. Update `src="..."` and ensure `width`, `height`, and `alt` are accurately specified.

---

## 🖥️ Local Preview & QA Suite

- **Interactive Multi-Device Suite**: Open `preview.html` or `index.html` in any browser to toggle between **Desktop (600px)**, **Mobile (375px)**, and **Side-by-Side** views.
- **Local Web Server**:
  ```bash
  python3 -m http.server 4321
  ```
  Visit [http://127.0.0.1:4321/index.html](http://127.0.0.1:4321/index.html) to view.
- **Copy Email Code**: Click the **"Copy Email Code"** button in the preview suite top bar to copy the raw HTML directly to your clipboard for your ESP (Mailchimp, HubSpot, Salesforce Marketing Cloud, etc.).

---

## 📋 Exact Content Hierarchy & Links

1. **Official Kairali Group Logo** (Centered)
2. **Greeting**: `Dear Guest and Travel Partner,` (Left-aligned)
3. **Introductory Notice**: `We’re pleased to share our 2026–27 rates for Villa Raag, Agonda, Goa and Kairali – The Ayurvedic Healing Village, Palakkad, Kerala.`
4. **Lead-in**: `Explore room rates, programmes and stay information in one place:`
5. **Master CTA**: `VIEW RATES AND DOCUMENTS →` (Links to `https://kairali-documents.vercel.app/?property=all`)
6. **Tariff Validity**: Stays covered through 30 September 2027.
7. **Contact Channels**:
   - Villa Raag: [`info@villaraag.com`](mailto:info@villaraag.com)
   - The Ayurvedic Healing Village: [`info@kairali.com`](mailto:info@kairali.com)
   - Central Reservations: [`+91 9555 156 156`](tel:+919555156156)
8. **Closing**: `We look forward to welcoming you.` / `Warm regards,` / `Kairali Ayurvedic Group` / `Villa Raag & The Ayurvedic Healing Village`
9. **Subtle Corporate Signature Footer**: Minimal, light warm ivory background.
