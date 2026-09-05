# Personal Site UI/UX Case Study

## Context

The site represents one person working across several creative disciplines. That creates a positioning and navigation challenge: the experience needs to feel cohesive without flattening the differences between tattoo work, social content, branding, websites, and visual projects.

The design direction intentionally avoids a generic portfolio aesthetic. Instead, it uses a scrapbook and studio-board language to communicate personality, process, and creative range.

## UX problem

A highly expressive visual style can create several risks:

- hierarchy becomes unclear
- decorative elements compete with content
- mobile layouts become fragile
- users cannot immediately tell what is clickable
- large assets slow the experience
- multiple disciplines feel disconnected

The design task was therefore not only to make the site distinctive. It was to make a distinctive site remain understandable.

## Experience structure

```text
First impression
├── identity
├── visual tone
└── primary positioning

Understand the offer
├── services
└── work process

Build trust
├── selected projects
└── tattoo portfolio

Take action
└── contact
```

The hierarchy moves from identity to offer to evidence to conversion.

## Visual-system decisions

### 1. Scrapbook as a system, not random decoration

The visual language uses paper, grids, tape, doodles, polaroids, and layered media.

A useful mental model is:

```text
Layer 1 | quiet background texture
Layer 2 | main photography and project media
Layer 3 | limited decorative accents
Layer 4 | text, controls, and CTAs
```

The most important usability rule is that decoration must never become the interaction layer.

### 2. Different media get different frames

The selected-work experience uses presentation patterns that reflect the content:

- phone-like frames for social content
- polaroid or print metaphors for visual work
- direct screen/project presentation where appropriate

This creates variety while keeping the overall site recognizable as one brand.

### 3. Typography carries brand personality

Large display typography creates a poster-like tone and gives the website its editorial personality.

The tradeoff is responsive behavior. Large titles need breakpoint-specific sizing and container rules so personality does not create clipping or unreadable wrapping.

### 4. RTL is part of composition

The page combines Hebrew RTL content with English brand phrases. Direction is therefore a visual-layout concern, not only a text property.

Section alignment, arrows, media direction, navigation, and decorative placement all need to feel natural in an RTL experience.

## Audit findings and iteration

A structured audit identified several categories of friction.

### Visual hierarchy

Some sections contained enough collage elements that multiple items competed for attention at once.

Response:

- reduce active decorative elements per section
- give primary text and CTAs cleaner surrounding space
- distinguish background texture from content-bearing layers

### Mobile robustness

Absolute positioning and negative spacing created compositions that could work at one width but become unstable at another.

Response:

- test specific mobile widths rather than one generic mobile breakpoint
- reduce decorative layers on smaller viewports
- protect content from overlap and horizontal overflow
- treat mobile composition as its own layout problem

### Affordance

Visual project objects could sometimes read as images rather than links.

Response:

- improve hover/focus/tap treatment
- keep interactive arrows and CTAs visible
- avoid decorative styling that obscures whether an object is actionable

### Accessibility

The visual design required explicit checks for:

- focus-visible states
- touch-target size
- reduced motion
- readable contrast
- navigation behavior
- content not being obscured by decorative layers

A production accessibility review should go further with keyboard testing, screen-reader testing, semantic checks, and automated tooling.

## Responsive QA model

The QA process was organized across desktop, tablet, and several mobile widths rather than a single "responsive" check.

Important checks include:

- no horizontal overflow
- fixed header does not cover anchors
- mobile menu opens and closes correctly
- hero composition remains intentional
- collage layers remain readable
- service cards stack cleanly
- selected-work links remain tappable
- tattoo frames preserve image alignment
- contact actions remain reachable

## Product perspective

Although this is a personal website, it still behaves like a product with different user goals.

A visitor may want to:

- understand who I am
- identify whether I offer a relevant service
- evaluate the quality and style of my work
- understand how I work
- contact me

The site needs to support these goals without requiring the visitor to decode the visual concept first.

## What I learned from the project

The main design lesson is that originality and usability are not opposing goals, but expressive interfaces need stronger rules than minimal interfaces.

The more visual freedom a system allows, the more important it becomes to define:

- hierarchy
- spacing rules
- layer behavior
- interaction affordance
- responsive fallback behavior
- asset budgets

That is what turns a collage aesthetic from decoration into a repeatable UI system.
