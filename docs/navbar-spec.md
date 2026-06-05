# Floating Theme-Adaptive Navbar Specification

## Overview

A premium floating glassmorphic navbar with auto-hide on scroll, theme adaptation based on underlying section content, and smooth morph transitions. Detached from viewport edges with editorial feel.

---

## Visual Structure

```
┌────────────────────────────────────────────────────────────────────┐
│  (20px gap from top)                                               │
│  ┌──────────────────────────────────────────────────────────────┐  │
│  │  ┌──────────────────────────────────────────────────────┐    │  │
│  │  │ Logo │ | │ Nav Links... │    │ Login │ CTA │ Lang │  │    │  │
│  │  └──────────────────────────────────────────────────────┘    │  │
│  │                    .navbar (56px height)                      │  │
│  └──────────────────────────────────────────────────────────────┘  │
│                     .navbar-wrapper (centered, max-width)           │
└────────────────────────────────────────────────────────────────────┘
```

---

## HTML Structure

```html
<!-- Wrapper: handles positioning, padding, transitions -->
<div class="navbar-wrapper">
  <!-- Navbar: handles background, border-radius, theme colors -->
  <nav class="navbar" data-theme="dark">
    <!-- Container: max-width constraint, inner padding -->
    <div class="navbar-container">
      <!-- Left: Logo + divider + nav links -->
      <div class="navbar-left">
        <a href="/" class="logo">
          <img src="logo.svg" alt="Brand">
        </a>
        <span class="nav-divider"></span>
        <div class="nav-links">
          <a href="#" class="nav-link">Link 1</a>
          <a href="#" class="nav-link">
            Link 2
            <svg><!-- dropdown arrow --></svg>
          </a>
        </div>
      </div>
      
      <!-- Right: Login + CTA + Language -->
      <div class="navbar-right">
        <a href="#" class="nav-login">Log in</a>
        <div class="nav-buttons">
          <a href="#" class="btn-ghost">Get in Touch</a>
          <button class="btn-lang">
            <img src="flag.png" alt="EN">
          </button>
        </div>
        <!-- Mobile hamburger (hidden on desktop) -->
        <button class="mobile-menu-btn" aria-label="Open menu">
          <svg viewBox="0 0 24 24">
            <line x1="3" y1="6" x2="21" y2="6" stroke="currentColor" stroke-width="2"/>
            <line x1="3" y1="12" x2="21" y2="12" stroke="currentColor" stroke-width="2"/>
            <line x1="3" y1="18" x2="21" y2="18" stroke="currentColor" stroke-width="2"/>
          </svg>
        </button>
      </div>
    </div>
  </nav>
</div>

<!-- Mobile menu overlay (outside navbar-wrapper) -->
<div class="mobile-menu-overlay"></div>
<div class="mobile-menu">
  <div class="mobile-menu-header">
    <a href="/" class="logo"><img src="logo.svg" alt="Brand"></a>
    <button class="mobile-menu-close" aria-label="Close menu">
      <svg viewBox="0 0 24 24">
        <line x1="4" y1="4" x2="20" y2="20" stroke="white" stroke-width="2"/>
        <line x1="20" y1="4" x2="4" y2="20" stroke="white" stroke-width="2"/>
      </svg>
    </button>
  </div>
  <nav class="mobile-menu-nav">
    <a href="#" class="mobile-menu-link">Link 1</a>
    <a href="#" class="mobile-menu-link">Link 2</a>
  </nav>
  <div class="mobile-menu-footer">
    <a href="#" class="btn-mobile-cta">Get in Touch</a>
    <a href="#" class="btn-mobile-login">Log in</a>
  </div>
</div>
```

---

## CSS Specification

### Core Properties

