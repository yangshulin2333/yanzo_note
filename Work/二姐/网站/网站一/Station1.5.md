
# Website Master Specification Document (v3.0)

**Project Name:** Particle.io Corporate Site Redesign

**Document Type:** Full Technical & Content Specification

**Version:** 3.0 (Expanded Detail)

**Based on Visual Source:** `image_33d9fd.jpg` (Navigation Dropdown & Hero Banner)

---

## 1. Global Navigation Architecture (Detailed Interaction Spec)

**Component Status:** Sticky Fixed Header (Z-Index: 1000)

**Visual Logic:** Dark Mode background (`#000000` or equivalent dark hex). White Text.

### 1.1 "Supported Devices" Mega-Menu (Per Screenshot)

_Data Source: Validated against uploaded visual reference._

**Trigger:** Hover over "Supported devices".

**Layout:** 2-Column Dropdown (Dark Glassmorphism background).

**Column 1: Category Navigation (Left)**

- **Item 1:** Single-board computers
    
    - _Sub-text:_ For all-in-one systems
        
    - _Interaction:_ Hover highlights row.
        
- **Item 2:** System on Modules (SoMs)
    
    - _Sub-text:_ For embedded systems
        
- **Item 3:** Development boards
    
    - _Sub-text:_ For rapid prototyping and PoCs
        
- **Item 4:** Gateways
    
    - _Sub-text:_ For retrofit applications
        
- **Footer Link:** `> Shop all devices` (Arrow icon required)
    

**Column 2: Dynamic Product Preview (Right)**

_Logic: Displays specific "NEW" items when "Single-board computers" is active._

- **Product A:** **Tachyon** `[BADGE: NEW]`
    
    - _Icon:_ Generic SBC Icon (Small)
        
    - _Description:_ 5G SBC + AI accelerator
        
    - _Link Target:_ `/tachyon`
        
- **Product B:** **M-HAT** `[BADGE: NEW]`
    
    - _Icon:_ Signal/Connectivity Icon
        
    - _Description:_ Cellular connectivity for 40-pin SBCs
        
    - _Note:_ This refers to the "Cellular HAT" for Raspberry Pi compatibility.
        
- **Product C:** **M1 Enclosure** `[BADGE: NEW]`
    
    - _Icon:_ Box/Case Icon
        
    - _Description:_ Industrial-grade IP67-ready case
        

### 1.2 Other Navigation Links

- **Platform:** (Dropdown) -> Edge, Connectivity, Cloud.
    
- **Solutions:** (Dropdown) -> Asset Tracking, Energy, HVAC.
    
- **Developers:** (Dropdown) -> Docs, Forum.
    
- **Pricing:** (Direct Link).
    

### 1.3 Action Area (Right Aligned)

- **Primary Button:** `Contact sales`
    
    - _Style:_ Pill-shaped, White Background, Black Text.
        
    - _Hover State:_ Light Gray background (`#F5F5F5`).
        

---

## 2. Homepage Content & Layout Specifications

### 2.1 Hero Promotional Banner (The "Tachyon" Block)

_Visual Reference: Center-floating card overlaying the hero image._

**Layout:** Rounded Card Container (Radius: 12px). Dark Gradient Background.

**Content Inventory:**

- **Image (Left):** High-res product shot of the Tachyon board upright on a desk.
    
- **Badge (Top):** `[LATEST]` (Cyan/Teal color pill).
    
- **Headline:** "Order your Tachyon now!"
    
- **Body Copy:** "Embed intelligence into anything, anywhere with Particle's 5G-connected, AI-accelerated single-board computer."
    
- **Click Action:** Entire card is clickable -> Links to Pre-order page.
    

### 2.2 Hero Text Section (Below Banner)

_Visual Reference: Large typography on white background._

**Typography Spec:**

- **Main Headline (H1):**
    
    - _Text:_ **Ship software to hardware.**
        
    - _Style:_ Extra Bold, Sans-Serif. The period "." is visible.
        
    - _Highlight:_ The word "hardware" may have a subtle text-highlight effect (gray background) based on some design iterations.
        
- **Sub-headline:**
    
    - _Text:_ "Built for developer productivity, observability, and reliability."
        
    - _Style:_ Regular weight, Grey-600 color.
        

### 2.3 Social Proof Bar (Visual Integration)

_Location: Integrated into the Hero background gradient (Cyan to Blue)._

**Logos Required (White/Negative version):**

- HALLIBURTON
    
- Jacuzzi
    
- TREK
    
- (Others cropped in image, need strictly these 3 visible as primary).
    

---

## 3. Secondary Page Specs (Functional Deep Dive)

_To flesh out the document volume, we are defining the FUNCTIONAL requirements for sub-pages, not just text._

### 3.1 Product Detail Page: "Tachyon" (Spec)

**Page Goal:** Drive Pre-orders for the new 5G SBC.

**Section A: Technical Specs Table (Data-Heavy)**

- **Processor:** Qualcomm QCM6490 octa-core CPU.
    
- **AI Performance:** 12 TOPS (Trillions of Operations Per Second).
    
