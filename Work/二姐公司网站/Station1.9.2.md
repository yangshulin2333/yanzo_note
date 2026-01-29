# Particle Master Documentation: The Ultimate IoT Resource

This master document synthesizes the complete Particle ecosystem—ranging from high-level business solutions to granular technical specifications.

---

## ## 1. Hardware Portfolio

Particle offers a tiered hardware strategy: **SBCs** for high-performance AI, **SoMs** for mass production, and **Gateways** for immediate industrial deployment.

### **Single Board Computers (SBC)**

- **Tachyon (5G):** * **Core:** Qualcomm Octa-core CPU + AI Accelerator.
    
    - **Connectivity:** 5G, Wi-Fi 6E, Bluetooth 5.2.
        
    - **Key Specs:** 4GB RAM, 64GB Flash, Ubuntu/Debian support.
        
    - **Use Case:** Edge AI, video inferencing (YOLOv8), and high-bandwidth gateways.
        

### **System-on-Modules (SoM)**

- **M-SoM:** The flagship multi-radio module supporting LTE-M/2G, Wi-Fi, and Satellite (Global).
    
- **B-SoM (B-Series):** Industrial-grade M.2 module. The **B404X** supports LTE-M (North America) with Verizon/AT&T/T-Mobile.
    
- **P2:** Tiny Wi-Fi-only module (Realtek RTL8721DM) with dual-band Wi-Fi and BLE 5.3.
    

### **Development Boards**

- **Photon 2:** The standard Wi-Fi prototyping board in a Feather form factor.
    
- **Boron (4th Gen):** Cellular/LTE-M prototyping board with integrated battery charging.
    
- **Muon:** Multi-radio development board (Cellular + Wi-Fi + LoRaWAN).
    

### **Industrial Gateways**

- **Monitor One:** IP67-rated rugged gateway for industrial monitoring (Modbus, CAN, RS-232 support).
    
- **Tracker One:** Fully enclosed asset tracker with GNSS, cellular, and Wi-Fi location fusion.
    

---

## ## 2. Software & Cloud Infrastructure

Particle’s **Platform-as-a-Service (PaaS)** model abstracts the complexity of IoT networking.

- **Device OS:** An open-source, lightweight operating system that provides hardware-agnostic APIs.
    
- **Console:** The "IoT Command Center." Features include:
    
    - **Fleet Health:** Real-time dashboards for signal strength, memory, and battery.
        
    - **Device Vitals:** Granular diagnostics (CGI tower IDs, RTT, Signal Quality).
        
    - **OTA Updates:** Intelligent firmware deployment (EtherFlash) that prevents "bricking."
        
- **Cloud Tools:**
    
    - **Logic:** Serverless computing engine triggered by device events.
        
    - **Ledger:** A "Digital Twin" key-value store for synchronizing state between cloud and device.
        
    - **Integrations:** 250+ pre-built connectors (Azure, AWS, Google Cloud, Webhooks).
        

---

## ## 3. Vertical Solutions (Use Cases)

|**Industry**|**Primary Value**|**Key Technology Used**|
|---|---|---|
|**HVAC**|Reduce truck rolls & sell uptime.|Remote Diagnostics, OTA Updates, Cellular.|
|**Smart Energy**|Prevent energy theft & monitor solar.|Real-time energy data capture, Logic.|
|**LEV (E-Bikes)**|Theft prevention & safety compliance.|Location Fusion, Speed Limiting, MDS.|
|**Emissions**|Regulatory compliance & leak detection.|Castellated SoMs, Global SIM, Alerting.|
|**Industrial**|Predictive maintenance.|Vibration/Temp sensors, Modbus expansion.|

---

## ## 4. Technical Frameworks & Tutorials

### **Core Firmware Methods**

- `Particle.function()`: Call a C++ function on the device from the cloud.
    
- `Particle.variable()`: Expose a device variable to the Cloud API.
    
- `Particle.publish()`: Broadcast an event to the cloud.
    
