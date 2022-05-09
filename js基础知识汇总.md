

# 基础JavaScript的总结

## 一、ECMAScript(javascript语法/基础)

​	下面都是一些基础js的语法例子，知识点都囊括进实例中了。

###	实例及相应属性方法

#### 	1、输入信息征集模板：

```js
var nm = prompt('请输入您的姓名：');
            var age = prompt('请输入您的年龄：');
            var yx = prompt('请输入您的邮箱：');
            var dz = prompt('请输入您的住址：');
            var gz = prompt('请输入您的工资');
            alert('我叫' + nm + '，我住在' + dz + '，我今年' + age + '岁了，' + '我的邮箱是' + yx + '，我的工资是' + gz);
```

#### 2、弹出用户输入的姓名：

```js
var names = prompt('请输入您的姓名：');
alert('您的姓名是' + names);
```

####  3、输入年龄弹出年龄：	

```js
var age = prompt('请输入您的年龄：');
alert('您今年' + age + '岁啦！');
```

#### 4、输入出生年份，计算年龄：

```js
var age = prompt('请输入您的出生年份：');
alert('您今年岁' + (2020 - age) + '啦');
```

#### 5、计算用户输入的两个值得和：

```js
var one = prompt('请输入第一个数字：');
var two = prompt('请输入第二个数字：');
var result = parseFloat(one) + parseFloat(two); 
alert('结果是' + result);
```

#### 6、根据年龄判断能否进入网吧：

```js
var age = prompt('请输入您的年龄：');
if (age >= 18) {
     alert('欢迎光临！');
 } else {
     alert('对不起，您不能进去！');
 }
```

#### 7、根据用户输入年份判断是否是闰年，条件是能被4整除，但不能被100整除的数，或者能被400整除的数：

```js
var years = prompt('请输入年份：');
 if (years % 4 == 0 && years % 100 != 0 || years % 400 == 0) {
     alert('您输入的年份是闰年！');
 } else {
     alert('您输入的年份是平年！');
 }
```

#### 8、输入姓名判断是否中奖， 只有阿离算中奖：

```js
var on = prompt('请输入您的姓名：');
 if (on == '阿离') {
     alert('恭喜您中奖啦！');
 } else {
     alert('对不起，您没中奖！');
 }
```

#### 9、根据分数来判定等级：

```js
var score = prompt('请输入您的考试分数：');
 if (score >= 90) {
     alert('您的等级是A');
 } else if (score >= 80) {
     alert('您的等级是B');
 } else if (score >= 70) {
     alert('您的等级是C');
 } else if (score >= 60) {
     alert('您的等级是D');
 } else {
     alert('您的等级是E');
 }
```

#### 10、用户输入一个0~59的数字，如果小于10，则前面加个0，否则直接输出：

```js
var num = prompt('请输入一个数字：');
 if (num <= 10) {
     alert('0' + num);
 } else {
     alert(num);
 }
```

#### 11、用户输入水果名称， 如果有则弹出价格， 如果没有， 则提示没有该水果(switch)：

```js
var fruit = prompt('请输入水果名：');
 switch (fruit) {
     case '苹果':
         alert('12元/斤');
         break;
     case '香蕉':
         alert('22元/斤');
         break;
     default:
         alert('没有该水果！');
 }
```

#### 12、用户输入两个值，比大小：

```js
var one = prompt('请输入第一个数字：');
 var two = prompt('请输入第二个数字：');
 if (one > two) {
     alert(one + '更大');
 } else if (one < two) {
     alert(two + '更大');
 } else {
     alert('一样大');
 }
```

#### 13、判断奇数还是偶数：

```js
var num = prompt('请输入一个数字：');
 if (num % 2 == 0) {
     alert('该数是偶数');
 } else {
     alert('该数是奇数');
 }

```

#### 14 、for循环--- 1~某个用户输入的值之间所有整数和：

```js
var num = prompt('请输入要从1到哪个数的累积求和：');
var result = 0;
for (var i = 1; i <= num; i++) {
     result = result + i;
 }
 console.log('累积求和的值为：' + result);
```

#### 15、for循环---n~m之间所有整数累积求和（n和m用户输入）：

```js
 var n = prompt('请输入初始值：');
 var m = prompt('请输入结束值：');
 var result = 0;
 for (i = n; i <= m; i++) {
     result = result + parseInt(i);
 }
 alert('累积和为：' + result);
```

#### 16、for循环--- n~m之间所有奇数和及偶数和累积求和（ n和m用户输入）：

```js
 var n = prompt('请输入初始值：');
 var m = prompt('请输入结束值：');
 var even = 0;
 var odd = 0;
 for (i = n; i <= m; i++) {
     if (i % 2 == 0) {
         even = even + parseInt(i);
     } else {
         odd = odd + parseInt(i);
     }
 }
 alert('偶数和为：' + even);
 alert('奇数数和为：' + odd);
```

#### 17、for循环---一行打印n个小星星：

```js
 var num = prompt('请输入要打印的小星星个数：'); //★
 var result = '';
 for (i = 1; i <= num; i++) {
     result = result + '★';
 }
 alert(result);
```

#### 18、for循环---一行打印一个小星星，打印n行：

```js
 var num = prompt('请输入要小星星要打印的行数：'); // \r和\n都可以换行
 var result = '';
 for (i = 1; i <= num; i++) {
     result = result + '★' + '\n';
    }
 alert(result);
```

#### 19、 双重for循环---打印n行m列的小星星：

```js
 var n = prompt('请输入要打印小星星的行数：');
 var m = prompt('请输入要打印小星星的列数：');
 var result = '';
 for (i = 1; i <= n; i++) {
     for (j = 1; j <= m; j++) {
        result = result + '★';
     }
    result = result + '\n';
 }
 alert(result);
```

#### 20、双重for循环---打印倒三角的小星星：

```js
 var n = prompt('请输入要打印小星星的行数：');
 var m = prompt('请输入要打印小星星的列数：');
 var result = '';
 for (i = 1; i <= n; i++) {
    for (j = i; j <= m; j++) {
        result = result + '★';
     }
     result = result + '\n';
 }
 alert(result);
```

#### 21、双重for循环---打印正三角的小星星：

```js
 var n = prompt('请输入要打印小星星的行数：');
 var m = prompt('请输入要打印小星星的列数：');
 var result = '';
 for (i = 1; i <= n; i++) {
     for (j = 1; j <= i; j++) {
         result = result + '★';
     }
     result = result + '\n';
 }
 alert(result);

```

####  22、双重for循环---九九乘法表：

```js
var result = '';
 for (i = 1; i <= 9; i++) {
     for (j = 1; j <= i; j++) {
         result = result + j + 'x' + i + '=' + j * i + '\t';
     }
     result = result + '\n' + '\n';
 }
 console.log(result);       
```

#### 23、while循环---打印人的一生，从1到100岁：

```js
 var i = 1;
 while (i <= 100) {
    console.log('你今年岁' + i + '啦!');
     i++;
 }
```

#### 24、while循环计算1-100的整数和：

```js
 var i = 1;
 var sum = 0;
 while (i <= 100) {
      sum += i;
     i++;
 }
 console.log('和为' + sum);
```

#### 25、while循环---弹出对话框：你爱我吗？如果输入“我爱你”，就提示结束，否则一直弹出：

```js
 var ask = prompt('你爱我吗？');
 while (ask != '我爱你') {
     ask = prompt('你爱我吗？');
 }
js alert('我也爱你');
```

#### 26、do while---打印人的一生，1-100岁：

```js
 var i = 1;
 do {
     console.log('我今年' + i + '岁啦');
     i++;
 } while (i <= 100)
```

#### 27、do while---计算1-100的整数和：

```js
 var i = 1;
 var sum = 0;
 do {
     sum += i;
     i++;
 } while (i <= 100)
 console.log('结果是' + sum);
```

#### 28、用户输入用户名和密码，输入户名为“admin”，密码为“123456”，则提示登录成功，否则一直让用户输入：

```js
 var user = prompt('请输入用户名:');
 var password = prompt('请输入密码:');
 while (user != 'admin' || password != '123456') {
     var user = prompt('请输入用户名:');
     var password = prompt('请输入密码:');
 }
 alert('恭喜你登录成功！');
```

#### 29、求整数1-100的和，要求去掉个位数为3的数（用双重for循环+continue实现）：

```js
 var sum = 0;
 for (var i = 1; i <= 100; i++) {
     if ((i - 3) % 10 == 0) { // 提取个位为3的数字
         continue; // 个位为3的数不参与此次循环
     }
     sum += i;
 }
 console.log('和为：' + sum);
```

#### 30、制作简单的ATM机（while+if else）：

```js
 var num = prompt('请输入您要的操作：\n1、存钱\n2、取钱\n3、显示余额\n4、退出');
 var money = 100;
 if (parseInt(num) > 4) {
     alert('输入错误，请重新选择！');
     var num = prompt('请输入您要的操作：\n1、存钱\n2、取钱\n3、显示余额\n4、退出');
 }
 while (parseInt(num) <= 4) {
     if (parseInt(num) == 1) {
         var cun = prompt('请输入存款金额');
         money += parseInt(cun);
         alert('您的余额为：' + money);
         var num = prompt('请输入您要的操作：\n1、存钱\n2、取钱\n3、显示余额\n4、退出');
     } else if (parseInt(num) == 2) {
         var qu = prompt('请输入要取的金额：');
         money -= parseInt(qu);
         alert('您的余额为：' + money);
         var num = prompt('请输入您要的操作：\n1、存钱\n2、取钱\n3、显示余额\n4、退出');
     } else if (parseInt(num) == 3) {
         alert('您的余额为：' + money);
         var num = prompt('请输入您要的操作：\n1、存钱\n2、取钱\n3、显示余额\n4、退出');
     } else {
        break;
     }
 }
 alert('您已退出登录！');
```

#### 31、新建数组，存放1-10个数：

```js
 var arr = [];
 for (var i = 0; i < 10; i++) {
     arr[i] = i + 1;
 }
 console.log(arr);
```

#### 32、将数组[2,0,1,77,0,52,0,25,7]中大于10的数选出来，放入新数组(for循环)：

```js
// 方法一：引入新变量j;
 var arr = [2, 0, 1, 77, 0, 52, 0, 25, 7];
 var newArr = [];
 var j = 0;
 for (var i = 0; i < arr.length; i++) {
     if (arr[i] > 10) {
         newArr[j] = arr[i];
         j++;
     }
 }
 console.log(newArr);
// 方法二：直接用newArr.length,新数组的长度来代替j变量的引入，即不引进新变量；
 var arr = [2, 0, 1, 77, 0, 52, 0, 25, 7];
 var newArr = [];
 for (var i = 0; i < arr.length; i++) {
     if (arr[i] > 10) {
         newArr[newArr.length] = arr[i];
     }
 }
 console.log(newArr);
```

#### 33、将数组[2,0,1,77,0,52,0,25,7]中0去掉，其余数选出来，放入新数组：

```js
 var arr = [2, 0, 1, 77, 0, 52, 0, 25, 7];
 var newArr = [];
 for (var i = 0; i < arr.length; i++) {
    if (arr[i] != 0) {
         newArr[newArr.length] = arr[i];
     }
 }
 console.log(newArr);
```

#### 34、 将数组['red', 'orange', 'yellow', 'green', 'blue', 'pink', 'purple']顺序倒过来：

```js
 var arr = ['red', 'orange', 'yellow', 'green', 'blue', 'pink', 'purple'];
 var newArr = [];
 for (var i = arr.length - 1; i >= 0; i--) {
     newArr[newArr.length] = arr[i];
 }
 console.log(arr);
 console.log(newArr);
```

#### 35、冒泡排序：即把无序的数组元素按一定顺序排列，如从小到大、从大到小。

```js
// 要求：把[5,4,3,2,1]从小到大排列；
// 分析：
// （1）第一个元素和后面所有元素比较，比之大调换位置（此处由里层for循环实现，调换位置需引进临时变量）；
// （2）接下来第二个、第三个、第四个依次和后面元素比较交换（此处由外层for循环实现）；
// （3）注意每个元素与后面元素比较的次数；
 var arr = [5, 4, 3, 2, 1]; //先定义数组；可以设定任何无序的元素形式，也可以任意元素个数进行试验；
 for (var i = 0; i < arr.length - 1; i++) { //外层for进行躺数循环，即几个索引号要与后续元素比较调换；
     for (var j = 0; j < arr.length - 1 - i; j++) { //内循环设置单个索引号与后续所有元素的比较调换，注意每个索引号比较的次数；
         if (arr[j] > arr[j + 1]) { //设置条件；
             var temp = arr[j]; //引入临时变量，实现对调；
             arr[j] = arr[j + 1];
             arr[j + 1] = temp;
         }
     }
 }
 console.log(arr); //输出；
```

#### 36、利用函数计算1-100的和：

```js
 var sum = 0;
 function getSums() {
     for (i = 1; i <= 100; i++) {
         sum += i;
     }
     return sum;
 }
 console.log(getSums());
```

####  37、利用函数计算任意两个数之间的整数和：

