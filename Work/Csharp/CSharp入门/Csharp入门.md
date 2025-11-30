#Csharp/Csharp入门


##### 数值类型一览表

| 类型       | 位数  | 记忆技巧               | 取值范围                                                   |
| -------- | --- | ------------------ | ------------------------------------------------------ |
| `sbyte`  | 8位  | **-128到127** (背下来) | -128 ~ 127                                             |
| `byte`   | 8位  | **0到255** (RGB颜色)  | 0 ~ 255                                                |
| `short`  | 16位 | **±3万** (约32K)     | -32,768 ~ 32,767                                       |
| `ushort` | 16位 | **6万5** (端口号)      | 0 ~ 65,535                                             |
| `int`    | 32位 | **±21亿** (地球人口)    | -2,147,483,648 ~ 2,147,483,647                         |
| `uint`   | 32位 | **42亿** (双倍int)    | 0 ~ 4,294,967,295                                      |
| `long`   | 64位 | **±922京** (天文数字)   | -9,223,372,036,854,775,808 ~ 9,223,372,036,854,775,807 |
| `ulong`  | 64位 | **1844京** (双倍long) | 0 ~ 18,446,744,073,709,551,615                         |

**"128-255, 3万-6万, 21亿-42亿, 京级别, decimal管钱"** *🎯*
<!-- more -->

###### 有符号整数类型

| 类型    | .NET类型       | 取值范围                                                | 位数 | 字节数 |
| ------- | -------------- | ------------------------------------------------------- | ---- | ------ |
| `sbyte` | `System.SByte` | -128 到 127                                             | 8    | 1      |
| `short` | `System.Int16` | -32,768 到 32,767                                       | 16   | 2      |
| `int`   | `System.Int32` | -2,147,483,648 到 2,147,483,647                         | 32   | 4      |
| `long`  | `System.Int64` | -9,223,372,036,854,775,808 到 9,223,372,036,854,775,807 | 64   | 8      |



###### 无符号整数类型

| 类型     | .NET类型        | 取值范围                        | 位数 | 字节数 |                                              |
| -------- | --------------- | ------------------------------- | ---- | ------ | -------------------------------------------- |
| `byte`   | `System.Byte`   | 0 到 255                        | 8    | 1      | 2^8  = 256<br />上限，RGB颜色值最大值        |
| `ushort` | `System.UInt16` | 0 到 65,535                     | 16   | 2      | 2^16 = 65,536 (6万5)  <br />上限，端口号范围 |
| `uint`   | `System.UInt32` | 0 到 4,294,967,295              | 32   | 4      | 2^32 = 4,294,967,296 (42亿9千万)             |
| `ulong`  | `System.UInt64` | 0 到 18,446,744,073,709,551,615 | 64   | 8      | 2^64 = 18,446,744,073,709,551,616 (1844京)   |

###### 使用示例

```csharp
// 有符号类型
sbyte sb = -128;
short s = -32768;
int i = -2147483648;
long l = -9223372036854775808L;

// 无符号类型
byte b = 255;
ushort us = 65535;
uint ui = 4294967295U;
ulong ul = 18446744073709551615UL;

//浮点型
decimal price = 19.99m;  // 商品价格，需要精确
```

###### 注意事项

- **默认类型**: 整数字面量默认为 `int` 类型
- **后缀标识**: 
  - `L` 或 `l`: long 类型
  - `U` 或 `u`: uint 类型
  - `UL` 或 `ul`: ulong 类型
- **溢出检查**: 使用 `checked` 关键字可以检查溢出
- **性能**: `int` 通常是性能最佳的整数类型



##### 溢出

```
时钟只有 12 个数字 (0-11 或 1-12)
当前时间：11点
过1小时后：12点 ✅ 正常
过2小时后：1点  ← 跳回开头！

计算机也一样：
byte 只有 256 个数字 (0-255)  
当前数值：255
加1后：0     ← 跳回开头！
```

**"满了就归零，最大变最小"** *🔄*

```
byte:    255 + 1 = 0       (满了归零)
int:     最大值 + 1 = 最小值  (满了变最小)
sbyte:   127 + 1 = -128    (满了变最小)
```

可以通过checked解决

```
int max = int.MaxValue;
int result1 = max + 1;           // 静默溢出
int result2 = checked(max + 1);  // 💥 OverflowException
```



##### 数据转换-隐式 

同类型大范围装小范围

- 有符号：long -> int -> short -> sbyte

- 无符号：ulong -> uint -> ushort -> byte

decimal类型，没办法隐式转换成double 和float。可以隐式的装整型