- `Particle.subscribe()`: Listen for events from the cloud or other devices.
    

### **Critical Diagnostic Metrics**

- **Signal Strength:** Measured in dBm, normalized to 0–100%.
    
- **Signal Quality:** Measure of relative noise and interference.
    
- **Round-Trip Time (RTT):** Latency of CoAP messages from cloud to device.
    
- **CGI (Cell Global Identity):** Used in cellular devices to identify the specific tower (MCC-MNC-LAC-CI).
    

---

## ## 5. Professional Services & Ecosystem

- **Particle Studios:** A professional engineering arm providing PCB design, enclosure engineering, and manufacturing scale-up.
    
- **Partner Program:** An ecosystem of design firms (e.g., Voxdale, Ovyl) and technology partners (Edge Impulse, Losant).
    
- **Community:** Over 10,000 developers active on the Discourse-powered forums for troubleshooting and brainstorming.
    

---

> **Note on Compliance:** All Particle solutions are encrypted by default and compliant with **SOC II, GDPR, CCPA, and Privacy Shield** standards.


---

## ## 6. 2026 Pricing & Fleet Scaling

Particle uses a "Block" system for scaling. Each block supports **100 devices**.

|**Plan**|**Price**|**Included Data Operations (Monthly)**|**Best For**|
|---|---|---|---|
|**Free**|$0|100K|Prototyping, educational, and personal projects.|
|**Basic**|$299 /block|720K|Simple products, low-frequency sensing, and remote control.|
|**Plus**|$599 /block|5M|High-res data, Edge ML, tracking, and multi-radio.|
|**Professional**|Custom|Flexible|Large-scale deployments with invoice billing & premium support.|
|**Enterprise**|Custom|Flexible|Mission-critical fleets requiring dedicated "Watchdog" support.|

### **Understanding Data Operations (Data Ops)**

A Data Operation is the unit of measure for cloud interaction.

- **1 Data Op consumed:** Publishing/Receiving a message (up to 1KB), Location Fusion calls, Logic function runs, and Ledger syncs.
    
- **Included (Free):** Webhooks, REST API calls, and **OTA firmware updates** (Wi-Fi/Cellular/Ethernet).
    

---

## ## 7. Advanced Device OS Capabilities

### **Connectivity & Networking**

- **Multi-Radio Transport:** Seamlessly switch between Wi-Fi, Cellular, LoRaWAN, and Satellite.
    
- **Cellular Primitives:**
    
    - `Cellular.RSSI()`: Get signal strength and quality.
        
    - `cellular_global_identity()`: Retrieve unique tower ID (MCC, MNC, LAC, CI) for location without GPS.
        
- **BLE (Bluetooth Low Energy):** Full central/peripheral support, iBeacon advertising, and secure pairing.
    

### **Data Management Primitives**

- **Particle Ledger:** Use `Particle.ledger` to manage digital twins. It handles state synchronization automatically, ensuring the device and cloud are always in sync even after reboots.
    
- **Asset OTA:** Efficiently update non-firmware assets (like ML models or configuration files) without a full firmware re-flash.
    
- **JSON Buffer Writer:** Built-in `JSONBufferWriter` for efficient, memory-safe creation of JSON payloads at the edge.
    

### **Hardware Control & Power**

- **FuelGauge:** Classes to monitor `getSoC()` (State of Charge) and `getVCell()` (Voltage) for battery-powered deployments.
    
- **Sleep Modes:** Advanced `System.sleep()` configurations for ultra-low power "hibernate" or "standby" states.
    

---

## ## 8. Security & Platform Integrity

- **Acquisition Note:** Particle was recently acquired by **Digi International**, expanding its industrial reach.
    
- **Encryption:** All communication is encrypted via TLS/DTLS by default.
    
- **TrustZone:** Modern hardware (like Photon 2) utilizes ARM TrustZone for secure execution environments.
    
- **Compliance:** Maintained SOC 2 Type II, GDPR, and CCPA certifications.
    

