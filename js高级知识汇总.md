# 高级JavaScript的总结

## JavaScript面向对象

### 一、面向对象编程简介

面向对象：具有灵活性、代码复用性、容易维护和开发，适用多人合作开发。

特性：封装性、继承性、多态性。

### 二、ES6中的类和对象

面向对象的思维特点：

- 抽取（抽象）对象公用的属性和行为组织（封装）成一个类（模板）；
- 对类进行实例化，获取类的对象。

面向对象编程我们要考虑有哪些对象，按照面向对象的思维特点，不断的创建对象，只会对象做事情。

#### 1、对象

在js中，对象时一组无需的相关属性和方法的集合，所有的事物都是对象。例如字符串、数值、数组、函数等。

对象由属性和方法组成：

- 属性：事物的特征，在对象中用属性来表示（常用名词）；
- 方法：事物的行为，在对象中用方法来表示（常用动词）；

#### 2、类

在 ES6中新增了类的概念，可以使用class关键词声明一个类，之后以这个类来实例化对象。

类，抽象了对象的公共部分，它泛指某一大类；对象，特指某一个，通过实例化的具体对象。

#### 3、创建类

语法：

```js
class Name {}//创建类
const xx = new Name()//创建实例对象
```

注意：类必须使用new实例化对象。

#### 4、类的constructor构造器

`constructior()`方法是类的构造函数（默认方法），用于传递参数，返回实例对象，通过new命令生成的对象实例时，自动调用该方法。

```js
// 1、创建明星类
class Star {
		constructor() {
				this.name = name;
		}
}
//也可以这样表达式方式定义类：let Star = class{}
// 2、利用类创建对象
const ldh = new Star('刘德华')
console.log(ldh.name);
```

注意事项：

- 通过class关键词创建的类，类名首字母大写；
- constructor函数接收参数，返回实例对象，因此无需加return；
- 生成实例必须要用new；
- 创建类，类名后不加小括号；生成的实例，类名后加小括号；构造函数不需要加function（内部都不要加）；

#### 5、类添加方法

注意类里面所有的函数都不要加function，且多个方法之间不要加逗号；

```js
// 创建明星类
class Star {
		constructor(name, age) {
				this.name = name
				this.age = age
		}
		sing(song) {
				console.log(this.name + song);
		}
}
// 利用类创建对象
const ldh = new Star('刘德华', 18)
ldh.sing('冰雨')//刘德华冰雨     调用ldh内的sing（）方法
```

一些注意：

- 在ES6中没有变量提升，因此必须先定义类，才可以实例化对象；
- 类里面的公共属性和方法一定要加this使用；
- 由于new会直接调用构造函数，因此如果我们需要创建实例对象的同时调用某内部的方法，则可以把方法写在constructor内，但前面必须加this，如下：

```js
// 创建明星类
class Star {
		constructor(name, age) {
						this.name = name
						this.age = age
						// this.sing = this.sing()//两者写法皆可
						this.sing()
				}
		sing() {
				console.log(this);
		}
}
// 利用类创建对象
const ldh = new Star('刘德华', 18)
//创建完实例后就会执行constructor内的this.sing()方法，即不需要在单独去调用
```

### 三、类的继承

#### 1、类的继承extends

**用关键词extends继承父类的属性和不带参数的方法。**

语法：

```js
// 父类
class Father {
		constructor() {}
}
// 子类:用extends继承父类的属性和不带参数方法
class Son extends Father {}
```

实例1：使用`extends`继承父类的函数(不带参数)；

```js
class Father{
	constructor(name){
		this.name = name;
	}

	run(){
		console.log("学会了Father的跑步技能")
	}
}

class Son extends Father{
	
}

var sonObj = new Son();
sonObj.run();   //输出结果为   "学会了Father的跑步技能"
```

#### 2、super关键词

super 是个函数，而且 ，它是 **父类的构造器**；子类中的 super ，**其实就是父类中，constructor 构造器的一个引用**；

如果一个子类，通过 extends 关键字继承了父类，那么，在子类的 constructor 构造器中，**必须 优先** 调用一下 `super()`；

实例2：`super`，调用父类中的构造函数；

