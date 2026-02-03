# Particle Master Documentation: The Ultimate IoT Resource

This master document synthesizes the complete Particle ecosystem—ranging from high-level business solutions to granular technical specifications.

---
## ## 0. Homepage Architecture & Copy Strategy

_(Added based on Visual Reference)_

**Goal:** Convert "Developers" into "Platform Users" immediately.

### **Section A: Global Navigation Bar**

- **Left:** Particle Logo.
    
- **Center Links:** Platform, Supported Devices, Solutions, Developers, Pricing.
    
- **Right (CTA):** Contact Sales (Button), Login/Console (Icon).
    

### **Section B: Hero Area (Above the Fold)**

- **Visual Focus:** A split-screen visual showing **VS Code (Code)** on the left and **Particle Console (Map/Vitals)** on the right. This visually proves the "Software to Hardware" connection.
    
- **Key Copy (H1 Headline):**
    
    > **"Ship software to hardware."**
    
- **Sub-headline (H2):**
    
    > "Built for **developer productivity**, observability, and reliability." _(Note: The words "developer productivity" are highlighted)._
    
- **Floating Banner (New Product):**
    
    - **Image:** Tachyon SBC.
        
    - **Text:** "Order your Tachyon now! Embed intelligence into anything... with 5G connected, AI accelerated single-board computer."
        

### **Section C: Social Proof (Logo Wall)**

- **Placement:** Immediately below Hero.
    
- **Strategy:** Show enterprise trust to validate the "Developer" tool.
    
- **Logos:** Halliburton, P&G, Goodyear, Jacuzzi, Trek.

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

## ## 14. Migration Guide: Gen 2/3 to Gen 4 (Photon 2 / Boron)

If you are upgrading from older hardware (Photon, Electron, or Argon), keep these critical changes in mind to ensure your code and hardware remain compatible.

### **Hardware Changes**

- **Logic Voltage:** While still 3.3V, Gen 4 pins are **NOT 5V tolerant**. Applying 5V to a GPIO will damage the MCU.
    
- **Form Factor:** Most Gen 4 devices use the **Feather form factor**. Ensure your existing shields or PCBs match the pinout.
    
- **Power Management:** Gen 4 devices have improved PMICs. For battery projects, use the new `PowerCheck` and `System.batteryLevel()` APIs instead of legacy fuel gauge libraries.
    

### **Firmware Adjustments**

- **System Threading:** In Device OS 6.x+, `SYSTEM_THREAD(ENABLED)` is often the default. Review your code to ensure thread-safe operations when accessing peripherals.
    
- **Wi-Fi Scanning:** On Photon 2, Wi-Fi scanning is significantly faster but uses a different underlying driver. Update any custom scanning logic to use the standard `WiFi.scan()` function.
    
- **BLE API:** The BLE API is now more robust. Use **NFC** on supported Gen 4 hardware for easy "Tap-to-Pair" setup in mobile apps.
    

---

## ## 15. Tachyon 5G: High-Performance Edge AI

The Tachyon is more than a microcontroller; it’s a Linux-based SBC designed for real-time inferencing.

### **AI Accelerator Workflow**

The Tachyon features an integrated NPU (often paired with Hailo-8 or similar accelerators in specific configurations).

**Python Example: Accessing the AI Accelerator**

Python

```
import hailo_sdk
import cv2

# Load a pre-compiled HEF (Hailo Executable File) updated via Asset OTA
model_path = "/etc/particle/assets/yolov8_detector.hef"

with hailo_sdk.InferContext(model_path) as context:
    cap = cv2.VideoCapture(0) # USB or MIPI Camera
    while True:
        ret, frame = cap.read()
        results = context.run(frame)
        
        # Publish detected anomalies to Particle Cloud via Python SDK
        if results.confidence > 0.85:
            particle.publish("anomaly_detected", str(results.label))
```

---

## ## 16. M-SoM Satellite Connectivity (NTN)

The **M-SoM** allows your device to stay connected even in "Dead Zones" using Non-Terrestrial Networks (NTN).

- **Mechanism:** When cellular signal drops below a specific threshold (e.g., -115 dBm RSRP), the M-SoM can failover to a satellite constellation (like Skylo).
    
