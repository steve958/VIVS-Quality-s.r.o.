# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a static HTML website for VIVS Quality s.r.o., a Slovak transport and logistics company. The site is built with pure HTML, CSS, and vanilla JavaScript, featuring AOS (Animate On Scroll) animations and Google Translate integration. The website is performance-optimized with critical CSS inlined and lazy-loading for non-critical resources.

## Architecture & Structure

### Core Files
- `index.html` - Main landing page with company overview, services, career form, and contact sections
- `about.html` - Company information page
- `gallery.html` - Fleet photo gallery with lightbox functionality
- `contact.html` - Contact information and form
- `careers.html` - Career opportunities page
- `style.css` - Single comprehensive stylesheet (2500+ lines) containing all styles
- `test_pages.html` - Development testing file

### Assets Organization
- Fleet images: `fleet1.jpg` through `fleet9.jpg` (vehicle photos, ~150-500KB each)
- Hero carousel images: `mainfleet1.jpg`, `mainfleet2.jpg` (~300-360KB)
- Company branding: `logo.jpg` (125KB)
- Background image: `header-bg.jpg` (237KB)
- Gallery directory: Contains duplicate copies of fleet images and logo variants

## Key Features & Technologies

### Animation System
- **AOS (Animate On Scroll)**: Loaded asynchronously from CDN with fallback handling
- **Animation Types**: `data-aos="fade-up|zoom-in|fade-right|flip-left"` with delay variations
- **Initialization**: `AOS.init()` with configuration: `duration: 800, easing: 'ease-in-out', once: true, offset: 100`
- **Performance**: 3-second timeout fallback if AOS fails to load

### Multi-language Support
- **Google Translate API**: Integrated with custom language switcher UI
- **Languages**: English (en), Serbian (sr), Slovak (sk), German (de)
- **Implementation**: `doGTranslate(lang_pair)` function with retry logic (5 attempts)
- **UI**: Flag-based selection using flagcdn.com (40px width flags)
- **Styling**: Google Translate banner hidden with custom CSS

### Hero Section Architecture
- **Background**: Multi-layer approach with gradient animations and image overlay
- **Gradients**: `gradientShift` animation cycling through color positions
- **Overlay System**: Dual pseudo-elements (::before for image, ::after for radial gradient)
- **Responsive Text**: `clamp()` functions for fluid typography (3rem - 6rem)

### Interactive Components
- **Lightbox Gallery**: Custom implementation with backdrop blur and modal controls
- **Quote Calculator**: Dynamic pricing with country/weight/service matrices
- **Floating Action Buttons**: Fixed position contact buttons with animation delays
- **Mobile Menu**: Accessible toggle with ARIA attributes and keyboard navigation

### Advanced CSS Architecture
- **CSS Custom Properties**: 48+ CSS variables for consistent theming
- **Responsive Design**: Mobile-first approach with 768px and 480px breakpoints  
- **Animations**: 8+ custom keyframe animations (float, pulse, gradientShift, etc.)
- **Layout Systems**: CSS Grid for complex layouts, Flexbox for component alignment
- **Performance**: Critical CSS inlined in `<head>` for above-the-fold content

## CSS Architecture & Design System

### Color System (CSS Custom Properties)
- **Primary Colors**: `--primary-blue: #1B365D`, `--secondary-orange: #F39C12`, `--accent-green: #27AE60`
- **Neutral Palette**: `--dark-gray: #2C3E50`, `--medium-gray: #7F8C8D`, `--light-gray: #BDC3C7`, `--pure-white: #FFFFFF`
- **Status Colors**: Success, Warning, Error, Info variants
- **Gradients**: Primary gradient and hero gradient with complex opacity layers

### Typography Scale
- **Fonts**: `--font-heading: 'Montserrat'`, `--font-body: 'Open Sans'`
- **Scale**: `--text-xs` (12px) through `--text-6xl` (60px) using rem units
- **Weights**: Light (300) through Extrabold (800)
- **Responsive**: `clamp()` functions for fluid scaling across devices

### Component Architecture
- **`.section`**: Base container (5rem padding desktop, 3rem tablet, 2rem mobile)
- **`.cards`**: CSS Grid with `minmax(350px, 1fr)` responsive columns
- **`.card`**: Glass morphism with `backdrop-filter: blur(10px)` and hover transforms
- **`.hero`**: Complex layered background with gradient animations and overlay system
- **`.stats-section`**: Full-width dark section with contrasting statistics display
- **`.coverage-section`**: Interactive country grid with flag-based visual design

### Advanced Layout Patterns
- **Flexbox**: Primary layout method for navigation, cards, and form elements
- **CSS Grid**: Used for responsive card grids, calculator forms, and coverage maps
- **Positioning**: Sticky navigation, fixed floating buttons, absolute overlays
- **Responsive Strategy**: Mobile-first with container queries and intrinsic sizing

