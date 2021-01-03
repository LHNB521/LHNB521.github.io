---
title: JavaScript数组去重
date: 2020-12-30 16:15:57
swiper: true
swiperImg: 'https://ssyerv1.oss-cn-hangzhou.aliyuncs.com/picture/c080ff4434354e35af9dab0a3ee1b9f7.jpg!sswm'
top: true
tags: js
categories: JavaSctipt
---
# JavaScript数组去重

数组去重，一般都是在面试题上看到，一般是要求手写数组去重方法的代码。如果被提问到数组去重的方法有哪些？如果你能回答出十种方法，面试官可能会对你刮目相看。
在真实的项目中碰到的数组去重，一般都是后台去处理，很好让前端处理数组去重。虽然日常项目用到的概率比降低，但还是需要了解一下，以防面试的时候可能回被问到。


## 数组去重方法


### 一、利用ES6 Set去重（ES6中最常用）


```javascript
function unique(arr){
	return Array.from(new Set(arr))
}
var arr=[1,1,'true','true',true,true,15,15,false,false, undefined,undefined, null,null, NaN, NaN,'NaN', 0, 0, 'a', 'a',{},{}];
console.log(unique(arr))
//[1, "true", true, 15, false, undefined, null, NaN, "NaN", 0, "a", {}, {}]
```


**注：不考虑兼容性，这种去重的方法代码最少。这种方法还是无法去掉“{}”空对象，后面的高级方法会添加去掉重复的“{}”的方法。**


### 二、利用for嵌套for，然后splice去重（ES5中最常用）


```javascript
function unique(arr){
	for(var i=0;i<arr.length;i++){
		for(var j=i+1;j<arr.length;j++){
			if(arr[i]==arr[j]){
				arr.splice(j,1);
				j--;
			}
		}
	}
	return arr;
}
var arr=[1,1,'true','true',true,true,15,15,false,false, undefined,undefined, null,null, NaN, NaN,'NaN', 0, 0, 'a', 'a',{},{}];
console.log(arr)
//[1, "true", 15, false, undefined, NaN, NaN, "NaN", "a", {…}, {…}]     //NaN和{}没有去重，两个null直接消失了
```


**双层循环，外层循环元素，内层循环时比较值。值相同时，则删除这个值。**


### 三、利用indexOf去重


```javascript
function unique(arr){
	if(!Array.isArray(arr)){
		console.log('不是数组')
		return
	}
	var array=[];
	for(var i=0; i<arr.length;i++){
		if(array.indexOf(arr[i])==-1){
			array.push(arr[i])
		}
	}
	return array;
}
var arr = [1,1,'true','true',true,true,15,15,false,false, undefined,undefined, null,null, NaN, NaN,'NaN', 0, 0, 'a', 'a',{},{}];
console.log(unique(arr))
// [1, "true", true, 15, false, undefined, null, NaN, NaN, "NaN", 0, "a", {…}, {…}]  //NaN、{}没有去重
```


**新建一个空的结果数组，for循环原数组，判断结果数组是否存在当前元素，如果有相同的值则跳过，不相同则push进树组。**


### 四、利用sort()


```javascript
function unique(arr){
	if(!Array.isArray(arr)){
		console.log('不是数组')
		return
	}
	arr = arr.sort()
	var array = [arr[0]];
	for(var i =1; i<arr.length; i++){
		if(arr[i]!==arr[i-1]){
			array.push(arr[i])
		}
	}
	return array
}
var arr = [1,1,'true','true',true,true,15,15,false,false, undefined,undefined, null,null, NaN, NaN,'NaN', 0, 0, 'a', 'a',{},{}];
console.log(unique(arr))
// [0, 1, 15, "NaN", NaN, NaN, {…}, {…}, "a", false, null, true, "true", undefined]      //NaN、{}没有去重
```


**利用sort()排序方法，然后根据排序后的结果进行遍历及相邻元素比对。**


### 五、利用includes


