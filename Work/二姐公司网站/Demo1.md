
### 官网建设核心资料库


**这版内容涵盖了具体的页面文案、技术参数逻辑、以及业务流程描述。** 请把这些详细内容作为 Context 喂给 AI，让它严格基于此生成内容。


#### 1. 首页 (Homepage) - 转化逻辑与关键文案

_目标：3秒内建立信任，展示“中国制造+国际品质”。_

- **Hero Section (首屏文案参考)**:
    
    - **Headline Option A (强调合作)**: "Your Premier OEM/ODM Partner for EV Charging Solutions."
        
    - **Headline Option B (强调技术)**: "Scalable, Smart, and Reliable EVSE Infrastructure for Global Markets."
        
    - **Sub-headline**: "Bridging advanced manufacturing with cutting-edge connectivity. We empower brands to launch world-class charging networks."
        
    - **CTA Button**: "Explore OEM Services" / "Inquire Now"
        
- **Key Value Propositions (核心卖点 - 图标+短文案)**:
    
    - **End-to-End Manufacturing**: "From industrial design (ID) to mass production, we handle the entire lifecycle under one roof." (参考 Flex)
        
    - **Global Certification**: "CE, TUV, UL, and CB certified hardware ready for EU and US markets."
        
    - **Smart Connectivity**: "Integrated with OCPP 1.6J/2.0.1 for seamless backend management." (参考 Particle)
        
- **Trust Bar (信任背书)**:
    
    - _指令_: 展示一行灰度 Logo，包括 TUV Rheinland, UL, CE, RoHS，以及 "Exporting to 30+ Countries".
        

---

#### 2. 产品中心 (Products) - 参数与描述细节

_目标：展示专业度，参数要细致（参考 Wallbox/Easee 的参数表）。_

**Category A: AC EV Chargers (交流桩 - 主力产品)**

- **文案描述**: "Compact yet powerful. Designed for residential and commercial applications, featuring dynamic load balancing and easy installation."
    
- **关键参数列表 (喂给 AI 的 Specs)**:
    
    - _Power Output_: 7kW (1-phase) / 11kW & 22kW (3-phase).
        
    - _Connector_: Type 2 (IEC 62196-2) / Type 1 (SAE J1772).
        
    - _Protection_: IP55 / IP65 Waterproof, IK10 Impact Resistance.
        
    - _Safety_: Built-in RCD (Type A + 6mA DC), PEN Fault Protection (No earth rod needed).
        
    - _Connectivity_: Wi-Fi, Bluetooth, 4G LTE, Ethernet.
        
    - _User Interface_: LED Ring status light, 4.3-inch LCD Screen (Optional), RFID Reader.
        

**Category B: DC Fast Chargers (直流快充)**

- **文案描述**: "High-performance DC charging stations designed for fleets, highways, and public parking. Modular power modules for easy scalability."
    
- **关键参数列表**:
    
    - _Power Range_: 30kW / 60kW / 120kW / 180kW (Modular Design).
        
    - _Standard_: CCS1, CCS2, CHAdeMO, GBT.
        
    - _Efficiency_: >95% peak efficiency.
        
    - _Cooling_: Forced Air Cooling / Liquid Cooling (Optional).
        

---

#### 3. OEM/ODM 解决方案 (OEM/ODM Solutions) - B2B 核心

_这是最重要的页面，参考 Flex/Jabil 的供应链描述。_

- **页面标题**: "Custom Engineering & Manufacturing Services"
    
- **流程描述 (Process Flow)**:
    
    1. **Requirement Analysis**: "We align with your brand identity and market specifications."
        
    2. **Industrial & Structural Design**: "Expert ID/MD teams to create unique, ergonomic casings."
        
    3. **Hardware & Software Development**: "Custom PCB layout and firmware adaptation (OCPP integration)."
        
    4. **Prototyping & Validation**: "Rapid 3D printing and rigorous lab testing (thermal, waterproof, voltage)."
        
    5. **Mass Production**: "ISO-certified factories ensuring consistent quality at scale."
        
- **服务关键词 (Keywords)**: White-label, SKD (Semi-Knocked Down), CKD (Completely Knocked Down), Mold Tooling, Private Labeling.
    

---

#### 4. 技术与软件 (Technology & Software)

_即使只卖硬件，也要吹软件，参考 Tuya/Particle。_

- **Dynamic Load Balancing (DLB)**:
    
    - _描述_: "Automatically adjusts charging power based on real-time household/building energy usage to prevent grid overload."
        
- **Solar Integration (光伏联动)**:
    
    - _描述_: "Eco-mode allows charging purely from surplus solar energy." (参考 Victron)
        
- **OCPP Interoperability**:
    
    - _描述_: "Fully agnostic hardware. Our chargers connect seamlessly to any third-party CSMS (Charging Station Management System) via OCPP 1.6J or 2.0.1."
        

---

#### 5. 关于我们与制造实力 (Company & Manufacturing)

_建立“源头工厂”的信任感。_

- **Factory Profile**:
    
    - "Located in [City, China], our manufacturing hub covers [XX,000] sqm with [XX] automated production lines."
        
    - "Monthly Capacity: [XX,000] AC units / [XX,000] DC units."
        
- **Quality Control (QC)**:
    
    - "Strict QC process including IQC (Incoming Quality Control), IPQC (In-Process), and OQA (Outgoing Quality Assurance)."
        
    - "100% Burn-in testing for every unit before shipment."
        

---

#### 6. 联系我们 (Contact & Inquiry)

_不要只放一个邮箱，要做成“询盘表单”。_

- **Form Fields (表单字段)**:
    
    - Name, Company Email, Country.
        
    - **Business Type (下拉菜单)**: Distributor / CPO (Charge Point Operator) / Installer / Brand Owner.
        
    - **Product Interest**: AC Chargers / DC Chargers / OEM Service.
        
- **FAQ Section (常见问题 - 增加 SEO)**:
    
    - Q: Do you support white-labeling? A: Yes, we offer full logo, color, and packaging customization.
        
    - Q: What is your MOQ (Minimum Order Quantity)? A: Flexible MOQ for sample testing.
        
    - Q: What is the warranty period? A: Standard 2-year warranty with options to extend.
        

---

**给 AI 的总指令 (System Prompt 建议)**:

> "You are an expert B2B web copywriter for the EV charging industry. Use the structured data above to generate website content. The tone should be professional, international, and technically accurate. Avoid Chinglish. Emphasize 'Reliability', 'Scalability', and 'Partnership'."
