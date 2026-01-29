# Station 2.0: Particle.io Master Web Architecture
**Document Status:** FINAL MERGE (Marketing + Technical Specs)
**Scope:** Homepage, Navigation, Sub-pages, Technical Documentation, Pricing.

---

# PART 1: THE FRONT DOOR (Homepage & Navigation)
*Source: Marketing & Layout Specifications*

## 1. Global Navigation (Header)
**Layout Spec:** Fixed Header. Left Logo, Center Links, Right Actions.

* **Logo:** [Particle Brand Asset]
* **Menu Item 1: Platform** (Dropdown: Edge, Connectivity, Cloud, Management)
* **Menu Item 2: Solutions** (Dropdown: Asset Tracking, HVAC, Smart Energy, EV)
* **Menu Item 3: Developers** (Dropdown: Docs, Tutorials, Community, Tools)
* **Menu Item 4: Pricing** (Link: `/pricing`)
* **Action Group:** [Login] [Contact Sales] [Primary: **Start for free**]

## 2. Hero Section (Above the Fold)
**Layout Spec:** Split Screen / Centered. High Visual Impact.

* **H1 Headline:** **"Application infrastructure for intelligent devices"**
* **Sub-headline:** "Ship software to hardware. Built for **developer productivity**, observability, and reliability."
* **Visual:** Split-screen showing VS Code (Left) vs. Particle Console Map (Right).
* **CTA Buttons:** [Start for free] [Contact Sales]
* **Social Proof:** Logos of Halliburton, P&G, Jacuzzi, Trek, Goodyear.

## 3. Core Platform Modules (Homepage Body)
**Layout Spec:** Z-Pattern (Alternating Text/Image).

* **Module A: Edge Infrastructure**
    * *Headline:* Embedded intelligence.
    * *Copy:* Reliably deploy OTA updates to any device—from microcontrollers to 5G AI computers.
    * *Features:* Bare metal runtime, Linux Support, OTA updates.
* **Module B: Connectivity**
    * *Headline:* Wireless connectivity that just works.
    * *Copy:* Abstracted layer for LTE, 5G, Wi-Fi, Satellite, and LoRaWAN.
    * *Features:* EtherSIM, Multi-radio transport.
* **Module C: Cloud Infrastructure**
    * *Headline:* Turning data into actions.
    * *Features:* Event Bus, Location Fusion, Ledger, Logic.
* **Module D: Application Development**
    * *Headline:* Software-defined everything.
    * *Features:* Blueprints [BETA], CLI, Workbench, Web IDE.

---

# PART 2: HARDWARE ECOSYSTEM (Deep Dive)
*Source: Technical Specifications*

## 4. Hardware Portfolio: The "Gen 4" Powerhouses
**Layout Spec:** Product Grid & Comparison Table.

### **A. Single Board Computers (SBC)**
* **Tachyon (5G):**
    * **Core:** Qualcomm Octa-core CPU + AI Accelerator (NPU).
    * **Connectivity:** 5G (Sub-6), Wi-Fi 6E, Bluetooth 5.2.
    * **OS:** Ubuntu/Debian Linux.
    * **Target:** Edge AI, video inferencing (YOLOv8), high-bandwidth gateways.

### **B. System-on-Modules (SoM)**
* **M-SoM:** Flagship multi-radio (LTE-M/2G + Satellite).
* **B-SoM (B404X):** Industrial M.2 module for North America (LTE-M).
* **P2:** Tiny Wi-Fi module (Realtek RTL8721DM) with dual-band support.

### **C. Industrial Gateways**
* **Monitor One:** IP67-rated rugged gateway (Modbus, CAN, RS-232).
* **Tracker One:** Fully enclosed asset tracker with GNSS/Wi-Fi fusion.

---

# PART 3: SOFTWARE & TECHNICAL IMPLEMENTATION

## 5. Device OS & Connectivity Primitives
* **Particle.publish():** Broadcast events to the cloud.
* **Particle.function():** Trigger device actions from the cloud.
* **Particle.variable():** Expose device state to APIs.
* **Connectivity:**
    * `Cellular.RSSI()`: Signal strength monitoring.
    * `cellular_global_identity()`: Tower triangulation (CGI).

## 6. Advanced Data Management (Ledger)
**Concept:** "Digital Twin" for state synchronization.
* **Cloud-to-Device:** Push configuration (e.g., polling intervals) to offline devices; syncs on reconnect.
* **Device-to-Cloud:** Store sensor readings (Temperature, Vibration) persistently.

## 7. Blueprints: Infrastructure as Code
**Status:** Beta 2026.
* **Function:** Package Firmware + Cloud Logic + Ledger Schema into a single template.
* **Benefit:** Zero-touch provisioning for large fleets (e.g., "North American HVAC Units").

---

# PART 4: SOLUTIONS & PRICING

## 8. Vertical Solutions (Use Cases)
| Industry | Key Value | Tech Stack |
| :--- | :--- | :--- |
| **HVAC** | Reduce truck rolls | Remote Diagnostics, OTA |
| **Smart Energy** | Theft prevention | Real-time monitoring, Logic |
| **E-Bikes** | Anti-theft | Location Fusion, Speed limiting |
| **Industrial** | Predictive Maintenance | Vibration sensors, Modbus |

## 9. 2026 Pricing Model
**System:** "Block" based scaling. Each block = 100 devices.

* **Free:** $0 (Up to 100 devices, 100K Data Ops).
* **Basic:** $299/block (Simple products, 720K Ops).
* **Plus:** $599/block (High-res data, Tracking, 5M Ops).
* **Enterprise:** Custom (SLA, Dedicated Watchdog).

**Billing Formula:**
$$Total\ Monthly\ Ops = (Devices \times Ops\ Per\ Day \times 30)$$

---

# PART 5: FOOTER & DEPLOYMENT

## 10. Final Deployment Checklist
1.  **Hardware:** UV-rated enclosure?
2.  **Firmware:** Application Watchdog enabled?
3.  **Security:** Webhooks using SSL?
4.  **Scaling:** Product Groups defined for OTA?

## 11. Global Footer
**Layout Spec:** 5-Column Grid, Dark Theme.

* **Col 1 (Products):** Hardware, Connectivity, Device OS, Tachyon [NEW].
* **Col 2 (Solutions):** Asset Tracking, Preventative Maintenance, Smart Energy.
* **Col 3 (Resources):** Docs, Tutorials, Support, Changelog.
* **Col 4 (Company):** About, Careers, Partners, [Contact Sales].
* **Col 5 (Legal):** Privacy, Terms, Social Icons (X, GitHub, LinkedIn).
* **Copyright:** © 2026 Particle Industries, Inc.