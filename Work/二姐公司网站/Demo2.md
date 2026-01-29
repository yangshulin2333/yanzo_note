# Station 4.0: Particle.io Master Ecosystem Document
**Base:** Station 1.9.2 (Technical Depth)
**Integration:** Station 1.3 (Marketing Frontend)
**Status:** Full Production Ready

---

# PART A: THE FRONT-END EXPERIENCE (From Station 1.3)
*This section defines the "unauthenticated" Homepage experience.*

## 1. Global Navigation (Header)
**Layout Spec:** Fixed Header. Left Logo, Center Links, Right Actions.
* **Logo:** [Particle Brand Asset]
* **Menu Structure:**
    * **Platform:** Edge, Connectivity, Cloud, Management.
    * **Solutions:** Asset Tracking, Energy, HVAC, EV.
    * **Developers:** Docs, Tools, Community.
    * **Pricing:** Link to Section 6.
* **CTA Group:** [Login] [Contact Sales] [**Start for free**]

## 2. Homepage Hero Section (Above the Fold)
**Layout Spec:** Split Screen Visual (VS Code vs. Console Map).
* **H1 Headline:** **"Application infrastructure for intelligent devices"**
* **Sub-headline:** "Ship software to hardware. Built for **developer productivity**, observability, and reliability."
* **Primary CTA:** [Start for free]
* **Trust Bar:** Halliburton, P&G, Jacuzzi, Trek, GoodYear.

## 3. The Platform Narrative (Z-Pattern Modules)
*Bridging the gap between "Marketing" and "Technical Specs".*

* **Module A (Edge):** "Embedded intelligence." Reliably deploy OTA updates to any device.
* **Module B (Connectivity):** "Connectivity that just works." Abstracting LTE, 5G, and LoRaWAN.
* **Module C (Cloud):** "Turning data into actions." Event Bus & Integrations.
* **Module D (App Dev):** "Software-defined everything." Blueprints, CLI, Workbench.

---

# PART B: THE TECHNICAL CORE (Station 1.9.2 Original Content)
*This is the deep-dive documentation for Developers and Architects.*

## 1. Hardware Portfolio
Particle offers a tiered hardware strategy: **SBCs** for high-performance AI, **SoMs** for mass production, and **Gateways** for immediate industrial deployment.

### **Single Board Computers (SBC)**
- **Tachyon (5G):**
    - **Core:** Qualcomm Octa-core CPU + AI Accelerator.
    - **Connectivity:** 5G, Wi-Fi 6E, Bluetooth 5.2.
    - **Key Specs:** 4GB RAM, 64GB Flash, Ubuntu/Debian support.
    - **Use Case:** Edge AI, video inferencing (YOLOv8), and high-bandwidth gateways.

### **System-on-Modules (SoM)**
- **M-SoM:** The flagship multi-radio module supporting LTE-M/2G, Wi-Fi, and Satellite (Global).
- **B-SoM (B-Series):** Industrial-grade M.2 module. The **B404X** supports LTE-M (North America).
- **P2:** Tiny Wi-Fi-only module (Realtek RTL8721DM) with dual-band Wi-Fi and BLE 5.3.

### **Development Boards**
- **Photon 2:** The standard Wi-Fi prototyping board in a Feather form factor.
- **Boron (4th Gen):** Cellular/LTE-M prototyping board with integrated battery charging.
- **Muon:** Multi-radio development board (Cellular + Wi-Fi + LoRaWAN).

### **Industrial Gateways**
- **Monitor One:** IP67-rated rugged gateway for industrial monitoring (Modbus, CAN, RS-232 support).
- **Tracker One:** Fully enclosed asset tracker with GNSS, cellular, and Wi-Fi location fusion.

## 2. Software & Cloud Infrastructure
Particle’s **Platform-as-a-Service (PaaS)** model abstracts the complexity of IoT networking.
- **Device OS:** An open-source, lightweight operating system that provides hardware-agnostic APIs.
- **Console:** The "IoT Command Center." Features include:
    - **Fleet Health:** Real-time dashboards for signal strength, memory, and battery.
    - **Device Vitals:** Granular diagnostics (CGI tower IDs, RTT, Signal Quality).
    - **OTA Updates:** Intelligent firmware deployment (EtherFlash).
- **Cloud Tools:**
    - **Logic:** Serverless computing engine triggered by device events.
    - **Ledger:** A "Digital Twin" key-value store for synchronizing state.
    - **Integrations:** 250+ pre-built connectors (Azure, AWS, Google Cloud).