```css
/* ===== WRAPPER ===== */
.navbar-wrapper {
  position: fixed;
  top: 20px;                          /* Gap from viewport top */
  left: 0;
  right: 0;
  z-index: 1000;                      /* Highest stacking context */
  display: flex;
  justify-content: center;
  padding: 0 40px;                    /* Horizontal viewport padding */
  pointer-events: none;               /* Allow clicks to pass through padding */
  transition: transform 300ms cubic-bezier(0.4, 0, 0.2, 1),
              opacity 300ms ease,
              padding 300ms ease;
}

/* Auto-hide state */
.navbar-wrapper.hidden {
  transform: translateY(-120px);
  opacity: 0;
  pointer-events: none;
}

/* ===== NAVBAR ===== */
.navbar {
  width: 100%;
  max-width: 1440px;                  /* Match content containers */
  height: 56px;
  display: flex;
  align-items: center;
  pointer-events: auto;               /* Re-enable clicks on navbar itself */
  
  /* Default state: transparent (hero section) */
  background: transparent;
  border: 1px solid transparent;
  border-radius: 0;
  backdrop-filter: none;
  
  transition: background 300ms ease,
              border-color 300ms ease,
              border-radius 300ms ease,
              backdrop-filter 300ms ease,
              box-shadow 300ms ease;
}

/* Scrolled state: glassmorphic */
.navbar.scrolled {
  border-radius: 16px;
}

/* Dark theme scrolled */
.navbar[data-theme="dark"].scrolled {
  background: rgba(1, 7, 14, 0.7);
  border-color: rgba(255, 255, 255, 0.12);
  backdrop-filter: blur(20px);
  -webkit-backdrop-filter: blur(20px);
  box-shadow: 0 8px 32px rgba(0, 0, 0, 0.3);
}

/* Light theme scrolled */
.navbar[data-theme="light"].scrolled {
  background: rgba(255, 255, 255, 0.8);
  border-color: rgba(0, 0, 0, 0.08);
  backdrop-filter: blur(20px);
  -webkit-backdrop-filter: blur(20px);
  box-shadow: 0 8px 32px rgba(0, 0, 0, 0.08);
}

/* ===== CONTAINER ===== */
.navbar-container {
  width: 100%;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 0 40px;
}
```

### Theme-Adaptive Colors

```css
/* ===== DARK THEME (white elements) ===== */
.navbar[data-theme="dark"] .logo img {
  filter: none !important;            /* Keep original (assumed white/light) */
}

.navbar[data-theme="dark"] .nav-link {
  color: rgba(255, 255, 255, 0.5);
}

.navbar[data-theme="dark"] .nav-link:hover {
  color: rgba(255, 255, 255, 0.8);
}

.navbar[data-theme="dark"] .nav-link svg path {
  stroke: rgba(255, 255, 255, 0.5) !important;
}

.navbar[data-theme="dark"] .nav-divider {
  background: rgba(255, 255, 255, 0.2);
}

.navbar[data-theme="dark"] .nav-login {
  color: #ffffff;
}

.navbar[data-theme="dark"] .btn-ghost {
  background: rgba(255, 255, 255, 0.05);
  border: 1px solid rgba(255, 255, 255, 0.1);
  color: #ffffff;
}

.navbar[data-theme="dark"] .btn-ghost:hover {
  background: rgba(255, 255, 255, 0.15);
  border-color: rgba(255, 255, 255, 0.5);
}

.navbar[data-theme="dark"] .mobile-menu-btn {
  background: rgba(255, 255, 255, 0.05);
  border: 1px solid rgba(255, 255, 255, 0.1);
}

.navbar[data-theme="dark"] .mobile-menu-btn svg {
  stroke: white !important;
}

/* ===== LIGHT THEME (dark elements) ===== */
.navbar[data-theme="light"] .logo img {
  filter: brightness(0) !important;   /* Invert to black */
}

.navbar[data-theme="light"] .nav-link {
  color: rgba(7, 12, 17, 0.6);
}

.navbar[data-theme="light"] .nav-link:hover {
  color: rgba(7, 12, 17, 0.9);
}

.navbar[data-theme="light"] .nav-link svg path {
  stroke: rgba(7, 12, 17, 0.6) !important;
}

.navbar[data-theme="light"] .nav-divider {
  background: rgba(7, 12, 17, 0.15);
}

.navbar[data-theme="light"] .nav-login {
  color: #070c11;
}

.navbar[data-theme="light"] .btn-ghost {
  background: rgba(7, 12, 17, 0.05);
  border: 1px solid rgba(7, 12, 17, 0.1);
  color: #070c11;
}

.navbar[data-theme="light"] .btn-ghost:hover {
  background: rgba(7, 12, 17, 0.1);
  border-color: rgba(7, 12, 17, 0.3);
}

.navbar[data-theme="light"] .mobile-menu-btn {
  background: rgba(7, 12, 17, 0.05);
  border: 1px solid rgba(7, 12, 17, 0.1);
}

.navbar[data-theme="light"] .mobile-menu-btn svg {
  stroke: #070c11 !important;
}
```

