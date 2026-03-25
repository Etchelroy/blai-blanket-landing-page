# Cozy Blanket Brand Landing Page - Research Brief

SUMMARY: A modern, conversion-focused landing page for a direct-to-consumer blanket brand that showcases product quality, builds emotional connection, and drives purchase intent through strategic content hierarchy and micro-interactions.

APPROACH: Next.js or Astro (static-first with optional interactivity) + Tailwind CSS for styling + Framer Motion for subtle animations. Choose Next.js if you need server-side commerce features (dynamic pricing, inventory); choose Astro if this is purely marketing-focused. Both enable fast Core Web Vitals scores critical for conversion. Add Shopify or custom cart integration only if selling directly; otherwise embed affiliate links or CTAs to external store.

REQUIREMENTS:

HERO SECTION
- Full-viewport hero with high-quality product lifestyle photography (blanket in cozy room setting)
- Primary headline emphasizing emotional benefit (comfort, relaxation, warmth) not just product name
- Secondary subheadline with specific value prop (e.g., "hand-stitched organic cotton, lifetime warranty")
- Single above-fold CTA button (Shop Now / Explore Collections) with subtle hover elevation
- Hero should load within 75ms (optimize image via WebP, lazy loading, srcset for responsive)

PRODUCT SHOWCASE SECTION
- 3-4 featured blanket collections in card layout with 2-column grid on desktop, 1-column on mobile
- Each card: hero image, collection name, 2-3 benefit bullets, price range, "View Details" link
- Implement smooth image fade-in on scroll using Intersection Observer (not scroll-jank)
- High-contrast product images against consistent neutral background for visual consistency

BENEFITS/WHY US SECTION
- 4 benefit modules in horizontal grid (responsive to vertical stack on mobile)
- Each module: icon (SVG, not image), short headline (4-6 words max), 1-sentence description
- Icons should use consistent stroke weight and 8px grid alignment
- Examples: "Sustainable Materials," "Lifetime Comfort Guarantee," "Free Shipping," "Handcrafted Quality"

TESTIMONIALS SECTION
- 3 customer testimonial cards with star ratings (5-star display as filled SVG icons)
- Include customer name, location (city/state), and 2-3 sentence quote
- Rotate testimonials on load or via simple dot indicator for 3 different testimonials
- Ensure real names/images (stock photos acceptable with disclaimer if needed)

CALL-TO-ACTION SECTION
- Exit-intent CTA offering incentive (10% off first order, free shipping threshold)
- Should appear after 80% scroll depth or 40 seconds on page
- Dismiss option required (X button) to avoid user friction
- Form captures email only (optional: first name), no heavy form friction

FOOTER
- Newsletter signup with inline email input + subscribe button
- Links: About, Care Guide, Shipping/Returns, Privacy Policy, Contact
- Social media icons (Instagram, Facebook, Pinterest) linking to brand accounts
- Copyright notice with year
- Subtle background color differentiation from main content

TECHNICAL REQUIREMENTS
- Fully responsive: tested at 375px (mobile), 768px (tablet), 1440px+ (desktop)
- Navigation: sticky header with logo + mobile hamburger menu on screens < 768px
- All text must meet WCAG AA contrast ratio (4.5:1 minimum for body text)
- Animations: Framer Motion for entrance animations (fade-in, slide-up, scale), keep duration 300-500ms, use ease-out curves
- Load time target: Largest Contentful Paint < 2.5s, Cumulative Layout Shift < 0.1

CONSTRAINTS:

- Image optimization mandatory: use next/image or Astro's Image component with srcset, defer non-critical images
- No external analytics library bloat; use native Web Vitals API or minimal tracking script
- Mobile-first CSS approach (develop for 375px first, then enhance)
- Browser support: Chrome/Edge 90+, Firefox 88+, Safari 14+, mobile Safari 14+
- Accessibility: semantic HTML, keyboard navigation support (tab order logical), skip-to-main link, ARIA labels where needed
- Performance budget: total JavaScript < 50kb gzipped (excluding third-party cart/shop integrations)

NOTES:

BEST PRACTICES
- Use system fonts for fast render (fallback: "Inter", sans-serif, or Outfit for slightly warmer feel matching brand comfort messaging)
- Implement hero image as background-image with object-fit: cover for consistent aspect ratio across viewports
- Product card images should have consistent aspect ratio (3:4 or 4:3) to prevent layout jank on load
- Color palette: warm neutrals (cream #FAF8F3, warm gray #8B8680, deep brown #4A403F) with single accent color (sage green #9CAF88 or terracotta #C97856) for CTAs and hover states

EDGE CASES & WATCH-OUTS
- Slow 3G networks: ensure critical LCP image loads with aggressive compression; test with DevTools throttling
- Dark mode: consider if brand aligns with it; if implemented, ensure color contrast maintained in both modes
- Form submission: prevent double-submit on CTA button (disable button + spinner state during submission)
- Newsletter signup: use server-side validation, sanitize email input, implement CAPTCHA if spam risk is high
- Image loading: use skeleton loaders (pulse animation) for product images while fetching to prevent CLS
- Testimonial rotation: if implementing carousel, disable auto-rotation on mobile to prevent unexpected jumps during read
- Cookie consent: if using tracking, display minimal but compliant banner (test GDPR compliance for EU traffic)
- Print styles: ensure hero and primary CTA remain visible if user prints page (unlikely but considerate UX)

DOCUMENTATION NEEDS FOR DEVELOPER
- Component inventory: Hero, ProductCard, BenefitModule, TestimonialCard, CTABanner, Footer, Navigation (file names, props, usage examples)
- Content structure: JSON or frontmatter format for testimonials, benefits, product collections (for easy updates without code changes)
- Color/spacing tokens: Tailwind config export with exact hex values, spacing scale (4px, 8px, 16px, 24px, 32px)
- Image optimization guide: required dimensions for each image type (hero: 1920x1080, product cards: 600x800, icons: 64x64)
- Deployment: static generation strategy, image CDN integration notes, environment variables for shop links or analytics