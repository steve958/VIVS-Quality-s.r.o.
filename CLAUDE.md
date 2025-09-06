# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a static HTML website for VIVS Quality s.r.o., a Slovak transport and logistics company. The site is built with pure HTML, CSS, and vanilla JavaScript, featuring AOS (Animate On Scroll) animations and Google Translate integration.

## Architecture & Structure

### Core Files
- `index.html` - Main landing page with company overview, services, career form, and contact sections
- `about.html` - Company information page
- `gallery.html` - Fleet photo gallery with lightbox functionality
- `contact.html` - Contact information and form
- `style.css` - Single stylesheet containing all styles
- `careers.html` - Career opportunities page

### Assets
- Fleet images: `fleet1.jpg` through `fleet9.jpg` (vehicle photos)
- Main carousel images: `mainfleet1.jpg`, `mainfleet2.jpg`
- Company branding: `logo.jpg`, `logo.png`
- Background: `header-bg.jpg`
- Additional gallery assets in `gallery/` directory

## Key Features & Technologies

### Animation System
- Uses AOS (Animate On Scroll) library loaded from CDN
- Animations triggered with `data-aos` attributes (fade-up, zoom-in, fade-right)
- Initialize with `AOS.init()` in script tags

### Multi-language Support
- Google Translate integration with custom language switcher
- Supports English, Serbian, Slovak, and German
- Flag-based language selection with `doGTranslate()` function
- Custom styling to hide Google Translate banner

### Image Carousel
- CSS-based infinite scroll carousel in hero section
- Uses `@keyframes scroll-carousel` animation
- Displays company fleet images with opacity overlay

### Interactive Elements
- Lightbox gallery functionality in `gallery.html`
- Fixed contact buttons (call/email) on main page
- Scroll-to-top button on contact page
- Hover effects on fleet images

### Layout System
- Flexbox-based responsive design
- Sticky navigation bar
- Footer always at bottom using flexbox
- Mobile-responsive with media queries at 768px breakpoint

## Styling Architecture

### Color Scheme
- Primary yellow: `#facc15` (service sections)
- Background yellow: `#f4c200` (forms/buttons)
- Dark footer: `#222` / `#000000`
- Light sections: `#f9f9f9`

### Typography
- Main heading font: 'Poppins' (Google Fonts)
- Base font: sans-serif
- Responsive font sizing

### Component Patterns
- `.section` - Standard content sections with padding
- `.cards` - Flexbox grid for service/feature cards
- `.hero` - Full-width header sections
- `.career-section` - Two-column layout for forms

## Development Commands

This is a static website with no build process. Files can be opened directly in a browser or served via any web server.

### Local Development
```bash
# Serve files locally (Python)
python -m http.server 8000

# Or using Node.js
npx serve .
```

### File Structure
```
/
├── index.html          # Main page
├── about.html          # About page  
├── gallery.html        # Photo gallery
├── contact.html        # Contact page
├── careers.html        # Careers page
├── style.css           # All styles
├── logo.jpg           # Company logo
├── header-bg.jpg      # Background image
├── mainfleet1.jpg     # Carousel image 1
├── mainfleet2.jpg     # Carousel image 2
├── fleet1-9.jpg       # Gallery images
└── gallery/           # Additional assets
    ├── fleet1-9.jpg   # Duplicate gallery images
    ├── logo.jpg       # Logo copy
    └── logo.png       # PNG logo variant
```

## Forms & Functionality

### Contact Forms
- Use `mailto:` action pointing to vivsquality@gmail.com
- No backend processing - relies on user's email client
- File uploads supported for CV attachments (careers form)

### Email Integration
- Career applications: `action="mailto:vivsquality@gmail.com"`
- Quick inquiries: Similar mailto integration
- Fixed contact buttons link to phone/email

## Content Management

### Company Information
- Company: VIVS Quality s.r.o.
- Location: Bratislava, Slovakia  
- Services: EU transport, courier services, vans up to 3.5t
- Fleet: Iveco and Fiat Ducato vehicles
- Contact: +421 911 868 337, vivsquality@gmail.com

### SEO & Meta Tags
- Comprehensive meta descriptions and keywords
- Open Graph tags for social sharing
- Twitter card metadata
- Multi-language meta content