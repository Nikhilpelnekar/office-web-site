# Build Notes

## Form Submission Implementation

All forms on this site use **WhatsApp as the primary submission channel**. This approach was chosen because:

1. The site is statically exported (no Node.js server)
2. WhatsApp is the client's preferred communication channel
3. Zero dependency on third-party services

### How it works:

1. User fills out form (client-side validation)
2. Form data is formatted into a WhatsApp message
3. `wa.me` link opens in new tab with pre-filled message
4. User can also choose email (`mailto:`) as fallback

### Lead Payload Structure

All forms send the following data structure:

```typescript
{
  name: string;           // Required
  company?: string;       // Optional
  email?: string;         // Optional (for some forms)
  phone: string;          // Required
  employees?: string;     // Employee count range
  requirement?: string;   // Service requirement
  message?: string;       // Additional message
  source: string;         // Page/form identifier for tracking
}
```

### CRM Integration (Future)

This payload structure is designed to map to **Zoho CRM** fields:

| Form Field | Zoho CRM Field |
|------------|----------------|
| name | First Name, Last Name |
| company | Company Name |
| email | Email |
| phone | Phone |
| employees | No. of Employees |
| requirement | Lead Source Detail |
| message | Description |
| source | Lead Source |

To enable direct CRM submission:
1. Create Zoho API endpoint
2. Update `submitLead()` in `src/lib/submitLead.ts`
3. Add authentication credentials to environment variables

## Environment Variables

All environment variables are prefixed with `NEXT_PUBLIC_` for client-side access:

| Variable | Required | Default |
|----------|----------|---------|
| `NEXT_PUBLIC_WHATSAPP_NUMBER` | Yes | `919876543210` (placeholder) |
| `NEXT_PUBLIC_SCHEDULING_URL` | Yes | `https://calendly.com/softtech-consultation` |
| `NEXT_PUBLIC_FORM_ENDPOINT` | No | - |
| `NEXT_PUBLIC_WEB3FORMS_KEY` | No | - |
| `NEXT_PUBLIC_GTM_ID` | No | - |
| `NEXT_PUBLIC_GA_ID` | No | - |
| `NEXT_PUBLIC_SITE_URL` | No | `https://www.softtechcomputers.com` |

## Font Loading

The site uses two primary fonts:

1. **Atkinson Hyperlegible** - Body text and headings
   - Loaded via `next/font/google`
   - Weights: 400 (regular), 700 (bold)

2. **Lato** - Subheadings and labels
   - Loaded via `next/font/google`
   - Weights: 400, 500, 600, 700

Both fonts use `font-display: swap` for optimal loading performance.

## Static Export Notes

This site uses `output: 'export'` in `next.config.ts`. Important implications:

- No server-side API routes
- No dynamic server features
- All pages are pre-rendered at build time
- Forms must use client-side submission (WhatsApp, mailto, or external service)

## Image Optimization

Due to static export, `next/image` with external URLs requires `unoptimized: true`. When adding real images:

1. Use WebP or AVIF formats
2. Provide appropriate dimensions
3. Lazy load below-fold images
4. Use placeholder blur for above-fold images

## CSS Variables

All brand colors are defined as CSS variables in `src/app/globals.css`:

```css
--brand-primary: #1d8bcc;
--brand-charcoal: #222021;
--brand-steel: #055c9d;
--brand-navy: #003060;
--brand-ocean: #045c9d;
--brand-azure: #1086d4;
--bg-white: #ffffff;
--bg-sand: #fef3e6;
--accent-teal: #4db6ac;
--border-gray: #d0d5db;
--success: #28a745;
--warning: #f0ad4e;
--error: #dc3545;
--contrast-coral: #ff6f61;
--whatsapp-green: #25D366;
```

To change colors site-wide, update these variables.

## Substitutions

If any library was unavailable:

- All specified libraries (framer-motion, lucide-react, @radix-ui/*) were available
- No substitutions were necessary

## Known Limitations

1. **Resume Upload** in Careers form: Since we're using WhatsApp-primary submission, file uploads open the user's email client. For true file upload, integrate Web3Forms or similar service.

2. **Google Maps Embed**: The contact page shows a placeholder. Replace with actual embed code:
   ```html
   <iframe src="https://www.google.com/maps/embed?pb=..." width="100%" height="450" style="border:0;" allowfullscreen="" loading="lazy"></iframe>
   ```

3. **Blog Posts**: Currently placeholder content. Replace with real articles or integrate a headless CMS.

4. **Industry Pages**: Only Manufacturing has a dedicated page. Create additional pages as needed by copying the template.