```js
 var num1 = prompt('请输入第一个数：');
 var num2 = prompt('请输入第二个数：');
 var sum = 0;
 function getSums(num1, num2) {
     for (i = num1; i <= num2; i++) {
         sum += i;
     }
     return sum;
 }
 var re = getSums(parseInt(num1), parseInt(num2));
 console.log(re);
```

#### 38、利用函数求任意数组中的最大值：

```js
 var arr = [1, 2, 3, 4, 5, 6, 7, 8, 9];
 var max = arr[0];

 function getMax() {
     for (i = 1; i < arr.length; i++) {
         if (arr[i] > max) {
             max = arr[i];
         }
     }
     return max;
 }
 var re = getMax();
 console.log(re);
```

#### 39、写一个函数，用户输入任意两个数字的任意算术运算（简单计算器），并弹出算数结果：

```js
 function getResult() {
     var num1 = prompt('请输入第一个数：');
     var fuhao = prompt('请输入运算符号：\n1、+  2、-  3、*  4、%');
     var num2 = prompt('请输入第二个数：');
     var result = 0;

     if (fuhao == 1) {
         result = parseFloat(num1) + parseFloat(num2);
     } else if (fuhao == 2) {
         result = parseFloat(num1) - parseFloat(num2);
     } else if (fuhao == 3) {
         result = parseFloat(num1) * parseFloat(num2);
     } else {
         result = parseFloat(num1) / parseFloat(num2);
     }
     return result;
 }
 var re = getResult();
 alert('运算结果是:' + re);
```

#### 40、用函数辨别用户输入的任意三个数字的最大值，并输出：

```js
 var num1 = prompt('请输入第一个数字：');
 var num2 = prompt('请输入第二个数字：');
 var num3 = prompt('请输入第三个数字：');

 function getMax(num1, num2, num3) {
     var result;
     if (num1 > num2) {
         result = num1;
     } else {
         result = num2
     }
     if (result > num3) {
         result = result;
     } else {
         result = num3;
     }
     return result;
 }

var re = getMax(parseFloat(num1), parseFloat(num2), parseFloat(num3));
alert('最大值是：' + re);
```

#### 41、利用函数arguments求任意个数的最大值：

```js
 function fn(arr) {
     var max = arguments[0];
     for (var i = 1; i < arguments.length; i++) {
         if (arguments[i] > max) {
             max = arguments[i];
         }
     }
     return max;
 }
 var re = fn(1, 2, 3, 1, 5, 222, 11, 7, 2);
 console.log(re);
```

#### 42、利用函数翻转一个数组：

```js
 function fn(arr) {
     var newArr = [];
     for (i = arr.length - 1; i >= 0; i--) {
        newArr[newArr.length] = arr[i];
     }
     return newArr;
 }
 var re = fn([1, 2, 3, 4, 5, 6, 7, 8, 9]);
 console.log(re);
```

#### 43、 函数封装数组冒泡排序：

```js
 function sort(arr) {
     for (var i = 0; i < arr.length - 1; i++) {
         for (var j = 0; j < arr.length - 1 - i; j++) {
             if (arr[j] > arr[j + 1]) {
                 var temp = arr[j];
                 arr[j] = arr[j + 1];
                 arr[j + 1] = temp;
             }
         }
     }
     return arr;
 }

var arr1 = sort([1, 4, 7, 3, 10, 9]);
 console.log(arr1);
```

#### 44、利用对象字面量创建对象：

```js
 var obj = {
     uname: '可可',
     age: 5,
     type: '阿拉斯加犬',
     color: 'brown',
     skilling: function() {
         console.log('汪汪汪');
         console.log('showFilm');
     }
 }
 
 console.log(obj.uname);
 console.log(obj['age']);
 console.log(obj.type);
 console.log(obj.color);
 obj.skilling();
```

#### 45、用new object 创建对象：

```js
 var obj = new Object();
 obj.uname = '鸣人';
 obj.sex = '男';
 obj.age = 19;
 obj.skill = function() {
     console.log('影分身之术');
 }

 console.log(obj.uname);
 console.log(obj.sex);
 console.log(obj.age);
 obj.skill();
```

#### 46、 用构造函数创建对象：

```js
 function hero(uname, type, blood) {
     this.name = uname;
     this.type = type;
     this.blood = blood;
     this.attack = function(attack) {
         console.log(attack);
     }
 }
 
 var lianpo = new hero('廉颇', '力量型', '500血量'); //构造函数必须用new调用
 console.log(lianpo.name, lianpo.type, lianpo.blood);
 lianpo.attack('近战');
 var houyi = new hero('后裔', '射手型', '100血量');
 console.log(houyi.name, houyi.type, houyi.blood);
 houyi.attack('远程');
```

#### 47、做一个简易的计算器：

```js
 function getResult() {
     do {
         var result = 0;
         var num = prompt('欢迎使用简易计算器：\n1、加法运算：\n2、减法运算：\n3、乘法运算：\n4、除法运算：\n5、退出：\n请输入您的选项：');
         if (parseFloat(num) != 1 && parseFloat(num) != 2 && parseFloat(num) != 3 && parseFloat(num) != 4 && parseFloat(num) != 5) {
             alert('请重新输入！');
             continue;
         } else if (parseInt(num) == 5) {
             break;
         } else if (parseInt(num) == 1) {
             first = prompt('请输入第一个数字：');
             second = prompt('请输入第二个数字：');
             result = parseFloat(first) + parseFloat(second);
         } else if (parseInt(num) == 2) {
             first = prompt('请输入第一个数字：');
             second = prompt('请输入第二个数字：');
             result = parseFloat(first) - parseFloat(second);
         } else if (parseInt(num) == 3) {
             first = prompt('请输入第一个数字：');
             second = prompt('请输入第二个数字：');
             result = parseFloat(first) * parseFloat(second);
         } else {
             first = prompt('请输入第一个数字：');
             second = prompt('请输入第二个数字：');
             result = parseFloat(first) / parseFloat(second);
         }
         alert('计算结果是：' + result);
     }
     while (num != 5)
     return '您已退出登录';
 }
 var re = getResult();
 alert(re);
```

#### 48、利用对象封装PI、最大值和最小值：

```js
 var mayMath = {
     PI: 3.141592653,
     mayMax: function() {
         var max = arguments[0];
         for (i = 1; i < arguments.length; i++) {
             if (max < arguments[i]) {
                 max = arguments[i];
             }
         }
         return max;
     },
     mayMin: function() {
         var min = arguments[0];
         for (i = 1; i < arguments.length; i++) {
             if (min > arguments[i]) {
                 min = arguments[i];
             }
         }
         return min;
     }
 }
 
 console.log(mayMath.PI);
 console.log(mayMath.mayMax(1, 2, -3, 4, 5, 6, 71, 8, 9));
 console.log(mayMath.mayMin(1, 2, -3, 4, 5, 6, 71, 8, 9));
```

#### 49、随机点名：（random本身表示随机生成一个0-1之间的数字，包含0，不包含1；）

```js
 function order(min, max) {
     return Math.floor(Math.random() * (max - min + 1) + min);//这段代码表示随机生成max和min之间的任意整数，包含max和min本身；
 }
 var arr = ['阿离', '范西西', '龟霸', '吹喜', '老吴', '贝总', '墨'];
 console.log(arr[order(0, arr.length - 1)]);
```

#### 50、 随机生成1 - 10 之间的数字，并让用户输入一个数字：

​	1、如果小了，提示数字小了，继续猜；

​    2、如果大了，提示数字大了，继续猜；

​    3、如果刚好等于，提示猜对了，结束程序；

方法一：（自写）

```js
 function guessNumber(min, max) {
     var number = Math.floor(Math.random() * (max - min + 1) + min);
     console.log(number);

     do {
         var num = prompt('请输入猜的数字：');
         if (num > number) {
             alert('数字大了，继续猜！');
         } else if (num < number) {
             alert('数字小了，继续猜！');
         } else
             return '猜对了!'
     } while (1)
 }
 alert(guessNumber(0, 10));
```

方法二：（pink视频法）

```js
 function guessNumber(min, max) {
     return Math.floor(Math.random() * (max - min + 1) + min);
 }
 var random = guessNumber(1, 10);
 console.log(random);
 while (true) {
     var num = prompt('请输入猜的数字：');
     if (num > random) {
         alert('数字大了，继续猜！');
     } else if (num < random) {
         alert('数字小了，继续猜！');
     } else {
         alert('猜对了!');
         break;
     }
 }
 alert(guessNumber(0, 10));
```

#### 51、日期对象的一些属性：

```js
 var date = new Date(); //日期对象要用new调用，此句话必须写在前面；
 console.log(date); //直接new Date()表示输出现在的时间；
 console.log(date.getFullYear()); //当前年
 console.log(date.getMonth() + 1); //当前月，默认0-11，所以加1；
 console.log(date.getDate()); //当前日；
 console.log(date.getDay()); //周几：周日至周六为0-6
 console.log(date.getHours()); //几点
 console.log(date.getMinutes()); //分
 console.log(date.getSeconds()); //秒
```

##### 1、距离1970.1.1总毫秒数的四种写法（括号内可接收某个时间作为参数，返回的是对应时间的时间戳）：

第1种：

```js
var date = new Date(); //日期对象要用new调用，此句话必须写在前面；
console.log(date.valueOf());第一种
```

第2种：

```js
var date = new Date(); //日期对象要用new调用，此句话必须写在前面；
console.log(date.getTime());第二种
```

第3种：

```js
 var date1 = +new Date();//用+new调用后直接就是总毫秒数
 console.log(date1);
```

第4种：

```js
console.log(Date.now());
//第四种不需要用new调用，Date.now()表示的就是总毫秒数，但是该方法为H5的新增内容，IE678不适用
```

##### 2、输出此时的年月日及周几：

```js
 var date1 = new Date();
 var year = date.getFullYear();
 var month = date.getMonth() + 1;
 var dates = date.getDate();
 var arr = ['星期天', '星期一', '星期二', '星期三', '星期四', '星期五', '星期六'];
 var day = date.getDay();
 console.log('今天是：' + year + '年' + month + '月' + dates + '号' + arr[day]);
```

#### 52、 封装一个函数返回当前时分秒： 例如08: 08: 08

```js
 function getTimes() {
     var date = new Date();
     var h = date.getHours();
     h = h < 10 ? '0' + h : h;
     var m = date.getMinutes();
     m = m < 10 ? '0' + m : m;
     var s = date.getSeconds();
     s = s < 10 ? '0' + s : s;
     return h + ':' + m + ':' + s;
 }
 console.log(getTimes());
```

#### 53、利用日期对象做一个倒计时案例：(此为重点案例，需明确知道如何分析如何做)

案例分析：

​	（1）、核心算法：输入的时间减去现在的时间就是剩余时间，但是不能直接拿时分秒相减，比如05分-25分，结果是负数；

​	（2）、用时间戳来做：用户输入的时间的总毫秒数减去现在的时间总毫秒数，就是剩余时间的毫秒数；

​	（3）、把剩余时间的总毫秒数转换成天、时、分、秒（时间戳转换成时分秒）注意一秒等于1000毫秒；

 公式如下：

```js
d = parseInt(总秒数 / 60 / 60 / 24); //计算天数

h = parseInt(总秒数 / 60 / 60 % 24); //计算小时

m = parseInt(总秒数 / 60 % 60); //计算分数

s = parseInt(总秒数 % 60); //计算秒数
```

代码如下：

```js
 function countTime(time) {
     var nowTime = +new Date();
     var inputTime = +new Date(time);
     var times = (inputTime - nowTime) / 1000; //转换成秒
     var s = parseInt(times % 60);
     s = s < 10 ? '0' + s : s;
     var m = parseInt(times / 60 % 60);
     m = m < 10 ? '0' + m : m;
     var h = parseInt(times / 60 / 60 % 24);
     h = h < 10 ? '0' + h : h;
     var d = parseInt(times / 60 / 60 / 24 % 30);
     d = d < 10 ? '0' + d : d;
     var y = parseInt(times / 60 / 60 / 24 / 30 % 12);
     y = y < 10 ? '0' + y : y;
     var n = parseInt(times / 60 / 60 / 24 / 30 / 12);
     n = n < 10 ? '0' + n : n;
     return n + '年' + y + '月' + d + '天' + h + '时' + m + '分' + s + '秒';
 }
 console.log(countTime('2022-9-16 13: 00: 00'));
 console.log(new Date());

```

#### 54、 数组对象的一些属性：

##### 1、检测是否为数组的两种方法：

(1)、变量名 **instanceof Array**，代码如下：

```js
 var arr1 = [1, 2, 3];
 var obj = {};
 console.log(arr1 instanceof Array); //true
 console.log(obj instanceof Array); //false
```

(2)、**Array.isArray**(参数/变量名)，H5新增；代码如下：

```js
 var arr2 = [1, 2, 3];
 var obj2 = {};
 console.log(Array.isArray(arr2)); //true
 console.log(Array.isArray(obj2)); //false
```

##### 2、添加/删除数组元素：

(1)、**push()**:末尾添加一个/多个数组元素，返回新数组长度：

```js
var arr = [1, 2, 3, 4, 5];
console.log(arr.push(6));
console.log(arr);
```

(2)、**pop()**:末尾删除一个数组元素，返回删除的元素：

```js
var arr = [1, 2, 3, 4, 5];
console.log(arr.pop());
console.log(arr);
```

