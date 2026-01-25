



我们要解决的第一个“不可抗力”是：**如何从屏幕上精准找到《鹅鸭杀》的窗口并实时抓取它的画面。**

---

### 第一步：安装“特工工具包”

请在你的命令行（CMD/Terminal）中输入以下命令，安装我们需要的第一批库。这些库是实现实战辅助的工业标准：

Bash

```
python3 -m pip install mss pywin32 opencv-python numpy
```

- **`mss`**: 极致的高速截屏工具，直接读取显存，解决延迟问题的核心。
    
- **`pywin32`**: 让我们能用 Python 控制和获取 Windows 窗口句柄（Handle）。
    
- **`opencv-python`**: 图像处理的“瑞士军刀”，用来判断画面内容。
    
- **`numpy`**: 图像数据的数学运算基础。
    
---

### 第二步：编写“画面同步”代码

这是我们的第一个脚本 `screen_test.py`。

**这个脚本的任务是：** 找到游戏窗口，并以最高频率把游戏画面实时显示在一个 Python 小窗口里。如果这一步能流畅运行，我们就解决了“延迟”和“画面获取”这两个最大的门槛。

请创建一个文件夹，新建 `screen_test.py`，把以下内容粘进去：

Python

```
import cv2
import numpy as np
from mss import mss
import pygetwindow as gw # 如果安装报错，可以用下面的 win32gui 方案
import win32gui
import time

def get_game_window(title="Goose Goose Duck"):
    """
    通过标题找到游戏窗口的坐标
    """
    hwnd = win32gui.FindWindow(None, title)
    if not hwnd:
        return None
    
    # 获取窗口坐标 (left, top, right, bottom)
    rect = win32gui.GetWindowRect(hwnd)
    return {
        "top": rect[1],
        "left": rect[0],
        "width": rect[2] - rect[0],
        "height": rect[3] - rect[1]
    }

def main():
    with mss() as sct:
        print("正在寻找游戏窗口...")
        
        while True:
            # 1. 实时更新窗口位置（防止你拖动游戏窗口）
            monitor = get_game_window("Goose Goose Duck")
            
            if monitor is None:
                print("\r找不到游戏，请先打开《鹅鸭杀》！", end="")
                time.sleep(1)
                continue

            # 2. 截取画面
            # sct.grab 会直接获取 monitor 指定区域的像素
            img = sct.grab(monitor)
            
            # 3. 转换格式，让 OpenCV 能处理
            frame = np.array(img)
            
            # 4. 显示画面 (验证延迟)
            cv2.imshow("GooseMind_Vision_Test", frame)

            # 5. 退出机制：按 'q' 键退出 (模仿视频中的逻辑)
            if cv2.waitKey(1) & 0xFF == ord('q'):
                break

    cv2.destroyAllWindows()

if __name__ == "__main__":
    main()
```

---

### 为什么这样写？（确保你掌握每一行）

1. **`win32gui.FindWindow`**: 这是在 Windows 系统的“电话本”里查名字，找到《鹅鸭杀》的门牌号（句柄）。
    
2. **`sct.grab(monitor)`**: 这就是视频里说的“死循环截屏”。它只截取游戏所在的那个框，不浪费性能去截桌面其他地方。
    
3. **`cv2.imshow`**: 它的作用是把抓到的画面弹出来。如果这个弹窗里的画面和你游戏里的一样流畅，说明我们的“采集引擎”完全合格，实战不会卡顿。
    

### 你需要做的：

1. **运行这个脚本**：在命令行输入 `python screen_test.py`。
    
2. **观察**：游戏画面是否出现在了 Python 的窗口里？当你移动游戏角色时，Python 窗口里的画面延迟高吗？
    

**如果你成功看到了画面，请告诉我，我们将进行下一步：教程序“认出”那个“组局”按钮，实现大厅自动判定。**