- **Cost Management:** Satellite Data Ops are typically more expensive. Use **Logic** at the edge to filter only critical alerts (e.g., "Fire Detected") for satellite transmission while caching routine telemetry for the next cellular handshake.
    

---

## ## 17. Industrial Asset Tracking: Bill of Materials (BOM)

To build a professional-grade tracking solution in 2026, we recommend the following components:

|**Component**|**Recommendation**|**Why?**|
|---|---|---|
|**Core**|**Tracker One (M404)**|Fully certified, IP67, includes integrated GNSS.|
|**Expansion**|**CAN/Modbus Card**|To pull engine diagnostics or industrial sensor data.|
|**Battery**|**18650 Li-Po (3.7V)**|Standard high-capacity support with integrated charging.|
|**Antenna**|**Internal Flex Antenna**|Optimized for the enclosure; supports LTE-M and GPS.|
|**Enclosure**|**M1 Industrial Case**|UV resistant and impact-rated for outdoor deployment.|


---

## 18. Blueprints: Simplified Fleet Deployment

**Blueprints** (Beta 2026) is Particle’s answer to "Infrastructure as Code" for IoT. It allows you to package your entire application—firmware, cloud logic, and ledger definitions—into a single template.

- **Standardization:** Ensure every device in a specific product line (e.g., "North American HVAC Units") has identical configurations.
    
- **Version Control:** Roll back cloud-side Logic or Ledger definitions alongside firmware versions if an update causes issues.
    
- **Zero-Touch Provisioning:** When a new device is claimed to a product using a Blueprint, it automatically receives the correct firmware and joins the relevant data pipelines.
    

---

## 19. Cloud-to-Device Ledger (Remote Configuration)

While Part 3 covered sending sensor data _to_ the cloud, the **Cloud-to-Device Ledger** is the standard for pushing settings _down_ to devices.

### **The "Settings" Pattern**

Instead of using `Particle.function()` (which is transient), a Ledger persists. If a device is offline when you change a setting, it will automatically sync the new value the moment it reconnects.

**Example: Remote Polling Interval Change**

C++

```
// In setup()
Ledger configLedger = Particle.ledger("device_config");

// In loop()
Variant config = configLedger.get();
if (config.isMap()) {
    // If the cloud updated "poll_rate" to 60, the device adopts it instantly
    int newRate = config.get("poll_rate").toInt();
    if (newRate > 0) pollingInterval = newRate * 1000;
}
```

---

## 20. Advanced Satellite Failover Logic (M-SoM)

For mission-critical tracking, the M-SoM can be programmed to prioritize cost-efficiency over a satellite link.

**Failover Strategy:**

1. **Check Cellular:** If `Cellular.ready()` is false for > 10 minutes.
    
2. **Evaluate Priority:** Is the current event "Critical" (e.g., Impact Detected)?
    
3. **Activate NTN:** Use `Satellite.connect()` only if the event is critical.
    
4. **Batching:** If not critical, store data in **Flash Memory** and wait for cellular restoration.
    

---

## 21. Summary of 2026 Hardware Selection

To wrap up this Master Doc, here is the quick-reference guide for your hardware choice:

|**If you need...**|**Use this device:**|
|---|---|
|**Low cost, indoor Wi-Fi**|**Photon 2**|
|**Rugged, outdoor cellular tracking**|**Tracker One**|
|**Mass production embedded cellular**|**M-SoM (M404)**|
|**Remote areas with no cell towers**|**M-SoM + NTN Satellite**|
|**Video processing or 5G speed**|**Tachyon**|

---

## 22. External Data Integration: PowerBI & Grafana

While the Particle Console is excellent for device management, professional operations require external dashboards for data analysis.

### **Option A: PowerBI (Business Intelligence)**

- **Mechanism:** Use **Particle Webhooks** to push data to an **Azure Event Hub** or a **Power Automate** endpoint.
    
- **Best For:** Creating executive reports, calculating ROI, and blending IoT data with financial records.
    
