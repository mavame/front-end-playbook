# Dynamit's Front-end Playbook

---

# Table of Contents

1. [Development Process](#development-process)
  * [Version Control](#version-control)
  * [Code Quality](#code-quality)
  * [Ops](#ops)
  * [Preventative Maintenance](#preventative-maintenance)
2. [Markup](#markup)
3. [Style Sheets](#style-sheets)
4. [JavaScript](#javascript)
5. [Performance](#performance)
6. [SEO](#seo)
7. [Accessibility](#accessibility)

---

# Development Process

## Version Control

- use version control
- use semver
- keep branching to a minimum, prune dead branches
- associate a ticket number with a commit when applicable

## Code Quality

- Adhere to the Code Style Guide
- DRY
- Leverage Technical Debt
- Use IE VMS to test code
- Thoroughly document code use JSDOC conventions

## Ops

- use codepen to rapidly protoype ideas 
- use the front-end starter kit when starting a project. Continually improve it by contributing learning during each project.
- use gulp to manage the asset compilation pipeline
- use webpack for asset bundling

## Preventative Maintenance

- keep tooling up to date
- keep disk perms clean

# Markup

- use semantic markup?
- structure pages (headings, sections) in logical, linear order
- `button type=button` outside the context of a form

# Style Sheets

- adhere to the Code Style Guide
- use Sass
- use low-specificty selectors. avoid ids, tags, combining selectors, prefer classes and attr selectors
- compose styles mobile-first (example of good media query)
- use bullet-proof font-face declaration

# JavaScript

- use lodash
- use js-cookie
- write in modules

# Performance

- use the following metrics as a baseline for performance (include table)
- consider subsetting fonts
- use progressive jpgs
- load scripts async (async attr)
- use dns prefetching
- gzip
- minify scripts and stylesheets
- reduce http requests
- cache assets for immediate loading on subseqent visits
- defer loading large images. use lofi preview images on initial load https://code.facebook.com/posts/991252547593574/the-technology-behind-preview-photos/

# SEO

Include a canonical url tag on each page. Use [trailing slashes](http://googlewebmastercentral.blogspot.com/2010/04/to-slash-or-not-to-slash.html) appropriately. Prefer `https` when available.

```html
<link rel="canonical" href="https://example.com/some-page" />
```

- use a well-formatted title tag on every page
- avoid keyword meta
- one h1 per page. h1 is most important page-specific content

# Accessibility
