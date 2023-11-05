---
coverY: 0
---

# 🐸 1.1 控制物体的运动

## 1.1.1 Start和Update事件

**Start()**函数在游戏开始运行的时候执行一次，特别适合进行组件初始化。

**Update()**函数每帧都会执行，在不同设备上更新的频率有所区别。

<mark style="color:blue;">Start()在组件开始运行调用。</mark>

<mark style="color:blue;">Update()更新该组件调用。</mark>

**Debug.Log()**用于向控制台输出信息。

```csharp
Debug.Log("组件开始执行");
```

## 1.1.2 修改物体位置

实际上就是修改Transform组件的数据。

### 两种方法

* 使用Translate()函数

```csharp
transform.Translate(1.5f,0,0);//沿着自身右侧方向前进1.5个单位
```

* 直接指定新的位置

```csharp
transform.position=new Vector3(1,4,6);
```

### 连续位移动画

让物体每帧都移动很小的距离。

把改变位置的代码写在Update()函数里。

```csharp
void Update(){
    transform.Translate(0,0,0.3f);
    //or
    transform.position+=new Vector3(0,0,0.3f);
```

#### 保证不同主机运行距离都相同

```csharp
void Update(){
    transform.Translate(0,0,0.3f*Time.deltaTime);
    //or
    transform.position+=new Vector3(0,0,0.3f*Time.deltaTime);
```

## 1.1.3 读取和处理输入

### 获取用户当前的纵轴输入与横轴输入

```csharp
void Update(){
    float v=Input.GetAxis("Vertical");
    float h=Input.GetAxis("Horizontal");
    Debug.Log("纵轴:"+v+""+"横轴"+h+"");
    }
```

* **Input.GetAxis()**函数的返回值是一个float类型。取值范围为-1\~1。
