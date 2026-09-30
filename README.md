<<<<<<< HEAD
# SOFT-TECH Computers Website

A high-conversion B2B marketing website for SOFT-TECH Computers Pvt. Ltd., built with Next.js 14, TypeScript, and Tailwind CSS.

## Quick Start

```bash
# Install dependencies
npm install

# Run development server
npm run dev

# Build for production (static export)
npm run build

# The static site will be exported to the `out` directory
```

## Environment Variables

Copy `.env.example` to `.env.local` and configure:

```bash
cp .env.example .env.local
```

Required environment variables:

| Variable | Description | Example |
|----------|-------------|---------|
| `NEXT_PUBLIC_WHATSAPP_NUMBER` | WhatsApp business number (no +, spaces, or dashes) | `919876543210` |
| `NEXT_PUBLIC_SCHEDULING_URL` | Calendly or scheduling URL | `https://calendly.com/softtech-consultation` |

Optional for analytics:

| Variable | Description |
|----------|-------------|
| `NEXT_PUBLIC_GTM_ID` | Google Tag Manager ID |
| `NEXT_PUBLIC_GA_ID` | Google Analytics ID |

## Deployment

This site is configured for static export (`output: 'export'`). After building, deploy the `out` directory to any static hosting:

- cPanel / shared hosting
- Netlify
- Vercel (static export)
- AWS S3 + CloudFront
- Any static file server

```bash
npm run build
# Upload contents of `out` directory to your hosting
```

## Project Structure

```
src/
├── app/                    # Next.js App Router pages
│   ├── layout.tsx          # Root layout with fonts, header, footer
│   ├── page.tsx            # Homepage
│   ├── about/              # About page
│   ├── services/           # Service pages
│   ├── industries/         # Industry pages
│   ├── clients/            # Client testimonials
│   ├── resources/          # Blog, downloads, FAQs
│   ├── careers/            # Job listings
│   ├── contact/            # Contact form
│   ├── privacy/            # Privacy policy
│   ├── terms/              # Terms of service
│   ├── sitemap.ts          # Dynamic sitemap
│   └── robots.ts           # Robots.txt
├── components/
│   ├── ui/                 # Reusable UI components
│   ├── layout/             # Header, Footer, Mobile nav
│   ├── sections/           # Homepage sections
│   └── shared/             # Shared components (forms, CTAs)
├── content/                # Typed content objects
├── lib/                    # Utilities, helpers, constants
└── styles/                 # Global CSS
```

## Replacing Placeholder Content

### Images
Replace placeholder images in `/public/placeholders/`:
- `hero-team.jpg` - Team/engineers photo for hero
- `about-team.jpg` - Team photo for about page
- `office.jpg` - Office location photo

### Logo
Add your logo file to `/public/logo.svg` or `/public/logo.png`. The site will automatically use it if present. Otherwise, the text fallback will display.

### Content
- Replace sample testimonials in `src/content/testimonials.ts`
- Replace sample case studies in `src/content/testimonials.ts`
- Replace sample blog posts in `src/app/resources/blog/page.tsx`
- Update job listings in `src/content/careers.ts`

## Form Submission

All forms use WhatsApp as the primary submission channel:

1. User fills out form
2. Form validates client-side
3. WhatsApp opens with pre-filled message
4. User can also choose email fallback

To enable external form service (Web3Forms/Formspree):
1. Set `NEXT_PUBLIC_FORM_ENDPOINT` in `.env.local`
2. Set `NEXT_PUBLIC_WEB3FORMS_KEY` if using Web3Forms

## SEO

- Per-page metadata via `generateMetadata`
- JSON-LD structured data (Organization, LocalBusiness, Service, FAQ, Breadcrumb)
- Auto-generated sitemap.xml
- Optimized for target keywords (Tally Mumbai, IT AMC, etc.)

## Performance Targets

- Lighthouse ≥90 on all categories
- Static export for maximum performance
- Optimized images (use WebP/AVIF when adding real assets)
- Minimal client-side JavaScript

## Tech Stack

- **Framework:** Next.js 14 (App Router)
- **Language:** TypeScript
- **Styling:** Tailwind CSS v4
- **Animation:** Framer Motion
- **Icons:** Lucide React
- **UI Primitives:** Radix UI (accordion, dialog, etc.)

## License

Private repository for SOFT-TECH Computers Pvt. Ltd.

## Support

For technical support with this website, contact the development team.
=======
# Soft-tech-computers-website
>>>>>>> 9fd5c5444fcbd4c9254469d714ae5c282e8bea96
