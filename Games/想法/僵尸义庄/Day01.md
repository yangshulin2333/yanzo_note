今天（Day 1）你不仅仅是“建了个项目”，你其实解决了一系列**工程化问题**并搭建了一个**跨平台架构**。

以下是今天的核心知识点复盘，请把它们刻在脑子里，这些都是面试官喜欢问的细节：

---

### 1. 开发环境与工程化 (Engineering)

- **网络环境排查**：你学会了如何绕过 Unity Hub 的网络限制。
    
    - **关键点**：Unity Hub 的下载器在非 TUN 模式下不走代理。解决方案是使用 **V2RayN 的 TUN 模式** 接管系统流量，或者去官网 Archive 直接下载 `.exe` 离线安装包。
        
- **版本选择**：
    
    - **Unity 6 (6000.x LTS)**：你使用的是最新的长期支持版本。LTS (Long Term Support) 代表稳定性，是商业项目的首选。
        
    - **模板选择 Universal 3D (URP)**：你没有选老旧的 Built-in 管线，而是选了 URP (Universal Render Pipeline)。
        
    - _面试话术：“我选择 URP 是因为它在手机端性能好，同时能支持高质量的光影效果（比如 Shader Graph）。”_
        

---

### 2. Unity 编辑器基础 (Editor Basics)

- **核心面板**：
    
    - **Hierarchy (层级)**：演员表。
        
    - **Inspector (属性)**：修改器（位置、颜色、脚本）。
        
    - **Project (项目)**：资源仓库。
        
    - **Console (控制台)**：报错和 Debug.Log 的地方。
        
- **灰盒测试 (Greyboxing)**：
    
    - 我们没有花时间找美术资源，而是用 **Capsule (胶囊体)** 代表主角，**Plane** 代表地面。这在游戏开发中叫“白模/灰盒”阶段，专注于验证核心玩法逻辑。
        

---

### 3. 核心架构：新输入系统 (New Input System)

这是你今天含金量最高的部分。你没有使用过时的 `Input.Manager`，而是部署了跨平台的 **Input System Package**。

#### A. 配置流程

1. **Input Actions Asset**：创建了 `.inputactions` 配置文件。
    
2. **Action Maps**：定义了 `Gameplay` 映射表。
    
3. **Composite Binding**：把 W/A/S/D 组合成一个 `Vector2` (2D向量)，实现了方向的标准化。
    
4. **Generate C# Class**：勾选这个选项，让 Unity 自动把配置生成代码类 (`GameControls.cs`)，方便我们在脚本里调用。
    

#### B. 代码逻辑 (Event-Driven)

你从“轮询”进化到了“事件驱动”。

- **旧方法 (Polling)**：
    
    C#
    
    ```
    void Update() {
        if (Input.GetKeyDown(KeyCode.Space)) { ... } // 每一帧都在问：按了吗？
    }
    ```
    
- **新方法 (Event-Driven)**：
    
    C#
    
    ```
    // 订阅事件：当“按键”发生时，通知我
    controls.Gameplay.Breath.started += ctx => StartBreath();
    ```
    
    - `started`: 按下的瞬间。
        
    - `performed`: 动作执行中（对于按钮通常和 started 几乎同时，对于摇杆是数值变化时）。
        
    - `canceled`: 松开的瞬间。
        
    - `ReadValue<Vector2>()`: 从上下文读取输入值（兼容 键盘WASD、手柄摇杆、手机虚拟摇杆）。
        

#### C. 生命周期管理

- **Awake**: 初始化 `new GameControls()` 并绑定事件。
    
- **OnEnable / OnDisable**: **必须**在这里开启 (`Enable`) 和关闭 (`Disable`) 输入监听。如果不写，输入系统不会工作，或者报错。
    

---

### 4. 踩坑与解决 (Troubleshooting)

这些报错经验非常宝贵：

1. **Old Input System Disabled**:
    
    - **现象**：用 `Input.GetAxis` 时报错，说新系统已激活。
        
    - **解决**：Project Settings -> Player -> Active Input Handling 改为 **Both**。
        
2. **Visual Studio 编码警告**:
    
    - **现象**：保存带中文/Emoji的代码时弹窗。
        
    - **解决**：保存为 **Unicode (UTF-8)**。这是标准做法，防止中文乱码。
        
3. **脚本改名报错**:
    
    - **原理**：C# 脚本的 **文件名** 必须和代码里的 `public class 类名` 完全一致，否则 Unity 挂载不上脚本。
        

---

### 🧠 面试模拟题 (Day 1 范围)

如果面试官问你下面这些，你应该能自信回答：

- **Q: 你为什么用 New Input System 而不用 Input.GetAxis？**
    
    - **A:** 因为我要做双端互通。旧系统要把键盘和触摸屏分开写，逻辑很乱。新系统通过 Action 抽象了“移动”这个动作，我只需要绑定一次，代码里统一读取 Vector2 即可，解耦了逻辑层和硬件层。
        
- **Q: 你的 Input System 代码写在哪里？**
    
    - **A:** 我让它自动生成了 C# Class，然后在 `PlayerController` 的 `Awake` 里实例化，并订阅了 `performed` 和 `canceled` 事件。
        
- **Q: 怎么处理 Unicode 字符保存问题？**
    
    - **A:** 统一使用 UTF-8 编码保存脚本。
        

---

### ✅ 下一步：Day 2 预告

今天你的主角是“瞎子”（只能在控制台打印）。

明天（Day 2）我们要让它“看得见”：

1. **UI 开发**：制作血条（肺活量条）。
    
2. **数据逻辑**：用 `Mathf` 数学函数计算肺活量的消耗与恢复。
    
3. **视觉反馈**：把控制台的文字变成屏幕上的 UI 动画。
    

好好休息，今天的进度非常完美！保持这个节奏，一个月拿下 Offer 很有希望！