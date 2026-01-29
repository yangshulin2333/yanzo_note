
# Website Content & Design Specifications (The "All-in-One" Master Deck)

**Reference Source:** [Particle.io](https://www.particle.io/)

**Status:** Final Complete Record (Homepage + Navigation + Sub-pages)

**Purpose:** Single source of truth for Developers.

---

## 1. Global Navigation Inventory (The Mega-Menu Structure)

**Implementation Note:** _These are the exact items and descriptions found in the dropdown menus (from your screenshots). Developers must implement this exact hierarchy._

### 1.1 "Platform" Dropdown [Source: Image 2]

**Layout Logic:** Two-Column Layout. "Application Development" gets special visual emphasis (dark/gray background).

- **Column 1: Application development**
    
    - _Sub-head:_ Software-defined everything
        
    - _Item:_ **Blueprints** [BETA] - Simplified deployment of applications for intelligent devices.
        
    - _Item:_ **Workbench** - Integrated development and debugging environment.
        
    - _Item:_ **Web IDE** - Write code, compile, and flash devices over the air.
        
    - _Item:_ **Command Line Interface (CLI)** - Interact with your devices and the Particle Device Cloud.
        
    - _Item:_ **Edge ML** [NEW] - Deploy and upgrade Edge ML models.
        
- **Column 2: Infrastructure Stack**
    
    - _Item:_ **Edge Infrastructure**
        
        - _Desc:_ Embedded Intelligence.
            
    - _Item:_ **Cloud infrastructure**
        
        - _Desc:_ Turning data into actions and insights.
            
    - _Item:_ **Network and connectivity**
        
        - _Desc:_ Wireless connectivity that just works.
            
    - _Item:_ **Management and oversight**
        
        - _Desc:_ Complete control of your devices in the field.
            

### 1.2 "Supported devices" Dropdown [Source: Image 4]

**Layout Logic:** Category List (Left) triggers Detail View (Right).

- **Category 1: Single-board computers**
    
    - _Desc:_ For all-in-one systems.
        
    - _Product A:_ **Tachyon** [NEW] - 5G SBC + AI accelerator.
        
    - _Product B:_ **M-HAT** [NEW] - Cellular connectivity for 40-pin SBCs.
        
    - _Product C:_ **M1 Enclosure** [NEW] - Industrial-grade IP67-ready case.
        
- **Category 2: System on Modules (SoMs)**
    
    - _Desc:_ For embedded systems.
        
    - _Link:_ Shop all SoMs >
        
- **Category 3: Development boards**
    
    - _Desc:_ For rapid prototyping and PoCs.
        
    - _Link:_ Shop all dev boards >
        
- **Category 4: Gateways**
    
    - _Desc:_ For retrofit applications.
        
    - _Link:_ Shop all gateways >
        
- **Footer Link:** Shop all devices >
    

### 1.3 "Solutions" Dropdown [Source: Image 6]

**Layout Logic:** Three-Row Layout by Category.

- **Row 1: By use case**
    
    - _Desc:_ Explore some of the ways customers use our technology.
        
    - _Item:_ **Asset tracking** - Build asset tracking capabilities into your products.
        
    - _Item:_ **Preventative maintenance** - Prevent breakdowns and subpar product performance.
        
    - _Item:_ **Equipment monitoring** - Make equipment and assets simple to monitor and manage.
        
- **Row 2: By industry**
    
    - _Desc:_ See where our customers are having the biggest impact.
        
    - _(Implied Items based on context):_ Smart Energy, HVAC, EV Charging.
        
- **Row 3: By service**
    
    - _Desc:_ Learn how Particle can offer additional resources.
        
    - _(Implied Items):_ Professional Services, Engineering Services.
        

### 1.4 "Developers" Dropdown [Source: Image 3]

**Layout Logic:** Single List with Descriptions.

- _Item:_ **Documentation** - Explore Particle's hardware, software, and developer tools.
    
- _Item:_ **Tutorials** - Step-by-step guidance through early prototyping examples.
    
- _Item:_ **Blog** - News, updates, and commentary from the Particle team.
    
- _Item:_ **Community** - Join the largest community of connected devices.
    
- _Item:_ **Reference** - Get into the details with additional Particle spec sheets.
    
- _Item:_ **Tools** - Professional-grade IDE, CLI, and SDKs to develop edge software.
    
- _Item:_ **Application notes** - In-depth technical guides for real-world Particle applications.
    

---

## 2. Homepage Content (Full Copydeck)

**Implementation Note:** _This section corresponds to the main scrollable area of the landing page._

### 2.1 Hero Section (Above Fold) [Source: Image 5]

- **Announcement Banner:** [NEW] Order your Tachyon now! Embed intelligence into anything, anywhere with Particle's 5G-connected, AI-accelerated single-board computer.
    
- **H1 Headline:** Ship software to hardware.
    
- **Sub-headline:** Built for developer productivity, observability, and reliability.
    
- **CTAs:** [Start for free] | [Contact sales]
    
- **Trust Signals:** Logos for Halliburton, P&G, GoodYear, Jacuzzi, Trek.
    

### 2.2 Feature Module A: Edge Infrastructure [Source: Image 1]

- **Label:** Edge infrastructure (Teal)
    
- **Headline:** Embedded intelligence
    
- **Body Copy:** Reliably deploy over-the-air software and model updates to any device — from KB-scale microcontrollers to GB-scale edge computers and AI accelerators.
    
- **Feature Tags (Icons):**
    
    - Bare metal runtime
        
    - Particle on Linux [NEW]
        
    - OTA software updates
        
    - Drivers and libraries
        
    - Device protection [NEW]
        

### 2.3 Feature Module B: Network and Connectivity [Source: Image 2]

- **Label:** Network and connectivity (Teal)
    
- **Headline:** Wireless connectivity that just works
    
- **Body Copy:** Connectivity shouldn't require a Ph.D in radios and protocols. Particle provides an abstracted communications layer that works reliably across a wide range of radios: LTE, 5G, Wi-Fi, satellite, and LoRaWAN.
    
- **Feature Tags (Icons):**
    
    - "It just works" connectivity
        
    - Particle.publish()
        
    - Encryption
        
    - EtherSIM
        
    - EtherSIM+ [NEW]
        
    - Multi-radio transport [NEW]
        

### 2.4 Feature Module C: Cloud Infrastructure (Inferred standard pattern)

- **Label:** Cloud infrastructure
    
- **Headline:** Turning data into actions and insights
    
- **Body Copy:** Machine data are only useful if they get used. Turn data into immediate action and helpful insights through Particle's real-time data automation infrastructure.
    
- **Feature Tags (Icons):**
    
    - Event Bus
        
    - Location Fusion
        
    - Ledger
        
    - REST API
        
    - Logic
        
    - Integrations
        

### 2.5 Hardware Showcase

- **Headline:** Hardware abstraction, not hardware ignorance.
    
- **Body:** Integrated with everything from our modules to Raspberry Pi and NVIDIA Jetson.
    
- **Product Tabs:** SBCs | SoMs | Dev Boards | Gateways.
    

### 2.6 Stats Strip

- **60 Billion** Messages delivered per month.
    
- **12 Million** OTA software updates per month.
    
- **240,000** Developers building with Particle.
    

### 2.7 Pre-Footer

- **Headline:** Order your Tachyon now!
    
- **Sub:** Embed intelligence into anything, anywhere.
    
- **CTAs:** [Start for free] | [Contact sales]
    

---

## 3. Sub-Page Content Templates (For Links Clicked in Nav)

**Implementation Note:** _These templates define the content structure for pages linked in the Navigation (Section 1)._

### Template A: Hardware Product Detail Page

- **Used for:** Links under "Supported Devices" (e.g., Tachyon, M-HAT, Tracker One).
    
- **Section 1: Product Hero**
    
    - **H1:** Product Name (e.g., "Tachyon").
        
    - **Price:** Display price prominently.
        
    - **Short Desc:** One sentence summary (from the nav description).
        
    - **CTA:** [Add to Cart] / [Pre-Order].
        
- **Section 2: Technical Specifications Table**
    
    - **Columns:** Processor, Connectivity, Memory, Power, I/O.
        
- **Section 3: Documentation Sidebar**
    
    - **Links:** Datasheet (PDF), Pinout Diagram, Setup Guide.
        

### Template B: Solution/Industry Page

- **Used for:** Links under "Solutions" (e.g., Asset Tracking, Smart Energy).
    
- **Section 1: Hero**
    
    - **H1:** [Solution Name] (e.g., "Asset Tracking").
        
    - **Sub:** "Build [Solution] capabilities into your products." (From nav desc).
        
    - **CTA:** [Contact Sales].
        
- **Section 2: Problem/Solution**
    
    - **The Problem:** Industry pain points (e.g., "Theft," "Downtime").
        
    - **The Solution:** How Particle solves it (e.g., "Real-time location fusion").
        
- **Section 3: Case Study**
    
    - **Content:** Customer quote + Logo (e.g., Jacuzzi or Trek).
        

### Template C: Feature Detail Page

- **Used for:** Links under "Platform" (e.g., Edge ML, Blueprints).
    
- **Section 1: Feature Hero**
    
    - **H1:** [Feature Name] (e.g., "Edge ML").
        
    - **Sub:** [Description] (e.g., "Deploy and upgrade Edge ML models").
        
- **Section 2: "How it Works"**
    
    - **Visual:** Code snippet or Workflow diagram.
        
    - **Copy:** Step-by-step explanation of the feature usage.
        

### Template D: Pricing Page

- **Used for:** "Pricing" Link.
    
- **Structure:**
    
    - **Free Plan:** $0/mo. For prototyping. Up to 100 devices.
        
    - **Enterprise Plan:** Custom pricing. For scaling. SLA support.
        
    - **Comparison Table:** Detailed feature list checkmarks.
        

---

## 4. Global Footer (Site Map)

- **Products:** Hardware, Connectivity, Cloud.
    
- **Solutions:** Asset Tracking, Energy, HVAC.
    
- **Resources:** Docs, Status, Support.
    
- **Company:** About, Careers, Contact.
    
- **Social:** Twitter, LinkedIn, GitHub, YouTube.