```js
class Father{
	constructor(name){
		// 第三步：最后接收子类传来的参数
		this.name = name;
	}

	run(){
		console.log("学会了" + this.name + "的跑步技能")
	}
}

class Son extends Father{
	constructor(name){
		//第二步：调用父类中的构造函数，再把参数传给父类
		super(name);
	}
}
//第一步：先在子类实例中传参数给子类的构造函数
var sonObj = new Son("Father");

sonObj.run();   //输出结果为   "学会了Father的跑步技能"
```

实例3：使用`super`调用父类构造函数中的普通函数；

```js
class Father{
	run(){
		return "Father";
	}
}

class Son extends Father{
	//这里的super.run()就是调用了父类中的run()方法
	//run()返回值是 "Father"
	run(){
		console.log("学会了" + super.run() + "的跑步技能");
	}
}

var sonObj = new Son();

sonObj.run();   //输出结果为   "学会了Father的跑步技能"
```

实例4：`super`必须要放到构造函数`this`的前面；

```js
class Father{
	constructor(FatherName){
		//接收子类传来的参数FatherName
		this.FatherName = FatherName;
	}
	FatherRun(){
		console.log(this.FatherName + "在跑");
	}
}

class Son extends Father{
	constructor(FatherName,SonName){
		//调用父类构造函数，并且传递参数
		//注意，super()一定要写在构造函数中this的上面
		super(FatherName,SonName);

		this.FatherName = FatherName;
		this.SonName = SonName;
	}
	SonRun(){
		console.log(this.SonName + "在学习" + this.FatherName + "的跑步技能");
	}
}

var sonObj = new Son("Father","Son");

sonObj.FatherRun();   //输出结果为   "Father在跑"
sonObj.SonRun();   //输出结果为   "Son在学习Father的跑
```

#### 3、补充this指向



```js
let that //用来接收this指向
class Star {
		constructor(uname, age) {
				that = this //用来把this指向赋值给全局变量that
				this.uname = uname
				this.age = age
				this.btn = document.querySelector('button')
				this.btn.onclick = this.sing
				this.jump() //会直接调用
		}
		sing() {
				console.log(this); //输出的是button标签
				console.log(this.uname); //输出undefined
		}
		jump() {
				console.log(this); //输出ldh实例对象
				console.log(that); //输出ldh实例对象
		}
}
const ldh = new Star('阿离', 18) //创建实例对象的同时就会调用constructor构造函数
```

this指向：

- constructor内的this指向实例对象；
- 方法内的this指向这个方法的调用者（如上例子中`sing()`是button标签调用，因此指向button标签）

### 四、补充事件和方法

#### 1、insertAdjacentHTML()

将指定的文本解析为HTML或XML，并将结果节点插入到指定位置。

语法：

```js
ele.inserAdjacentHTML(type,text)
//ele为插入到的元素，text为需要插入的文本，该文本为字符串形式的标签，如："<div></div>"
//type有指定的节点位置：
//beforebegin  //在本身之前插入
//afterbegin	//在第一个子节点直接插入
//beforeend  //在最后一个子节点直接插入
//afterend  //在本身之后插入
```

注意：之前我们插入节点是用creatElement()来创建元素，之后appendChild()或者insertBefore()来把指定元素添加到相应节点的前面或者后面，但是此方法中的指定元素只能是用creatElement（）创建出来的元素不能是字符串的模板形式；而ele.inserAdjacentHTML(type,text)就可以直接添加对应的字符串模板的标签。

#### 2、insertAdjacentElement()

移动元素到指定位置。

语法：

```js
ele.insertAdjacentElement(position,element) // element移动的元素
//position为：
//beforebegin //在本身之前插入
//afterbegin //在第一个子节点直接插入
//brforeend //在最后一个子节点直接插入
//afterend //在本身之后插入
```

注意，此处的element为对应的现有的元素标签。

#### 3、dblclick双击鼠标事件

```js
const two = document.querySelector('.two')
two.addEventListener('dblclick', () => {
		alert('您双击了鼠标')
})
```

#### 4、文本框处于选中状态input.select()

```js
const btn = document.querySelector('button')
const input = document.querySelector('input')
one.addEventListener('click', () => {
		input.select()
})
```

## 构造函数与原型

### 一、构造函数和原型

#### 1、构造函数的原型对象prototype 

构造函数通过原型分配的行数是所有对象所`共享的`。

JS规定，每一个构造函数都有一个 `prototype` 属性，指向另一个对象，注意这个prototype就是一个对象，这个对象的所有属性和方法都会被构造函数所拥有。

我们把那些不变的方法直接定义在prototype对象上，这样所有对象的实例就可以共享这些方法。