- 浮点型：double -> float ->  所有整型（有符号，无符号）
- decimal -> 所有整型（有符号，无符号）

不同类型

- 无符号的 无法 隐式转换成有符号的，
- 有符号的大范围可以装有符号的 则可以转换
- 浮点数可以装载任何类型的整数



| 转换类型      | 安全性     | 意图明确性       | C# 决策  |
| ------------- | ---------- | ---------------- | -------- |
| char → int    | ✅ 容器更大 | ✅ 明显是数值提升 | 允许隐式 |
| char → long   | ✅ 容器更大 | ✅ 明显是数值提升 | 允许隐式 |
| char → ushort | ✅ 技术安全 | ❌ 意图不明确     | 要求显式 |

虽然 `char` 和 `ushort` 在内存中完全一样（都是16位无符号整数），但 **C# 把它们当作不同的类型**！

```
char c = 'A';
ushort us = c;    // 即使技术可行，语义不明确

// 问题：这是把字符当数字用？还是意外的类型混淆？
// C# 说：我不确定你的意图，请明确说明！


char c = 'A';     // 65
int i = c;        // 65 (更大的容器)

// 原理：小杯子的水倒进大杯子，绝对安全！
// 16位的值放进32位的空间，不会有任何问题
```

##### region

`#region` 和 `#endregion` 是 C# 中的**预处理指令**，用于代码的组织和折叠。

```
#region 区域名称
// 这里放置相关的代码
#endregion
```

##### 字符串插值 $""

```
string name = "小明";
int age = 18;

// 使用字符串插值
string message = $"我叫{name}，今年{age}岁";
Console.WriteLine(message); // 输出：我叫小明，今年18岁
```

###### 可以在{}里写表达式

```
int x = 10;
int y = 20;

Console.WriteLine($"10加20等于{x + y}");        // ✅ 输出：10加20等于30
Console.WriteLine($"10乘20等于{x * y}");        // ✅ 输出：10乘20等于200
Console.WriteLine($"现在是{DateTime.Now}");     // ✅ 输出当前时间
```

######  格式化：在{}里用冒号:

```
{变量:格式}


DateTime today = DateTime.Now;
Console.WriteLine($"完整时间：{today}");                    // 2024/1/15 14:30:25
Console.WriteLine($"只要日期：{today:yyyy-MM-dd}");        // 2024-01-15
Console.WriteLine($"中文日期：{today:yyyy年MM月dd日}");     // 2024年01月15日

double num = 1234.567;
Console.WriteLine($"{num:F2}");  // 1234.57（2位小数）
Console.WriteLine($"{num:C}");   // ￥1,234.57（货币）
Console.WriteLine($"{num:N}");   // 1,234.57（千分位逗号）
Console.WriteLine($"{num:P}");   // 123,456.70%（百分比）
```



##### 数据转换-显式

###### 1.括号强转

注意会存在溢出问题、精度问题

浮点型转 整型会直接把小数 位抛弃

bool 和 string 类型不支持括号强转

###### 2.Parse 方法

把字符串转换成其他数据类型

基本语法：**数据类型.Parse(字符串)**

```
//int.Parse() - 转换成整数
string str1 = "123";
int num1 = int.Parse(str1);    // 123

//double.Parse() - 转换成小数
string str1 = "3.14";
double num1 = double.Parse(str1);  // 3.14

//bool.Parse() - 转换成布尔值
string str1 = "true";
bool flag1 = bool.Parse(str1);  // true

//DateTime.Parse() - 转换成日期
string str1 = "2024-01-15";
DateTime date1 = DateTime.Parse(str1);  // 2024年1月15日
```

注意数据类型需要与字符串转的类型保持一致，可以使用TryPares（） 保证安全

```
Console.WriteLine("请输入数字：");
string input = Console.ReadLine();

bool success = int.TryParse(input, out int number);
//     ↑                          ↑
//   是否成功？                 转换结果

if (success) 
{
    Console.WriteLine($"转换成功！数字是：{number}");
}
else 
{
    Console.WriteLine("转换失败！请输入有效数字。");
}


// double.TryParse
bool success1 = double.TryParse("3.14", out double d);

// bool.TryParse  
bool success2 = bool.TryParse("true", out bool b);

// DateTime.TryParse
bool success3 = DateTime.TryParse("2024-01-15", out DateTime dt);


```

###### 3.Convert 方法

Convert = 转换

简单说：一个专门做类型转换的工具箱，比 Parse 更强大！

就像：

Parse 是"专用工具"（只能 字符串→其他类型）
Convert 是"万能工具箱"（几乎任何类型都能互相转换）

基本语法：**Convert.To目标类型(要转换的值)**