## Development Commands

This is a static website with no build process. Files can be opened directly in a browser or served via any web server.

### Local Development
```bash
# Serve files locally (Python)
python -m http.server 8000

# Or using Node.js  
npx serve .

# Or using PHP (if available)
php -S localhost:8000

# Or using Live Server (VS Code extension)
# Right-click index.html → "Open with Live Server"
```

### Performance Testing
```bash
# Test all pages for functionality
# Open test_pages.html to verify navigation and forms

# Performance audit (using Chrome DevTools)
# Run Lighthouse audit on each page
# Check Core Web Vitals (LCP, CLS, FID)

# Image optimization check
# Verify all images are properly sized (fleet images ~150-500KB)
```

### Content Updates
```bash
# When adding new fleet images:
# 1. Add to root directory as fleetX.jpg
# 2. Update gallery.html with new image entries
# 3. Update gallery/ directory if maintaining duplicates
# 4. Optimize images to ~200-400KB for web performance
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

## JavaScript Functionality

### Core Interactive Features
- **Mobile Menu Toggle**: Accessible implementation with ARIA attributes and keyboard support
- **Quote Calculator**: Dynamic pricing engine with country/weight/service matrices
- **Google Translate Integration**: Retry logic with 5-attempt fallback system
- **AOS Animation Init**: Defensive loading with timeout fallback
- **Lightbox Gallery**: Custom modal implementation (if present in gallery.html)

### Event Handling
- **Form Validation**: Built-in HTML5 validation with custom styling
- **Keyboard Navigation**: Escape key handling for mobile menu and modals  
- **Click Interactions**: Country cards, floating buttons, and calculator
- **Focus Management**: Proper focus flow for accessibility

## Forms & Email Integration

### Contact System Architecture
- **Method**: `mailto:` actions pointing to vivsquality@gmail.com
- **Encoding**: `enctype="multipart/form-data"` for file uploads
- **Form Types**:
  - Career applications (with CV upload support)
  - Quick inquiry form (name/email/message)
  - Quote calculator (dynamic price generation)

### Form Field Patterns
- **Required Fields**: HTML5 `required` attribute with custom CSS validation styling
- **Input Types**: `text`, `email`, `tel`, `file`, `textarea`, `select`
- **File Handling**: CV uploads with `.pdf,.doc,.docx` accept attribute
- **Accessibility**: Proper label associations and error messaging

## Content Management

### Company Information
- Company: VIVS Quality s.r.o.
- Location: Bratislava, Slovakia  
- Services: EU transport, courier services, vans up to 3.5t
- Fleet: Iveco and Fiat Ducato vehicles
- Contact: +421 911 868 337, vivsquality@gmail.com

### SEO & Meta Tags
- **Meta Structure**: Comprehensive descriptions and keyword targeting
- **Open Graph**: Full OG tags for Facebook/LinkedIn sharing
- **Twitter Cards**: Summary card with large image support
- **Performance**: Preconnect to Google Fonts, DNS prefetch for CDNs
- **Multi-language**: Meta content adapts to Google Translate selections

## Performance Optimizations

### Critical Rendering Path
- **Inline Critical CSS**: Above-the-fold styles inlined in `<head>`
- **Async Resource Loading**: Non-critical CSS loaded with `media="print" onload="this.media='all'"`
- **Font Loading**: Preconnect to Google Fonts with crossorigin attribute
- **CDN Prefetching**: DNS prefetch for external resources (AOS, FontAwesome)

### Image Optimization
- **File Sizes**: Fleet images optimized to 150-500KB range
- **Loading Strategy**: `loading="eager"` for logo, lazy loading for gallery images
- **Formats**: JPEG for photos, maintain quality/size balance
- **Responsive Images**: CSS object-fit and aspect-ratio for consistent display

### JavaScript Performance
- **Async Loading**: AOS library loaded asynchronously with callback
- **Error Handling**: Fallbacks for failed library loads
- **Minimal Inline JS**: Only critical functionality inline, rest async
- **Event Delegation**: Efficient event handling for dynamic content

## Accessibility Standards

### WCAG Compliance Features
- **Semantic HTML**: Proper heading hierarchy (h1-h6), nav, main, section elements
- **ARIA Attributes**: Complete implementation for mobile menu and interactive elements
- **Focus Management**: Visible focus indicators with high contrast
- **Keyboard Navigation**: Full keyboard support for all interactive elements
- **Screen Reader Support**: Skip links and sr-only content classes
- **Color Contrast**: Meets WCAG AA standards with high contrast mode support
- **Reduced Motion**: `prefers-reduced-motion` media query support