- 原型是什么？

  *一个对象，我们也称prototype为原型对象，每个构造函数都有*

- 原型的作用是什么？

  *共享方法*

一般情况下，我们的公共属性定义在构造函数里面，公共的方法放到原型对象上。

#### 2、实例对象的对象原型`__proto__`

构造函数生成的实例对象有一个属性 `__proto__` , 指向其构造函数的原型对象 `prototype`。

所以实例对象的 `__proto__` 和构造函数的 `prototype` 是等价的。

实例对象方法和属性查找规则： 先在对象自己身上找，没有再去构造函数的prototype上及原型链上找。

```js
function Star(name, age) {
  this.name = name;
  this.age = age;
}

Star.prototype.sing = function() {
  console.log('我会唱歌');
}

var ldh = new Star('刘德华', 18);
var zxy = new Star('张学友', 19);
console.log(ldh.sing === zxy.sing); // true
ldh.sing();
console.log(ldl.__proto__ === Star.prototype); // true
```

#### 3、constructor构造函数

对象原型（**proto**）和构造函数的原型对象（prototype）里面都有一个属性`constructor`属性, constructor我们称为构造函数，因为它指回构造函数本身。

constructor主要用于记录该对象引用于哪个构造函数，它可以让原型对象重新指向原来的构造函数。

#### 4、构造函数，原型对象以及实力对象的关系

<img src="C:\Users\19979357151\AppData\Roaming\Typora\typora-user-images\image-20210210225036068.png" alt="image-20210210225036068" style="zoom:67%;" />

#### 5、原型链

只要是对象就有`__proto__`对象原型，那么构造函数Star的原型对象prototype肯定也有`__proto__`,此时这个`Star.prototype.__proto__`指向的是Object的原型对象Object.prototype，继续往上追溯，`Obejct.prototype.__proto__`指向的就是null了，这个从下而上的追溯关系就是原型链。



<img src="C:\Users\19979357151\AppData\Roaming\Typora\typora-user-images\image-20210210230047667.png" alt="image-20210210230047667" style="zoom: 67%;" />

#### 6、this指向

1. 在构造函数中，this指向的是实例对象。（此处指向实例对象ldh）
2. 原型对象prototype的函数中，this指向实例对象。（此处指向实例对象ldh）

#### 7、扩展内置对象

我们可以对数组对象或者其他内置对象进行扩展，就跟之前基础JS中的数组、字符串、对象等等的内置对象方法一样。

我们把方法封装在数组Array的原型对象上，这样所有的数组实例都可以用这个方法。

```js
Array.prototype.sum = function() {
		var sum = 0
		for (var i = 0; i < this.length; i++) {
				sum += this[i]
		}
		return sum
}

var arr = [1, 2, 3, 4, 5]
console.log(arr.sum());
```

#### 8、继承

**补充call()方法：修改函数运行时的this指向**;

用法：`fn.call(thisObj,arg1,agr2,...)`

- thisobj当然调用函数需要指定的this指向对象，后面argue1，arg2...则是正常的函数参数；
- 如果直接fn.call()，则相当于fn()，调用函数，未修改this，默认指向window；

借用父构造函数继承属性,利用原型对象继承方法。

（1）、修改this指向继承父构造函数的属性

在子构造函数内部调用父构造函数同时用call()修改this指向子构造函数，因此子构造函数就继承了父构造函数的属性；

（2）、借用原型对象的来继承父构造函数的方法

- 子原型对象 = 父构造函数的实例对象（因为父实例对象是可以用父构造函数的方法，同时由于子原型对象等于的是父实例对象，因此子构造函数可以有自身的方法封装在原型对象上，而不会影响父构造函数）
- 把子构造函数的constructor手动指回子构造函数（因为上面把子构造函数的原型对象等于了父实例对象，因此内部的constructor会指向父构造函数，因此此处需要手动修改指回来）

```js
function Father(name, age) {
  this.name = name;
  this.age = age;
}
function Son(name, age){
  Father.call(this, name, age);//利用call()更改Father的this指向成Son来使得Son继承Father的属性
}
Father.prototype.money = funciton() {
  console.log('money');
}
Son.prototype = new Father();//把子构造函数的原型对象等于父构造函数的实例对象
Son.prototype.constructor = Son;//由于上面对构造函数进行了赋值，子构造函数的constructor就指向为父构造函数了，因此此处手动改回指向子构造函数
Son.prototype.other = function() {//这是子构造函数自己的方法
  console.log('other');
}
var son = new Son('姓名', 18);
console.log(son);
```