### Smooth Transitions (applied to all theme-affected elements)

```css
.logo img,
.nav-link,
.nav-link svg path,
.nav-divider,
.nav-login,
.btn-ghost,
.mobile-menu-btn,
.mobile-menu-btn svg {
  transition: all 300ms ease;
  will-change: filter, color, background, border-color, stroke;
}
```

### Responsive Breakpoints

```css
/* Large screens (1920px+) */
@media (min-width: 1920px) {
  .navbar { max-width: 1680px; }
}

/* Large screens (1600px+) */
@media (min-width: 1600px) {
  .navbar { max-width: 1400px; }
}

/* Tablet landscape (1024-1279px) */
@media (max-width: 1279px) {
  .navbar-wrapper { padding: 0 24px; }
  .navbar-container { padding: 0 24px; }
}

/* Tablet portrait (≤1023px) */
@media (max-width: 1023px) {
  .navbar-wrapper { padding: 0 16px; }
  .navbar-container { padding: 0 16px; }
  .navbar { height: 52px; }
  .navbar.scrolled { border-radius: 14px; }
  
  .nav-links,
  .nav-login,
  .nav-buttons { display: none; }
  .mobile-menu-btn { display: flex; }
}

/* Mobile (≤767px) */
@media (max-width: 767px) {
  .navbar-wrapper { top: 12px; }
  .navbar { height: 48px; }
  .navbar.scrolled { border-radius: 12px; }
  .navbar-container { padding: 0 12px; }
}
```

---

## JavaScript Specification

```javascript
(function() {
  const navbar = document.querySelector('.navbar');
  const navbarWrapper = document.querySelector('.navbar-wrapper');
  const mobileMenuBtn = document.querySelector('.mobile-menu-btn');
  const mobileMenu = document.querySelector('.mobile-menu');
  const mobileMenuOverlay = document.querySelector('.mobile-menu-overlay');
  const mobileMenuClose = document.querySelector('.mobile-menu-close');
  
  let lastScrollY = 0;
  let ticking = false;
  
  // ===== SCROLL HANDLER =====
  function handleScroll() {
    const scrollY = window.scrollY;
    const scrollDelta = scrollY - lastScrollY;
    
    // Auto-hide: hide on scroll down (past 100px), show on scroll up
    if (scrollY > 100) {
      if (scrollDelta > 0) {
        navbarWrapper.classList.add('hidden');
      } else if (scrollDelta < 0) {
        navbarWrapper.classList.remove('hidden');
      }
    } else {
      navbarWrapper.classList.remove('hidden');
    }
    
    // Scrolled state: add glassmorphic background
    if (scrollY > 50) {
      navbar.classList.add('scrolled');
    } else {
      navbar.classList.remove('scrolled');
    }
    
    // Theme detection
    detectTheme();
    
    lastScrollY = scrollY;
    ticking = false;
  }
  
  // ===== THEME DETECTION =====
  function detectTheme() {
    // Fixed detection point (60px from top of viewport)
    const detectionY = 60;
    const themedSections = document.querySelectorAll('section[data-theme], footer[data-theme]');
    let currentTheme = 'dark'; // Default
    
    themedSections.forEach(section => {
      const rect = section.getBoundingClientRect();
      // Check if the detection point is within this section
      if (rect.top <= detectionY && rect.bottom >= detectionY) {
        currentTheme = section.dataset.theme;
      }
    });
    
    navbar.dataset.theme = currentTheme;
  }
  
  // ===== SCROLL LISTENER (throttled via rAF) =====
  window.addEventListener('scroll', function() {
    if (!ticking) {
      requestAnimationFrame(handleScroll);
      ticking = true;
    }
  }, { passive: true });
  
  // ===== MOBILE MENU =====
  function openMobileMenu() {
    mobileMenu.classList.add('is-active');
    mobileMenuOverlay.classList.add('is-active');
    document.body.classList.add('menu-open');
    mobileMenuBtn.setAttribute('aria-expanded', 'true');
    // Focus first link for accessibility
    const firstLink = mobileMenu.querySelector('.mobile-menu-link');
    if (firstLink) firstLink.focus();
  }
  
  function closeMobileMenu() {
    mobileMenu.classList.remove('is-active');
    mobileMenuOverlay.classList.remove('is-active');
    document.body.classList.remove('menu-open');
    mobileMenuBtn.setAttribute('aria-expanded', 'false');
    mobileMenuBtn.focus();
  }
  
  if (mobileMenuBtn) {
    mobileMenuBtn.addEventListener('click', openMobileMenu);
  }
  if (mobileMenuClose) {
    mobileMenuClose.addEventListener('click', closeMobileMenu);
  }
  if (mobileMenuOverlay) {
    mobileMenuOverlay.addEventListener('click', closeMobileMenu);
  }
  
  // Close on Escape key
  document.addEventListener('keydown', function(e) {
    if (e.key === 'Escape' && mobileMenu.classList.contains('is-active')) {
      closeMobileMenu();
    }
  });
  
  // Close on resize to desktop
  window.addEventListener('resize', function() {
    if (window.innerWidth > 1023 && mobileMenu.classList.contains('is-active')) {
      closeMobileMenu();
    }
  });
  
  // Initial state
  handleScroll();
})();
```