## 3. Vertical Solutions (Use Cases)
| Industry | Primary Value | Key Technology Used |
| :--- | :--- | :--- |
| **HVAC** | Reduce truck rolls & sell uptime. | Remote Diagnostics, OTA Updates, Cellular. |
| **Smart Energy** | Prevent energy theft & monitor solar. | Real-time energy data capture, Logic. |
| **LEV (E-Bikes)** | Theft prevention & safety compliance. | Location Fusion, Speed Limiting, MDS. |
| **Emissions** | Regulatory compliance & leak detection. | Castellated SoMs, Global SIM, Alerting. |
| **Industrial** | Predictive maintenance. | Vibration/Temp sensors, Modbus expansion. |

## 4. Technical Frameworks & Tutorials
### **Core Firmware Methods**
- `Particle.function()`: Call a C++ function on the device from the cloud.
- `Particle.variable()`: Expose a device variable to the Cloud API.
- `Particle.publish()`: Broadcast an event to the cloud.
- `Particle.subscribe()`: Listen for events from the cloud or other devices.

### **Critical Diagnostic Metrics**
- **Signal Strength:** Measured in dBm, normalized to 0–100%.
- **Signal Quality:** Measure of relative noise and interference.
- **Round-Trip Time (RTT):** Latency of CoAP messages from cloud to device.
- **CGI (Cell Global Identity):** Used in cellular devices to identify the specific tower.

## 5. Professional Services & Ecosystem
- **Particle Studios:** A professional engineering arm providing PCB design, enclosure engineering, and manufacturing scale-up.
- **Partner Program:** An ecosystem of design firms (e.g., Voxdale, Ovyl).
- **Community:** Over 10,000 developers active on the Discourse-powered forums.

> **Note on Compliance:** All Particle solutions are encrypted by default and compliant with **SOC II, GDPR, CCPA, and Privacy Shield** standards.

## 6. 2026 Pricing & Fleet Scaling
Particle uses a "Block" system for scaling. Each block supports **100 devices**.

| Plan | Price | Included Data Ops | Best For |
| :--- | :--- | :--- | :--- |
| **Free** | $0 | 100K | Prototyping, educational. |
| **Basic** | $299 /block | 720K | Simple products, remote control. |
| **Plus** | $599 /block | 5M | High-res data, Edge ML, tracking. |
| **Enterprise** | Custom | Flexible | Mission-critical fleets. |

### **Understanding Data Operations (Data Ops)**
- **1 Data Op consumed:** Publishing/Receiving a message (up to 1KB), Location Fusion calls, Logic function runs, and Ledger syncs.
- **Included (Free):** Webhooks, REST API calls, and **OTA firmware updates**.

## 7. Advanced Device OS Capabilities
### **Connectivity & Networking**
- **Multi-Radio Transport:** Seamlessly switch between Wi-Fi, Cellular, LoRaWAN, and Satellite.
- **Cellular Primitives:** `Cellular.RSSI()`, `cellular_global_identity()`.
- **BLE:** Full central/peripheral support, iBeacon advertising.

### **Data Management Primitives**
- **Particle Ledger:** Use `Particle.ledger` to manage digital twins.
- **Asset OTA:** Efficiently update non-firmware assets (ML models, config files).
- **JSON Buffer Writer:** Built-in `JSONBufferWriter` for efficient payloads.

### **Hardware Control & Power**
- **FuelGauge:** Monitor `getSoC()` and `getVCell()` for battery deployments.
- **Sleep Modes:** Advanced `System.sleep()` configurations.

## 8. Security & Platform Integrity
- **Acquisition Note:** Particle was recently acquired by **Digi International**.
- **Encryption:** TLS/DTLS by default.
- **TrustZone:** ARM TrustZone support (e.g., Photon 2).
- **Compliance:** SOC 2 Type II, GDPR, CCPA.

## 9. Product Lifecycle & Advisories
- **LTS:** Long Term Support releases of Device OS.
- **Sunsets:** Migration paths from 2G/3G to LTE-M and 5G.
- **Technical Advisories (TAN):** Critical updates (e.g., TAN006).

## 10. Hardware Comparison: The "Gen 4" Powerhouses
| Feature | Tachyon (5G SBC) | M-SoM (Multi-Radio) | B-SoM / Boron (LTE-M) |
| :--- | :--- | :--- | :--- |
| **Primary Radio** | 5G (Sub-6 GHz) | LTE-M / 2G + Satellite | LTE-M (Cat M1) |
| **Secondary Radio** | Wi-Fi 6E, BT 5.2 | Wi-Fi, BLE 5.0 | BLE 5.0 |
| **Processor** | Qualcomm Octa-core | Realtek RTL872x | Nordic nRF52840 |
| **Edge AI** | High (NPU) | Low (TFLite) | Low (Basic patterns) |

## 11. Advanced Implementation: Multi-Sensor Ledger
**C++ Boilerplate:**
```cpp
#include "Particle.h"
Ledger sensorLedger;
void setup() { sensorLedger = Particle.ledger("env_data"); }
void loop() {
    // Logic to set data every 5 mins
    Variant data; data.set("temp", 24.5);
    sensorLedger.set(data);
}