(3)、**unshift()**:开头添加一个数组元素，返回新的数组长度：

```js
var arr = [1, 2, 3, 4, 5];
console.log(arr.unshift(0));
console.log(arr);
```

(4)、**shift()**:开头删除一个数组元素，返回删除的第一个元素：

```js
var arr = [1, 2, 3, 4, 5];
console.log(arr.shift());
console.log(arr);
```

##### 3、关于splice的多种用法：

splice(开始的位置，替换的个数，替换为)， 内部可以传递3个参数，根据这3个参数可以分别实现删除、插入、替换等功能。开始的位置为索引号，后续变化从该索引号元素开始。

(1)、删除

splice(开始的位置，删除个数)，如果删除个数不写，默认从开始位置往后全删。

```js
var arr = [1, 2, 3, 4, 5];
splice(0,1);
splice(0);
```

(2)、替换

splice(开始的位置，替换的个数，替换为)，默认从开始位置算起，把相应需要替换的个数那部分元素替换成需要替换的元素。(替换为的元素可以是多个，一直写下去)

```js
var arr = [1, 2, 3, 4, 5];
conse.log(arr);//[1,2,3,4,5]
conse.log(splice(0,2,1,1));//[1,1,3,4,5]
```

(3)、插入

splice(开始的位置，0，追加的元素)，其实本质与替换一样，此处需要替换的元素为0个，因此加入替换为的元素就相当于插入元素。

```js
var arr = [1, 2, 3, 4, 5];
conse.log(arr);//[1,2,3,4,5]
conse.log(splice(0,0,6,6));//[1,6,6,2,3,4,5]
```

##### 4、数组排序

(1)、**reverse()** 颠倒顺序，返回新数组：

```js
var arr1 = [1, 2, 3, 4, 5, 6, 7, 8, 9];
console.log(arr1.reverse());
```

(2)、**sort()** 对数组元素排序，仅限个位数元素从小到大,**如果需所有元素，则需引进函数固定格式如下(此即为冒泡排序)**：

格式：

```js
变量名.sort(function(a, b) {
     return a - b; //选择a-b或者b-a，a-b是从小到大，b-a是从大到小；
     return b - a;//选择a-b或者b-a，a-b是从小到大，b-a是从大到小；
 })
```

代码如下：

```js
 var arr = [1, 2, 4, 0, 4, 7, 3, 9, 5];
 console.log(arr.sort()); //此为个位数的排序；
 
 var arr1 = [1, 2, 17, 5, 9, 4, 3, 12, 35];
 console.log(arr1.sort()); //如果有十位数或者以上，单独用sort只会按最前面的那位数排序；
 
 var arr2 = [11, 2, 3, 9, 32, 45, 16, 25, 6, 10];
 arr2.sort(function(a, b) {
     return b - a;//冒泡排序
 });
 console.log(arr2);
```

##### 5、数组的索引方法（根据元素查索引号，即返回位置）：

(1)、**indexOf('元素'，开始的位置)** 从前往后查，如果存在该元素，则返回索引号，有重复只取靠前的索引号，若无该元素，则返回-1；

注意：**开始的位置即索引号可以不写，不写默认从头到尾；**

```js
 var arr = ['red', 'white', 'blue', 'green', 'pink', 'blue'];
 console.log(arr.indexOf('green')); //3
 console.log(arr.indexOf('blue')); //2
 console.log(arr.indexOf(('blue'), 3)); //5
 console.log(arr.indexOf('brown')); //-1
```

(2)、**lastIndexOf('元素'，开始的位置)** 从后往前，如果存在该元素，则返回索引号，有重复只取靠后的索引号，若无该元素，则返回-1：

```js
 var arr1 = ['red', 'white', 'blue', 'green', 'pink', 'blue'];
 console.log(arr1.lastIndexOf('green')); //3
 console.log(arr1.lastIndexOf('blue')); //5
 console.log(arr1.lastIndexOf('brown')); //-1
```

##### 6、数组转换为字符串：

(1)、**tostring()** ：逗号分隔转换后的字符串，返回的是一个字符串：

```js
 var arr = ['red', 'white', 'blue', 'green', 'pink', 'blue'];
 console.log(arr.toString());
```

(2)、**join('分隔符')** 转换成的字符串用分隔符相连，如果无分隔符，默认用逗号分隔，返回的是字符串：

```js
 var arr1 = ['red', 'white', 'blue', 'green', 'pink', 'blue'];
 console.log(arr.join(' & '));
```

#### 55、把数组[1000,1200,2000,3000,2500,800,1500]中小于2000的元素取出来生成新的数组输出：

```js
 var arr = [1000, 1200, 2000, 3000, 2500, 800, 1500];
 var newArr = [];
 for (var i = 0; i < arr.length; i++) {
     if (arr[i] < 2000) {
         // newArr[newArr.length] = arr[i]; //这是以前的做法；
         newArr.push(arr[i]); //这是现在的做法
     }
 }
 console.log(newArr);
```

#### 56、去除数组['c', 'a', 'z', 'a', 'x', 'a', 'x', 'c', 'b'] 中重复的元素（ 重点案例）：

思路：遍历旧数组的元素，查询新数组，如果该元素在新数组没有出现就放进去；

```js
 function unique(arr) {
     var newArr = [];
     for (var i = 0; i < arr.length; i++) {
         if (newArr.indexOf(arr[i]) === -1) {
             newArr.push(arr[i]);
         }
     }
     return newArr;
 }
 console.log(['c', 'a', 'z', 'a', 'x', 'a', 'x', 'c', 'b']);
 console.log(unique(['c', 'a', 'z', 'a', 'x', 'a', 'x', 'c', 'b']));
```

补充：ES6语法中还有一个新的数据类型set，类似于数组形式，但是内部元素不能重复，因此还可以用该方式对数组去重

关于set：

创建数据：new Set([内部元素])  ===>  {内部元素}

即，例 new Set([1,2,3,4,5])  ===>  {1,2,3}

```js
var arr = ['c', 'a', 'z', 'a', 'x', 'a', 'x', 'c', 'b'];
var newArray = [...new Set(arr)];
//先创建set数据形式，再把arr数据作为元素放进去,得到{}形式的数据，再...解构赋值，再套[]转化为数组
```

#### 57、 字符串对象的一些属性：

##### 1、根据字符返回位置(与上面的数组返回位置类似)：

(1)、**indexOf('要查找的字符'，开始的位置)**，如果有该字符，返回索引号，如果无返回-1;默认只查一个；

```js
 var str = '改革春风吹满地，春天来了';
 console.log(str);
 console.log(str.indexOf('春')); //2
 console.log(str.indexOf(('春'), 3)); //8
```

(2)、**lastIndexOf('要查找的字符'，开始的位置)** ,从后往前查找，只找到第一个匹配的字符：

```js
 var str1 = '改革春风吹满地，春天来了';
 console.log(str1);
 console.log(str1.lastIndexOf('春'));
 console.log(str1.lastIndexOf(('春'), 2));
```

##### 2、根据位置返回字符：

(1)、**charAt(索引号)** 返回指定位置字符：

```js
 var str = 'andy';
 console.log(str);
 console.log(str.charAt(1)); //n
```

(2)、**charCodeAt(索引号)** 返回指定位置字符的ASCII码，此方法主要是后期游戏开发判断用户输入的按键，每个按键对应一个ASCII码，例如攻击、跳跃....:

```js
 var str1 = 'andy';
 console.log(str1);
 console.log(str1.charCodeAt(1)); // n的ASCII码是110
```

(3)、**变量名[索引号]**， 获取指定位置的字符，该法为H5属性，效果与第一种一致：

```js
 var str2 = 'andy';
 console.log(str1);
 console.log(str2[1]);
```

##### 3、拼接几个字符串或者截取字符串内的部分字符：

(1)、**concat(字符串1，字符串2，...)**， 拼接两个及以上字符串，等效于+，一般用+的多：

```js
 var str1 = 'andy';
 var str2 = 'red';
 console.log(str1.concat(str2)); //andyred
```

(2)、**substr(start,length)** 从start处开始截取字符，注意不截取start该位的字符，截取的长度是length的长度(此方法重点记住，下面两种可了解)：

```js
 var str3 = '改革春风吹满地';
 console.log(str3.substr(0, 7)); //改革春风吹满地 
 console.log(str3.substr(1, 6)); //革春风吹满地
```

(3)、**slice(start,end)** 从start开始截取，至end结束，用法同**substring(start,end)** 类似，注意以下不同点：

- (x,y]的位数区间，x如果大于y，则返回空，而不会自动互换位置不受影响
- y可以为负值，如果y为负值时，其y真正的意思是y+字符串的length得出来的数字

```js
 var str4 = '改革春风吹满地';
 console.log(str4.slice(0, 6)); //改革春风吹满
 console.log(str4.slice(1 6)); //革春风吹满
```

(4)、**substring(start,end)** 从start开始截取，至end结束，注意end处本身截取不到,和slice基本相同，但不接受负值：

- start和end代表的是元素的第几个，如x,y表示（x,y]，不包含第x个，包含第y个
- 如果只有一个参数x，则会从x至结尾
- 如果x<y则，会自动调换位置，依旧变成(x,y]
- 如果x为0，相当于从0位开始取(0,y]，此时第一个元素是可以取到的
- 如果y为负数，则直接输出x及之前的位数的元素

```js
 var str5 = '改革春风吹满地';
 console.log(str5.substring(0, 6)); //改革春风吹满
```

##### 4、替换字符：

**replace('被替换字符','替换为的字符')** 注意只会替换从左到右的第一个：

```js
 var str = 'andybye';
 console.log(str);
 console.log(str.replace('y', '*'));
```

##### 5、字符转换成数组：

**split('分隔符')** 此处的分隔为为原字符串中的分隔符，即以该分隔符为断点来分隔成数组：

```js
 var str = 'red,pink,blue';
 var str1 = '1&2&3&4&5&6';
 console.log(str);
 console.log(str.split(','));
 console.log(str1.split('&'));
```

#### 58、查找字符串'abcoefoxyzzopp'中O出现的位置及次数：

 核心算法：

​		先查找第一个o的位置； 然后只要indexOf返回不为-1，就继续查找，因为indexOf只能查到第一个，后面继续查找时索引号需加1，才可继续查找；

```js
 var str = 'abcoefoxyzzopp';
 var index = str.indexOf('o');
 var num = 0;
 while (index !== -1) {
     console.log(index);
     index = str.indexOf('o', index + 1);
     num += 1;
 }
 console.log(num);
```

#### 59、把字符串'abcoefoxyzzopp'中所有O都替换成*：

分析：

​		在while循环内，用indexOf把字符串中只要查到的o位置不为-1，就用replace替换掉， 由于indexOf只能查到第一个o，但是因为我们每查一个就替换一个，所以能一直查下去直到没有o，退出循环

```js
 var str = 'abcoefoxyzzopp';
 console.log(str);
 while (str.indexOf('o') !== -1) {
     str = str.replace('o', '*');
 }
 console.log(str);
```



## 二、webapi之DOM（页面文档对象模型）

### DOM元素注册

#### 1、获取HTML元素的方法

（1）、根据ID获取：getElementById('id名称')

```js
var timer = document.getElementById('time');
console.log(timer);
```

(2)、根据标签名获取：getElementByTagNaame('标签名')

​		注意返回的是一个伪数组集合，要输出元素，需遍历或者加索引号。

```js
var div = document.getElementsByTagName('div');
div[0].style.backgroundColor = 'pink';
```

(3)、HTML5新增的方法， 有兼容性，IE678不支持：

①、document.getElementsByClassName('类名')，注意返回的是一个伪数组集合，要输出元素，需遍历或者加索引号。

```js
 var now = document.getElementsByClassName('now');
 now[0].style.fontSize = '20px';
```

②、document.querySelector('选择器')，根据指定选择器返回第一个对象,不同选择器需加相应符号。

```js
var ago = document.querySelector('.ago');
ago.style.color = 'red';
```

③、document.querySelectorAll('选择器')， 指定选择器所有对象集合， 注意返回的是一个伪数组集合， 要输出元素， 需遍历或者加索引号。

```js
var ago = document.querySelectorAll('.ago');
ago[0].style.fontStyle = 'italic';
```

(4)、获取body对象： document.body

```js
var bodys = document.body;
bodys.style.backgroundColor = '#ddd';
```

(5)、获取html元素：document.documentElement

```js
var htmls = document.documentElement
htmls.style.backgroundColor = '#ccc';
```

#### 2、 修改元素内容：

（1）、innerText:改变起始到终点的内容，不识别html标签，同时去掉空格和换行；

```js
var time = document.getElementById('time');
time.innerText = '离职帝在<a>这里</a>等你！';
```

（2）、innerHTML:改变起始到终点的内容，识别html标签，同时保留空格和换行；

```js
var time = document.getElementById('time');
time.innerHTML = '离职帝在<a href="javascript:;">这里</a>等你！';
```

####  3、自定义属性操作：

（1）、获取自定义属性：element.getAttribute('属性')，获取的是自定义属性；注意获取内置属性直接用elmment.属性；

```js
 var div = document.querySelector('div');
 console.log(div.getAttribute('data-index'));
```

