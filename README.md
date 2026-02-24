# Reworked — Shopify 2.0 Theme

A custom Shopify 2.0 theme for **Reworked**, a luxury custom clothing brand. The theme features a **"Drop Soon" landing page** and a **registration/notify-me page**, both fully customizable from the Shopify Theme Editor.

**Design aesthetic:** White background · Black font · Minimalist luxury fashion · Elegant typography using Cormorant Garamond (serif headings) + Montserrat (sans-serif body). A calligraphic logo appears as a large, faint watermark behind the content on both pages.

---

## File Structure

```
reworked-shopify/
├── config/
│   └── settings_schema.json       # Theme settings schema
├── layout/
│   └── theme.liquid               # Minimal Shopify layout wrapper
├── sections/
│   ├── drop-soon.liquid           # "Drop Soon" hero section
│   └── register-form.liquid       # Registration / notify-me form section
├── templates/
│   ├── page.drop-soon.json        # JSON template → drop-soon section
│   └── page.register.json         # JSON template → register-form section
└── README.md
```

---

## How to Import to Shopify

### Option A — Shopify CLI (recommended)

```bash
# Install Shopify CLI
npm install -g @shopify/cli @shopify/theme

# Authenticate
shopify auth login --store your-store.myshopify.com

# Push the theme
shopify theme push --path /path/to/reworked-shopify
```

### Option B — Theme Kit

```bash
# Install Theme Kit
curl -s https://shopify.github.io/themekit/scripts/install.py | python

# Configure config.yml in project root (see Theme Kit docs)
theme push
```

### Option C — Manual Upload via Shopify Admin

1. In your Shopify Admin, go to **Online Store → Themes**.
2. Click **Add theme → Upload zip file**.
3. Zip the contents of this repository (all folders + files, not the outer folder itself) and upload.

---

## How to Set Up the Pages

### 1. Create the "Drop Soon" page

1. Go to **Online Store → Pages** in your Shopify Admin.
2. Click **Add page**.
3. Give it a title (e.g. *Drop Soon*).
4. Under **Theme template**, choose **`page.drop-soon`**.
5. Save the page.

### 2. Create the "Register" page

1. Click **Add page** again.
2. Give it a title (e.g. *Register* or *Join the List*).
3. Under **Theme template**, choose **`page.register`**.
4. Save the page.

---

## How to Upload the Logo

1. In Shopify Admin go to **Online Store → Themes → Customize**.
2. Navigate to the **Drop Soon Hero** or **Register Form** section.
3. Under **Logo Background**, click **Select image** and upload your logo PNG/SVG.
4. Use the **Logo opacity** and **Logo size** sliders to fine-tune the watermark appearance.

---

## How to Customize from the Theme Editor

1. Go to **Online Store → Themes → Customize**.
2. Click the page preview or use the page selector to navigate to your Drop Soon or Register page.
3. Click the section in the left sidebar to expand its settings.

### Drop Soon Hero — available settings

| Group | Settings |
|---|---|
| Logo Background | Logo image, Opacity (1–100%), Size (20–90 vw) |
| Navigation Bar | Brand name, Top-right text, Nav text color |
| Hero Text | Label text + size, Heading + desktop size + mobile size, Subtitle + size |
| Button | Text, URL, Font size, Vertical/horizontal padding, Corner radius, Frosted glass toggle |
| Colors | Background, Heading, Body, Label, Subtitle, Button bg/text/border, Hover bg/text |
| Extras | Show scroll indicator toggle |

### Register Form — available settings

| Group | Settings |
|---|---|
| Logo Background | Logo image, Opacity (1–100%), Size (20–90 vw) |
| Navigation | Brand name, Back button text + URL, Nav color |
| Form Content | Heading + size, Subtitle (rich text) + size, Form max width |
| Phone Field | Label, Placeholder |
| Email Field | Show/hide toggle, Label, Optional indicator, Placeholder |
| Submit Button | Submit text, Submitting text, Font size, Padding, Corner radius |
| Input Styling | Corner radius |
| Consent & Success | Consent text, Success heading, Success message, Success button text |
| Colors | Background, Heading, Body, Field labels, Subtitle, Hint/consent, Input bg/text/border/focus, Button bg/text, Hover bg/text |

---

## Features

- **Shopify 2.0** — JSON templates with section-based architecture
- **Fully Theme-Editor customizable** — every visual property is a schema setting
- **Faint logo watermark** — large background image with adjustable opacity
- **Elegant typography** — Cormorant Garamond (headings) + Montserrat (body) via Google Fonts
- **Staggered animations** — fade-in + slide-up on page load for all content elements
- **Drop Soon hero** — full-viewport height, frosted-glass CTA button, animated scroll indicator
- **Register Form** — phone + optional email, 40+ international country codes with flag emojis, digits-only validation, fetch POST to `/contact`, success state after submission
- **Responsive** — mobile breakpoint at 600px with scaled typography
- **Scoped CSS** — all styles use `#section-{{ section.id }}` to prevent conflicts when multiple sections are used
- **Unique animation keyframes** — keyframe names include `{{ section.id }}` to support multiple instances