### 二、ES5的一些方法

#### 1、数组方法

迭代遍历方法:forEach()、map()、filter()、some()、every()等

（1）、forEach()遍历数组，forEach跟jQuery的each用法类似

```js
array.forEach(function(currentValue, index, arr))
```

调用forEach()方法，对数组的每一项进行遍历，内部以一个函数作为参数，这个函数可以有三个参数：

- currentValue: 数组当前项的值
- index: 数组当前项的索引
- arr: 数组对象本身

```js
var arr = [1,2,3]
arr.forEach(function(value, index, array){
	console.log('每个数组元素'+ value)
  	console.log('每个数组元素的索引值'+ index)
  	console.log('数组本身'+ array)
})
```

**注意：forEach()内部如果有return并不会退出循环。forEach()方法没有返回值**

（2）、 filter()过滤器

```js
array.filter(function(currentValue, index, arr))
```

- currentValue: 数组当前项的值
- index: 数组当前项的索引
- arr: 数组对象本身

filter()方法用于筛选创建一个新的数组，新数组中的元素是通过检查指定数组中符合条件的所有元素，主要用于筛选数组。**filter()方法是直接返回一个新的数组。**

```js
let arr = [1, 2, 3, 4, 5, 6, 7, 8, 9]
let newArr = arr.filter((value, index) => {
		return value >= 5
})
console.log(newArr);//[5,6,7,8,9]
```

(3)、map(),常用于对数组内的所有元素进行遍历操作

```js
array.map(function(currentValue, index, arr))
```

map() 方法创建一个新数组，其结果是该数组中的每个元素都调用一个提供的函数后返回的结果。
注意：map() 方法是直接返回一个新的数组

- currentValue: 数组当前项的值
- index: 数组当前项的索引
- arr: 数组对象本身

```js
var array1 = [1, 4, 9, 16];
var map1 = array1.map(function(value, index, arr) {
return value * 2
});
console.log(map1) //[2,8,18,32]
```

(4)、some()

```js
array.some(function(currentValue, index, arr))
```

some()方法用于检测数组中的元素是否满足指定条件，通俗点查找数组中是否有满足条件的元素
注意： some()方法返回值是布尔值，如果查找到这个元素，就返回true,如果查找不到则返回false
如果找到第一个满足条件的元素，则终止循环，不在继续查找

- currentValue: 数组当前项的值
- index: 数组当前项的索引
- arr: 数组对象本身

```js
var arr=[10,30,4]
var b = arr.some(function(value){
	return value > 20
})
console.log(b) //true
```

some()内遇到return true 就会终止循环。具有唯一性。

(5)、every()

```js
array.every(function(currentValue, index, arr))
```

every() 方法测试一个数组内的所有元素是否都能通过某个指定函数的测试。它返回一个布尔值。
注意：every() 方法必须每个元素都符合条件才能返回true，若有一个不符合，则返回false。
若收到一个空数组，此方法在一切情况下都会返回 true。

- currentValue: 数组当前项的值
- index: 数组当前项的索引
- arr: 数组对象本身

(6)、isArray()

```js
Array.isArray(obj)
```

Array.isArray() 用于确定传递的值是否是一个 Array

- obj是需要检测的值。如果是数组则返回true,否则返回false



总结数组方法的区别：

1. filter 是查找满足条件的元素，返回的是一个数组，而且是把所有满足条件的元素返回回来
2. some 是查找满足条件的元素是否存在，返回的是一个布尔值，如果查找第一个满足条件的元素，就终止循环。如果数组中查询唯一个元素，用some方法更为合适，因为它找到这个元素，就不在进行循环，效率更高
3. every是查找所有的元素是否符合条件，返回的是一个布尔值
4. map是创建一个新数组，其结果是该数组中的每个元素都调用一个提供的函数后返回的结果

#### 2、字符串方法

（1）、trim() 方法会从一个字符串的两端删除空白字符

```js
str.trim()
```

trim() 方法并不影响原字符串本身，它返回的是一个新字符串。

#### 3、对象方法

（1）、Object.keys() 用于获取对象自身的所有属性名

```js
Object.keys(obj)
```

效果类似for  in ，此处返回的是一个由属性名组成的数组。

