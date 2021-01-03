---
title: JavaScript变量、数组
date: 2021-01-02 19:22:59
tags: js
swiper: true
swiperImg: '/medias/3.jpg'
top: true
categories: JavaScript
---
# JS变量、数组

## 一，变量
1.ECMAScript的变量是松散型变量。
*松散型变量：可以用来保存任何类型的数据，换句话来说，每个变量仅仅是一个用于保存的占位符而而已。
*定义变量要是用var操作符。（var是一个关键字），后跟变量名（既是一个标识符）。
如下：
```javascript
var message;
```
*改代码就是定义了一个名字为message的变量，该变量可以保存任何类型的数据。
**注意：**_既用var操作符定义的变量将成为该变量的作用域的局部变量。_
如果在函数中使用var定义一个变量，那么这个变量在函数退出后就会被销毁。
例如_;_
错误例子：
```javascript
function test(){
  var message="hi";//局部变量
}
test();
alert(message);//错误
```
正确例子：
```javascript
function test(){
  var message="hi";
  alert(message);
}
test();
```
## 二.数据类型
1.ECMAScript中有**5中简单的数据类型（也称为基本数据类型）**；
**5种数据类型:Undefind,NULL,Boolean,Number,String.**
*****还有一种复杂的数据类型：**Object，**（Object 本质上是由一组无序的名值对组成的。ECMAScript
不支持任何创建自定义类型的机制，而所有值最终都将是上述 6 种数据类型之一。）
1.注意：对为声明的变量，执行typeof操作符都返回了undefined值。
_即便未初始化的变量会自动被赋予 undefined 值，但显式地初始化变量依然是_
_明智的选择。如果能够做到这一点，那么当 typeof 操作符返回 "undefined" 值时，_
_我们就知道被检测的变量还没有被声明，而不是尚未初始化。_
如：
```javascript
var message; // 这个变量声明之后默认取得了 undefined 值
// 下面这个变量并没有声明
// var age
alert(typeof message); // "undefined"
alert(typeof age); // "undefined"
```
## 三.字符串
1.要把多个字符串连起来可以用+号链接；
2.如果变量需要连接，用+号就比较麻烦，ES6新增一种模板字符串，表示方法：


```javascript
var name="小明";
var age=20;
var message='你好,${name},你今年${age}岁了！';
alert(message);
```


#### 3.toUpperCase
toUpperCase()把一个字符串全部变成大写：


```javascript
var s="Hello";
s.toUpperCase();//\返回“HELLO”
```


#### 4.toLowerCase
toLowerCAse()把一个字符串全变成小写：


```javascript
var s="HELLO";
s.toLowerCase();//返回“hello”
```


#### 5.indexOf
indexOf()会搜索指定的字符串出现的位置：


```javascript
var s="hello,word";
s.indexOf("world");//返回7
s.indexOf("World");//没有找到的字符串，返回-1
```




#### 6.substring
substring()返回指定索引区间的字符串：


```javascript
var s="hello,word";
s.substring(0,5);//从索引0开始到5（不包括5），返回“hello”
s.substring(7);//从索引7开始到结束，返回“world”
```


## 四.数组
1.在js中数组可以包含任何类型的数据类型，并通过索引来访问每个元素。
取得他的长度直接访问length属性：


```javascript
var arr=[1,2,3,14,"hello",null,true];
arr.length;//6
```


注意：如果给arr.length附一个新的值会导致arr大小变化


```javascript
var arr = [1, 2, 3];
arr.length; // 3
arr.length = 6;
arr; // arr变为[1, 2, 3, undefined, undefined, undefined]
arr.length = 2;
arr; // arr变为[1, 2]
```


#### 2.indexOf
与String类似，arr也可以通过indexOf()来搜索一个指定的元素的位置：


```javascript
var arr = [10, 20, '30', 'xyz'];
arr.indexOf(10); // 元素10的索引为0
arr.indexOf(20); // 元素20的索引为1
arr.indexOf(30); // 元素30没有找到，返回-1
arr.indexOf('30'); // 元素'30'的索引为2
```


#### 3.slice
slice()就是对应String的substring（）版本，他截取arr的部分元素，然后返回一个新的arr：


