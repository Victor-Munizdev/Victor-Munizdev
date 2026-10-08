# Victor Muniz — Portfolio

Personal site of Victor Muniz, Full-Stack Developer / Software Engineer.

**Live:** [munizvr.vercel.app](https://munizvr.vercel.app) (Portuguese) · [munizvr.vercel.app/en](https://munizvr.vercel.app/en) (English)

The page is built to answer four questions in a few seconds: who I am, what I do, why that is different, and how to reach me. It presents case studies, experience, process, stack and services around one idea: end-to-end ownership, from the problem to production support.

## Stack

| Area | Choice |
| --- | --- |
| Framework | Next.js 15 (App Router), React 18, TypeScript (strict) |
| Styling | Tailwind CSS v4, design tokens in `app/globals.css` |
| Motion | GSAP (ScrollSmoother, ScrollTrigger) with `@gsap/react` |
| Icons and type | Lucide, Geist |
| Hosting | Vercel |

## How it is built

- **Server Components by default.** Every section renders on the server and the page is statically generated. Only three pieces run on the client: the mobile menu, the language dropdown and the scroll choreography.
- **Content is data.** All copy lives in typed files under `data/`. Each text is a `Localized` value, so the compiler rejects a string that is missing in Portuguese or English.
- **Two indexable locales.** Portuguese is served at `/` and English at `/en`, each with its own canonical URL and `hreflang` alternates. The header dropdown links the two.
- **Motion that degrades.** GSAP loads in a separate chunk after hydration. The HTML is complete without JavaScript, and `prefers-reduced-motion` disables smoothing, pinning and scrubbing.
- **SEO.** Per-locale metadata, generated Open Graph and Twitter images, `robots.txt`, `sitemap.xml` and JSON-LD (`ProfilePage` / `Person`).

## Project structure

```
app/
  (pt)/            Portuguese root layout and page (/)
  (en)/en/         English root layout and page (/en)
  globals.css      Design tokens and base styles
  robots.ts, sitemap.ts
components/
  layout/          Header, footer, mobile menu, language dropdown
  sections/        Hero, proof, cases, experience, process, stack, services, credentials, contact
  motion/          Smooth-scroll wrapper and GSAP choreography
  ui/              Small primitives (button link, external link, section, tags, flags)
data/              All content, in Portuguese and English
lib/               i18n, SEO, Open Graph image, motion modules
types/             Content types
public/            Screenshots and certificates
```

`PRODUCT.md` records the product context and `DESIGN.md` records the design system.

## Editing content

Content changes do not touch components.

- **Add a case study:** append an object to `caseStudies` in `data/cases.ts`. A metric is only published with its source and period in `context`.
- **Update experience:** edit `data/experience.ts`. The first role is rendered as the current one.
- **Change interface text:** edit `data/dictionary.ts`.

## Running locally

Requires Node.js 18.18 or later.

```bash
npm install
npm run dev      # http://localhost:3000
npm run build    # production build
npm run start    # serve the production build
```

### Environment

No variable is required. `NEXT_PUBLIC_SITE_URL` overrides the public URL used in canonical links, the sitemap and Open Graph tags; see `.env.example`.

## Quality

Measured with Lighthouse against a local production build:

| | Performance | Accessibility | SEO |
| --- | --- | --- | --- |
| Mobile | 98 | 100 | 100 |
| Desktop | 100 | 100 | 100 |

The layout was checked at 390, 412, 430, 820 and 1440 px in both languages, with keyboard navigation and reduced motion.

## Contact

- Email: [munizzvr@gmail.com](mailto:munizzvr@gmail.com)
- LinkedIn: [linkedin.com/in/munizvr](https://www.linkedin.com/in/munizvr/)
- GitHub: [github.com/Victor-Munizdev](https://github.com/Victor-Munizdev)