```javascript
function unique(arr){
    if(!Array.isArray(arr)){
    	return 
    }
    var array= [];
    for(var i=0;i<arr.length;i++){
    	if(!array.includes(arr[i])){
    		array.push(arr[i]);
    	}
    }
    return array;
}
var arr = [1,1,'true','true',true,true,15,15,false,false, undefined,undefined, null,null, NaN, NaN,'NaN', 0, 0, 'a', 'a',{},{}];
console.log(unique(arr))
//[1, "true", true, 15, false, undefined, null, NaN, "NaN", 0, "a", {…}, {…}]     //{}没有去重
```


### 六、利用hasOwnProperty


```javascript
function unique(arr){
	var obj = {};
	return arr.filter(function(item,index,arr){
		return obj.hasOwnProperty(typeof item+item)?fasle : (obj[typeof item + item]=true)
	})
}
var arr = [1,1,'true','true',true,true,15,15,false,false, undefined,undefined, null,null, NaN, NaN,'NaN', 0, 0, 'a', 'a',{},{}];
        console.log(unique(arr))
//[1, "true", true, 15, false, undefined, null, NaN, "NaN", 0, "a", {…}]   //所有的都去重了
```


**利用hasOwnPeoperty判断是否存在对象属性**


### 七、利用filter


```javascript
function unique(arr){
	return arr.filter(function(item,index,arr){
		//当前元素，在原始数组中的第一个索引==当前索引，否则返回当前元素
		return arr.indexOf(item,0)===index;
	});
}
var arr = [1,1,'true','true',true,true,15,15,false,false, undefined,undefined, null,null, NaN, NaN,'NaN', 0, 0, 'a', 'a',{},{}];
console.log(unique(arr))
//[1, "true", true, 15, false, undefined, null, "NaN", 0, "a", {…}, {…}]
```


### 八、利用递归去重


```javascript
function unique(arr){
	var array=arr;
	var len=array.length;
	array.sort(function(a,b){    //排序后更加方便去重
		return a,b;
	})
	function loop(index){
		if(index>=1){
			if(array[index]===array[index-1]){
				array.splice(index,1);
			}
			loop(index,1);
		}
	}
	loop(len-1);
	return array;
}
var arr = [1,1,'true','true',true,true,15,15,false,false, undefined,undefined, null,null, NaN, NaN,'NaN', 0, 0, 'a', 'a',{},{}];
console.log(unique(arr))
//[1, "a", "true", true, 15, false, 1, {…}, null, NaN, NaN, "NaN", 0, "a", {…}, undefined]
```


### 九、利用Map数据结构去重


```javascript
function unique(arr){
	let map = new Map();
	let array = new Array();   //数组用于返回结果
	for(let i = 0; i< arr.length; i++){
		if(map.has(arr[i])){    //如果有该key值
			map.set(arr[i],true);
		}else{
		 map.set(arr[i],false);     //如果没有key值
		 array.push(arr[i]);
		}
	}
	return array;
}
var arr = [1,1,'true','true',true,true,15,15,false,false, undefined,undefined, null,null, NaN, NaN,'NaN', 0, 0, 'a', 'a',{},{}];
console.log(unique(arr))
//[1, "a", "true", true, 15, false, 1, {…}, null, NaN, NaN, "NaN", 0, "a", {…}, undefined]
```


**创建一个空的Map数据结构，遍历需要去重的数组，把数组的每一个元素作为key存到Map中。由于Map中不会出现不同的key值，所以最终得到的结果就是去重后的结果。**


### 十一、利用reduce+includes


```javascript
function unique(arr){
	return arr.reduce((prev,cur)=>prev,includes(cur)?prev:[...prev,cur],[]);
}
var arr = [1,1,'true','true',true,true,15,15,false,false, undefined,undefined, null,null, NaN, NaN,'NaN', 0, 0, 'a', 'a',{},{}];
console.log(unique(arr));
// [1, "true", true, 15, false, undefined, null, NaN, "NaN", 0, "a", {…}, {…}]
```


注：这些方法都是面试时候经常问到的JS问题应该多看啊
（end）
