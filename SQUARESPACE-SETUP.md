# Setting Up the aPeer Landing Page on Squarespace

These instructions walk you through deploying the aPeer landing page on Squarespace at apeer.app.

---

## Before You Start

You need:
- A Squarespace account (any paid plan works, but Business or higher gives you full code injection access)
- The domain apeer.app pointed at Squarespace (Squarespace Domains or external DNS)
- The three files from this folder: `index.html`, `privacy.html`, `styles.css`

---

## Option A: Full Custom Code (Recommended)

This approach gives you the most control and preserves the design exactly as built. It uses Squarespace's "Code Injection" and blank pages.

### Step 1: Connect your domain

1. Log in to Squarespace
2. Go to Settings > Domains
3. Either transfer apeer.app to Squarespace or connect it via DNS
4. Make sure apeer.app is set as the primary domain

### Step 2: Create a blank site

1. When creating your site, choose the most minimal template available (Squarespace sometimes calls these "blank" or "Brine family" templates)
2. You do not need any of the default content -- you will be replacing everything

### Step 3: Inject the CSS globally

1. Go to Settings > Advanced > Code Injection
2. In the "Header" field, paste the following:

```html
<style>
/* Paste the ENTIRE contents of styles.css here */
</style>
```

3. Open the `styles.css` file in a text editor (TextEdit on Mac works -- make sure it is in plain text mode, not rich text)
4. Select all the text (Cmd+A), copy it (Cmd+C)
5. Paste it between the `<style>` and `</style>` tags in the Squarespace Header code injection field
6. Click Save

### Step 4: Set up the home page

1. Go to Pages in the Squarespace sidebar
2. Delete or hide all default pages
3. Create a new Blank page (or use an existing one and clear it)
4. Name it "Home" and set it as your home page
5. Add a "Code Block" to the page:
   - Click the + button to add a section
   - Choose "Code" (you may need to search for it)
   - Toggle OFF "Display Source" in the code block settings
6. Open `index.html` in a text editor
7. Copy everything between (and including) the first `<section>` tag and the closing `</script>` tag -- this is the body content. Specifically, copy from `<!-- Navigation -->` through the closing `</script>` tag (do NOT include the `<html>`, `<head>`, or `<body>` tags -- Squarespace provides those)
8. Paste into the Code Block
9. Click Save

### Step 5: Set up the meta tags for the home page

1. While editing the Home page, click the gear icon (page settings)
2. Go to the SEO tab
3. Set the SEO Title to: `aPeer -- Find your game.`
4. Set the SEO Description to: `aPeer connects you with real people for real games in your area. Post a game. See who shows up.`
5. If there is an "Social Image" option, upload an OG image (1200x630px recommended) -- you can create one later
6. Save

### Step 6: Set up the privacy page

1. Go to Pages > Add a new page
2. Choose Blank or use a page template with minimal structure
3. Set the URL slug to `privacy` (so it becomes apeer.app/privacy)
4. Add a Code Block to this page
5. Open `privacy.html` in a text editor
6. Copy the body content -- everything from `<header class="privacy-header">` through the closing `</footer>` tag
7. Paste into the Code Block (Display Source toggled OFF)
8. In page settings (gear icon), set:
   - SEO Title: `Privacy Policy -- aPeer`
   - SEO Description: `aPeer privacy policy. How we collect, use, and protect your data.`
9. Save

### Step 7: Update the privacy link

In the home page code block, the footer links to `/privacy.html`. On Squarespace, the URL will be `/privacy` (no .html extension). Update this in the code:

Find: `href="/privacy.html"`
Replace with: `href="/privacy"`

Do the same in the privacy page footer code.

### Step 8: Upload the favicon

1. Go to Design > Browser Icon (Favicon)
2. Upload the `favicon.svg` file
3. If Squarespace requires a PNG, convert the SVG to a 32x32 PNG first (you can use any free online SVG-to-PNG converter)

### Step 9: Hide Squarespace navigation

Since you have your own navigation in the code, hide the default Squarespace header:

1. Go to Design > Site Styles (or the paintbrush icon)
2. Find Header settings and set the header to "hidden" or minimize it
3. Alternatively, add this to the Code Injection Header field (after your CSS):

```html
<style>
  header#header { display: none !important; }
  .header-menu { display: none !important; }
  footer.footer-wrapper { display: none !important; }
</style>
```

This hides the default Squarespace header and footer since you have custom ones.

### Step 10: Replace the TestFlight link

When you have your real TestFlight link, find and replace all instances of:
`https://testflight.apple.com/join/PLACEHOLDER`

There are 3 instances in the home page (nav CTA, hero button, bottom CTA).

---

## Option B: Simpler Approach (If Code Injection Is Limited)

If you are on a Squarespace Personal plan (which has limited code injection):

1. Use the Squarespace page builder to create sections that match the design
2. Use the built-in text blocks for headings and body text
3. Use Button blocks for CTAs
4. Set the site-wide colors in Design > Site Styles:
   - Background: #1C1917
   - Text: #F5F5F4
   - Accent: #14B8A6
   - Secondary text: #A8A29E
5. This will not match the design exactly but will capture the color palette

Option A is strongly recommended for preserving the design.

---

## After Setup Checklist

- [ ] Visit apeer.app on desktop and verify the full page loads
- [ ] Visit apeer.app on your phone (Safari) and verify mobile layout
- [ ] Tap the "Join the beta" button and verify it goes to TestFlight
- [ ] Visit apeer.app/privacy and verify the privacy page loads
- [ ] Check that the footer links work (Privacy, Contact email)
- [ ] Verify the favicon appears in the browser tab
- [ ] Test the page scroll -- the navigation bar should get a blur background when you scroll down
- [ ] Run a Lighthouse check (in Chrome DevTools) to verify no major issues

---

## File Reference

| File | Purpose |
|------|---------|
| `index.html` | Home page content and structure |
| `privacy.html` | Privacy policy page |
| `styles.css` | All styling for both pages |
| `favicon.svg` | Browser tab icon (teal square with "a") |
| `SQUARESPACE-SETUP.md` | This file |

---

## Notes

- The CSS uses CSS custom properties (variables) extensively. All colors are defined once in `:root` and referenced throughout. If you ever need to adjust a color, change it in one place.
- The design uses the system font stack (-apple-system, SF Pro) which matches the app exactly on Apple devices.
- The nav blur effect requires a small JavaScript snippet (included at the bottom of index.html). This works in Squarespace Code Blocks.
- All spacing uses the same token values as the app (4, 8, 12, 16, 20, 24, 32, 40px).
- The dark color palette matches the app's DarkColors exactly: background #1C1917, surface #292524, primary #14B8A6, text #F5F5F4.
