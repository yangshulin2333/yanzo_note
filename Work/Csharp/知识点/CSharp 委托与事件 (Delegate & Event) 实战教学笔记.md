
# C# 委托与事件实战笔记

**核心概念：**

- **委托 (Delegate)：** 函数的“容器”或“签名标准”。（可以理解为“函数指针”）。
    
- **事件 (Event)：** 基于委托封装的“通知机制”，实现了 **发布者 (Publisher)** 与 **订阅者 (Subscriber)** 的解耦。
    

---

## 练习一：一家三口吃饭 (多播委托基础)

场景描述： 妈妈做饭，做好后通知全家（爸爸、孩子、妈妈自己）一起吃饭。

教学重点： 理解 += (多播/订阅) 和 Invoke (触发) 的流程。

### 完整代码实现

C#

```
using System;

namespace FamilyDinner
{
    // 1. 定义委托 (规定了“吃饭”这个动作的签名：无返回值，无参数)
    public delegate void EatHandler();

    // --- 发布者 (Publisher) ---
    public class Mom
    {
        // 2. 声明事件 (本质是一个受保护的委托列表)
        public event EatHandler OnDinnerReady;

        public void Cook()
        {
            Console.WriteLine("【妈妈】正在厨房做饭...");
            System.Threading.Thread.Sleep(1000); // 模拟耗时
            Console.WriteLine("【妈妈】饭做好了！开饭！");

            // 3. 触发事件 (广播)
            // ?.Invoke() 是 C# 的安全写法：如果不为空(有人订阅)，则执行
            OnDinnerReady?.Invoke();
        }

        public void Eat() => Console.WriteLine("-> 妈妈坐下来吃饭。");
    }

    // --- 订阅者 (Subscribers) ---
    public class Dad
    {
        public void Eat() => Console.WriteLine("-> 爸爸放下报纸，过来吃饭。");
    }

    public class Kid
    {
        public void Eat() => Console.WriteLine("-> 孩子洗手，开始吃饭。");
    }

    // --- 主程序 ---
    class Program
    {
        static void Main(string[] args)
        {
            Mom mom = new Mom();
            Dad dad = new Dad();
            Kid kid = new Kid();

            // 4. 订阅事件 (核心步骤)
            // 注意：传递的是方法名 (dad.Eat)，不要加括号 ()
            mom.OnDinnerReady += dad.Eat;
            mom.OnDinnerReady += kid.Eat;
            mom.OnDinnerReady += mom.Eat; // 妈妈自己也订阅

            // 5. 开始流程
            mom.Cook(); 
            // 运行结果：妈妈喊完后，三个人的 Eat 方法会依次自动执行
        }
    }
}
```

---

## 练习二：怪物死亡 (观察者模式/解耦)

场景描述： 怪物死亡时，需要同时发生：玩家加钱、UI 刷新、成就计数。

教学重点： 解耦 (Decoupling)。怪物类不需要引用 UI 或 Player 类，只管“广播”死亡消息。

### 完整代码实现

C#

```
using System;

namespace GameLogic
{
    // --- 被观察者 (怪物) ---
    public class Monster
    {
        public string Name { get; set; }

        // 使用 C# 内置的 Action 委托 (等同于 delegate void xxx())
        // 这里的 OnDeath 就是“死亡事件”
        public event Action OnDeath;

        public Monster(string name) => Name = name;

        public void Die()
        {
            Console.WriteLine($"\n=== 怪物 {Name} 死亡 ===");
            
            // 触发事件：通知所有关心的系统
            OnDeath?.Invoke();
        }
    }

    // --- 观察者模块 ---
    public class Player
    {
        public int Gold { get; private set; } = 0;
        public void AddGold() 
        {
            Gold += 10;
            Console.WriteLine($"[逻辑] 玩家金币+10 (当前: {Gold})");
        }
    }

    public class UIManager
    {
        public void UpdateUI() => Console.WriteLine($"[界面] UI面板已刷新数据...");
    }

    public class AchievementSystem
    {
        public int KillCount { get; private set; } = 0;
        public void AddKillCount()
        {
            KillCount++;
            Console.WriteLine($"[成就] 击杀计数+1 (当前: {KillCount})");
        }
    }

    // --- 主程序 ---
    class Program
    {
        static void Main(string[] args)
        {
            // 1. 初始化各个独立模块
            Monster slime = new Monster("史莱姆");
            Player player = new Player();
            UIManager ui = new UIManager();
            AchievementSystem ach = new AchievementSystem();

            // 2. 绑定逻辑 (Wiring)
            // 谁关心怪物死没死，谁就来订阅
            slime.OnDeath += player.AddGold;
            slime.OnDeath += ui.UpdateUI;
            slime.OnDeath += ach.AddKillCount;

            // 3. 模拟游戏运行
            slime.Die();
            
            // 扩展思考：
            // 如果以后要加一个“播放死亡音效”，只需再写一个 AudioSystem 
            // 然后 slime.OnDeath += audio.PlaySound; 即可，完全不用改 Monster 类的代码。
        }
    }
}
```

---

## 教学核心 Q&A (针对学生常见疑问)

### 1. 为什么代码里要写 `event` 关键字？不写能不能跑？

- **能跑，但不安全。**
    
- 如果不加 `event`（只写 `public Action OnDeath`），外部类（比如 Player）可以做破坏性操作：
    
    - `monster.OnDeath = null;` （清空了别人的订阅，灾难！）
        
    - `monster.OnDeath.Invoke();` （假传圣旨，没死却喊死了！）
        
- **加了 `event`：** 编译器强制外部只能用 `+=` (订阅) 和 `-=` (取消)，且只能在 `Monster` 内部触发 `Invoke`。
    

### 2. `OnDinnerReady?.Invoke()` 是什么意思？

- 这是 **Null 检查 + 执行** 的组合拳。
    
- 等同于：
    
    C#
    
    ```
    if (OnDinnerReady != null) 
    {
        OnDinnerReady();
    }
    ```
    
- **作用：** 防止如果没一个人订阅事件（清单是空的），直接调用会报“空指针异常”导致游戏崩溃。
    

### 3. `+=` 后面为什么不加括号 `()`？

- `dad.Eat()` 是**动作**（动词）：表示“现在立刻吃饭”。
    
- `dad.Eat` 是**地址**（名词）：表示“吃饭这个方法在哪里”。
    
- **委托存的是地址**，等到 `Invoke` 的时候才会根据地址去找方法并执行。