```
// 从字符串转换
int num1 = Convert.ToInt32("123");      // 123
int num2 = Convert.ToInt32("-456");     // -456

// 从小数转换（四舍五入）
int num3 = Convert.ToInt32(12.3);       // 12
int num4 = Convert.ToInt32(12.7);       // 13
int num5 = Convert.ToInt32(12.5);       // 12（偶数舍入）

// 布尔值→整数（true=1, false=0）
int num6 = Convert.ToInt32(true);       // 1
int num7 = Convert.ToInt32(false);      // 0

Console.WriteLine($"12.7转整数：{num4}");  // 输出：12.7转整数：13

```

1. Convert.ToInt32() - 转换成整数

2. Convert.ToDouble() - 转换成小数

3. Convert.ToString() - 转换成字符串
4.  Convert.ToBoolean() - 转换成布尔值
5. Convert.ToDateTime() - 转换成日期

| 方法         | 输入类型     | 安全性           | null处理   | 特点       |
| ------------ | ------------ | ---------------- | ---------- | ---------- |
| **Parse**    | 只能字符串   | 不安全（会崩溃） | 崩溃       | 专用，快速 |
| **TryParse** | 只能字符串   | 安全             | 返回false  | 专用，安全 |
| **Convert**  | 几乎任何类型 | 不安全（会崩溃） | 返回默认值 | 万能，灵活 |

###### 4.ToString() 方法

**ToString()** = 转换成字符串

基本语法：对象.ToString()

```
ToString() 方法：
int number = 123;
string result = number.ToString();  // "123"

Convert.ToString()：
int number = 123;
string result = Convert.ToString(number);  // "123"

主要区别：null 处理
string nullString = null;

// ToString() 会崩溃
// string result1 = nullString.ToString();  // ❌ 崩溃！空引用异常

// Convert.ToString() 安全
string result2 = Convert.ToString(nullString);  // ✅ 返回 ""（空字符串）

Console.WriteLine($"结果：'{result2}'");  // 输出：结果：''

```

| 类型         | 默认格式             | 常用自定义格式 | 示例         |
| ------------ | -------------------- | -------------- | ------------ |
| **int**      | "123"                | "D4"（补零）   | "0123"       |
| **double**   | "3.14159"            | "F2"（小数位） | "3.14"       |
| **double**   | "1234.56"            | "C"（货币）    | "¥1,234.56"  |
| **double**   | "0.85"               | "P"（百分比）  | "85.00%"     |
| **DateTime** | "2024/1/15 14:30:45" | "yyyy-MM-dd"   | "2024-01-15" |
| **bool**     | "True"/"False"       | 无特殊格式     | "True"       |

ToString() 的格式化（重要！）

```
数字格式化

double number = 1234.5678;

// 基本转换
string str1 = number.ToString();              // "1234.5678"

// 指定小数位数
string str2 = number.ToString("F2");          // "1234.57"（保留2位小数）
string str3 = number.ToString("F0");          // "1235"（无小数位，四舍五入）

// 货币格式
string str4 = number.ToString("C");           // "¥1,234.57"（货币格式）

// 百分比格式
double percent = 0.85;
string str5 = percent.ToString("P");          // "85.00%"

// 带千位分隔符
int bigNumber = 1234567;
string str6 = bigNumber.ToString("N");        // "1,234,567.00"

Console.WriteLine($"保留2位小数：{str2}");        // 输出：保留2位小数：1234.57
Console.WriteLine($"货币格式：{str4}");          // 输出：货币格式：¥1,234.57
Console.WriteLine($"百分比格式：{str5}");        // 输出：百分比格式：85.00%

```

```
日期格式化

DateTime date = new DateTime(2024, 1, 15, 14, 30, 45);

// 基本转换
string str1 = date.ToString();                    // "2024/1/15 14:30:45"

// 自定义格式
string str2 = date.ToString("yyyy年MM月dd日");      // "2024年01月15日"
string str3 = date.ToString("yyyy-MM-dd");        // "2024-01-15"
string str4 = date.ToString("HH:mm:ss");          // "14:30:45"
string str5 = date.ToString("yyyy年MM月dd日 HH:mm"); // "2024年01月15日 14:30"

// 预定义格式
string str6 = date.ToString("D");                 // "2024年1月15日"（长日期）
string str7 = date.ToString("T");                 // "14:30:45"（长时间）

Console.WriteLine($"中文日期：{str2}");             // 输出：中文日期：2024年01月15日
Console.WriteLine($"标准日期：{str3}");             // 输出：标准日期：2024-01-15
Console.WriteLine($"时间：{str4}");               // 输出：时间：14:30:45


```



