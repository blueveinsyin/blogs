# number 运算
## a++ vs ++a
* a++ 的值就是做加法运算之前的值
* ++a 的值就是做加法运算之后的值

## +a为求值运算符 -a为负数运算符

# string运算 只支持+
* 连接运算 '123' + '456'
* 1 + '2' 先把数字1变成字符串;不要这么做
* '2' - 1 先把字符串变成数字 1;不要这么做

# 比较运算符
* 永远不要使用== 要使用===
* ===: 基本类型的数据看值是否相等; 对象看地址是否相等
* NaN !== NaN

# 位运算
* 位运算取整
* 位运算交换a b的值
* 位运算判断奇偶

# 点运算符（经常用）
* 对象.属性名 = 属性值
* js有特殊逻辑，点前面不是对象，就会把它封装成对象

# void 运算符
* void 表达式或语句
* 求表达式的值，或执行语句
* 然后void的值总为undefined

# 逗号运算符
* let a = (1,2,3,4,5)
* 那么a的值就是5
* let f = (x)=>(console.log('平方值为'),x*x)
* 注意上面的括号不能省

# 运算符优先级
* 圆括号优先级最高
```js
if((!a) ==== 1){}
```
 
## 相同的运算符
* +/ 从左到右 a + b + c
* = 从右往左 a = b = c

