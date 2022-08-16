

# javaScript

##  00 学前准备

资料链接：

+ JavaScript https://wangdoc.com/javascript/basic/index.html
+ <a href="https://segmentfault.com/a/1190000040481518">50个JS项目 </a>
+ https://hyperv28.msdi.cn/tfs/KeyTechnology/Demo_Frontend/_git/demo_main
+ http://docs.fes.msdi.cn/showPage?kId=6242b958525fe95c0589c5f4&dId=62e87d477c699abe63fb7e45

Alt+TAB 切换程序   alt+f4 退出程序   win+L 锁屏 ctrl+x剪切   win+D切换到桌面    ctrl+shift+esc 打开任务管理器

ctrl+L 选中一行

## 01 语法基础

### 1.1 变量

1. 变量提升：所有的变量的声明语句，还有function都会被提升到当前作用域代码的头部。

2. 赋值表达式（`=`）、严格相等运算符（`===`）和相等运算符（`==`）

3. JS代码运行的两个阶段

   + 解析（编译）阶段：语法检查，变量及函数声明
   + 运行阶段：变量的赋值，代码流程执行

4. 如果函数与变量同名，那么函数声明会替换变量声明

   >   console.log(a);
   >
   >   function a() {
   >
   > ​    console.log('aaaa');
   >
   >   }

### 1.2 数据类型

1. 数据类型：
   + null，undefined和布尔值
   + 数值
   + 字符串
   + 对象：
     + 一组“键值对”（key-value）的集合，对象的每一个键名又称为“属性”（property），它的“键值”可以是任何数据类型。如果一个属性的值为函数，通常把这个属性称为“方法”；
     + 对象的每一个键名又称为“属性”（property），它的“键值”可以是任何数据类型。如果一个属性的值为函数，通常把这个属性称为“方法”
   + 函数
     + 对于`var`命令来说，局部变量只能在函数内部声明，在其他区块中声明，一律都是全局变量；
     + 函数参数如果是原始类型的值（数值、字符串、布尔值），传递方式是传值传递；
     + 函数参数是复合类型的值（数组、对象、其他函数），传递方式是传址传递
   + 数组

2. “+” 可作为数学运算符也可作为字符串拼接，从前往后运算，遇到一个字符串，后面所有都是字符串拼接

3. undefined和null

   + undefined表示一个声明了没有赋值的变量
   + null表示一个空

   > tips：不同数据类型在谷歌中颜色不同
   
### 1.3 数据类型之间的转换
1. 其他类型转为字符串型：
+ number.toString();
+ String(number);
+ “+n；

2. 数值类型转换
   + Number()
   + parseInt（）

### 1.4 运算符的优先级

+ （）

+ 一元运算符 ++ -- ！

+ 算数运算符 * /  %  +  -

+ 关系运算符  >  <  >= ....

+ 相等运算符  ==  ===   ！=   ！==

+ 逻辑运算符  先&&  后||

+ 赋值运算符  =

    
  
### 1.5 JS流程控制

1. if语句

2. switch（要判断的值） {  case 值1：

   ​                                             code；

   ​                                             break；

   ​                                         case 值2： }

3. 循环：while   do while   for

### 1.6  函数

1. 声明：
   + function 函数名（形参1，形参2，....） {函数体}
   + var f = function() {函数体}
2. 匿名函数：（function（）{函数体} ）——自调用匿名函数，立即执行。
3. 将函数作为值返回：闭包

> 闭包：定义在一个函数内部的函数，将函数内部和函数外部连接起来。

+ 读取外层函数内部的变量，让这些变量始终保持在内存中；

+ 封装对象的私有属性和私有方法。

  *外层函数每次运行，都会生成一个新的闭包，而这个闭包又会保留外层函数的内部变量，所以内存消耗很大。因此不能滥用闭包，否则会造成网页的性能问题。*

1. `eval`命令接受一个字符串作为参数，并将这个字符串当作语句执行.

   > ```
   > eval('var a = 1;');
   > a // 1
   > ```

2. ```
   将类似数组转为真正数组：
   var arr = Array.prototype.slice.call(arrayLike);
   ```

3. 错误提示

   + `SyntaxError`对象是解析代码时发生的语法错误；
   + `ReferenceError`对象是引用一个不存在的变量时发生的错误；
   + `RangeError`对象是一个值超出有效范围时发生的错误；
   + `TypeError`对象是变量或参数不是预期类型时发生的错误；
   + `URIError`对象是 URI 相关函数的参数不正确时抛出的错误；