---

## Mobile Menu CSS

```css
/* ===== OVERLAY ===== */
.mobile-menu-overlay {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(0, 0, 0, 0.5);
  z-index: 1001;
  opacity: 0;
  visibility: hidden;
  transition: opacity 300ms ease, visibility 300ms ease;
}

.mobile-menu-overlay.is-active {
  opacity: 1;
  visibility: visible;
}

/* ===== MENU PANEL ===== */
.mobile-menu {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  max-height: 100vh;
  background: #01070e;
  z-index: 1002;
  display: flex;
  flex-direction: column;
  transform: translateY(-100%);       /* Slide from top */
  transition: transform 300ms cubic-bezier(0.4, 0, 0.2, 1);
  padding-bottom: env(safe-area-inset-bottom, 20px);
}

.mobile-menu.is-active {
  transform: translateY(0);
}

/* ===== MENU HEADER ===== */
.mobile-menu-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 16px;
  padding-top: calc(16px + env(safe-area-inset-top, 0px));
  border-bottom: 1px solid rgba(255, 255, 255, 0.1);
}

.mobile-menu-close {
  width: 44px;
  height: 44px;
  display: flex;
  align-items: center;
  justify-content: center;
  background: transparent;
  border: none;
  cursor: pointer;
}

.mobile-menu-close svg {
  width: 24px;
  height: 24px;
}

/* ===== MENU NAV ===== */
.mobile-menu-nav {
  flex: 1;
  display: flex;
  flex-direction: column;
  padding: 16px;
  overflow-y: auto;
}

.mobile-menu-link {
  display: block;
  padding: 14px 16px;
  color: rgba(255, 255, 255, 0.7);
  font-size: 18px;
  font-weight: 500;
  text-decoration: none;
  transition: color 200ms ease, background 200ms ease;
}

.mobile-menu-link:hover {
  color: #ffffff;
  background: rgba(255, 255, 255, 0.05);
}

/* ===== MENU FOOTER ===== */
.mobile-menu-footer {
  display: flex;
  gap: 12px;
  padding: 16px;
  border-top: 1px solid rgba(255, 255, 255, 0.1);
}

.btn-mobile-cta,
.btn-mobile-login {
  flex: 1;
  padding: 14px 20px;
  font-size: 16px;
  font-weight: 600;
  text-align: center;
  text-decoration: none;
  border: none;
  cursor: pointer;
  transition: background 200ms ease, border-color 200ms ease;
}

.btn-mobile-cta {
  background: #ffffff;
  color: #070c11;
}

.btn-mobile-cta:hover {
  background: #2F6FEB;
  color: #ffffff;
}

.btn-mobile-login {
  background: rgba(255, 255, 255, 0.05);
  border: 1px solid rgba(255, 255, 255, 0.1);
  color: #ffffff;
}

.btn-mobile-login:hover {
  background: rgba(255, 255, 255, 0.15);
  border-color: rgba(255, 255, 255, 0.5);
}

/* ===== BODY LOCK ===== */
body.menu-open {
  overflow: hidden;
}
```

