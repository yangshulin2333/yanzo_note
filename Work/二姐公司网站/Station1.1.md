
# Website Content & Design Specifications

**Reference Model:** [Particle.io](https://www.particle.io/)

**Scope:** Full Site Architecture (Homepage + Sub-pages)

**Purpose:** Detailed specifications for content generation and layout implementation.

---

## 1. Global Navigation (Shared Header)

**Design Logic:**

Tiered menu structure separating "Business Decision Makers" from "Technical Implementers."

**Content Specs:**

- **Mega-Menu (Left):**
    
    - **Platform:** Dropdown listing the 3 core pillars (Edge, Connectivity, Cloud).
        
    - **Solutions:** Split into two columns: _Industries_ (Verticals) & _Use Cases_ (Horizontals).
        
    - **Developers:** Direct links to Docs, Community, and Tools.
        
    - **Pricing:** Simple text link.
        
- **Action Group (Right):**
    
    - **Secondary Button:** "Login" or "Contact Sales" (Ghost style).
        
    - **Primary Button:** "Start for Free" (High contrast accent color).
        

---

## 2. Homepage (The Hub)

**Design Logic:** High-impact "Showcase" style. Z-Pattern layout for readability.

### 2.1 Hero Section (Above Fold)

- **Layout:** Centered text, maximum white space.
    
- **H1 Headline:** Functional definition. Formula: _[Core Infrastructure] for [Target Device]._
    
- **Sub-headline:** Focus on Speed and Reliability. Max 2 sentences.
    
- **CTAs:** Primary + Secondary (Matched to Header).
    
- **Social Proof:** Row of grayscale, high-authority client logos (Fortune 500 level) at the bottom.
    

### 2.2 Feature Pillars (The Z-Pattern)

- **Layout:** Alternating `Text-Left/Image-Right` $\leftrightarrow$ `Image-Left/Text-Right`.
    
- **Module A (Edge Infrastructure):**
    
    - _Kicker:_ "EDGE INFRASTRUCTURE"
        
    - _Headline:_ Focus on **Remote Control** & **OTA Updates**.
        
    - _Tags:_ Bare Metal, Device OS, Linux.
        
- **Module B (Connectivity):**
    
    - _Kicker:_ "NETWORK AND CONNECTIVITY"
        
    - _Headline:_ Focus on **Abstraction** ("Just works").
        
    - _Tags:_ EtherSIM, Multi-radio, End-to-End Encryption.
        
- **Module C (Cloud):**
    
    - _Kicker:_ "CLOUD INFRASTRUCTURE"
        
    - _Headline:_ Focus on **Actionable Data**.
        
    - _Tags:_ Event Bus, REST API, Ledger.
        

### 2.3 Stats Authority Strip

- **Layout:** Full-width background color.
    
- **Content:**
    
    - **Metric 1:** Volume (e.g., 60B Messages).
        
    - **Metric 2:** Throughput (e.g., 12M Updates).
        
    - **Metric 3:** Ecosystem (e.g., 240k Developers).
        

### 2.4 Pre-Footer Conversion

- **Layout:** Minimalist, centered.
    
- **Headline:** Imperative command (e.g., "Start building today").
    
- **CTAs:** Repeat Hero buttons.
    

---

## 3. Platform Detail Page (Template)

**Context:** Landing page for specific features (e.g., "Connectivity").

**Design Logic:** Technical, diagram-heavy, "How it works" focus.

### 3.1 Product Hero

- **Layout:** Split screen (Text Left, Abstract 3D graphic Right).
    
- **H1 Headline:** Specific Product Name (e.g., "Cellular Connectivity").
    
- **Sub-headline:** Technical summary of capabilities (Bandwidth, Latency, Coverage).
    

### 3.2 "How It Works" Visualization

- **Layout:** Full-width Step-by-Step Diagram.
    
- **Content:**
    
    - _Step 1:_ Device/Sensor input.
        
    - _Step 2:_ The specific platform processing (The "Magic").
        
    - _Step 3:_ Output/App visualization.
        

### 3.3 Feature Grid (Iconography)

- **Layout:** 3x2 Grid.
    
- **Card Structure:**
    
    - _Icon:_ Line-art style.
        
    - _Title:_ Granular feature name (e.g., "Global Roaming").
        
    - _Description:_ 1-sentence technical explanation.
        

### 3.4 Technical Specs Table

- **Layout:** Data Table or List View.
    
- **Content:** Supported protocols, hardware compatibility list, encryption standards.
    

### 3.5 Hardware Cross-Link

- **Layout:** "Compatible Hardware" Strip.
    
- **Content:** Thumbnails of physical modules that work best with this software feature. -> _Links to Hardware Page._
    

---

## 4. Solutions / Industry Page (Template)

**Context:** Landing page for verticals (e.g., "Smart Energy").

**Design Logic:** Trust-building, Case Study focus.

### 4.1 Industry Hero

- **Layout:** Full-bleed background image (Real-world photography).
    
- **H1 Headline:** "Smart Solutions for [Industry Name]."
    
- **CTA:** "Contact Sales" (Enterprise focus).
    

### 4.2 Challenge vs. Solution

- **Layout:** Two-column comparison.
    
- **Col 1 (The Challenge):** Bullet list of industry pain points (e.g., "High maintenance costs").
    
- **Col 2 (Our Solution):** Matching list of platform benefits (e.g., "Predictive maintenance").
    

### 4.3 Customer Story (Social Proof)

- **Layout:** Large Blockquote.
    
- **Elements:**
    
    - Quote text focusing on ROI/Efficiency.
        
    - Headshot of Client Executive (CTO/VP).
        
    - "Read Case Study" link.
        

---

## 5. Hardware Product Page (Template)

**Context:** E-commerce detail view for physical devices.

**Design Logic:** Clean, white background, shopping-focused.

### 5.1 Product Stage

- **Layout:** Carousel Gallery (Left) + Buy Box (Right).
    
- **Buy Box Elements:**
    
    - Product Title & SKU.
        
    - Price (highlighting bulk discounts).
        
    - Stock Status ("In Stock").
        
    - Primary Button: "Add to Cart" / "Buy Now".
        

### 5.2 Technical Resources Sidebar

- **Layout:** Sticky sidebar or distinct list.
    
- **Links:** Datasheet (PDF), Pinout Diagram, CAD Files. -> _Links to Developer Hub._
    

### 5.3 Tabbed Details

- **Layout:** Horizontal Tabs.
    
- **Tabs:** Overview | Tech Specs | FAQ | Compliance.
    

---

## 6. Pricing Page

**Context:** Conversion & Comparison.

**Design Logic:** Clear differentiation between "Self-Serve" and "Enterprise".

### 6.1 Toggle Switch

- **Element:** "Monthly" vs. "Yearly" (Highlight "Save 20%").
    

### 6.2 Pricing Cards (3-Column)

- **Card 1 (Free):** For prototyping. Cost: $0. CTA: "Sign Up".
    
- **Card 2 (Growth):** For scaling. Cost: $X/mo. CTA: "Buy Now".
    
- **Card 3 (Enterprise):** For mass deployment. Cost: Custom. CTA: "Contact Sales".
    

### 6.3 Feature Matrix

- **Layout:** Long comparison table.
    
- **Logic:** Checkmarks vs. Empty circles. Grouped by "Cloud Features," "Support Level," "Hardware Discounts."
    

---

## 7. Developer Hub (Landing)

**Context:** Technical Resource Center.

**Design Logic:** Search-first, high information density.

### 7.1 Search Hero

- **Layout:** Simple, centered.
    
- **Element:** Large Search Input Field ("Search docs, API references...").
    

### 7.2 Quick Start Grid

- **Layout:** 4-Card Grid.
    
- **Cards:** "Getting Started," "Hardware Reference," "Cloud API," "Tutorials."
    

### 7.3 Code Showcase

- **Layout:** Split View (Description Left / Code Block Right).
    
- **Content:** Dark-mode code snippet showing a "Hello World" or simple function to demonstrate ease of use.
    

---

## 8. Global Footer

**Design Logic:** Site Map style for SEO and Navigation.

**Columns:**

- **Products:** Full list of platform features.
    
- **Hardware:** Direct links to popular devices.
    
- **Solutions:** Industry verticals.
    
- **Resources:** Documentation, Forum, Status Page.
    
- **Company:** About Us, Careers, Contact, Legal.
    
- **Social:** Icons (GitHub, Twitter, LinkedIn).