4. `try...catch`结构允许在最后添加一个`finally`代码块，表示不管是否出现错误，都必需在最后运行的语句。

5. 相等（==）运算符会自动转换变量类型

6. ![image-20220726104926380](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20220726104926380.png)

7. arguments的使用：当前函数的一个内置对象，存储了传递的所有实参

### 1.7 对象

1. **Object对象**

    + 对象声明：
      + var obj = {键1：值1，键2：值2 ，方法1：匿名函数...}；
      + 实例化方式：var obj = new Object（）；obj.属性1=值1；
      + 实例化自定义构造函数：function Func() {this.属性=值；this.方法=function（）{}}    var f = new Func（）； 构造函数首字母要大写
      
    + js所有其他对象都继承自Object；

    + Object对象本身方法，直接定义在Object对象的方法；实例方法：定义在`Object`原型对象`Object.prototype`上的方法。它可以被`Object`实例直接使用。

    + new关键字执行过程：

      1）new构造函数在内存中创造一个空对象；

      2）让this指向这个新对象

      3）执行构造函数里的代码，给这个新对象添加属性和方法

      4）返回这个新对象

    调用对象属性：对象名.属性名； 对象名['属性名']

    调用对象方法：对象名.方法名（）

2. 构造函数：专门用来生产实例对象的函数

     + 函数体内用了this关键字，代表所要生产的对象实例；
     + 生产对象的时候，必须用new命令。

3. this：属性或方法当前所在的对象

    + this运行在哪个对象下，就指向那个对象

4. 对象循坏：for（键 in 对象）

5. 获取n-m之间的随机数值：Math.random()*(m-n)+n

6. 原型链继承

     (1) prototype属性，原型对象的所有属性和方法，都能被实例对象共享；

     (2)原型链：所有对象都有自己的原型对象，所有对象都继承了Object.prototype的属性；

     (3)实例对象本身没有某个属性或方法的时候，它会到原型对象去寻找该属性或方法；

     (4)实例对象自身就有某个属性或方法，它就不会再去原型对象寻找这个属性或方法.

7. 构造函数的继承

     （1）在子类的构造函数中，调用父类的构造函数；Super

     （2）让子类的原型指向父类的原型。

     > ```
     > Sub.prototype = Object.create(Super.prototype);
     > Sub.prototype.constructor = Sub;
     > Sub.prototype.method = '...';
     > ```

8. 生成对象的方法：

    （1）new 构造函数，返回一个实例；

    （2） Object.create(实例对象)，从一个实例对象生成另一个实例对象。

9. 对象拷贝：

    + 确保拷贝后的对象，与原对象具有同样的原型；
    + 确保拷贝后的对象，与原对象具有同样的实例属性。

10. Promise对象：为异步操作提供统一接口，充当异步操作与回调函数之间的中介。

    三种状态来控制异步操作：

    + 异步操作未完成（pending）
    + 异步操作成功（fulfilled）
    + 异步操作失败（rejected）

    使用then添加回调函数

    Promise 的回调函数属于异步任务，会在同步任务之后执行

11. DOM：文档对象模型，将网页转化为一个JS对象

     ![image-20220727110311747](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20220727110311747.png)

### 1.8 作用域

1. 没有声明，直接赋值的变量是全局变量。

## 02 JS操作CSS

1. 操作 CSS 样式最简单的方法，就是使用网页元素节点的`getAttribute()`方法、`setAttribute()`方法和`removeAttribute()`方法，直接读写或删除网页元素的`style`属性。

2. CSSStyleDeclaration 接口可以直接读写 CSS 的样式属性，不过，连词号需要变成骆驼拼写法。

   > ```
   > var divStyle = document.querySelector('div').style;
   > 
   > divStyle.backgroundColor = 'red';
   > ```

## 03 事件

1. `EventTarget.addEventListener()`用于在当前节点或对象上（即部署了 EventTarget 接口的对象），定义一个特定事件的监听函数。一旦这个事件发生，就会执行监听函数。该方法没有返回值。
2. JS为事件绑定监听函数三种方法：
   + HTML的on-属性，如<div onclick="console.log('触发事件')"> —— 冒泡阶段触发
   + 元素节点对象的事件属性，可以指定监听函数—— 冒泡阶段触发
   + 所有DOM节点实例都有 eventTarget.addEventListener(type，listener，true/false) 方法，用来为该节点定义事件的监听函数， true表示捕获阶段触发，false表示冒泡阶段触发