（2）、 设置自定义属性值； element.setAttribute('属性', '值'), 注意， 改内置属性值直接element.属性 = '值'，

​		特殊的一个是class，为保留字，要用className，但是在该代码不用，直接用class就行，当然该代码主要用于修改自定义，也可改内部的；

```js
var div = document.querySelector('div');
div.className = 'last';//直接修改class时得写成className
div.setAttribute('data-index', 3);
```

(3)、 移除自定义属性： element.removeAttribute('属性');

```js
var div = document.querySelector('div');
div.removeAttribute('data-index');
```

(4)、 H5的关于自定义属性的操作：

①、设置自定义属性：H5规定自定义属性以data-开头并赋值，例如data-index；

②、获取H5的自定义属性：element.dataset.名,或者element.dataset['名']，此处的名为data-之后的名字。

​		如有多个单词串起来的，则去掉中间的-号，采用驼峰命名法；

​		注意：本方法输出的是所有带有后面名的自定义属性的集合，返回的是一个伪数组集合，要输出元素，需遍历或者加索引号；

```js
var div = document.querySelectorAll('div'); //此处如果为获取的集合，那么下面获取的自定义属性也是集合；
 console.log(div.dataset.index);
console.log(div);
console.log(div[0].dataset.index);
```

#### 4、节点操作：非标准都有兼容问题

（1）、父级节点：获取的子节点.parentNode，获取的是离子节点最近的父节点，如果没有则返回null；

```js
var first = document.querySelector('.first');
first.parentNode.style.backgroundColor = 'green';
```

(2)、 子节点： 父级节点.children，非标准， 返回所有子元素节点， 不包含文本节点等， 带索引号可返回相应节点；（此处不讲解标准法：父级节点.childNodes,他也返回所有子节点，但是包含文本节点，我们不需要；）

```js
var father = document.querySelector('.father');
father.children[1].style.color = '#fff';
```

(3)、第一个或最后一个子节点：同上有标准非标准，

- 父级节点.firstChild 或 父级节点.lastChild,为标准，但是包含文本节点；

- 父级节点.firstElementChild 或 父级节点.lastElementChild,为非标准，只选择元素节点；

代码此处就不演示了。

