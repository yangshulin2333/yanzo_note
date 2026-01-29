这是一份为您精心准备的**“B2B充电桩官网内容架构提取方案”**。

您可以直接将这份文档发给您的开发同事，告诉他：“**这是我们对标国际大厂（如Wallbox, Flex, Particle）梳理出的网站内容标准。请把这些作为‘语料’喂给AI，让它根据这些结构和风格，生成我们公司的英文官网文案。**”

---

### **提取对象分析 (Context)**

- **参考源**：Wallbox / Easee (品牌感与C端体验), Flex / Jabil (制造实力与供应链), Particle / Tuya (物联网与平台能力), Evaisun (同行竞品).
    
- **目标受众**：海外B2B客户（运营商、能源公司、分销商）。
    
- **核心诉求**：既要展示“中国制造的性价比与产能”，又要具备“欧美本土品牌的信任感与技术范儿”。
    

---

### **1. 通用站点架构 (Sitemap Structure)**

_告诉AI：我们需要一个清晰的B2B导航结构，参考以下层级：_

- **Home (首页)**: 3秒内讲清“我们是谁” + 核心产品展示 + 信任背书。
    
- **Products & Hardware (产品中心)**:
    
    - _按场景分_: Home Charging (家用), Commercial & Public (商用/公共), Fleet (车队).
        
    - _按形态分_: AC Chargers (交流), DC Fast Chargers (直流快充), Accessories (配件).
        
- **Solutions / Services (解决方案/服务)**:
    
    - _关键_：OEM/ODM Services (代工定制 - **这是中国厂商的核心卖点**).
        
    - _关键_：Software & App (软件平台 - 参考Particle/Tuya的描述).
        
- **Technology (技术实力)**: Smart Charging (智能充电), Load Balancing (负载均衡), Manufacturing (工厂智造).
    
- **Trust & Support (信任与支持)**: Certifications (证书 UL/CE/TUV), Case Studies (案例), Partner Program (招商).
    
- **Contact (联系)**: "Get a Quote" (询价) 而不仅仅是 Contact Us。
    

---

### **2. 核心文案风格 (Tone of Voice / Style Guide)**

_告诉AI：文案不要有“中式翻译腔”，请模仿以下两种风格的混合：_

- **风格A：北欧简约风 (参考 Easee/Wallbox)**
    
    - _特点_：短句，强调“简单”、“智能”、“以人为本”。
        
    - _关键词_: Simple, Smart, Powerful, Effortless, Future-proof.
        
    - _例句_: "Small. Smart. Full of Power." (小巧。智能。充满力量。)
        
    - _例句_: "Charging made easy." (让充电变得简单。)
        
- **风格B：工业权威风 (参考 Flex/Jabil)**
    
    - _特点_：强调规模、可靠性、供应链能力。
        
    - _关键词_: Scalable, End-to-End, Reliability, Global Footprint, Advanced Manufacturing.
        
    - _例句_: "Enabling critical technologies to market at scale." (助力关键技术规模化上市。)
        

**给AI的指令（Prompt示例）**：

> "Generate website copy that balances **technical authority** (like Flex) with **user-friendly simplicity** (like Easee). Use active verbs and avoid generic fluff."

---

### **3. 关键板块内容拆解 (Key Content Modules)**

_这些是网站必须包含的“积木块”，请开发同事重点关注：_

#### **A. Hero Section (首屏)**

- **参考**: Wallbox, Easee
    
- **内容**: 高清产品渲染图（应用场景） + 一句直击痛点的Slogan。
    
- **Slogan参考库**:
    
    - "Empowering the Future of E-Mobility." (赋能电动出行的未来)
        
    - "Smart EV Charging Solutions for Business & Home." (面向商业与家庭的智能充电方案)
        
    - "Your Trusted OEM/ODM Partner in EV Charging." (您值得信赖的充电桩代工伙伴)
        

#### **B. Trust Signals (信任背书 - 针对B端极为重要)**

- **参考**: Flex, Jabil, Evaisun
    
- **必须展示**:
    
    - **Certifications Bar**: 将 UL, CE, CB, TUV, RoHS 等Logo做成一行灰色图标带，放在显眼位置。
        
    - **By the Numbers (数字说话)**:
        
        - "XX+ Years Experience" (行业经验)
            
        - "XX,000+ Units Shipped" (出货量)
            
        - "XX+ Countries Served" (出口国家)
            
        - "XX,000 m² Factory Area" (工厂面积 - 体现产能)
            

#### **C. Service Capability (OEM/ODM 能力)**

- **参考**: Flex (Supply Chain/Design)
    
- **文案要点**: 不要只卖货，要卖“能力”。
    
    - "End-to-End Manufacturing" (端到端制造)
        
    - "Customization (SKD/CKD)" (支持散件组装/深度定制)
        
    - "Rapid Prototyping" (快速打样)
        
    - "Global Logistics" (全球物流支持)
        

#### **D. Software/IoT (软件与智能)**

- **参考**: Particle, Tuya
    
- **文案要点**: 即使你们主要卖硬件，也要强调设备是“Connected” (联网的)。
    
    - "OCPP 1.6J/2.0.1 Compliant" (协议兼容)
        
    - "Remote Monitoring & Maintenance" (远程监控运维)
        
    - "API Integration" (API集成能力)
        

---

### **4. 行业关键词库 (Keywords for AI)**

_请让开发同事把这组词喂给AI，确保生成的英文是行业标准的：_

- **产品词**: EVSE (Electric Vehicle Supply Equipment), Wallbox, DC Fast Charger, Level 2 Charger, Tethered/Untethered (带线/不带线).
    
- **技术词**: Dynamic Load Balancing (动态负载均衡), V2G (Vehicle to Grid), RFID Authentication, OTA Updates (远程升级), PME (Pen Fault Protection - 英国市场专用).
    
- **商业词**: White-label (白牌/贴牌), Turnkey Solution (交钥匙方案), Scalability (扩展性), TCO (Total Cost of Ownership - 总拥有成本).
    

---

**建议下一步：**

您可以直接把上面这部分内容复制下来，发到你们的项目群里。如果开发同事需要更具体的某个页面的“英文提示词（Prompt）”，您可以随时回来找我。