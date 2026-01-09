
### 📝 Day 4 开发笔记：赋予游戏灵魂

#### 1. 僵尸升级 (Zombie Upgrade)

- **模型替换**：用 Mixamo 的 3D 僵尸模型替换了胶囊体。
    
- **动画配置**：
    
    - 导入了 `Idle` (待机) 和 `Run` (奔跑) 动画。
        
    - **关键设置**：Rig 类型设为 `Humanoid`；动画文件开启 `Loop Time` (循环)；Animator 中取消 `Apply Root Motion` (防止滑步)。
        
- **代码驱动**：更新 `ZombieController.cs`，通过 `agent.velocity` 判断是否移动，并传参给 Animator 的 `isRunning`。
    

#### 2. 摄像机跟随 (Camera Follow)

- **脚本实现**：编写 `CameraFollow.cs`，使用 `LateUpdate` 和 `Vector3.Lerp` 实现平滑跟随。
    
- **上帝视角**：确定了黄金参数 `Position(0, 10, -8)`, `Rotation(45, 0, 0)`。
    

#### 3. 主角升级 (Player Upgrade)

- **资源处理 (难点)**：
    
    - **本体**：下载 `With Skin` + `T-Pose` 的 FBX 文件。
        
    - **动画**：下载 `Without Skin` 的动作文件 (`Idle`, `Run`, `Crouch`)。
        
    - **骨骼修复**：解决了 Mixamo 导入时的 `Jaw/LeftEye` 骨骼冲突报错；使用 `Copy From Other Avatar` 修复了动画文件的红字报错。
        
- **状态机逻辑 (Animator)**：
    
    - 实现了 `Idle` <-> `Run` <-> `Crouch` (蹲下) 的三态切换。
        
    - 利用 `Has Exit Time` 的取消，实现了蹲下松手后瞬间切回奔跑的流畅感。
        
- **材质修复**：使用 `Extract Textures` 找回了丢失的模型贴图。
    

#### 4. 核心交互机制

- **代码更新**：在 `PlayerController.cs` 中加入了动画控制 (`anim.SetBool`)。
    
- **面朝向优化**：加入了 `Quaternion.LookRotation` 让主角奔跑时自动转向移动方向。
    
- **硬核机制**：修改代码实现了 **“屏息时禁止移动”** (按空格蹲下时强制 `moveInput = Vector2.zero`)，避免了“蹲着滑步”的怪异效果。
    

#### 5. 常见 Bug 修复手册

- **T-Pose 问题**：Animator 里的状态必须填入带有动画数据的 Animation Clip（通常藏在 FBX 文件的子级里），不能填空的或者错误的引用。
    
- **滑步问题**：动画文件必须勾选 `Loop Time`；代码逻辑要确保停止输入时速度归零。
    

---

**是否需要我帮你把这些内容创建为一个新的笔记，方便以后复习？**