- **Flow:** `Device` $\rightarrow$ `Particle Cloud` $\rightarrow$ `Webhook` $\rightarrow$ `Azure` $\rightarrow$ `PowerBI`.
    

### **Option B: Grafana (Operational Monitoring)**

- **Mechanism:** Route your data through an **InfluxDB** or **Prometheus** instance.
    
- **Best For:** Real-time engineering dashboards, high-frequency telemetry, and technical alerting.
    
- **Flow:** `Device` $\rightarrow$ `Particle Cloud` $\rightarrow$ `Webhook` $\rightarrow$ `InfluxDB` $\rightarrow$ `Grafana`.
    

---

## 23. The "Block" Billing Calculator

To avoid surprise costs, use this formula to estimate your monthly "Block" requirements.

$$Total\ Monthly\ Ops = (Devices \times Ops\ Per\ Day \times 30)$$

**Example Scenario: 250 Asset Trackers**

1. **Ops per Day:** 24 publishes (1 per hour) + 2 Ledger syncs = **26 Ops/Day**.
    
2. **Daily Fleet Total:** $250 \times 26 = 6,500\ Ops/Day$.
    
3. **Monthly Fleet Total:** $6,500 \times 30 = 195,000\ Monthly\ Ops$.
    
4. **Billing:** * One **Free** block covers 100K Ops.
    
    - You would need **two additional Basic Blocks** ($2 \times \$299$) to cover the remaining 95K Ops and the extra 150 devices.
        

---

## 24. Full System Implementation: The "Sentinel" Boilerplate

This C++ code combines everything we've discussed: **Ledger for config**, **Variables for status**, and **Publish for alerts**.

C++

```
#include "Particle.h"

SYSTEM_THREAD(ENABLED);

// Object definitions
Ledger config;
double currentTemp = 0;
int alertThreshold = 30; // Default 30C

void setup() {
    config = Particle.ledger("sentinel_config");
    Particle.variable("temp", currentTemp);
}

void loop() {
    // 1. Read Sensor
    currentTemp = analogRead(A0) * 0.1; // Dummy math

    // 2. Remote Configuration (Cloud-to-Device)
    Variant settings = config.get();
    if(settings.isMap()) {
        alertThreshold = settings.get("threshold").toInt();
    }

    // 3. Conditional Alerting (Edge Logic)
    if (currentTemp > alertThreshold) {
        Particle.publish("ALARM/OVERTEMP", String(currentTemp), PRIVATE, WITH_ACK);
        delay(60000); // Debounce alert
    }
    
    delay(5000);
}
```

---

## 25. Final Checklist for Deployment

1. **Hardware:** Is the device in a UV-rated enclosure?
    
2. **Firmware:** Is the **Application Watchdog** enabled?
    
3. **Security:** Are all **Webhooks** using SSL (HTTPS)?
    
4. **Scaling:** Have you defined your **Product Groups** in the Console for staged OTA rollouts?

## Global Footer

**Layout Spec:** Dark Theme (`#000000` Background), 5-Column Grid, Full Width.

**Content Inventory:**

- **Column 1: Products**
    
    - [Link] Hardware
        
    - [Link] Connectivity
        
    - [Link] Device Management
        
    - [Link] Device OS
        
    - [Link] Tachyon **(Label: NEW)**
        
- **Column 2: Solutions**
    
    - [Link] Asset Tracking
        
    - [Link] Preventative Maintenance
        
    - [Link] Condition Monitoring
        
    - [Link] Smart Energy
        
- **Column 3: Resources**
    
    - [Link] Documentation (Docs)
        
    - [Link] Tutorials
        
    - [Link] Support
        
    - [Link] Status
        
    - [Link] System Changelog
        
- **Column 4: Company**
    
    - [Link] About Us
        
    - [Link] Careers
        
    - [Link] Partners
        
    - [Button] Contact Sales (Primary CTA Style)
        
- **Column 5: Connect & Legal**
    
    - **Social Icons:** Twitter (X), GitHub, LinkedIn, YouTube, Instagram.
        
    - [Link] Privacy Policy
        
    - [Link] Terms of Service
        

**Bottom Bar:**

- **Copyright Text:** "© 2026 Particle Industries, Inc. All rights reserved."