(4）、兄弟节点：上一个和下一个；同上也有两种，标准和非标准；

- 元素.nextSibling 或 元素.previousSibling 为标准，包含文本节点；

- 元素.nextElementSibling 或 元素.previousElemnetSibling 为非标准，返回元素节点；

 代码同样省略。

#### 5、创建节点：通过js创造节点标签，并添加到相应的位置；

（1）、创建节点：document.createElement('需要生成的标签');

```js
var father = document.querySelector('.father');
var li = document.createElement('li');
```

（2）、添加节点：把生成的节点放置在某个位置，从而显示出来；添加节点有两种情况；

  ①、 添加到某个父元素的子节点列表的末尾， 即添加在最后一个；父元素.appendChild(创建的元素)；

```js
father.appendChild(li);
father.children[father.children.length - 1].innerHTML = '我是最后一个！'; //此处我们给新增在最后面的li赋值；
```

②、添加到指定父元素的指定某个子节点前面； 父元素.insertBefore(创建的元素，父元素.children[填写需要放置位置的索引号])；

```js
var newli = document.createElement('li');
father.insertBefore(newli, father.children[1]);
newli.innerHTML = '我是随便放的，应该是在第二个吧';
```

#### 6、 删除节点： 父级节点.removeChild('要删除的子节点'), 返回值是删除的节点；

代码略。

#### 7、复制节点：要复制的节点.cloneNode();不接参数；使用时复制完需要接着添加节点放置在某个位置；

代码略。



### 事件高级

#### 8、通过事件监听来注册事件

​		之前的注册事件为传统的注册事件（btn.onclick = function(){}），现在通过事件监听来注册事件。

（1）、addEventListener(type,listener[,useCapture])，这个标注的模板我也不知道为什么是这样奇怪；（IE9之前不支持）

- type： 指的是事件类型的字符串， 如点击click， 经过mouseover 等， 此处前面不需要加on， 记得用引号括起来；

- listerner:指的是某个函数,function(){};

- useCapture:可选参数，是个布尔值，记得true或者false，默认不写是false；

```js
var div = document.querySelector('div');
div.addEventListener('click', function() {
     div.style.width = '200px';
 })
```

（2）、attachEvent(eventNameWithOn,callback)，这是IE9之前的版本用这个事件监听来注册事件,其他浏览器不支持，一般情况不用，现在IE9之前的少，也不怎么需要设置兼容性，这个作为了解；

- eventNameWithOn:指的是事件类型的字符串， 如点击onclick等，此处要加on；

-  callback：指的是事件处理回调函数；

```js
var div = document.getElementById('time');
 div.attachEvent('onclick', function() {
     div.style.height = '90px';
 })
```

#### 9、删除事件：

（1）、传统方式：

​		事件.onclick = null;

 (2)、监听方式---ie9以上及其它浏览器（此处IE9以下的点击事件为detachEvent(),具体细节与下面一致，就不在重复写了）：

​		事件.removeEventListener(type,listener[,useCapture]),里面参数上面写过，不再重复；

```js
ul.children[0].addEventListener('click', fn) //此处引用函数，直接写fn，不用加括号
 function fn() {
     alert('你好呀'); //先注册一个点击事件
     ul.children[0].removeEventListener('click', fn) //此为点击事件之后该函数被移除，下次点击就没有这个函数了。
 }
```

#### 10、事件流：分为捕获阶段、当前目标阶段、冒泡阶段；

​		捕获阶段：由DOM最顶层节点开始，然后逐级向下传播到具体的元素接收过程；

​		冒泡阶段:事件开始时由具体的元素接收,然后逐级向上传播到DOM最顶层节点的过程;

 注意:

- JS只能执行捕获阶段或者冒泡阶段其中的一个阶段;
- onclick和attachEvent()只能得到冒泡阶段；
- addEventListener(), 如果第三个参数为true， 则在捕获阶段调用事件， 如果为false， 则在冒泡阶段调用事件； 默认为冒泡阶段；
-  实际开发一般使用冒泡阶段，很少用捕获阶段；
- 有些事件是没有冒泡阶段的，比如：onblur、onfocus、onmouseenter、onmouseleave;

#### 11、事件对象：

获取事件对象格式：

​		传统：**eventTarget.onclick = function(event) {}**

​										或

​		监听：**eventTarget.addEventListener('click',event){}**

-  eventTarget.addEventListener('type', function(event) {})  //ie678不识别addaddEventListener,只能用onclick；
-  括号里面的event就是事件对象，有了事件才有事件对象；可以简写evt或者e;
-  事件发生后，这个事件对象里面包含了关于这个事件的type的所有属性和方法；
-  例如点击事件，event就包括了这个点击事件点击的是哪个元素，事件类型......
-  ie678不识别e， 需要用window.event来获取事件对象； 考虑兼容问题可以用e = e || window.event;

（1）、事件对象的属性：

- e.Target: 返回触发事件的对象（ 标准）， 注意前面的this是谁绑定返回谁， target是点击谁返回谁， 当父子都有点击事件时需区分；
-  此方法可以设置点击对象改变相应属性之类的设置
- e.srcElement: 返回触发事件的对象（ 非标准）， IE678适用；
- e.type: 返回触发事件的类型， 如click mouseover 注意不带on；
- e.preventDefault（）: 阻止默认事件（行为），标准，比如不让链接跳转；方法加括号无参数
- e.returnValue: 阻止默认事件（行为），非标准，比如不让链接跳转，IE678适用；
-  e.stopPropagation（）: 阻止冒泡事件，标准；方法加括号无参数；
-  e.cancleBubble: 阻止冒泡事件，非标准，ie678适用，此处true表示阻止；

注意：阻止冒泡兼容写法：一般不考虑兼容，因为ie678基本没了。

```js
 if (e && e.stopPropagation) {
   e.stopPropagation;
 } else {
   window.event.cancleBubble = true;
 }
```

#### 12、事件委托：

​		不要给每个子元素添加事件监听器，而是把事件监听器设置在父元素上，这样每次点击子元素，利用冒泡事件影响每个子节点，

​		即每次点击其中一个子元素，都会使父元素上的事件监听器产生反应，达到效果，如此一来就只设置了一个事件监听器，提高程序性能；

#### 13、常用鼠标事件（补充知识点）：

（1）、禁止鼠标右键菜单：contextmenu配合对象事件的禁止默认事件preventDefault

```js
document.addEventListener('contextmenu', function(e) {
     e.preventDefault();
 })
```

上述代码禁用了整个文档的右键菜单事件；

(2)、 禁止鼠标选中： selectstart配合对象事件的禁止默认事件preventDefault

```js
document.addEventListener('selectstart', function(e) {
     e.preventDefault();
 })
```

（3）常见的鼠标事件：

- mousedown：当鼠标指针移动到元素上方，并**按下鼠标按键（左、右键均可）**时，会发生 `mousedown` 事件。与 `click` 事件不同，`mousedown` 事件仅需要按键被按下，而不需要松开即可发生。

- mouseup：当在元素上**松开鼠标按键（左、右键均可）**时，会发生 `mouseup` 事件。
  与 `click` 事件不同，`mouseup` 事件仅需要松开按钮。当鼠标指针位于元素上方时，放松鼠标按钮就会触发该事件。

- mousemove：该件是一个实时响应的事件，当**鼠标指针的位置发生变化时**（至少移动一个像素），就会触发 mousemove 事件。该事件响应的灵敏度主要参考鼠标指针移动速度的快慢以及浏览器跟踪更新的速度。

- click：当鼠标指针停留在元素上方，然后**按下并松开鼠标左键**时，就会发生一次 `click` 事件。
  注意：触发`click`事件的条件是**按下并松开鼠标左键！**按下并松开鼠标右键并不会触发`click`事件。

  

#### 14、鼠标事件对象：

当某事件为鼠标事件时，事件对象就是鼠标事件对象：

- e.clientX :返回鼠标相对浏览器窗口可视区的X坐标；
-  e.clientY: 返回鼠标相对浏览器窗口可视区的X坐标；
-  e.pageX: 返回鼠标相对浏览器文档页面的Y坐标； IE9 + 支持
-  e.pageY: 返回鼠标相对浏览器文档页面的X坐标； IE9 + 支持
-  e.screenX: 返回鼠标相对电脑屏幕的X坐标；
- e.screenX: 返回鼠标相对电脑屏幕的Y坐标；

#### 15、常见键盘事件：

- onkeyup: 某个键盘按键被松开时开始触发；
-  onkeydown:某个键盘按键被按下时触发（不松口一直不触发）；
- onkeypress:某个键盘按键按下时触发，但是它不识别功能键，比如Ctrl，shift ，删除键.....

```js
document.addEventListener('keyup', function() {
     console.log('我是谁'); //任意按下键盘触发该事件
 })
```

#### 16、键盘事件对象：

 当某事件为键盘事件时，事件对象就是键盘事件对象。

 keyCode : 返回该键的ASCII码值；

注意：

（1）、keyup和keydown不区分大小写，即返回的是同一个ASCII值，keypress区分大小写；

（2）、实际开发用的多的是keyup和keydown；

（3）、keydown和keypress在文本框的特点：他们两个都是按下按键触发， 但是按下瞬间文字还没输出时， 代码就执行完毕， 即事件执行完毕但相应按键还没来得及输出显示；

（4）、keyup事件触发时， 文字已经落入文本框， 即按下瞬间， 文字已经显示在文本框内， 松开后触发事件执行事件；

## 三、webapi之BOM（浏览器对象模型）

### 一些对应的属性及实例

#### 1、window对象常见事件：

（1）、window.onload=function(){}或者window.addEventListener('load',function(){})  

​		是窗口（页面）加载事件，当文档内容完全加载完成才会触发该事件（包括图像，脚本文件，css文件）。

注意： 

- 有了window.onload就可以把js代码用这个包起来， 然后把js代码放置在任意位置。 等所有文档文件加载完才会处理这个js；
- 传统注册window.onload 只能写一次，如果有多个，默认以最后一个为准；
- 如果用事件监听addEventListener来使用这个，则没有次数限制，默认按顺序来；

（2）、document.addEventListener('DOMContentLoaded',function(){})

- 仅当DOM加载完成（不包括样式表，图片，flash等），就开始执行该事件；
- 当页面图片很多时， 如果用window.onload效率会很慢， 因为要等图片都家在哪完成才会执行， 影响客户体验；
- 因此此时可以用这个比较合适，包住js；

#### 2、调整窗口大小时触发事件（即只要窗体大小发生改变就会触发设置好的事件）：

​			**window.onresize = function(){}** 或者 **window.addEventListener('resize',function(){})**

- 只要窗体大小发生像素变化， 就会触发事件；
- 我们经常用这个事件来完成响应式布局；
-  window.innerwidth表示当前屏幕宽度； 

#### 3、定时器：

（1）、window.setTimeout(调用函数，[延迟的毫秒数]);

- 延迟的毫秒数过了之后调用函数调用该定时器事件；

- window事件在调用时一般省略window这个词，延迟的毫秒数可不写，不写为立即执行；
- 有三种写法：直接写函数，或者setTimeout(调用的函数，[延迟的毫秒数]) 或者 setTimeout('调用的函数()',[延迟的毫秒数]) ；
- 由于页面中会有很多定时器，一般用var 把定时器赋值给一个变量，来进行标识；
- 这里的调用函数是一个回调函数（callback），即需要等待时间后才执行，之前学的点击事件函数也是回调函数，需要等待点击之后才执行；

```js
function callback() {
    console.log('爆炸了');
 }
 var time1 = setTimeout(callback, 3000); //经过三秒后执行这个定时器；
```

（2）、window.setInterval(调用函数，[延迟的毫秒数]);

- 每延迟该毫秒数之后调用一次定时器事件，一直重复调用；     
-  window事件在调用时一般省略window这个词，延迟的毫秒数可不写，不写为立即执行；
- 有三种写法：直接写函数，或者setInterval(调用的函数，[延迟的毫秒数]) 或者 setInterval('调用的函数()',[延迟的毫秒数]) ;
- 由于页面中会有很多定时器，一般用var 把定时器赋值给一个变量，来进行标识；

```js
function callback() {
     console.log('我一直在叫');
 }
var time2 = setInterval(callback, 2000);
```

(3)、 停止setTimeout这个定时器：window.clearTimeout(定时器的标识符)；

- window事件在调用时一般省略window这个词，用clearTimeout(定时器的标识符)；
- 括号的参数就是之前var 定义的定时器的标识符；

```js
var btn = document.querySelector('button');
 var time3 = setTimeout(function() {
     console.log('一个等待被取消的定时器');
 }, 3000);
 btn.addEventListener('click', function() {
     clearTimeout(time3);
 })
```

#### 3、执行队列的执行过程，按事件循环；

​		先执行主线程中执行栈的同步路，同时把执行栈中异步任务提交给对应的异步进行处理（例如点击事件，定时器等），

​		如果是定时器，则到时间把异步任务推到任务队列中，如果是点击事件，必须点击后才会推入到任务队列；

​		主线程执行完毕，就会查询任务队列，并取出一个任务，推入主线程来执行，执行完，继续查询，再执行；（该过程为事件循环）；

```js
console.log('1');
setTimeout(function() {
     console.log('3');
 }, 3000)
 document.addEventListener('click', function() {
    console.log('4');
 })
console.log('2');
// 输出的是：1，然后是2，最后是3，如果之后再点击则输出4；
```

#### 4、URL的解析：

完整的URL：

​		  **protocol: //host[:port]/path/[?query]#fragment**

- protocal:通信协议，常用的http,ftp,maito等
-  host: 主机域名；
- port:端口号，可选，省略时使用方案的默认端口，如http的默认端口是80；
- path:路径，由零或者多个/符号隔开的字符串，一般用来表示主机上的一个目录或者文件地址；
- query:参数，以键值对的形式，通过&符号分隔开；
- frament:片段，#后面的内容常见于链接锚点；

例如http://www.itcast.cn/index.html?name=andy&age=18#link

#### 5、location对象的属性：

-  location.href:获取或设置整个URL；（重）
-  location.host:返回主机域名；
- location.port：返回端口号，如果未写则返回空字符串；
- location.pathname：返回路径；
-  location.search:返回参数；（重）
- location.hash:返回片段，#后面内容常见于链接锚点；

#### 6、location对象的方法：

- location.assign()：跟href属性一样，跳转页面，此跳转可以后退（也成重定向页面）
- location.replace():替换当前页面，因为不记录历史，所以不能后退页面
- location.reload(): 重新加载页面， 相当于刷新按钮或者F5， 如果参数为true， 则为强制刷新ctrl + F5

#### 7.navigator对象：

​		navigator对象包含相关浏览器的信息，它有很多属性，我们最常用的是userAgent，

​		 该属性可以返回由客户发送给服务器的user-agent头部的值。有一段代码根据此属性判断用户使用哪个终端打开的页面，如果需要上网复制。

#### 8、history对象：

​		window提供了一个history对象，与浏览器历史记录进行交互，该对象包含用户（在浏览器窗口中）访问过的URL；

-  history.back():可以后退的功能；
-  history.forward:前进功能；
-  history.go(参数):前进后退功能，参数如果是1，前进一个页面，如果是-1，后退一个页面；只能前进后退一个页面；

### PC端网页特效



#### 9、PC端的网页特效：

（1）**offset**系列：offset是偏移量，使用该系列相关属性可以动态得到该元素的位置（偏移）、大小等；

注意：

- 获取元素距离带有定位的父元素的位置；
- 获得的元素自身大小（宽度、高度），不带单位；
-  element.offsetParent:返回作为该元素最近的带有定位的父级元素，如果父级元素没有定位，则返回body；
- element.offsetTop:返回相对该元素最近的带有定位的父级元素的上方偏移，若父级元素无定位，则以body为准；
-  element.offsetLeft:返回相对该元素最近的带有定位的父级元素的左侧偏移，若父级元素无定位，则以body为准；
- element.offsetWidth:返回自身，包括padding、边框、内容区的宽度，返回值不带单位；
- element.offsetHeight:返回自身，包括padding、边框、内容区的高度，返回值不带单位；

（2）、元素可视区**client**系列：

​      client是客户端的意思，我们使用client系列相关属性来获取元素可视区的相关信息，通过client系列的相关属性。

-  可以动态得到该元素的边框大小、元素大小等；
- element.clientTop:返回元素上边框的大小；
-  element.clientLetf返回元素左边框的大小；
-  element.clientWidth:返回自身，包括padding、内容区的宽度，不包含边框，返回值不含单位；
- element.clientHeight:返回自身，包括padding、内容区的高度不包含边框，返回值不含单位；
- 注意：offsetWidth和clientWidth的区别就是前者包含边框，后者不含边框；

#### 10、立即执行函数：不需要调用，立即执行；

主要作用：创建一个独立的作用域，里面所有的变量均为局部变量，命名不冲突；

语法：

​		**(function(虚参) {})(实参)** 或**(function(虚参) {}(实参))** 

​		我们可以把第二个括号理解为调用过程，所以第二个括号里面写的是实参；

```js
(function(a, b) {
     console.log(a + b);
 })(1, 2); //注意如果有多个立即执行函数，中间用分号隔开，表示上下是独立的立即执行函数；
 
(function(a, b) {
     console.log(a * b);
 }(2, 3));
 
 (function sum(c, d) { //当然此处也可以不用匿名函数，直接写上函数名称；
     console.log(c / d);
 }(10, 2))
```

#### 11、元素滚动scroll系列

（1）、属性：

​		scroll翻译过来就是滚动的意思，我们利用scroll系列相关属性可以动态获得该元素的大小、滚动距离等；

- element.scrollTop:返回被卷去的上侧距离，返回值不带单位；
- element.scrollLeft:返回被卷去的左侧距离，返回值不带单位；
- element.scrollWidth:返回自身实际宽度，不含边框，返回值不带单位；
- element.scrollHeight:返回自身实际高度，不含边框，返回值不带单位；

（2）、scroll事件：

```js
var div = document.querySelector('.sc');
div.style.height = '100px';
div.style.width = '40px'
div.style.backgroundColor = 'skyblue';
div.innerHTML = `哈哈哈哈哈哈哈哈哈哈哈哈哈哈`
div.style.overflow = 'scroll';//因为是自身滚动，必须加overflow为scroll
div.addEventListener('scroll', function() {
    console.log(div.scrollTop);//触发div的滚动事件打印被滚去的高度
})
```

注意补充： 

**元素被滚去的距离用element.scrollTop和element.scrollLeft，**

**但是如果页面的滚动的距离则用window.pageXOffset和window.pageYOffset**

（3）、页面卷曲的头部兼容问题解决方案：

兼容性：

-  声明了DTD（ DTD为！ DOCTYPE） 时， 使用document.documentElement.scrollTop;
- 未声明DTD（ DTD为！ DOCTYPE） 时， 使用document.body.scrollTop;
-  新方法， 使用window.pageYoffset;
- 同理left也一样，此处就省略；

 解决兼容性代码如下：

```js
function getScroll() {
         left: window.pageXOffset || document.documentElement.scrollLeft || document.body.scrollLeft || 0,
         top: window.pageYOffset || document.documentElement.scrollTop || document.body.scrollTop || 0
    }
 }
 getScroll().left;
 // 或者
 getScroll().top;
```

  (4)、滚动窗口主文档至特定位置：window.scroll（x,y）

​		x,y不跟单位，直接写对应位置的坐标即可。

#### 12、补充鼠标事件：mouseenter事件和mouseover事件：

都是表示鼠标经过触发。

 区别：

- mouseenter只经过自身盒子才会触发，但是mouseover事件鼠标经过自身会触发，经过子盒子会再一次触发；
- 因为mouseenter不会冒泡，mouseover会冒泡；
- 跟mouseebter搭配的mouseleave鼠标离开事件，同样不会冒泡；

#### 13、动画封装：

（1）、概述：

​		通过定时器setInterval（）不断移动盒子的位置实现动画效果；

 步骤：

- 获得盒子的当前位置，offsetLeft;
-  让盒子在当前位置加上1个移动距离，element.style.left = element.offsetLeft +1;
- 利用定时器重复上面操作；
- 加一个结束定时器的条件；
- 注意元素需添加定位，才能使用element.style.left；

（2）、动画函数简单封装：

​		注意动画要添加两个参数：动画对象和移动到的距离；

下面是最初动画封装版本：

```js
//最初版本：
function animate(obj, target) {
     var timer = setInterval(function() {
                 clearInterval(timer);
             } else {
                 obj.style.left = obj.offsetLeft + 1 + 'px';
             }
        }, 15) //每15毫秒调用一次定时器；
 } //封装函数完成；

 var div = document.querySelector('.move'); //获取元素；
 var btn1 = document.querySelector('.btn_move');
 btn1.addEventListener('click', function() {
     animate(div, 1000); //调用函数；
 })
```

优化： 为什么需要优化？

​		因为按上面的代码，当有多个元素时，则每次调用函数都会库存空间生成一个同样名字的timer的变量来存储定时器，相当于开辟了很多库存空间，而且每次变量的名字还是一样的，会造成歧义，因此需要优化。

 优化点1：

​		由于我们获取的元素是变量，那么我们可以把每个定时器的名字赋值为相应元素的一个属性，如此一来每个定时器的名称都是不一样的， 即每个元素都有自己专门的定时器。

 优化点2：

​		上面是添加的按钮点击事件来控制div的动画函数，但是如果一直点击，就会一直触发定时器，就会在很短时间内重复，所以速度会很快。因此我们需要做的是，让元素只有一个定时器在执行，即每次执行定时器之前我们都需要清除之前的定时器。

优化后的代码：

```js
function animate(obj, target) {
     clearInterval(obj.timer); //清除之前的定时器；
     obj.timer = setInterval(function() { //把定时器的名字赋值为每个对象obj.timer，当实参传进来时，每个元素都有相应的obj.timer；
             if (obj.offsetLeft >= target) {
                 clearInterval(obj.timer);
             } else {
                 obj.style.left = obj.offsetLeft + 1 + 'px';
             }
         }, 15) //每15毫秒调用一次定时器；
 } //封装函数完成；

 var div = document.querySelector('.move'); //获取元素；
 var btn1 = document.querySelector('.btn_move');
 btn1.addEventListener('click', function() {
     animate(div, 1000); //调用函数；
 })
```

（3）、缓动效果原理：

​		缓动原理就是让元素运动速度有所变化，最常见的就是让速度慢慢停下来；

思路： 让盒子每次移动的距离慢慢变小，速度就会慢慢落下来；

核心算法：

- （目标值-现在位置） / 10 ，作为每次移动的距离，此处的10可以根据需求改；
- 此处比如以100为例，第一次（100-0）/10 =10,第二次（100-10）/10=9，第三次（100-19）/10=8.1 ，......
-  每次移动的距离都在变小，所以速度就慢下来了；注意js中最好不要有小数，因为小数本身就不是很精确，下面会特意提到怎么去掉；
-  停止的结束条件：让当前的盒子位置等于目标的位置就停止；

缓动效果实现：

​		下面我们在上面优化后的代码上进行缓动效果的添加：（为了达到想要效果，我们添加两个点击事件，一个到500，一个到800，显示返回移动）。

```js
function animate(obj, target) {
     clearInterval(obj.timer); //清除之前的定时器；
     obj.timer = setInterval(function() { //把定时器的名字赋值为每个对象obj.timer，当实参传进来时，每个元素都有相应的obj.timer；
         var step = (target - obj.offsetLeft) / 10; //由于要每次动态更新offsetLeft值，因此必须在定时器内部声明step变量；
         if (obj.offsetLeft == target) { //此处>=改成==，因为我们需要返回，即从800回到500，那么>号就不能让定时器停止下来；
             clearInterval(obj.timer);
         } else {
             step = step > 0 ? Math.ceil(step) : Math.floor(step);
             obj.style.left = obj.offsetLeft + step + 'px'; //把原先的1换成step；
             // 此处的step由于是小数，所以会导致实际移动位置与设计的不符，因此需要转换成整数，此处我们向上取整，例8.3取9；
             // 从左往右走没问题， 因为一直是正数， 但是当从800回到500就有问题了， 因为从800到500的过程step是负值，
             // 这个时候就不能向上取整， 得向下取整， 例 - 8.3 取 - 9；
         }
     }, 15); //每15毫秒调用一次定时器；

 } //封装函数完成；

 var div = document.querySelector('.move'); //获取元素；
 var btn500 = document.querySelector('.btn500');
 var btn800 = document.querySelector('.btn800');
 btn500.addEventListener('click', function() {
     animate(div, 500); //调用函数；
 })

 btn800.addEventListener('click', function() {
     animate(div, 800); //调用函数；
 })
```

#### 14、返回顶部：

​		window.scroll(x, y); //x y不跟单位，直接写数字，滚动到窗口相应位置；例如页面的返回顶部按键；

### 移动端网页特效

#### 15、触屏（触摸）事件：

（1）、概述：

​		 移动端不用考虑兼容问题，所以可以直接写js代码，同时可以直接用html5和css3的一些样式之类；

常见触摸事件：

-  touchstart:手指触摸到一个DOM元素触发；
-  touchmove： 手指在一个DOM元素上滑动触发；
-  touchuend:手指从一个DOM元素移开时触发；

（2）、触摸事件对象：

​		TouchuEvent是一类描述手指在触摸平面（触摸屏、触摸板等）的状态变化的事件。这类事件用于描述一个或者很多个触点，使开发者可以检测触点的移动，触点的增加或者减少等待；

-  touches:正在触摸屏幕所有手指的一个列表；
-  targetTouches:正在触摸当前DOM元素上的手指的一个列表；
- changeTouches:手指状态发生了改变的列表，从无到有，从有到无的变化；

注意：

- 一般targetTouches用的多；
-  获取其中列表的某一个手指，用索引号e.targetTouches[0],获取第一个；必须加e对象事件获取；

（3）、移动端拖动元素： 

​		我们可以用touchstart、touchmove、touchend事件拖动元素；但是拖动元素需要获取当前手指坐标值，我们可以用targetTouch[0]里面的pageX和pageY获取；记住前面要加e.

移动端拖动原理：

- 手指移动中，计算出手指移动的距离，然后用原来的位置  +  手指移动得距离；
- 手指移动得距离  =  手指滑动中的位置  -  手指开始触摸的位置；

拖动元素三部曲：

- 触摸元素touchstart:获取手指初始坐标，同时获取盒子原来的位置；
- 移动手指touchmove：计算手指的移动距离，并且移动盒子；
- 离开手指touchend;

注意：

-  获取手指最终位置时只能用e.targetTouches[索引号].pageX 或者pageY在start或者move事件中获取，不能在end事件中获取；
- touchend事件最后一定要加e.preventDefault();这段代码来清除touchend事件中默认自带的屏幕滚动事件，否则获取的坐标会不准确；
- 初始值坐标可以在touchstart事件中获取var x = e.targetTouches[0].pageX;

#### 16、移动端的常见特效：

（1）轮播图：

​		 可以用css3的translateX+过渡（transition）来进行，而不用像pc端那样用定位位置；

新事件：

​		**transitionend**，该事件为等过渡完成后再执行的事件；我们的无缝跳转是需要等过渡完成后再去判断的，可以用该事件；

（2）补充知识：classList属性

​		classList属性是HTML5新增的属性，返回元素的类名（class），但是ie10以上才支持，由于移动端不需要考虑兼容，可以直接用；该属性用于在元素中添加、移除、切换css类名；

添加类：在后面添加类名，且不会覆盖之前的类名；

```js
element.classList.add('类名'); //不需要加点；
```

 例：

```js
focus.classList.add('current');此处我们就给轮播图添加current类名；
```

移除类：

```js
element.classList.remove('类名');
```

切换类：自动判断，如果有该类名，则移除该类名，如果没有该类名则添加该类名，最好的例子就是开关灯事件；

```js
element.classList.toggle('类名');
```

#### 17、移动端click事件延时解决方案；

​		考虑到移动端双击问题因此存在300ms的延时；

 方案：

（1）、禁止缩放：`<mate name="viewport" content="user=scalable=no">`这段代码加载head处；

（2）、利用touch事件封装一个解决300ms问题函数，但是代码太多，此处不写，如有需要网上搜；

（3）、利用插件fastclick：一个js文件；

​		注意相应的插件使用规范；

#### 18、移动端常用的开发插件：

 swiper：https://www.swiper.com.cn/  轮播图，注意是引用dist内的css和js文件；一般用压缩的min文件；

 superslide: http://www.superslide2.com./  标签栏切换、轮播、文字滚动......

 iscroll: https://github.com/cubiq/iscroll  滚动

 插件使用：

-  确认插件实现的功能：
- 去官网查看使用说明；
- 下载；
- 打开demo实际文件，查看需要引入的相关文件，并且引入；
- 复制demo实际文件的结构HTML、样式css及js代码；

#### 19、移动端常用的开发框架：

​		前端常用框架：Bootstrap 、Vue 、 Angular 、React等，既能开发PC端，也能开发移动端；

​		注意Bootstrap在引入js文件之前需要引入相应jq文件才能使用；

#### 20、本地存储：

（1）、特性：

- 数据存储在用户的浏览器中；
- 设置、读取方便，甚至页面刷新也不会丢失数据； 
-  容量大，sessionStorage约5M，localStorage约20M；
-   只能存储字符串，可以将对象JSON.stringify()编码后存储；

（2）、**window.sessionStorage** ，注意window可省略；

特点：

- 生命周期为关闭浏览器窗口；
- 在同一个窗口（页面）下数据可以共享；
- 以键值对的形式存储使用；

 sessionStorage 方法：

- 存储数据：sessionStorage.setItem(key,value);注意key加引号；
- 获取数据：sessionStorage.getItem(key);注意key加引号；
- 删除数据：sessionStorage.removeItem(key);注意key加引号；
- 清空数据：sessionStorage.clear();清空所有的数据；

（3）、**window.localStorage** 注意window可省略；

特点：

- 生命周期永久生效，除非手动删除，否则关闭页面也会存在；
- 可以多窗口（页面）共享（同一浏览器可以共享）；
- 以键值对的形式存储使用；

localStorage 方法：

- 存储数据：localStorage.setItem(key,value);注意key加引号；
- 获取数据：localStorage.getItem(key);注意key加引号；
- 删除数据：localStorage.removeItem(key);注意key加引号；
- 清空数据：localStorage.clear();清空所有的数据；



## 四、关于webapi的一些案例

### 一些案例

#### 1、早中晚问候：图片切换

```html
<div>
		<img src="images/z.jpg" alt="">
		<p>早上好呀</p>
</div>
```

```js
//案例：识别现在几点钟，如果是早上，则显示早上图片加问候语，如果是下午和晚上，则分别显示下午和晚上的；
// 1、获取元素：
var img = document.querySelector('img');
var p = document.querySelector('p');
// 2、注册事件：
var date = new Date();
var h = date.getHours;
if (h < 12) {
		img.src = 'images/z.jpg';
		p.innerHTML = '早上好呀！';
} else if (h < 18) {
		img.src = 'images/x.jpg';
		p.innerHTML = '下午好呀！';
} else {
		img.src = 'images/w.jpg';
		p.innerHTML = '晚上好呀！';
}
```

#### 2、点击按钮切换背景：排他思想

```html
<button>按钮</button>
<button>按钮</button>
<button>按钮</button>
<button>按钮</button>
<button>按钮</button>
```

```js
// 案例：鼠标点击某个按钮，该按钮背景颜色变成粉红色，其余依旧保持灰色；
// 分析：
// 1、 由于有多个button， 因此势必要用到for循环， 将每个button的点击事件都改变背景色；
// 2、 由于当点击某个button改变颜色时， 需要再次要求其余背景颜色不变， 因此要再一次用for循环， 即双重for循环；
// 3、 保证自己改变， 其他不变， 即排他思想；
// 代码如下：
// 1、获取事件
var btns = document.getElementsByTagName('button');
// 2、注册事件
for (var i = 0; i < btns.length; i++) {
		btns[i].onclick = function() {
				for (var i = 0; i < btns.length; i++) {
						btns[i].style.backgroundColor = ''; //利用内部for循环保证其他button背景色不变
				}
				this.style.backgroundColor = 'pink'; //注意此处不能用btns[i]，因为循环是在页面打开瞬间完成的，相当于内部处理，所以无论点击哪一个，i都是等于5，因此报错；

		}
}
```

#### 3、背景切换

```css
body {
		background-repeat: no-repeat;
}

.box {
		margin: auto 0;
		margin-top: 100px;
		text-align: center;
}

img {
		width: 100px;
		height: 50px;
}
```

```html
<div class="box">
	<img src="images/1.jpg" alt="">
	<img src="images/2.jpg" alt="">
	<img src="images/3.jpg" alt="">
	<img src="images/4.jpg" alt="">
</div>
```

```js
// 案例： 点击某张图片， 改图填充为整个界面的背景图片；
// 1、获取元素
var bodys = document.body;
var imgs = document.querySelector('.box').querySelectorAll('img');
// 2、注册事件
for (i = 0; i < imgs.length; i++) {
	imgs[i].onclick = function() {
			var url = this.src; //此处我定义个一个变量接收图片路径，也可以下面url不要直接输this.src
			bodys.style.backgroundImage = 'url(' + url + ')';
	}
}
```

#### 4、表格行背景颜色改变

```css
table {
	width: 1000px;
	margin: 50px auto;
	text-align: center;
	border-collapse: collapse;
}

th {
	border: 1px solid #000;
}

td {
	border: 1px solid #000;
}

.bg {
	background-color: pink;
}
```

```html
<table cellspacing=0>
	<thead>
			<tr>
					<th>姓名</th>
					<th>年龄</th>
					<th>性别</th>
					<th>学历</th>
					<th>籍贯</th>
					<th>婚姻</th>
					<th>收入</th>
			</tr>
	</thead>
	<tbody>
			<tr>
					<td>张三</td>
					<td>16</td>
					<td>男</td>
					<td>小学</td>
					<td>江西上饶</td>
					<td>未婚</td>
					<td>10000</td>
			</tr>
			<tr>
					<td>张三</td>
					<td>16</td>
					<td>男</td>
					<td>小学</td>
					<td>江西上饶</td>
					<td>未婚</td>
					<td>10000</td>
			</tr>
			<tr>
					<td>张三</td>
					<td>16</td>
					<td>男</td>
					<td>小学</td>
					<td>江西上饶</td>
					<td>未婚</td>
					<td>10000</td>
			</tr>
			<tr>
					<td>张三</td>
					<td>16</td>
					<td>男</td>
					<td>小学</td>
					<td>江西上饶</td>
					<td>未婚</td>
					<td>10000</td>
			</tr>
			<tr>
					<td>张三</td>
					<td>16</td>
					<td>男</td>
					<td>小学</td>
					<td>江西上饶</td>
					<td>未婚</td>
					<td>10000</td>
			</tr>
	</tbody>
</table>
```

```js
// 案例：鼠标经过哪一行该行背景色变为粉红色， 离开恢复；
// 分析：
// 1、 该案例我们用calssName引进选择器样式来做；
// 2、 表头不参与变色；
// 3、 新事件： 经过 onmousemove； 离开 onmouseout；
var trs = document.querySelector('tbody').querySelectorAll('tr');
// 方法一： 新加类选择器
for (var i = 0; i < trs.length; i++) {
		trs[i].onmouseover = function() {
				this.className = 'bg';
		}
		trs[i].onmouseout = function() {
				this.className = '';
		}
}
// ----------------分割线-------------------
// 方法二： 直接根据事件不同改背景颜色：
// for (var i = 0; i < trs.length; i++) {
//     trs[i].onmouseover = function() {
//         this.style.backgroundColor = 'pink';
//     }
//     trs[i].onmouseout = function() {
//         this.style.backgroundColor = '';
//     }
// }

```

#### 5、密码显示和隐藏切换

```css
div {
	position: relative;
	width: 200px;
	height: 30px;
	overflow: hidden;
	margin: 50px auto;
	text-align: left;
	border-bottom: 1px solid #ccc;
}

input {
	outline: none;
	border: none;
	vertical-align: middle;
}

:-ms-input-placeholder {
	color: #ccc;
	font-size: 12px;
}

::-webkit-input-placeholder {
	font-size: 12px;
	color: #ccc;
}

label {
	position: absolute;
	right: 0;
	top: 0;
}

img {
	width: 30px;
	height: 30px;
	margin-top: -5px;
}
```

```html
<div>
	<input type="password" id="psd" placeholder="请输入密码">
	<label for="">
			<img src="images/2.jpg" alt="" id="eye">
	</label>
</div>

```

```js
// 案例：点击闭眼图标时，变成睁眼状态，同时密码可见，继续点击图标，又变回闭眼状态，同时密码栏隐藏文字信息；
// 分析：
// 1、获取元素：
var psd = document.getElementById('psd');
var eye = document.getElementById('eye');
var flag = 0; //引入一个变量来确认点击事件
// 2、注册事件：
eye.onclick = function() {
	if (flag == 0) {
			eye.src = 'images/1.jpg';
			psd.type = 'text';
			flag = 1;

	} else {
			eye.src = 'images/2.jpg';
			psd.type = 'password';
			flag = 0;
	}
}
```

#### 6、点击关闭二维码

```css
div {
	position: relative;
	width: 150px;
	margin: 50px auto;
	text-align: center;
	border: 1px solid #ccc;
}

span {
	position: absolute;
	padding: 0 3px;
	top: -1px;
	left: -20px;
	border: 1px solid #ccc;
	cursor: pointer;
}
```

```html
<div>
	<p>手机淘宝</p>
	<img src="images/erweima.png" alt="">
	<span>X</span>
</div>
```

```js
// 案例：点击x号，隐藏二维码；
// 1、获取事件：
var span = document.querySelector('span');
var div = document.querySelector('div');
// (var span = document.getElementsByTagName('span');
//此处之所以不用TagName是因为TagName是对象的集合，以伪数组显示，后续修改属性或者添加属性必须带上索引号或者遍历，)
// 否则无法成功注册事件，其他的还有ClassName、queryselectorAll
// (var div = document.getElementsByTagName('div');)
//此处之所以不用TagName是因为TagName是对象的集合，以伪数组显示，后续修改属性或者添加属性必须带上索引号或者遍历，
// 否则无法成功注册事件，其他的还有ClassName、queryselectorAll

// 2、注册事件：
span.onclick = function() {
		div.style.display = 'none';
}
```

#### 7、精灵图背景循环

```js
// 案例分析：用js来设置背景为精灵图片的小图标的背景循环；
// 分析：
// 1、 首先要求精灵图片本身摆放要有一定的规律， 如此才能通过循环来获取position， 如竖着放或者横着放；
// 2、其余bg属性无需更改，css中已经设定好，此处只需循环bgposition即可；
// 代码如下：
// 1、获取事件：
var spans = document.querySelectorAll('span');
// 2、注册事件：
for (var i = 0; i < spans.length; i++) {
		spans[i].style.backgroundPosition = '0 ' + -i * 56 + 'px';
}
```

#### 8、密码框错误信息提示

```css
div {
	width: 400px;
	text-align: left;
	margin: 50px auto;
}

span {
	font-size: 14px;
}

input {
	outline: none;
	margin-right: 10px;
}

i {
	font-style: normal;
	font-size: 10px;
}
```

```html
<div>
	<span>设置密码:</span>
	<input type="password" placeholder="请输入密码">
	<i></i>
</div>
```

```js
// 案例：如果用户离开密码框，里面输入的个数不是6-16，则提示信息错误，否则提示信息输入正确：
// 1、获取事件：
var psd = document.querySelector('input');
var i = document.querySelector('i');
// 2、注册事件：
psd.onblur = function() {
	if (psd.value.length < 6) {
			i.innerHTML = '密码较短，最短支持6个字符！';
			i.style.color = 'red';
	} else if (psd.value.length <= 16) {
			i.innerHTML = '密码格式正确！';
			i.style.color = 'green';
	} else {
			i.innerHTML = '密码较长，最长支持16个字符！';
			i.style.color = 'red';
	}
}
```

#### 9、新浪下拉列表（单个）

```css
ul {
	width: 70px;
	margin: 20px auto;
	padding: 0;
	text-align: center;
	list-style: none;
	background-color: #FCFCFC;
}

li {
	cursor: pointer;
}

li:hover {
	color: red;
}

.tbody {
	display: none;
}

.tbody li {
	border: 2px solid #EBBE7A;
	border-top: none;
	background-color: #fff;
}
```

```html
<ul>
	<section class="header">
			<li>微博</li>
	</section>
	<section class="tbody">
			<li>私信</li>
			<li>评论</li>
			<li>@我</li>
	</section>
</ul>
```

```js
// 案例：新浪下拉列表；
// 1、获取事件：
var ul = document.querySelector('ul');
var header = document.querySelector('.header').querySelector('li');
var tbody = document.querySelector('.tbody');
var lis = document.querySelector('.tbody').querySelectorAll('li');
// 2、注册事件：
ul.onmouseover = function() {
	header.style.backgroundColor = '#EDEEF0';
	tbody.style.display = 'block';
}
ul.onmouseout = function() {
	header.style.backgroundColor = '';
	tbody.style.display = '';
}
for (var i = 0; i < lis.length; i++) {
	lis[i].onmouseover = function() {
			this.style.backgroundColor = '#FFF5DA';
			this.style.borderLeftWidth = '1px';
	}
}
for (var i = 0; i < lis.length; i++) {
	lis[i].onmouseout = function() {
			this.style.backgroundColor = '';
			this.style.borderLeftWidth = '';
	}
}
```

#### 10、开关灯

```js
// 案例：点击开关灯按钮，实现界面的开关灯效果：
var btn = document.querySelector('button');
var ht = document.documentElement;
var flag = 0;
btn.onclick = function() {
	if (flag === 0) {
			ht.style.backgroundColor = '#000';
			flag = 1;
	} else {
			ht.style.backgroundColor = '#fff';
			flag = 0;
	}
}
```

#### 11、表单全选取消

```css
table {
	width: 300px;
	text-align: center;
	margin: 50px auto;
	border-collapse: collapse;
}

thead {
	background-color: rgb(10, 214, 163);
	color: #fff;
}

tbody {
	text-align: left;
	background-color: #eee;
}

td,
th {
	border: 1px solid #ccc;
}

tbody td {
	padding-left: 10px;
}
```

```html
<table>
	<thead>
			<tr>
					<th><input type="checkbox" id="all"></th>
					<th>商品</th>
					<th>价格</th>
			</tr>
	</thead>
	<tbody>
			<tr>
					<td><input type="checkbox" class="choose"></td>
					<td>iphone8</td>
					<td>8000</td>
			</tr>
			<tr>
					<td><input type="checkbox" class="choose"></td>
					<td>ipad pro</td>
					<td>5000</td>
			</tr>
			<tr>
					<td><input type="checkbox" class="choose"></td>
					<td>ipad air</td>
					<td>2000</td>
			</tr>
			<tr>
					<td><input type="checkbox" class="choose"></td>
					<td>apple watch</td>
					<td>2000</td>
			</tr>
	</tbody>
</table>
```

```js
// 案例： 上面一个打钩， 下面四个自动打钩， 上面勾去掉， 下面四个自动去掉， 下面四个全部勾选时， 全选才会被勾选；
// 另外经过下面的行时背景颜色改变；
// 1、获取事件：
var all = document.getElementById('all');
var choose = document.getElementsByClassName('choose');
var td = document.querySelector('tbody').querySelectorAll('td');
// 2、注册事件：
// （1）、先设定上面全选按钮事件，下面的整体和全选对应：
all.onclick = function() {
		console.log(all.checked); //可以测试到all.checked的返回值是true和false；
		for (var i = 0; i < choose.length; i++) {
				// -------------分隔符------------
				// if (all.checked == true) {
				//     choose[i].checked = this.checked;
				// } else {
				//     choose[i].checked = false;
				// } //该if...else判定方式也可以换成choose[i].checked=this.checked，即直接等于就行；如下；
				// -------------分隔符------------
				choose[i].checked = this.checked;
		}
}
// （2）、设定下面按钮的事件：
for (var i = 0; i < choose.length; i++) {
		choose[i].onclick = function() {
				var flag = true;
				//每次点击都要检测下面所有复选框是否都选中：
				for (var i = 0; i < choose.length; i++) {
						if (!choose[i].checked) { //任何一个只要是勾选了，取反就是false，进入下一个循环，不改变flag值，若有没勾选则flag改为false；
								flag = false;
						}
				}
				all.checked = flag;
		}
}
```

#### 12、tab栏切换

```css
* {
	padding: 0;
	margin: 0;
}

ul {
	list-style: none;
}

.tap {
	width: 1000px;
	margin: 20px auto;
}

.tab_list {
	overflow: hidden;
	background-color: #F1F1F1;
	margin-bottom: 15px;
}

.tab_list ul li {
	float: left;
	padding: 10px 20px;
	cursor: pointer;
}

.current {
	color: #fff;
	background-color: #C81623;
}

.item {
	display: none;
}
```

```html
<div class="tap">
		<div class="tab_list">
				<ul>
						<!-- ----方法一：直接在html里面添加新属性date-index------>
						<!-- <li class="current" data-index="0">商品介绍</li>
						<li data-index="1">规格与包装</li>
						<li data-index="2">售后保障</li>
						<li data-index="3">商品评价（50000）</li>
						<li data-index="4">手机社区</li> -->
						<!--  -->
						<!-- -------------分割线------------ -->
						<!--  -->
						<!-- ----方法二：不在html内添加新属性，date-index属性在js里面添加------>
						<li class="current">商品介绍</li>
						<li>规格与包装</li>
						<li>售后保障</li>
						<li>商品评价（50000）</li>
						<li>手机社区</li>
				</ul>
		</div>
		<div class="tab_com">
				<div class="item" style="display:block">介绍板块</div>
				<div class="item">规格包装板块</div>
				<div class="item">售后服务板块</div>
				<div class="item">商品购物评价板块</div>
				<div class="item">手机交流沟通社区板块</div>
		</div>
</div>
```

```js
// 方法一：在html里面添加新属性data-index，用来定位点击li时，显示信息的对应item序号：
// ///上面tab_list栏(current事件)
// // 1、 获取事件:
// var tab_list = document.querySelector('.tab_list');
// var lis = document.querySelectorAll('li');
// var tap_com = document.querySelector('.tab_com');
// var items = tap_com.querySelectorAll('.item');
// // 2、注册事件:
// for (var i = 0; i < lis.length; i++) {
//     lis[i].onclick = function() {
//         for (var i = 0; i < lis.length; i++) {
//             lis[i].className = '';
//         }
//         this.className = 'current';
//         ///tab_com栏显示隐藏
//         var index = this.getAttribute('data-index'); //给tab_list的li添加新属性，用来定位点击哪个li，下面的相应序号item显示，其余已经按排他思想隐藏
//         for (var i = 0; i < items.length; i++) {
//             for (var i = 0; i < items.length; i++) {
//                 items[i].style.display = 'none';
//             }
//             items[index].style.display = 'block';
//         }
//     }
// }
//
// ----------------分割线-------------------
// 方法二：不在html内添加新属性，data-index属性在js里面添加，用来定位点击li时，显示信息的对应item序号：
///上面tab_list栏(current事件)
// 1、 获取事件:
var tab_list = document.querySelector('.tab_list');
var lis = document.querySelectorAll('li');
var tap_com = document.querySelector('.tab_com');
var items = tap_com.querySelectorAll('.item');
// 2、注册事件:
for (var i = 0; i < lis.length; i++) {
		// console.log(lis[i].getAttribute('date-index'));//此条代码用来测试获取方法一中的data-index属性值序号，从而确定用js新增属性而不用html
		lis[i].setAttribute('data-index', i); //此条代码就是用js新增lis的每个li的data-index属性；
		lis[i].onclick = function() {
				for (var i = 0; i < lis.length; i++) {
						lis[i].className = '';
				}
				this.className = 'current';
				///tab_com栏显示隐藏
				var index = this.getAttribute('data-index'); //此条代码为引进index变量来返回date-index的属性值，以便于下面索取；
				// var index = dataset.index;
				// console.log(this.dataset.index);
				for (var i = 0; i < items.length; i++) {
						for (var i = 0; i < items.length; i++) {
								items[i].style.display = 'none';
						}
						items[index].style.display = 'block'; //索取lis中点击时的index-date序号，即点击的是哪个li;
				}
		}
}
```

#### 13、新浪下拉列表（多个）

```css
* {
	margin: 0;
	padding: 0;
}

ul {
	list-style: none;
	font-size: 14px;
}

.nav {
	width: 1000px;
	margin: 10px auto;
}

.nav>li {
	position: relative;
	float: left;
	width: 50px;
	margin-right: 5px;
}

.nav>li>ul {
	position: absolute;
	text-align: left;
	display: none;
}

.nav>li>ul>li {
	width: 80px;
	font-size: 12px;
	border: 1px solid #ccc;
}
```

```html
<ul class="nav">
		<li>
				<a href="#">微博</a>
				<ul>
						<li>私信</li>
						<li>评论</li>
						<li>@我</li>
				</ul>
		</li>
		<li>
				<a href="#">博客</a>
				<ul>
						<li>博客评论</li>
						<li>未读提醒</li>
				</ul>
		</li>
		<li>
				<a href="#">邮箱</a>
				<ul>
						<li>免费邮箱</li>
						<li>VIP邮箱</li>
						<li>企业邮箱</li>
						<li>新浪邮箱客户端</li>
				</ul>
		</li>
</ul>
```

```js
var nav = document.querySelector('.nav');
var lis = nav.children;
for (var i = 0; i < lis.length; i++) {
		lis[i].onmouseover = function() {
				this.children[1].style.display = 'block';
		}
		lis[i].onmouseout = function() {
				this.children[1].style.display = 'none';
		}
}
```

#### 14、留言板

```css
* {
	padding: 0;
	margin: 0;
}

textarea {
	margin-left: 50px;
	outline: none;
}

li {
	width: 400px;
	list-style: none;
	background-color: pink;
	font-size: 14px;
	margin: 5px 10px;
}

a {
	float: right;
}
```

```html
<textarea name="" id="" cols="30" rows="10"></textarea>
<button>确定</button>
<ul></ul>
```

```js
var text = document.querySelector('textarea');
var btn = document.querySelector('button');
var ul = document.querySelector('ul');
// 设置留言事件：
btn.onclick = function() {
		if (text.value != '') {
				var li = document.createElement('li');
				// 设置敏感词过滤事件，用正则表达式的replace（/表达式/[switch],replacement）替换方法：
				li.innerHTML = text.value.replace(/激情|gay/g, '**') + '<a href="javascript:;">删除</a>';
				ul.insertBefore(li, ul.children[0]);
				text.value = '';
		} else {
				alert('请重新输入，不能为空');
		}
		var as = document.querySelectorAll('a'); //a不能在外面获取，因为预解析，未点击的话a还没生成，直接在外面var是没用的
		for (var i = 0; i < as.length; i++) {
				as[i].onclick = function() {
						ul.removeChild(this.parentNode);
				}
		}
}
```

#### 15、新增表单

```css
table {
	border-collapse: collapse;
	margin: 10px auto;
}

th {
	width: 100px;
	border: 1px solid #000;
}

td {
	text-align: center;
	border: 1px solid #000;
}
```

```html
<table>
		<tr>
				<th>姓名</th>
				<th>科目</th>
				<th>成绩</th>
				<th>操作</th>
		</tr>
</table>
```

```js
// 案例：新增表单，并附加a链接的删除键；
// 1、获取元素：
var tb = document.querySelector('table');
var datas = [{
		name: '离职帝',
		subject: 'javascript',
		score: '100'
}, {
		name: '福建老吴',
		subject: 'java',
		score: '70'
}, {
		name: '重庆枫叶',
		subject: 'css',
		score: '90'
}, {
		name: '海南鸡仔',
		subject: 'C语言',
		score: '20'
}];
for (var i = 0; i < datas.length; i++) { //外for循环生成行
		var trs = document.createElement('tr');
		tb.appendChild(trs);
		for (var k in datas[i]) { //内部for循环获取数组里面的对象属性值，同时生成列，并把属性值赋值给列
				var tds = document.createElement('td');
				tds.innerHTML = datas[i][k];
				trs.appendChild(tds);
		}
		//单独创建删除选项
		var del = document.createElement('td');
		del.innerHTML = '<a href="javascript:;">删除</a>';
		trs.appendChild(del);
}
//由于上面并不是点击事件，因此按顺序下来，此处已经生成了a，因此可以直接获取a元素
var as = document.querySelectorAll('a');
for (var i = 0; i < as.length; i++) {
		as[i].addEventListener('click', fn)

		function fn() {
				tb.removeChild(this.parentNode.parentNode);
		}
}
```

#### 16、京东倒时器

```css
section {
		width: 500px;
		height: 150px;
}

div {
		float: left;
		width: 100px;
		height: 50px;
		line-height: 50px;
		border: 1px solid #ccc;
		margin: 20px;
		text-align: center;
		vertical-align: middle;
		font-size: 20px;
		font-weight: 700;
		color: chocolate;
}
```

```html
<section>
		<div></div>
		<div></div>
		<div></div>
</section>
```

```js
// 案例：制作京东倒计时案例；
window.addEventListener('load', function() { //设置window页面加载；
		countDown(); //先调用一次该函数，这样刷新时就不会因为计时器有一秒的延迟而产生空白；
		setInterval(countDown, 1000); //调用计时器；

		function countDown() {
				var nowTime = +new Date(); //获取总的毫秒数；
				var inputTime = +new Date('2020-8-31 00:00:00'); //获取截止时间的总的毫秒数；
				var times = parseInt((inputTime - nowTime) / 1000);
				// console.log(times);
				var s = parseInt(times % 60);
				s = s < 10 ? '0' + s : s;
				var m = parseInt(times / 60 % 60);
				m = m < 10 ? '0' + m : m;
				var h = parseInt(times / 60 / 60 % 24);
				h = h < 10 ? '0' + h : h;
				// console.log(times);
				// console.log(s);
				// console.log(m);
				// console.log(h);
				var sec = document.querySelector('section');
				sec.children[0].innerHTML = h;
				sec.children[1].innerHTML = m;
				sec.children[2].innerHTML = s;
		}
})
```

#### 17、发送验证码

```html
<input type="text" placeholder="请输入验证码"> <button>发送</button>
```

```js
var btn = document.querySelector('button');
var times = 10;
btn.addEventListener('click', function() {
		btn.disabled = true;
		var timer = setInterval(function() {
				if (times == 0) {
						clearInterval(timer);
						btn.disabled = false;
						btn.innerHTML = '发送';
						times = 10;
				} else {
						times--;
						btn.innerHTML = '还有' + times + '秒';
				}
		}, 1000)
})
```

#### 18、五秒后页面跳转

```html
<div></div>
<button>跳转</button>
```

```js
var btn = document.querySelector('button');
btn.addEventListener('click', function() {
		location.assign('https://www.hao123.com/');
});
var div = document.querySelector('div');
var times = 5;
setInterval(function() {
				if (times == 0) {
						location.assign('https://www.hao123.com/');
				} else {
						div.innerHTML = '还剩' + times + '秒跳转';
						times--;
				}
		},
		1000)
```

#### 19、页面交互：获取URL参数信息

登录页面：login.html 

```html
<div>登录页面</div>
<span>用户名：</span>
<form action="index.html">
		<input type="text" name="username" id="user" autocomplete="off">
		<input type="submit" name="" id="" value="登录">
</form>
```

主页：index.html

```html
<div>首页</div>
<div class="in"></div>
```

```js
var div = document.querySelector('.in');
var user = location.search; //获取整个URL的参数；
console.log(user);
var one = user.substr(1); //截取user参数去掉？后面的字符串；
console.log(one);
var two = one.split('='); //把字符串转换成数组；
console.log(two);
var gets = two[1];
div.innerHTML = gets + ' 欢迎您！';
```

#### 20、页面交互：跳转、前进、后退

首页：history_index.html

```html
<button class="one">跳转</button>
<button class="two">前进</button>
```

```js
var btn1 = document.querySelector('.one');
var btn2 = document.querySelector('.two');
btn1.addEventListener('click', function() {
		location.href = 'history-list.html';
});
btn2.addEventListener('click', function() {
		history.forward();
})
```

列表页：history-list.html

```html
这个列表页
<button class="three">后退</button>
```

```js
var btn3 = document.querySelector('button');
btn3.addEventListener('click', function() {
		history.back();//后退
})
```

#### 21、点击显示鼠标在盒子中的坐标

```css
* {
		margin: 0;
		padding: 0;
}

div {
		width: 200px;
		height: 200px;
		background-color: pink;
		margin: 50px;
}
```

```html
<div></div>
```

```js
var div = document.querySelector('div');
document.addEventListener('click', function(e) {
		var x = e.pageX - div.offsetLeft; //相对于div的左边x等于鼠标相对于文档页面的x 减去 div相对于body的左距离；
		var y = e.pageY - div.offsetTop; //相对于div的左边y等于鼠标相对于文档页面的y 减去 div相对于body的上距离；
		console.log(x);
		console.log(y);
		div.innerHTML = 'x坐标是' + x + ',' + 'y坐标是' + y;
})
//注意使用offsetLeft和offsetTop是相对于带有定位的父盒子的左偏移和上偏移，如果没有此处则以body为准
```

#### 22、模态框拖拽

案例:模态框的拖拽

原理：

（1）、模态框内触发mousedown鼠标按下事件，获取模态框的相对于body的位置，及鼠标按下时的位置，得到差值；

（2）、在mousedown事件内再触发document的mousemove事件（因为整个文档页面都可以进行鼠标的移动），获取鼠标移动时的位置；

（3）、用鼠标移动时的位置减去（1）中的差值（该差值即为鼠标在模态框内的位置），得到模态框最终相对body的位置（注意把该值赋值给模态框的定位left和top来控制模态框的实时移动，同时注意offset值和page值是不带单位的，left需要加px单位）；

（4）、再继续在mousedown事件内触发mouseup事件（鼠标松开），松开的同时移除（3）中的鼠标移动事件，使得模态框的实时移动停止；

```html
<div class="login"></div>
```

```js
const login = document.querySelector('.login')
		// 1、注册在模态框内的鼠标按下mousedown事件
login.addEventListener('mousedown', (e) => {
		// 获取鼠标在模态框内的位置
		let login_x = e.pageX - login.offsetLeft
		let login_y = e.pageY - login.offsetTop
				// 2、注册鼠标移动事件
		document.addEventListener('mousemove', move)
				// 移动调用事件单独写，因为下面移除该事件时也需要用
		function move(e) {
				login.style.left = e.pageX - login_x + 'px'
				login.style.top = e.pageY - login_y + 'px'
		}
				//3、注册鼠标松开事件
		login.addEventListener('mouseup', () => {
				// 移动鼠标移动事件
				document.removeEventListener('mousemove', move)
		})
})
```

#### 23、放大镜效果

案例：设置类似淘宝图片放大镜效果

原理：

（1）、鼠标进入box_small内，遮挡框和大图框box_big显示；

（2）、鼠标离开box_small时，遮挡框和大图框box_big隐藏；

（3）、鼠标在box_small内移动时注册mousemove事件，获取遮挡框的位置；

（4）、鼠标在box内的位置为e.pageX - box_small.offsetLeft，遮挡框的位置为鼠标位置再减去盒子自身大小的一半，即减去bg.offsetWidth,对应高度同理；

（5）、将遮挡框位置赋值给对应的定位left和top，需要注意遮挡框的坐标有最大值和最小值，即有位置限制；

（6）、针对左侧的遮挡框的移动距离对应右侧大图的移动距离，成比例，对应的是两者的最大移动距离和实际移动距离成比例。

```css
.img1 {
	position: absolute;
	left: 0;
	top: 0;
	width: 720px;
	vertical-align: top;
}

.img2 {
	width: 180px;
	vertical-align: middle;
}

.box_small {
	position: absolute;
	left: 100px;
	top: 100px;
	width: 180px;
}

.bg {
	display: none;
	position: absolute;
	left: 0;
	top: 0;
	width: 90px;
	height: 160px;
	background-color: pink;
	opacity: .6;
}
/* 大盒子设置为小图片的大小，溢出隐藏 */

.box_big {
	display: none;
	position: absolute;
	left: 400px;
	top: 100px;
	width: 180px;
	height: 320px;
	overflow: hidden;
}
```

```html
<!-- 左边小盒子 -->
<div class="box_small">
		<!-- 图2设置为：180 * 320 -->
		<img src="./桌面壁纸/测试2.jpg" alt="" class="img2">
		<!-- 遮挡框 -->
		<div class="bg"></div>
</div>
<!-- 右边大盒子 -->
<div class="box_big">
		<!-- 图1设置为：720 * 1280 -->
		<img src="./桌面壁纸/测试1.jpg" alt="" class="img1">
</div>
```

```js
const box_small = document.querySelector('.box_small')
const bg = document.querySelector('.bg')
const box_big = document.querySelector('.box_big')
const box_big_img = document.querySelector('.img1')
// 1、注册小盒子内鼠标经过事件
box_small.addEventListener('mouseover', (e) => {
// 鼠标经过box_small时显示遮挡框和box_big
bg.style.display = 'block'
box_big.style.display = 'block'
})
// 2、注册鼠标离开事件
box_small.addEventListener('mouseout', () => {
bg.style.display = 'none'
box_big.style.display = 'none'
})
// 3、注册鼠标在box_small内的移动事件
box_small.addEventListener('mousemove', (e) => {
// 获取鼠标在box_small内的坐标
let mouse_x = e.pageX - box_small.offsetLeft
let mouse_y = e.pageY - box_small.offsetTop
let bg_x = mouse_x - (bg.offsetWidth / 2)
let bg_y = mouse_y - (bg.offsetHeight / 2)
// 设置遮挡框在box_small的位置限制条件：
if (bg_x < 0) {
		bg_x = 0
} else if (bg_x >= (box_small.offsetWidth - bg.offsetWidth)) {
		bg_x = box_small.offsetWidth - bg.offsetWidth
}
if (bg_y < 0) {
		bg_y = 0
} else if (bg_y >= (box_small.offsetHeight - bg.offsetHeight)) {
		bg_y = box_small.offsetHeight - bg.offsetHeight
}
console.log(bg_y);
console.log(bg_x);
// 设置遮挡框在box_small内的位置
bg.style.left = bg_x + 'px'
bg.style.top = bg_y + 'px'
// box_big内图片的移动(注意是按比例移动，小图最大移动的比例=大图最大移动的比例，小图移动的距离可以用模态框的位置确定)
// 小图移动距离 / 小图最大移动距离 = 大图移动距离 /大图最大移动距离 
// 注意是按最大移动距离来算比例的不是图片宽度高度来算
let move_x = bg_x * (box_big_img.offsetWidth - box_big.offsetWidth) / (box_small.offsetWidth - bg.offsetWidth)
let move_y = bg_y * (box_big_img.offsetHeight - box_big.offsetHeight) / (box_small.offsetHeight - bg.offsetHeight)
box_big_img.style.left = -move_x + 'px'
box_big_img.style.top = -move_y + 'px'
})
```