##### 异常捕获

try-catch 基本结构

```
try
{
    // 可能出现异常的代码
}
catch (异常类型 变量名)
{
    // 处理异常的代码
}
finally //可选部分
{
	//总是执行（无论是否有异常）常用于资源清理
}
//结构不需要加分号；

```

完整的异常处理结构

```
try
{
    // 可能出现异常的代码
}
catch (具体异常类型1 ex)
{
    // 处理特定异常
}
catch (具体异常类型2 ex)
{
    // 处理另一种异常
}
catch (Exception ex)
{
    // 处理所有其他异常
}
finally
{
    // 无论是否有异常都会执行的代码
}

```

##### 运算符

###### 自增

```
int a = 5;
int x = ++a; // a先变6，x得到6
int y = a++; // y先得到6，a后变7
```

###### 短路求值

```
// ✅ 正确：先判断不为空，再访问属性
if (obj != null && obj.Property > 0)

// ✅ 正确：先判断有权限，再执行操作  
if (user.IsAdmin && user.CanDelete && DeleteFile())

// ✅ 正确：先判断索引有效，再访问数组
if (index >= 0 && index < array.Length && array[index] > 0)

```

例子：

```
// 用户登录检查
bool canLogin = user != null &&           // 先检查用户存在
                user.IsActive &&          // 再检查是否激活  
                user.Password == inputPwd && // 再检查密码
                !user.IsLocked;           // 最后检查是否锁定

// 如果user为null，后面的检查都不会执行，避免了异常！

```

###### 位运算符：

- & (按位与)：两位都是1才是1
- | (按位或)：有一位是1就是1
- ^ (按位异或)：两位不同才是1
- ~ (按位取反)：0变1，1变0





计算机只认识两种状态：

- 1 = 有电/开/是/真
- 0 = 没电/关/否/假

###### 权限数值对照表

| 权限名称   | 数值 | 二进制 | 说明     |
| ---------- | ---- | ------ | -------- |
| None       | 0    | 0000   | 无权限   |
| Read       | 1    | 0001   | 读权限   |
| Write      | 2    | 0010   | 写权限   |
| Delete     | 4    | 0100   | 删除权限 |
| Admin      | 8    | 1000   | 管理权限 |
| ReadWrite  | 3    | 0011   | 读+写    |
| FullAccess | 15   | 1111   | 全权限   |

##### 字符串拼接

基本语法：

```
string.Format("模板字符串 {0} {1} {2}", 参数0, 参数1, 参数2)
```

例子

```
string name = "张三";
int age = 25;
string result = string.Format("我叫{0}，今年{1}岁", name, age);
// 输出：我叫张三，今年25岁
```

##### 运算符

基础用法

```
// 替代 if-else
int age = 18;
string result = age >= 18 ? "成年人" : "未成年";
// 输出：成年人

// 等价于：
string result;
if (age >= 18)
    result = "成年人";
else
    result = "未成年";

```

规则 

- !(逻辑非)优先级最高
- &&(逻辑与)优先级高于||(逻辑或)
- 逻辑运算符优先级 低于 算数运算符 ，条件运算符(逻辑非除外)

###### 位运算符

| 符号   | 名称   | 作用      | 示例            |     |        |
| ---- | ---- | ------- | ------------- | --- | ------ |
| `&`  | 按位与  | 都是1才是1  | `5 & 3 = 1`   |     |        |
| `    | `    | 按位或     | 有1就是1         | `5  | 3 = 7` |
| `^`  | 按位异或 | 不同为1    | `5 ^ 3 = 6`   |     |        |
| `~`  | 按位取反 | 0变1，1变0 | `~5 = -6`     |     |        |
| `<<` | 左移   | 向左移位    | `5 << 1 = 10` |     |        |
| `>>` | 右移   | 向右移位    | `5 >> 1 = 2`  |     |        |

##### for循环

```
for (int i = 0; i < 5; i++)
{
    Console.WriteLine($"第{i+1}次循环");
}
```

执行顺序：

初始化 (int i = 0) - 只执行一次
判断条件 (i < 5) - 每次循环前检查
执行循环体 - 条件为真时执行
迭代 (i++) - 循环体执行后执行
回到步骤2



###### foreach vs for

```
int[] numbers = {1, 2, 3, 4, 5};

// for循环 - 可以获取索引，可以修改
for (int i = 0; i < numbers.Length; i++)
{
    numbers[i] *= 2; // 可以修改
    Console.WriteLine($"索引{i}: {numbers[i]}");
}

// foreach循环 - 更简洁，只读遍历
foreach (int num in numbers)
{
    Console.WriteLine(num); // 只能读取
}

```
#### C#入门实践