3. 监听函数内部的*this* 指向触发事件的那个元素节点

4. 事件的传播：

   ![image-20220727150748931](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20220727150748931.png)

   捕获阶段依次为：`window`、`document`、`html`、`body`、`div`、`p`；

   冒泡阶段依次为`p`、`div`、`body`、`html`、`document`、`window`。

5. 事件代理：事件会在冒泡阶段向上传播到父节点，因此可以把子节点的监听函数定义在父节点上，由父节点的监听函数统一处理多个子元素的事件。

## 04 浏览器模型

1.  网页中嵌入JS代码的四种方法：

   + <script>元素直接嵌入代码

   + <script> 标签加载外部脚本 脚本必须是纯js

   + 事件属性

   + URL协议，javascript：协议，即在URL的位置写入代码

2. 工作原理：

   ![image-20220727163858218](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20220727163858218.png)

3. defer属性：脚本文件下载阻塞网页渲染的问题，一个方法是对`<script>`元素加入`defer`属性。它的作用是延迟脚本的执行，等到 DOM 加载生成后，再执行脚本。

4. async属性：使用另一个进程下载脚本，下载时不会阻塞渲染，无法保证脚本的执行顺序。

5. 浏览器的组成：

   + 渲染引擎：将网页代码渲染为用户视觉可感知的平面文档；

   + JS引擎：读取网页中的JS代码，对齐处理后运行。

     浏览器内部对JS处理过程：

     ![image-20220727165938242](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20220727165938242.png)



## 05 npm包管理器

1. `npm` 是 Node.js 标准的软件包管理器

2. 安装单个软件包：npm install <package-name>  
   + `--save` 安装并添加条目到 `package.json` 文件的 dependencies。
   + `--save-dev` 安装并添加条目到 `package.json` 文件的 devDependencies。

   默认本地安装，-g表示全局安装

   > npm root -g 查看安装的位置

   在代码中使用安装的包，用require（包名）导入

3. 更新软件包：npm update / npm update <package-name>

4. 运行任务：npm run <task-name>

5. 查看npm包安装的版本：npm list

6. 安装旧版本包：npm install <package>@<version>

7. 卸载软件包：npm uninstall <package-name>

   使用 `-S` 或 `--save` 标志，则此操作还会移除 `package.json` 文件中的引用;`-D` 或 `--save-dev` 标志从文件中移除开发依赖项。

8. package.json

   + 如果项目具有 `package.json` 文件，则通过运行：npm install， 它会在 `node_modules` 文件夹（如果尚不存在则会创建）中安装项目所需的所有东西

     ![image-20220728113509115](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20220728113509115.png)

     ![image-20220728114542023](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20220728114542023.png)

6. package-lock.json：固化当前安装的每个软件包的版本

7. npm语义版本控制：

   ![image-20220728144429445](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20220728144429445.png)

   

## 06 Node.js

      1. 事件循环
      2. 当将一个函数传给 `process.nextTick()` 时，则指示引擎在当前操作结束（在下一个事件循环滴答开始之前）时调用此函数。

## 07 DOM

1. 获取页面元素：
   + 根据ID获取；getElementById（）
   + 根据标签名获取
   + 通过HTML5新增方法获取
   + 特殊元素获取

## 08 实战

1.  function.call：对传入的参数的任何内容调用一个函数，应用在将特定类型的方法用于不同类型的对象时。
2.  箭头函数

```javascript
//function
function fn(a, b){
	return a + b;
}
//arrow function
var foo = (a, b)=>{ return a + b };
```

使用function定义的函数中this指向是随着调用环境的变化而变化的；

使用箭头函数时，this指向没有变化。

3. ![image-20220803172123741](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20220803172123741.png)
4. z-index
   + z-index堆叠上下文只有在postion:relative/absolute/fixed脱离文档流控制时才生效，static时无效；
   + 当父元素和子元素都处于堆叠上下文时，子元素继承父元素的优先级，故父元素大的就大，如果父元素没有处于堆叠上下文时，即z-index:auto;或者position:static;时，子元素不会继承父元素的优先级；
   + z-index为0时依然处于堆叠上下文中，比负值高，比正值低；
   + z-index为负值时不仅会处于z-index为0和正值元素的后面，还会处于非堆叠元素的后面。
5. JS中$符号
   + 表示变量 
   + 正则中，表示结尾；
   + **表示一个查找对象的函数**  $=function(id) { return (typepf(id)=='object')?id:document.getElementByIdx_x(id); };







