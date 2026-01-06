
## 析构函数
```
 ~类名()
 {
     Console.WriteLine("析构函数被调用!");
 }
```
## 垃圾回收机制
C# 的垃圾回收机制（Garbage Collection, GC）是自动内存管理的一部分，用于释放那些不再被应用程序使用的对象，以避免内存泄漏。以下是其主要特点：

### 工作原理

1. **代数的内存管理**:
   - 内存根据对象的生命周期分为三代（Generation 0、Generation 1、Generation 2）。
   - Generation 0：短生命周期对象。
   - Generation 1：中等生命周期对象。
   - Generation 2：长生命周期对象。

2. **标记和压缩**:
   - **标记**：垃圾回收器（GC）会遍历所有对象并标记那些仍然可达的对象。
   - **清理**：未标记的对象被认为是垃圾，会被清理。
   - **压缩**：清理后，内存会被压缩，以消除碎片。

3. **触发条件**:
   - 当堆内存不足时。
   - `GC.Collect()` 手动调用垃圾回收。
   - 系统有空闲的时候进行后台回收。

### 优势

- **自动管理**：开发者不必手动释放内存。
- **减少泄漏**：大大降低了内存泄漏的可能性。

### 注意事项

- **非确定性**：具体何时进行垃圾回收不可预测。
- **大对象堆（LOH）**：大的对象直接分配在Generation 2，并且需要更长时间才能被回收。

### 最佳实践

- **减少对象分配**：尽量复用对象，避免频繁创建和销毁。
- **Dispose模式**：对于非托管资源，使用 `IDisposable` 接口来手动释放。
- **弱引用**：使用 `WeakReference` 避免阻止对象被GC。

垃圾回收机制有效地管理内存，但开发者仍需注意最佳实践，以确保应用程序的性能和稳定性。



## 是索引器

索引器（Indexer）允许对象通过索引访问内部元素，就如同数组一样。索引器可以定义在类或结构中，语法类似于属性。

### 基本语法

```csharp
public return_type this[type index]
{
    get { /* 返回索引对应的值 */ }
    set { /* 设置索引对应的值 */ }
}
```

- **return_type**：索引器返回的元素类型。
- **type**：索引的类型（通常是`int`）。

### 特性

- **类似数组访问**：通过对象实例直接使用`obj[index]`来进行访问。
- **多样性**：可定义多个不同参数类型的索引器（重载）。
- **隐式实现**：不需要声明字段，只是对已有集合的访问。

### 示例代码

```csharp
public class SampleCollection<T>
{
    private T[] array = new T[100];

    public T this[int index]
    {
        get
        {
            if (index < 0 || index >= array.Length)
                throw new IndexOutOfRangeException();
            return array[index];
        }
        set
        {
            if (index < 0 || index >= array.Length)
                throw new IndexOutOfRangeException();
            array[index] = value;
        }
    }
}
```

### 使用

```csharp
var collection = new SampleCollection<string>();
collection[0] = "Hello";
collection[1] = "World";
Console.WriteLine(collection[0]); // 输出 "Hello"
Console.WriteLine(collection[1]); // 输出 "World"
```

### 关键点

1. **多索引参数**：可以定义多参数的索引器。
2. **访问修饰符**：索引器可以有不同的访问修饰符（`public`、`private`等）。
3. **只读或只写**：可以定义只读（没有`set`）或只写索引器（没有`get`）。

### 应用场景

- **封装集合操作**：简化对类中集合属性的访问。
- **自定义集合类**：创建自定义集合类，提供自然的数组式访问。

索引器使得类的实例更具可访问性和灵活性，尤其在处理类似数组的集合时，提供了方便、可读性高的操作方式。