```js
let obj = {
		age: 18,
		name: '阿离',
		sex: '男'
}
console.log(Object.keys(obj)); //['age','name','sex']
```

如果需要具体到某个属性则可以对该数组进行forEach()遍历

(2)、Object.defineProperty()定义对象中新增属性或修改原有的属性

```js
Object.defineProperty(obj, prop, descriptor)
```

- obj: 必需。目标对象
- prop: 必需。 需定义或修改的属性名字
- **descriptor**: 必需。目标属性所拥有的特性

Object.defineProperty() 第三个参数descriptor说明： 以对象形式{}书写

- value：设置属性的值，默认为undefined
- writable:值是否可以重写（是否可以再次被修改）。true | false 默认为false
- enumerable: 目标属性是否可以被枚举（即是否可以被遍历出来）。true | false 默认为false
- configurable: 目标属性是否可以被删除或是否可以再次修改特性（是否可以修改**descriptor**）true | false 默认为false

```js
let obj = {
		age: 18,
		name: '阿离',
		sex: '男'
}
Object.defineProperty(obj, 'color', {
		value: 'green',
		writable: true,
		enumerable: true,
		configurable: true
})
console.log(obj);
```

**补充**：直接删除对象属性采用`delete obj.属性`

```js
let obj = {
		age: 18,
		name: '阿离',
		sex: '男'
}
console.log(obj);
delete obj.age
console.log(obj);
```



## 函数进阶

### 一、函数的定义和调用

#### 1、函数的定义的三种方式

```js
// 1. 自定义函数
function fun(){}

// 2. 函数表达式（匿名函数）
var fun = function(){}

// 利用 new Function('参数1', '参数2', '函数体');
// 参数必须时字符串格式
var f = new Function('a','b','console.log(a + b)')
f(1,2) // 3
```

注意：

- Function内参数必须是以字符串格式
- 第三种方式基本不用，效率低
- 所有函数都是Function的实例对象
- 函数也属于对象

关于Function构造函数的图例，此处略，同之前的原型对象。

#### 2、函数的调用

- 普通函数：fn()或者fn.call()
- 对象的方法：对象.方法()
- 构造函数：new 构造函数
- 绑定事件函数：点击调用
- 定时器函数：每隔相应时间自动调用
- 立即执行函数：(function(){}())或(function(){})()

### 二、this

关于各种this指向及案例参考博客园题主主题帖 https://www.cnblogs.com/zjjDaily/p/9482958.html

a、 this显式绑定

 含义： 当一个函数没有明确的调用对象的时候， 也就是单纯作为独立函数调用的时候， 将对函数的this使用默认绑定： 绑定到全局的window对象

 在显式绑定下： 函数将取得在“ 包含对象“ 里的永久居住权， 一直都会” 住在这里“

```js
var a = 1;
console.log(this.a); //1 this指向全局变量window
var obj = {
    a: 2,
    fire: function () {
        var a = 3;
        console.log(this.a); //2 因为是obj.fire()，调用了fire函数，因为this指向了obj，输出了obj下的a=2
        function innerFire() {
            var a = 4;
            console.log(this.a); //1 未明确调用对象，this指向window
        }
        innerFire(); //没有明确调用的对象
        console.log(this.a); //2 this指向obj
    }
}
obj.fire();
```

b、隐式绑定

 当函数被一个对象“ 包含” 的时候， 我们称函数的this被隐式绑定到这个对象里面， 这时候， 通过this可以直接访问所绑定的对象里面的其他属性。

```js
var obj = {
    a: 1,
    fire: function () { //此时函数的this被隐式绑定到了对象obj
        console.log(this == obj); // obj中有fire函数，因而默认this指向obj
        console.log(this.a); // 1 this.a 相当于obj.a =1
    }
}
obj.fire(); // 输出1 
```

 **动态绑定：**
 this实在代码运行期绑定而不是在书写期.

```js
var obj = {
    a: 1, // a是定义在对象obj中的属性 1
    fire: function () {
        console.log(this.a)
    }
}
var a = 2; // a是定义在全局环境中的变量 2
obj.fire(); //1  此时fire的指向时obj
var fireInGrobal = obj.fire; //因为fireInGrobal是全局变量，this对于obj的绑定丢失，绑定到了全局window
fireInGrobal(); // 输出 2 输出全局变量啊
```

