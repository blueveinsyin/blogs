
# 一切都在内存里
1. 开机：操作系统在c盘中、开机通电、读取固件、启动开机程序、将操作系统加载到内存中运行
2. 操作系统启动内核、启动进程、进程会有编号、启动系统服务、用户登录、运行shell和操作系统对话
3. 比如开启了chrome就会有chrome进程、这个主进程会开启辅助进程（网络服务、gpu加速）、每一个新的网页就会开启一个子进程
# 浏览器的功能
1. 发起请求，下载html、解析html，下载css、解析css，渲染页面（解析html解析css，把两者合起来放在屏幕上），下载js，解析js，执行js
2. 浏览器的功能模块：用户界面模块、渲染引擎（代码）、js引擎、存储(用户的cookie、设置）等
3. 功能模块都出于不同的线程：比如知乎页面会开启js引擎、渲染引擎。这俩可以理解为线程；js引擎与渲染引擎跨线程通信，因为js是单线程。由于跨线程操作慢，dom的速度慢。如果进程是车间，那么线程就是车间的流水线。

# js引擎
1. chrome 用的是 v8引擎，c++编写的
2. safari用的是JavScriptCore
3. 网景使用的是spidermonkey，后来被firefox使用，c++
4. node.js用的v8引擎

# js引擎功能
1. 编译：把js代码翻译为机器能执行的字节码或者机器码
2. 优化：改写代码，使其更加高效
3. 执行：执行上面的字节码或者机器码
4: 垃圾回收：把js用完的内存回收，方便之后再使用

# 在运行js之前，这个世界为我们准备了什么东西？
1. 浏览器需要提供API：window/document/setTimeout（这些都是浏览器给js提供的功能）
2. 把这些提供好的功能叫runtime env

## js代码在那里？
### stack 和 heap存放数据
1. stack：每个数据顺序存放
2. heap：每个数据随机存放
3. 非对象都放在stack区里，数组&函数都是对象
4. = 号总是会把右边的东西复制到左边（不存在传值和传址）

## 写js代码之前需要什么
1. console
2. Document
3. Object
4. Array
5. Function
* 以上5个都是window的属性，每一个都保存不同的地址（其他对象）

### 变量和对象不是同一个东西
1. 变量是容器，存放对象的地址
2. 对象在heap里面，就是一坨数据
3. 同理属性和对象也不是一个东西哦
4. 前者为内存地址，后者为内存本身（储存数据）

### 原型链
`var obj={}`
`obj.toString()`
* obj有一个隐藏的属性，属性存储了一个Object.prototype对象的值
* obj.toString()发现obj上没有toString这个属性
* 就去隐藏属性对应的对象里面找了
* 于是就找到了Object.prototype
* 每个新创建的对象实例都有一个隐藏属性，隐藏属性会指向对象的共有属性就是原型
* 共有属性无法篡改；对象的共有属性也有隐藏属性，指向Object，Object的隐藏属性是null
