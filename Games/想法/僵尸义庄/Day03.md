
# Unity学习笔记 Day 3：僵尸自动寻路 (Zombie Pathfinding)

**核心任务**：让僵尸能够智能避开障碍物，自动追踪玩家。

## 1. 核心原理：NavMesh (导航网格)
Unity 内置的 AI 寻路系统。
* **原理**：通过“烘焙” (Bake) 地形，计算出蓝色的“可行走区域”。
* **作用**：AI 只能在蓝色区域内移动，会自动绕开没烘焙的障碍物（墙壁、箱子）。

---

## 2. 操作步骤

### 第一步：烘焙地形 (Bake)
1.  **打开面板**：点击顶部菜单 `Window` -> `AI` -> `Navigation`。
2.  **设置静态 (Static)**：
    * 在场景中选中**地面 (Plane)** 和 **障碍物 (Cube)**。
    * 在 Inspector 面板右上角，勾选 **Static** (或下拉选择 `Navigation Static`)。
    * *注意：只有静态物体才能参与烘焙。*
3.  **执行烘焙**：
    * 回到 Navigation 面板，点击 **Bake** 标签页。
    * 点击底部的 **Bake** 按钮。
    * **成功标志**：场景地面变成了**蓝色**。

### 第二步：配置僵尸 (NavMesh Agent)
1.  选中场景里的 **Zombie** (圆柱体)。
2.  点击 `Add Component`，搜索并添加 **NavMesh Agent** 组件。
3.  **关键参数**：
    * `Speed`：移动速度 (例如 3.5)。
    * `Stopping Distance`：停止距离 (例如 1.5，防止僵尸跟玩家贴脸穿模)。

---

## 3. 代码驱动 (ZombieController.cs)

**核心逻辑**：获取 Agent 组件 -> 每帧更新目标位置。

```csharp
using UnityEngine;
using UnityEngine.AI; // ⚠️ 1. 必须引入这个命名空间！

public class ZombieController : MonoBehaviour
{
    private NavMeshAgent agent; // 定义代理组件
    
    // 记得在 Inspector 里把 Player 拖进去
    public Transform player;    

    void Start()
    {
        // 2. 获取身上的 NavMeshAgent 组件
        agent = GetComponent<NavMeshAgent>();
    }

    void Update()
    {
        // 3. 每一帧都告诉僵尸：去玩家现在的位置
        // SetDestination 会自动计算最短路径并绕开障碍
        if (player != null)
        {
            agent.SetDestination(player.position);
        }
    }
}
````

---

## 4. 常见问题 (Debug)

- **僵尸不动**：
    
    1. 检查有没有给代码里的 `Player` 变量赋值（拖拽主角）。
        
    2. 检查地面是不是变蓝了（NavMesh 是否烘焙成功）。
        
    3. 检查僵尸有没有卡在地板下面（Y轴位置不对）。
        
- **僵尸穿墙**：
    
    - 说明墙壁没有勾选 `Static`，或者勾选后忘记重新点 `Bake` 了。