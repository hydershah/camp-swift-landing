# Camp Swift Landing Page - Implementation Notes

## Status: REQUIRES ACTION BEFORE DEPLOYMENT

---

## Completed Items

| Item | Status | Notes |
|------|--------|-------|
| Page Structure | Done | All required sections in correct order |
| GTM Integration | Done | GTM-M8CKNQMC implemented in head and body |
| Meta Pixel | Done | Pixel ID 1502927760991301 configured |
| Brand Styling | Done | Green/earth tone palette matching land company aesthetic |
| Mobile Responsive | Done | Breakpoints at 1024px and 768px |
| Anchor Navigation | Done | All standard IDs (hero, services, expertise, testimonials, contact) |
| Scroll Tracking | Done | 25/50/75/100% depth events pushed to dataLayer |
| Phone Click Tracking | Done | Events pushed to GTM and Meta Pixel |

---

## REQUIRED BEFORE GO-LIVE

### 1. HubSpot Form Configuration
**Location:** `index.html` line ~680

```javascript
portalId: "YOUR_HUBSPOT_PORTAL_ID", // REPLACE WITH ACTUAL PORTAL ID
formId: "YOUR_HUBSPOT_FORM_ID", // REPLACE WITH ACTUAL FORM ID
```

**Required Form Fields:**
- First Name
- Last Name
- Email
- Phone
- Timeline (dropdown - qualification field)
- Down Payment (dropdown - qualification field)
- Lead Source (hidden field - pre-populated as "Camp Swift Landing Page")
- UTM parameters (hidden fields)
- Click IDs: gclid, gbraid, wbraid, fbclid (hidden fields)

### 2. Testimonials
**Location:** `index.html` lines ~460-520

**CRITICAL:** The testimonials section contains placeholders. Per system prompt rules, you CANNOT invent testimonials.

**Action Required:**
- Source 3 verified customer testimonials from Eden Land Company
- Include: Full review text, reviewer name, location, star rating
- Replace placeholder text with actual testimonials

### 3. Images
**Location:** Hero section uses Unsplash placeholder

**Action Required:**
- Replace hero image with actual Camp Swift photography from https://www.edenlandcompany.com/properties-1/camp-swift
- Update `og:image` meta tag with actual image URL

### 4. Phone Number
**Location:** Navigation and CTAs

**Current:** (512) 757-1234 (placeholder)

**Action Required:** Confirm and update with actual Eden Land Company phone number

### 5. Site ID & SiteKey (Pending URL)
**Status:** Awaiting final URL assignment

Once URL is assigned (swift.edenlandcompany.com or similar):
- Update `og:url` meta tag
- Configure Site ID for form submission
- Configure SiteKey for MegaTag if applicable

---

## Tracking Implementation Details

### Google Tag Manager
```html
<!-- Head -->
<script>(function(w,d,s,l,i){w[l]=w[l]||[];w[l].push({'gtm.start':
new Date().getTime(),event:'gtm.js'});...})(window,document,'script','dataLayer','GTM-M8CKNQMC');</script>

<!-- Body (immediately after opening tag) -->
<noscript><iframe src="https://www.googletagmanager.com/ns.html?id=GTM-M8CKNQMC"...></iframe></noscript>
```

### Meta Pixel
```javascript
fbq('init', '1502927760991301');
fbq('track', 'PageView');
```

### Events Pushed
| Event | Trigger | Destination |
|-------|---------|-------------|
| `form_submission` | HubSpot form submit | GTM dataLayer |
| `Lead` | Form submit | Meta Pixel |
| `scroll_depth` | 25/50/75/100% scroll | GTM dataLayer |
| `phone_click` | Phone link click | GTM + Meta Pixel |

---

## Form Submission Attribution

The HubSpot form is configured to capture:
- Lead Source: "Camp Swift Landing Page"
- UTM Parameters: utm_source, utm_medium, utm_campaign, utm_content, utm_term
- Google Click IDs: gclid, gbraid, wbraid
- Meta Click IDs: fbclid

These are captured via URL parameters and passed to hidden form fields.

---

## Section Anchor IDs

| Section | ID | Purpose |
|---------|-----|---------|
| Hero | `#hero` | Main landing section |
| Features | `#services` | Property features grid |
| Why Choose | `#expertise` | Differentiators |
| Testimonials | `#testimonials` | Customer reviews |
| Location | `#location` | Map and proximity info |
| Contact | `#contact` | Lead capture form |

---

## Content Sources

All copy derived from web search results for Camp Swift and Eden Land Company:

- **Property Details:** Half-acre homesites, rolling hills, pines and oaks
- **Location:** 37 miles from Austin, 10 min from downtown Bastrop
- **Proximity:** 45 min to Austin-Bergstrom, near Tesla/Samsung/SpaceX
- **Financing:** Owner financing, 5% down
- **Company:** 1,500+ lots sold, 40+ years combined experience, San Marcos based

---

## Pre-Launch Checklist

- [ ] Replace HubSpot Portal ID and Form ID
- [ ] Add 3 verified customer testimonials
- [ ] Replace hero image with actual Camp Swift photos
- [ ] Verify phone number
- [ ] Set final URL in og:url meta tag
- [ ] Test form submission end-to-end
- [ ] Verify GTM container fires correctly
- [ ] Verify Meta Pixel events in Events Manager
- [ ] Test mobile responsiveness on actual devices
- [ ] Check all anchor links scroll correctly
- [ ] Validate no console errors

---

## File Structure

```
camp-swift-landing/
├── index.html          # Complete landing page
└── IMPLEMENTATION-NOTES.md  # This file
```

---

## Customer ID Reference

```
Customer ID: cd9509ee-e88a-4def-8083-a5d878f9370f
Site ID: [Pending URL assignment]
SiteKey: [Pending URL assignment]
```