---

## Section Theme Attributes

Add `data-theme` attribute to all sections to enable theme detection:

```html
<!-- Dark sections -->
<section class="hero" data-theme="dark">...</section>
<section class="cta-section" data-theme="dark">...</section>
<section class="insights-section" data-theme="dark">...</section>
<footer class="footer" data-theme="dark">...</footer>

<!-- Light sections -->
<section class="client-logos" data-theme="light">...</section>
<section class="section" data-theme="light">...</section>
<section class="faq-section" data-theme="light">...</section>
```

---

## Behavior Summary

| Scroll Position | State | Background | Theme | Auto-hide |
|-----------------|-------|------------|-------|-----------|
| 0-50px | Hero | Transparent | Based on section | Always visible |
| 50px+ | Scrolled | Glassmorphic | Based on section | Hides on down, shows on up |

| Action | Result |
|--------|--------|
| Scroll down (past 100px) | Navbar slides up and fades out |
| Scroll up | Navbar reveals smoothly |
| Pass over dark section | Logo white, text white, bg dark glass |
| Pass over light section | Logo black, text dark, bg light glass |
| Click hamburger (mobile) | Full-width menu slides from top |
| Click overlay/close/Esc | Menu closes |
| Resize to desktop | Menu auto-closes |

---

## Design Tokens

```css
:root {
  /* Navbar dimensions */
  --navbar-height-desktop: 56px;
  --navbar-height-tablet: 52px;
  --navbar-height-mobile: 48px;
  --navbar-top-gap: 20px;
  --navbar-max-width: 1440px;
  
  /* Glassmorphic backgrounds */
  --navbar-bg-dark: rgba(1, 7, 14, 0.7);
  --navbar-bg-light: rgba(255, 255, 255, 0.8);
  --navbar-blur: blur(20px);
  
  /* Border colors */
  --navbar-border-dark: rgba(255, 255, 255, 0.12);
  --navbar-border-light: rgba(0, 0, 0, 0.08);
  
  /* Text colors */
  --navbar-text-dark: #ffffff;
  --navbar-text-dark-muted: rgba(255, 255, 255, 0.5);
  --navbar-text-light: #070c11;
  --navbar-text-light-muted: rgba(7, 12, 17, 0.6);
  
  /* Transitions */
  --navbar-transition-duration: 300ms;
  --navbar-transition-easing: ease;
  --navbar-hide-easing: cubic-bezier(0.4, 0, 0.2, 1);
  
  /* Border radius */
  --navbar-radius-desktop: 16px;
  --navbar-radius-tablet: 14px;
  --navbar-radius-mobile: 12px;
}
```

---

## Checklist

- [ ] Fixed position with z-index 1000+
- [ ] 20px gap from viewport top
- [ ] Max-width matches content containers (1440px default)
- [ ] Transparent background in hero
- [ ] Glassmorphic background when scrolled (50px+)
- [ ] Border-radius only when scrolled
- [ ] Auto-hide on scroll down (100px+)
- [ ] Auto-reveal on scroll up
- [ ] Theme-adaptive colors (dark/light)
- [ ] Smooth 300ms transitions on all properties
- [ ] Mobile hamburger menu at ≤1023px
- [ ] Full-width slide-from-top mobile menu
- [ ] ARIA attributes for accessibility
- [ ] Escape key closes mobile menu
- [ ] Body scroll lock when menu open
- [ ] Responsive scaling at all breakpoints