```ja
var a = 2;
var obj = {
    a: 1, // a是定义在对象obj中的属性
    fire: function () {
        console.log(this.a)
    }
}

function otherFire(fn) { //全局函数，this绑定window
    fn();
}
otherFire(obj.fire); // 输出2   this对于obj的绑定丢失，绑定到了全局this上面
```

下面粗浅的列举部分this指向

- 普通函数调用：this指向window

- 构造函数调用：实例对象，原型对象里面方法也指向实例对象

- 对象方法调用：该方法所属对象

- 事件绑定对象：绑定事件对象

- 定时器函数：window（指的是定时器函数内部的this,延时函数内部的回调函数的this指向全局对象window（ 当然我们可以通过bind方法改变其内部函数的this指向））

- 立即执行函数：window

- 箭头函数的this指向是指向：**箭头函数里面的this是在定义它时绑定的，指向它的父级作用域，而不是调用它对象，这个this的指向是不能通过call和apply改变的。**

  ```js
  function ali() {
  		this.age = 0;
  		setTimeout(() => {
  				console.log(this);
  		}, 2000); //指向window
  		setTimeout(function() {
  				console.log(this); //指向ali
  		}, 2000)
  }
  let p = new ali()
  ```

### 三、改变this指向的方法

call、apply、bind三者为改变this指向的方法。

共同点：第一个参数都为改变this的指针。若第一参数为null/undefined，this默认指向window

（1）、call（无数个参数）

- 第一个参数：改变this指向
- 第二个参数：实参
- 使用之后会自动执行该函数

```js
function fn(a,b,c){
        console.log(this,a+b+c); // this指向window
    }
fn();
fn.call(document,1,2,3);//call改变之后this指向document  
//输出 #document 6   1,2,3是实参 结果相加为6
```

(2)、apply（两个参数）

- 第一个参数：改变this指向
- 第二个参数：数组（里面为实参）,即参数必须写在数组内，相当于arguments
- 使用时候会自动执行函数

```js
function fn(a,b,c){
        console.log(this,a+b+c); 
    }
fn();
fn.apply(document,[1,2,3]); 
//输出 #document 6   1,2,3是实参 结果相加为6
```

注意：apply会把传递的数组自动转换为相应的元素格式

```js
//call 的传参和apply的传参
function say(arg1,arg2){
  console.log(this.name,arg1,arg2);
};
var obj = {
  name : 'tom',
  say : function(){
    console.log(this.name);
  }
}
say.call(obj,'one','two');//tom one two
say.spply(obj,['one','two']);//tom one two  效果一样
```

补充：如果我们求数组的值，用到的就是for循环，如果在代码中经常求最大值和最小值的话，会显得代码很乱。所以，就考虑一中最简单的方法求最大值。

使用Math里面自带的max和min方法

```js
var arr = [1, 2, 3, 4, 5, 6, 7, 8, 9, 1]
console.log(Math.max.apply(null, arr));//9
```

(3)、bind（无数个参数）

- 第一个参数：改变this指向
- 第二个参数之后：实参
- 返回值为一个新的函数
- 使用的时候需要手动调用下返回 的新函数（不会自动执行）

```js
let aaa = {
		name: '阿离'
}
function fn() {
		console.log(this); 
}
fn()//此处调用打印window
let newFn = fn.bind(aaa)//不会执行函数，返回的是一个新函数
newFn()//要调用新函数才会有输出，此处调用打印aaa对象
```

**案例：点击按钮后禁用，五秒钟后再次可以点击**

```js
btn.addEventListener('click', function() {
		this.disabled = true
		let num = 5
		let timer = setInterval(() => {
				if (num > 1) {
						num--
						this.innerHTML = `${num}后重新发送`
						console.log(this);//注意此处是定时器，本来this指向window，但是因为用了箭头函数，因此this指向这个定时器的父作用域，即btn；
				} else {
						this.disabled = false
						this.innerHTML = '发送'
						clearInterval(timer)
				}
		}, 1000);
})
```

```js
//下面代码与上面一个意思，不过定时器没有用箭头函数，this指向window，因此下面用bind(this)，把this指向改为btn
btn.addEventListener('click', function() {
		this.disabled = true
		let num = 5
		let timer = setInterval(function() {
				if (num > 1) {
						num--
						this.innerHTML = `${num}后重新发送`
						console.log(this);
				} else {
						this.disabled = false
						this.innerHTML = '发送'
						clearInterval(timer)
				}
		}.bind(this), 1000);
})
```