---

## ## 9. Product Lifecycle & Advisories

- **Long Term Support (LTS):** Particle provides specific LTS releases of Device OS for enterprise stability.
    
- **Sunsets:** 2G/3G networks are being phased out globally. Particle offers migration paths to LTE-M and 5G (Tachyon).
    
- **Technical Advisories (TAN):** Critical updates (e.g., TAN006 for GNSS interface) are published regularly to ensure fleet reliability.
    

## ## 10. Hardware Comparison: The "Gen 4" Powerhouses

Choosing between Particle's top-tier modules depends on your computational needs and connectivity environment.

|**Feature**|**Tachyon (5G SBC)**|**M-SoM (Multi-Radio)**|**B-SoM / Boron (LTE-M)**|
|---|---|---|---|
|**Primary Radio**|5G (Sub-6 GHz)|LTE-M / 2G + Satellite|LTE-M (Cat M1)|
|**Secondary Radio**|Wi-Fi 6E, BT 5.2|Wi-Fi (Dual-band), BLE 5.0|BLE 5.0|
|**Processor**|Qualcomm Octa-core (AI)|Realtek RTL872x|Nordic nRF52840|
|**Operating System**|Linux (Ubuntu/Debian)|Particle Device OS|Particle Device OS|
|**Edge AI**|High (Integrated NPU)|Low (Simple TFLite)|Low (Basic patterns)|
|**Form Factor**|Single Board Computer|M.2 SoM|M.2 SoM / Feather|
|**Best For**|Video, Gateways, Edge ML|Global Asset Tracking|Static Industrial Sensors|

---

## ## 11. Advanced Implementation: Multi-Sensor Ledger

**Particle Ledger** is the preferred method for state management in 2026. Unlike standard variables, Ledgers are persistent and support complex data structures.

### **C++ Boilerplate: Multi-Sensor Sync**

C++

```
#include "Particle.h"

// Define the Ledger for environmental data
Ledger sensorLedger;

void setup() {
    // Initialize Ledger (Cloud-side must have a corresponding definition)
    sensorLedger = Particle.ledger("env_data");
}

void loop() {
    static unsigned long lastUpdate = 0;
    if (millis() - lastUpdate > 300000) { // Every 5 minutes
        lastUpdate = millis();

        // Prepare data object
        Variant data;
        data.set("temp", 24.5);
        data.set("humidity", 45);
        data.set("status", "optimal");

        // Sync with Cloud - Ledger handles retries and persistence automatically
        sensorLedger.set(data);
    }
}
```

---

## ## 12. Asset OTA: Beyond Firmware

**Asset OTA** allows you to update specific files on your device without re-flashing the entire firmware binary. This is critical for:

- **Machine Learning:** Pushing new `.tflite` model files to the edge.
    
- **UI/UX:** Updating image assets for localized displays.
    
- **Config:** Large lookup tables or localization strings.
    

> **Technical Tip:** Use the Particle CLI to bundle assets:
> 
> `particle bundle assets/ --saveTo my_assets.bin`

---

## ## 13. System Health & Watchdog Strategies

To ensure 99.9% uptime for remote industrial units, implement the **Application Watchdog**:

1. **Hardware WDT:** Integrated into Gen 4 devices to reset the system if it hangs.
    
2. **Software Watchdog:** Triggered via `ApplicationWatchdog wd(60000, System.reset);` to monitor specific loops.
    
3. **Cloud Connection Health:** Use `Cellular.vitals()` to monitor signal-to-noise ratios (SNR). Values below **5dB** typically indicate impending connection drops in LTE-M environments.
    

---

### **Next Steps for Your Project**

- **Would you like me to generate a tailored bill of materials (BOM) based on a specific use case?**
    
- **Do you need a Python script example for interacting with the Tachyon 5G's AI accelerator?**
    
- **Would you like a step-by-step guide for migrating a Gen 2 (Electron/Photon) project to Gen 4 (Boron/Photon 2)?**