##### ReadKey 和 KeyChar

Console.ReadKey() 用于读取用户按下的单个按键，KeyChar 是获取按键对应的字符。

###### ReadKey 基础

语法：ConsoleKeyInfo keyInfo = Console.ReadKey();

基本用法

```
Console.WriteLine("请按任意键:");
ConsoleKeyInfo key = Console.ReadKey();
Console.WriteLine($"\n你按下了: {key.Key}");
```

###### ReadKey 的三种形式

ReadKey() - 显示按键

ReadKey(true) - 隐藏按键

KeyChar 获取按键对应的字符值

```
ConsoleKeyInfo key = Console.ReadKey();

Console.WriteLine($"按键: {key.Key}");        // 按键名称
Console.WriteLine($"字符: {key.KeyChar}");    // 对应字符
Console.WriteLine($"ASCII: {(int)key.KeyChar}"); // ASCII码
```

###### 常用按键枚举

```
ConsoleKey.Enter       // 回车
ConsoleKey.Escape      // ESC
ConsoleKey.Backspace   // 退格
ConsoleKey.Delete      // 删除
ConsoleKey.Tab         // Tab
ConsoleKey.Spacebar    // 空格
ConsoleKey.UpArrow     // 上箭头
ConsoleKey.DownArrow   // 下箭头
ConsoleKey.LeftArrow   // 左箭头
ConsoleKey.RightArrow  // 右箭头
ConsoleKey.F1          // F1功能键
// ... F2-F12

```

##### 控制台窗口设置
![](assets/Csharp入门/file-20251201034844509.png)
保存后，重新启动

主要原因是因为VS2022默认不在使用命令提示符窗口，而是使用的终端窗口

而终端窗口会影响我们之后知识的学习


缓冲区大小必须 ≥ 窗口大小



###### Windows 控制台的约束：

窗口不能大于缓冲区 - 你不能看到比实际存在更多的内容
缓冲区不能小于窗口 - 不能删除正在显示的内容

```
try
{
    // 先设置缓冲区大小，再设置窗口大小
    Console.SetBufferSize(200, 40);  // 缓冲区要 >= 窗口大小
    Console.SetWindowSize(180, 40);  // 然后设置窗口大小
    Console.WriteLine("窗口大小设置成功！");
}
catch (Exception ex)
{
    Console.WriteLine($"设置失败: {ex.Message}");
}
// 检查当前控制台信息
Console.WriteLine($"当前窗口: {Console.WindowWidth} x {Console.WindowHeight}");
Console.WriteLine($"当前缓冲区: {Console.BufferWidth} x {Console.BufferHeight}");
Console.WriteLine($"最大窗口: {Console.LargestWindowWidth} x {Console.LargestWindowHeight}");
```

######  清空控制台

Console.Clear();

###### 设置光标位置：

横纵距离不通 1y = 2x(中文占两个字符)

Console.SetCursorPosition( 10,5 );

###### 背景颜色设置

```
 Console.BackgroundColor = ConsoleColor.Blue;
 Console.Clear();
```

###### 文字颜色设置

```
Console.ForegroundColor = ConsoleColor.Red;
```

###### 光标显隐

```
Console.CursorVisible = false;
```

###### 关闭控制台

```
Environment.Exit(0);
```
###### 随机数
语法：Random 随机数变量名 = new Random();

```
Random r = new Random();
int i = r.Next(); #生成一个非负的随机数
int i = r.Next(100);生成一个0~99的随机数，左包含右不包含
int i = r.Next(5,100);生成一个5~99的随机数，左闭右开
```

##### 项目调试
###### 设置断点
- **断点 (Breakpoint F9)**：在代码行左侧点击鼠标，可以设置或取消断点。这样，当程序运行到此行时会暂停执行。
###### 调试模式
- **开始调试 (F5)**：启动调试器执行程序，程序会在设置的断点处暂停。
- **停止调试**：停止当前调试会话。
###### 调试控制
- **逐语句执行 (Step Over, F10)**：执行当前代码行，然后暂停在下一行。不进入函数内部。
- **逐过程执行 (Step Into, F11)**：进入当前函数内部执行，适合查看函数内的具体执行情况。
- **执行到返回 (Step Out, Shift+F11)**：运行到当前函数返回到调用它的地方。
- **继续执行 (Continue, F5)**：让程序继续执行到下一个断点。
###### 观察数据
- **监视 (Watch)**：可以监视变量值的变化，右键变量并选择“添加到监视”。
- **局部变量 (Locals)**：查看当前作用域内所有变量的值。