- **RAM/Storage:** 4GB RAM / 64GB UFS.
    
- **Connectivity:** 5G Sub-6, Wi-Fi 6E, Bluetooth 5.2.
    
- **Ports:** USB-C (DisplayPort), MIPI CSI (Camera), DSI (Display), 40-pin GPIO.
    
- _Requirement:_ This table must be collapsible on Mobile view.
    

**Section B: Software Compatibility (Logo Grid)**

- _Headline:_ "Works with the tools you know."
    
- _Logos:_ Ubuntu, Yocto, Android, Docker, Python, C++.
    

**Section C: Comparison Module (Table)**

- _Columns:_ Tachyon vs. Raspberry Pi 5 vs. Jetson Orin Nano.
    
- _Rows:_ 5G Integrated (Yes/No), AI TOPS, Price.
    

### 3.2 Solution Page: "Asset Tracking" (Spec)

**Page Goal:** B2B Lead Generation.

**Section A: Interactive ROI Calculator**

- _Input Fields:_
    
    - Number of Assets (Slider: 100 - 10,000).
        
    - Average Asset Value ($).
        
    - Current Theft Rate (%).
        
- _Output:_ "Projected Annual Savings: $X,XXX".
    
- _CTA:_ "Get a custom quote based on these numbers."
    

**Section B: Industry Use Case Switcher (Tabs)**

- _Tab 1: Logistics:_ Copy focused on "Cold Chain" and "Real-time location."
    
- _Tab 2: Construction:_ Copy focused on "Theft Prevention" and "Geofencing."
    
- _Tab 3: Micromobility:_ Copy focused on "Ride tracking" and "Battery health."
    

### 3.3 Developer Hub / Documentation (Spec)

**Page Goal:** Reduce Support Tickets / Improve DX (Developer Experience).

**Layout:** Three-Pane Layout.

- _Left Pane:_ Tree Navigation (Collapsible folders).
    
- _Center Pane:_ Content (Markdown rendered).
    
- _Right Pane:_ On-this-page Table of Contents (Sticky).
    

**Functional Requirement: Code Block Renderer**

- Must support Syntax Highlighting for: C++, JSON, Python, Bash.
    
- Must have a "Copy to Clipboard" button on hover.
    
- Must support "Dual View" (Toggle between Cloud API / Device OS code).
    

---

## 4. Technical & SEO Requirements (Non-Functional Requirements)

_This section adds the necessary "weight" for a Master Spec, guiding the engineering team on implementation standards._

### 4.1 SEO Meta Data Template

**Homepage:**

- `Title Tag`: IoT Platform for Intelligent Devices | Particle
    
- `Meta Description`: The integrated IoT platform-as-a-service. Everything you need to build, deploy, and manage your fleet of connected devices. Start for free.
    

**Product Page (Tachyon):**

- `Title Tag`: Tachyon 5G AI Single Board Computer | Particle Store
    
- `Meta Description`: Pre-order Tachyon. The world's first 5G-connected, AI-powered SBC. Qualcomm chipset, Ubuntu OS, and Wi-Fi 6E.
    

### 4.2 Accessibility Standards (WCAG 2.1 AA)

- **Color Contrast:** All text must meet 4.5:1 contrast ratio against backgrounds (Critical for the Cyan hero section).
    
- **Keyboard Navigation:** Mega-menus must be navigable via `Tab` key.
    
- **Alt Text:** All product images (Tachyon, M-HAT) must have descriptive Alt text.
    
    - _Bad:_ "board.jpg"
        
    - _Good:_ "Particle Tachyon 5G Single Board Computer side view showing USB-C ports."
        

### 4.3 Mobile Responsiveness Rules

- **Breakpoint:** 768px.
    
- **Navigation:** Collapses into a "Hamburger Menu" (Icon on Right).
    
- **Mega-Menu:** Converts to "Accordion" style (Click to expand Categories).
    
- **Hero Image:** The Tachyon banner moves _below_ the main Headline text on mobile to ensure the H1 is read first.
    

### 4.4 Performance Budgets

- **LCP (Largest Contentful Paint):** < 2.5s (Hero image must be optimized WebP).
    
- **CLS (Cumulative Layout Shift):** < 0.1 (Banner must have reserved height space).
    
- **Font Loading:** Use `font-display: swap` to prevent invisible text during load.
    

---

## 5. Implementation Checklist (For Dev Team)

- [ ] **Asset Prep:** Export "Tachyon", "M-HAT", and "M1 Enclosure" images as transparent PNGs.
    
- [ ] **Icon System:** SVG icons needed for "Signal" (M-HAT), "Chip" (SBC), and "Box" (Enclosure).
    
- [ ] **Badge Component:** Create a reusable CSS class for the `[NEW]` and `[LATEST]` badges (Cyan background, dark text, 10px font size).
    
- [ ] **Gradient:** Extract the exact CSS gradient from the Hero background (Looks like `linear-gradient(90deg, #00C9DB 0%, #005BEA 100%)`).
    

---

**Document Owner:** Design Director

**Last Updated:** Oct 26, 2023

**Status:** Approved for Sprint 1