```javascript
var arr = ['A', 'B', 'C', 'D', 'E', 'F', 'G'];
arr.slice(0, 3); // 从索引0开始，到索引3结束，但不包括索引3: ['A', 'B', 'C']
arr.slice(3); // 从索引3开始到结束: ['D', 'E', 'F', 'G']
```
注意：slice()的起止包括开始不包括结束。
如果不给slice（）传递参数，他就会从头到结尾截取所有的元素。利用这一点，可以容易的复制一个arr:


```javascript
var arr = ['A', 'B', 'C', 'D', 'E', 'F', 'G'];
var aCopy = arr.slice();
aCopy; // ['A', 'B', 'C', 'D', 'E', 'F', 'G']
aCopy === arr; // false
```


#### 4.push和pop
push()向arr的末尾添加若干元素，
pop()则把arr得最后一个元素删掉：


```javascript
var arr = [1, 2];
arr.push('A', 'B'); // 返回Array新的长度: 4
arr; // [1, 2, 'A', 'B']
arr.pop(); // pop()返回'B'
arr; // [1, 2, 'A']
arr.pop(); arr.pop(); arr.pop(); // 连续pop 3次
arr; // []
arr.pop(); // 空数组继续pop不会报错，而是返回undefined
arr; // []
```


#### 5.unshift和shift
unshift()在arr头部添加若干元素。
shift()在arr的第一个元素删掉。

```javascript
var arr = [1, 2];
arr.unshift('A', 'B'); // 返回Array新的长度: 4
arr; // ['A', 'B', 1, 2]
arr.shift(); // 'A'
arr; // ['B', 1, 2]
arr.shift(); arr.shift(); arr.shift(); // 连续shift 3次
arr; // []
arr.shift(); // 空数组继续shift不会报错，而是返回undefined
arr; // []
```


#### 6.sort
sort()可以对当前arr进行排序，他会直接修改arr的元素位置，直接调用时，按照默认顺序：


```javascript
var arr = ['B', 'C', 'A'];
arr.sort();
arr; // ['A', 'B', 'C']
```




#### 7.reverse
reverse()把整个arr的元素给掉个个，颠倒一下：


```javascript
var arr = ['one', 'two', 'three'];
arr.reverse(); 
arr; // ['three', 'two', 'one']
```


#### 8.splice
splice()可以从指定的索引开始删除若干个元素，然后从该位置添加若干个元素：


```javascript
var arr = ['Microsoft', 'Apple', 'Yahoo', 'AOL', 'Excite', 'Oracle'];
// 从索引2开始删除3个元素,然后再添加两个元素:
arr.splice(2, 3, 'Google', 'Facebook'); // 返回删除的元素 ['Yahoo', 'AOL', 'Excite']
arr; // ['Microsoft', 'Apple', 'Google', 'Facebook', 'Oracle']
// 只删除,不添加:
arr.splice(2, 2); // ['Google', 'Facebook']
arr; // ['Microsoft', 'Apple', 'Oracle']
// 只添加,不删除:
arr.splice(2, 0, 'Google', 'Facebook'); // 返回[],因为没有删除任何元素
arr; // ['Microsoft', 'Apple', 'Google', 'Facebook', 'Oracle']
```


#### 9.concat
concat()把当前的arr和另一个arr链接起来，并返回新的arr：


```javascript
var arr = ['A', 'B', 'C'];
var added = arr.concat([1, 2, 3]);
added; // ['A', 'B', 'C', 1, 2, 3]
arr; // ['A', 'B', 'C']
```
注意：concat()并没有修改当前的arr，反而返回了一个新的arr。
实际上，concat()方法可以接受任意个元素和arr，并自动吧arr拆开，然后全部添加到新的arr里


```javascript
var arr = ['A', 'B', 'C'];
arr.concat(1, 2, [3, 4]); // ['A', 'B', 'C', 1, 2, 3, 4]
```


#### 10.join 
join()把当前的arr的每个元素都用指定的字符串链接起来，然后返回链接后的字符串。


```javascript
var arr = ['A', 'B', 'C', 1, 2, 3];
arr.join('-'); // 'A-B-C-1-2-3'
```




#### 11.多维数组
如果数组的某个元素又是一个arr，则可以形成多维数组


```javascript
var arr = ['A', 'B', 'C', 1, 2, 3];
arr.join('-'); // 'A-B-C-1-2-3'
```


#### 12.filter
把超过数组中超过2000的去掉，filter主要是返回了一个新的数组。
```javascript
    var arr = [1500,1200,2000,2100,1800];
    var newArr=arr.filter(function(item){
        return item < 2000;
    })
    console.log(newArr);
```


