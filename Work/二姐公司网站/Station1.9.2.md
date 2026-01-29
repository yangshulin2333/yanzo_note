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

**Would you like me to create a specific implementation guide for one of these hardware modules or dive deeper into a particular cloud integration?**