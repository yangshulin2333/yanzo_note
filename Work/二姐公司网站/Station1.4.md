
# Website Content & Design Specifications (Master Copydeck)

**Reference Source:** [Particle.io](https://www.particle.io/)

**Scope:** Homepage + Core Sub-Pages (Platform, Solutions, Hardware, Pricing)

**Status:** Ready for Implementation

---

## 1. Global Navigation (Site-Wide Header)

**Design Logic:**

Tiered menu structure. Separates "Platform Overview" from "Specific Use Cases."

**Content Inventory:**

- **Logo:** [Particle Brand Asset]
    
- **Platform (Dropdown):** Edge Infrastructure, Connectivity, Cloud, Management.
    
- **Solutions (Dropdown):** Asset Tracking, Smart Energy, EV Charging, HVAC.
    
- **Developers:** Documentation, Tools, Community, Support.
    
- **Store:** Hardware & Accessories.
    
- **Pricing:** [Link]
    
- **Action Group:** [Login] (Secondary) | [Start for Free] (Primary/Accent).
    

---

## 2. Homepage (The Hub)

**Design Logic:** High-impact showcase. Uses a "Z-Pattern" layout for the core technology pillars.

### 2.1 Hero Section

- **H1 Headline:** Application infrastructure for intelligent devices.
    
- **Sub-headline:** Ship software to hardware. Built for developer productivity, observability, and reliability.
    
- **CTAs:** [Start for free] | [Contact sales]
    
- **Trust Bar:** "Trusted by industry leaders" + Logos (Halliburton, P&G, Jacuzzi, Trek, GoodYear).
    

### 2.2 Feature Modules (The "Edge" Content from your Image)

- **Module A: Edge Infrastructure**
    
    - **Headline:** Embedded intelligence
        
    - **Body:** Reliably deploy over-the-air software and model updates to any device — from KB-scale microcontrollers to GB-scale edge computers and AI accelerators.
        
    - **Tags:** Bare metal runtime, Particle on Linux **NEW**, OTA software updates, Drivers and libraries, Device protection **NEW**.
        
- **Module B: Connectivity**
    
    - **Headline:** Wireless connectivity that just works
        
    - **Body:** Connectivity shouldn't require a Ph.D. in radios. We provide an abstracted layer for LTE, 5G, Wi-Fi, satellite, and LoRaWAN.
        
    - **Tags:** EtherSIM, Multi-radio transport **NEW**, Encryption, "It just works" connectivity.
        
- **Module C: Cloud & Management**
    
    - **Headline:** Turning data into actions
        
    - **Body:** Machine data are only useful if they get used. Turn data into immediate action through real-time automation.
        
    - **Tags:** Event Bus, Ledger, REST API, Logic, Fleet Health.
        

### 2.3 Hardware Preview

- **Headline:** Hardware abstraction, not hardware ignorance.
    
- **Copy:** Integrated with everything from our modules to Raspberry Pi and NVIDIA Jetson.
    

---

## 3. Sub-Page: Platform Detail (Focus: Connectivity)

**Context:** The technical deep-dive page for the "Connectivity" pillar.

**Design Logic:** Diagram-heavy, technical specs, "Global Map" visuals.

### 3.1 Hero Section

- **H1:** Global connectivity, solved.
    
- **Sub-head:** One SIM, global coverage. Automatically connects to the best signal across 350+ carriers worldwide.
    

### 3.2 Feature Grid (Icon + Description)

- **EtherSIM:** Auto-connecting global SIM. No contract negotiation required.
    
- **Multi-Radio:** Seamlessly switch between Cellular, Wi-Fi, and LoRaWAN without rewriting code.
    
- **Security:** Data is encrypted from device to cloud (DTLS/TLS). No open ports.
    
- **Data Operations:** Pooled data plans across your entire fleet.
    

### 3.3 Technical Specs Table

- **Networks:** LTE-M, NB-IoT, 2G/3G Fallback, Wi-Fi 6E.
    
- **Carriers:** AT&T, Vodafone, Telefonica, and 350+ roaming partners.
    
- **Management:** Real-time SIM activation/deactivation via Console.
    

---

## 4. Sub-Page: Solutions Detail (Focus: Asset Tracking)

**Context:** Landing page for business verticals.

**Design Logic:** Problem/Solution structure, Case Study evidence.

### 4.1 Solution Hero

- **H1:** Intelligent Asset Tracking & Monitoring.
    
- **Sub-head:** Reduce theft, lower maintenance costs, and prevent downtime with a fully integrated tracking solution.
    

### 4.2 "The Challenge" vs "The Solution"

- **Challenge:** "Asset tracking is hard. GPS drift, dead zones, and battery drain kill ROI."
    
- **Solution:** "Particle Location Fusion combines GPS, Wi-Fi, and Cell Tower triangulation for precise indoor/outdoor tracking."
    

### 4.3 Key Features List

- **Seamless Integration:** CAN Bus controller for vehicle data (OBD-II).
    
- **Sensors:** Monitor temperature, motion, sound, and air quality alongside location.
    
- **Hardware:** **Tracker One** (IP67 waterproof, field-ready) or **Monitor One** (Rugged Gateway).
    

### 4.4 Social Proof

- **Quote:** "We reduced equipment theft by 40% in the first year." — _Customer Case Study_
    

---

## 5. Sub-Page: Hardware Store (Product Detail)

**Context:** E-commerce style page for specific devices (e.g., Tachyon, Tracker).

**Design Logic:** Clean product shots, "Buy Box," and technical datasheets.

### 5.1 Product: Tachyon (5G Single-Board Computer)

- **H1:** Tachyon 5G SBC
    
- **Price:** $324 (Pre-order)
    
- **Short Description:** A 5G-connected, AI-accelerated computer. The power of a smartphone in a Raspberry Pi form factor.
    
- **Specs Highlights:**
    
    - **SoC:** Qualcomm QCM6490 (Octa-core).
        
    - **AI:** 12 TOPS NPU for edge machine learning.
        
    - **Connectivity:** 5G Sub-6GHz + Wi-Fi 6E.
        
    - **OS:** Ubuntu + Yocto Linux.
        

### 5.2 Product: Monitor One (Gateway)

- **H1:** Monitor One
    
- **Short Description:** Rugged IP67 gateway for industrial equipment monitoring.
    
- **Specs Highlights:**
    
    - **Ports:** CAN Bus, Modbus, I/O expansion card slot.
        
    - **Power:** 6-30V DC input + large LiPo battery backup.
        
    - **Durability:** Waterproof, dustproof, impact resistant.
        

---

## 6. Sub-Page: Pricing Page

**Context:** Conversion page.

**Design Logic:** Clear comparison table.

### 6.1 Plan Cards

- **Free Plan:**
    
    - **Cost:** $0 / month.
        
    - **Includes:** Up to 100 devices. 100k Data Operations. Cellular data included.
        
    - **Ideal for:** Prototyping and Pilots.
        
    - **CTA:** [Sign Up Free]
        
- **Enterprise Plan:**
    
    - **Cost:** Custom.
        
    - **Includes:** Volume discounts, Pooled Data, SLA, Manufacturing Grace Period (6 months).
        
    - **Ideal for:** Scaling fleets (1k+ devices).
        
    - **CTA:** [Contact Sales]
        

### 6.2 FAQ Section

- **Q:** What is a Data Operation?
    
- **A:** Each data transmission (publish, subscribe, or stored location) counts as 1 Data Op.
    
- **Q:** Is the SIM card really free?
    
- **A:** Yes, the Free plan includes cellular connectivity for your first 100 devices.
    

---

## 7. Global Footer

**Content Inventory:**

- **Products:** Hardware, Connectivity, Device Management.
    
- **Solutions:** Smart Energy, Asset Tracking, HVAC.
    
- **Resources:** Docs, Tutorials, Support, Status.
    
- **Legal:** Privacy Policy, Terms of Service.