# Performance and QA Case Study

## Why performance was a design problem

The website's visual identity depends on rich, layered assets. Several source textures and decorative SVG exports were very large, so optimization could not be treated as a simple "compress everything" task.

The real question was:

> Which assets can be deferred or re-exported without damaging the visual identity, and which assets are critical to the first impression?

## Asset review

The source project contained several decorative paper and texture assets in the multi-megabyte range, including some larger than 20 MB.

This created three competing goals:

1. preserve the intended scrapbook composition
2. avoid unnecessary first-load cost
3. prevent visual regressions caused by aggressive format conversion

## Optimization decisions

### Defer content that is safely below the fold

Below-the-fold imagery can use lazy loading and asynchronous decoding where the user does not need it immediately.

### Keep critical first-viewport assets available

Hero and identity assets contribute directly to the first impression, so blindly lazy-loading them can make the page feel visually incomplete during entry.

### Re-export source artwork when compression is risky

Very large texture-style SVGs may contain complex vector data or embedded information. Re-exporting from the design source gives more control than running an automatic optimizer and hoping the appearance remains unchanged.

### Respect reduced motion

Hover and motion polish should have a reduced-motion-safe fallback so visual personality does not require animation for every user.

## Remaining performance opportunities

- re-export the heaviest texture assets into optimized formats after visual comparison
- generate responsive variants for assets displayed much smaller than their source dimensions
- run Lighthouse against the deployed production build
- measure Largest Contentful Paint and layout stability after asset changes
- validate caching and compression in the actual hosting environment
- test social-preview assets separately from in-page media

## QA strategy

The site uses a visually layered layout, so QA needs to cover more than whether the page technically renders.

### Desktop

Key checks:

- no unexpected layout jumps
- fixed navigation remains readable
- collage layers align as intended
- project links and CTAs remain clearly interactive
- all sections maintain hierarchy at large widths

### Tablet

Key checks:

- no horizontal overflow
- desktop and mobile navigation transition at the intended breakpoint
- overlapping composition remains controlled
- typography scales without awkward wrapping

### Mobile

The source QA plan explicitly considers multiple phone widths rather than treating mobile as one viewport.

Key checks:

- no horizontal overflow
- header and menu behavior remain stable
- hero composition remains intentional
- decorative assets do not obscure copy
- cards and CTAs remain tappable
- selected work remains understandable without hover
- tattoo and contact layouts remain usable

## Production checks

A complete launch pass also includes:

- social and contact link verification
- Open Graph metadata
- sitemap and robots behavior
- browser-console review
- successful production build
- deployed-site testing rather than relying only on local development

## Product-design takeaway

Performance work on a visual portfolio should not happen separately from design.

When visual assets are the interface language, the right optimization process is:

```text
Measure
   ↓
Understand visual role
   ↓
Choose defer / resize / re-export / keep
   ↓
Compare visually
   ↓
Test across devices
```

That keeps performance decisions tied to the user experience instead of optimizing file sizes in isolation.
