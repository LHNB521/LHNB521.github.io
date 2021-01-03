---
title: JaCSS定位详解
date: 2021-01-02 19:44:54
tags: CSS
top: true
swiper: true
swiperImg: '/medias/1.jpg'
categories: CSS
---
# CSS定位详解

**CSS有个重要的基本属性，前端开发必须掌握：`display` 和`position`**
`display`属性指定网页的布局。两个重要的布局：弹性布局`flex`和网格布局`grid`。


## 一、position属性的作用


`position`属性用来指定一个元素在网页上的位置，一共有5种定位方式，即`position`属性的主要五个值。


- static
- relative
- fixed
- absolute
- sticky



## 二、static属性值


`static`是`position`属性的默认值。如果省略`position`属性，浏览器就认为该元素是`static`定位。
**注意：`static`定位所导致的元素位置，是浏览器自主决定的，所以这时`top`、`bootom`、`left`、`right`这四个属性无效。**


## 三、relative，absolute，fixed


`relative`、`absolute`、`fixed`这三个属性值有一个共同点，都是对于某个基点的定位，不同之处仅仅在于基点不同。所以，只要理解了它们的基点是什么，就很容易掌握这三个属性值。
这三种定位都不会对其他元素位置产生影响，因此元素之间可能 产生重叠。


### 3.1 relative属性值


`relative`表示，相对于默认位置（即`static`时的位置）进行偏移，即定位基点是元素的默认位置。
它必须搭配`top`、`bottom`、`left`、`right`这四个属性一起使用，用来指定偏移的方向和距离。


```html
<style>
        .a{
            width: 60px;
            height: 60px;
            background-color: aqua;
            float: left;
        }
        .b{
            width: 60px;
            height: 60px;
            background-color: rgb(47, 47, 196);
            float: left;
            position: relative;
            top: 30px;
        }
        .c{
            width: 60px;
            height: 60px;
            background-color: red;
            float: left;
        }
    </style>
<body>
    <div class="a">a</div>
    <div class="b">b</div>
    <div class="c">c</div>
</body>
```
![image.png](https://cdn.nlark.com/yuque/0/2020/png/510079/1608296918973-8fe5a7c1-e325-492f-85a2-e981336508f3.png#align=left&display=inline&height=163&margin=%5Bobject%20Object%5D&name=image.png&originHeight=325&originWidth=546&size=26548&status=done&style=none&width=273)
上面代码中，`div`元素从默认位置向下偏移`30px`(即距离顶部`30px`)。


### 3.2 absolute属性值


`absolute`表示，相对于上级元素（一般是父级元素）进行偏移，即定位基点是父元素。
它有一个重要的限制条件：定位基点（一般是父级元素）不能是`static`定位，否则定位基点就会变成整个网页的根元素`html`。另外，`absolute`定位也必须搭配`top`、`bottom`、`left`、`right`这四个属性一起使用。


```html
    <style>
        .father{
            width: 200px;
            height: 200px;
            background-color: aqua;
            position: relative;
        }
        .son{
            width: 60px;
            height: 60px;
            background-color: rgb(47, 47, 196);
            position: absolute;
            top: 40px;
        }
        
    </style>
<body>
    <div class="father">
        <div class="son">son</div>
    </div>
</body>
```
![image.png](https://cdn.nlark.com/yuque/0/2020/png/510079/1608296878970-7d3785a1-9c44-4709-a3f5-157b0afdfad6.png#align=left&display=inline&height=156&margin=%5Bobject%20Object%5D&name=image.png&originHeight=450&originWidth=722&size=30724&status=done&style=none&width=250)
上面代码中，父元素是`relative`定位，子元素是`absolute`定位，所以子元素的定位基点是父元素，相对于父元素的顶部向下偏移`40px`。如果父元素是`static`定位，上例的子元素就是距离网页的顶部向下偏移`40px`。
**注意，`absolute`定位的元素会被“正常页面流”忽略，即在“正常页面流”中，该元素所占空间为零，周边元素不受影响。**


### 3.3 fixed 属性值


`fixed`表示，相对于视口（浏览器窗口）进行偏移，即定位基点是浏览器窗口。这会导致元素的位置不随页面滚动而变化，好像固定在网页上一样。
它如果搭配`top`，`bottom`，`left`,`right`这四个属性一起使用，表示元素的初始位置是基于视口计算的，否则初始位置就是元素的默认位置。


## 四、sticky 属性值


`sticky`跟前面四个属性值都不一样，它会产生动态效果，很像`relative`和`fixed`的结合：一些时候是`relative`定位（定位基点是自身默认位置），另一些时候自动变成`fixed`定位（定位基点是视口）。
因此，它能够形成“动态固定”的效果。比如，网页的搜索工具栏，初始加载时在自己的默认位置（`relative`定位）。
页面向下滚动时，工具栏变成固定位置，始终停留在页面头部（`fixed`定位）。
等到页面重新向上滚动回到原位，工具栏也会回到默认位置。
`sticky`生效的前提是，必须搭配`top`,`bootom`,`left`,`right`这四个属性一起使用，不能省略，否则等同于`relative`定位，不产生‘动态固定’的效果。原因是这四个属性用来定义‘偏移距离’，浏览器把它当做`sticky`的生效门槛。
它的具体规则是，当页面滚动，父元素开始脱离视口时（即部分完全不可见），`fixed`定位自动切换回`relative`定位。
请看一下示例代码。（**注意：除了已被淘汰的IE以外，其他浏览器目前都支持`sticky`。但是，Safari浏览器需要加上浏览器前缀`-webkit-`。**）


```html
#toolbar{
	position:-webkit-sticky;/*safari浏览器*/
	position:sticky;       /*其他浏览器*/
	top:20px;
}
```


上面代码中，页面向下滚动时，`#toolbar`的父元素开始脱离视口，一旦视口的顶部与`#toolbar`的距离小于`20px`(门槛值），`#toolbar`就会自动变成`fixed`定位，保持与视口顶部20px的距离。页面会继续向下滚动，父元素彻底离开视口（即整个父元素完全不可见），`#toolbar`恢复成`relative`定位。
## 五、sticky 的应用
`sticky`定位可以实现一些很有用的效果。除了上面提到“动态固定”效果，还有以下用法。
### 5.1 堆叠效果


堆叠效果（stacking）指的是页面滚动时，下方的元素覆盖上方的元素。下面是一个图片堆叠的例子，下方的图片会随着页面滚动，覆盖上方图片
Html代码：
```html
<div><img src="pic1.jpg"></div>
<div><img src="pic2.jpg"></div>
<div><img src="pic3.jpg"></div>
```


css代码：
```css
div{
	position:sticky;
	top:0;
}
```


### 5.2 表格的表头锁定


Html代码：
```html
<table>
  <thead>
    <tr> <th>名字</th> <th>颜色r</th> </tr>
  </thead>
  <tbody>
    <tr> <td>Bob</td> <td>Yellow</td> </tr>
    <tr> <td>Michelle</td> <td>Purple</td> </tr>
    <tr> <td>Bob</td> <td>Yellow</td> </tr>
    <tr> <td>Michelle</td> <td>Purple</td> </tr>
    <tr> <td>Bob</td> <td>Yellow</td> </tr>
    <tr> <td>Michelle</td> <td>Purple</td> </tr>
    <tr> <td>Bob</td> <td>Yellow</td> </tr>
    <tr> <td>Michelle</td> <td>Purple</td> </tr>
    <tr> <td>Bob</td> <td>Yellow</td> </tr>
    <tr> <td>Michelle</td> <td>Purple</td> </tr>
    <tr> <td>Bob</td> <td>Yellow</td> </tr>
    <tr> <td>Michelle</td> <td>Purple</td> </tr>
    <tr> <td>Bob</td> <td>Yellow</td> </tr>
    <tr> <td>Michelle</td> <td>Purple</td> </tr>
    <tr> <td>Bob</td> <td>Yellow</td> </tr>
    <tr> <td>Michelle</td> <td>Purple</td> </tr>
    <tr> <td>Bob</td> <td>Yellow</td> </tr>
    <tr> <td>Michelle</td> <td>Purple</td> </tr>
    <tr> <td>Bob</td> <td>Yellow</td> </tr>
    <tr> <td>Michelle</td> <td>Purple</td> </tr>
    <tr> <td>Bob</td> <td>Yellow</td> </tr>
    <tr> <td>Michelle</td> <td>Purple</td> </tr>
    <tr> <td>Bob</td> <td>Yellow</td> </tr>
    <tr> <td>Michelle</td> <td>Purple</td> </tr>
    <tr> <td>Bob</td> <td>Yellow</td> </tr>
    <tr> <td>Michelle</td> <td>Purple</td> </tr>
    <tr> <td>Bob</td> <td>Yellow</td> </tr>
    <tr> <td>Michelle</td> <td>Purple</td> </tr>
    <tr> <td>Bob</td> <td>Yellow</td> </tr>
    <tr> <td>Michelle</td> <td>Purple</td> </tr>
    <tr> <td>Bob</td> <td>Yellow</td> </tr>
    <tr> <td>Michelle</td> <td>Purple</td> </tr>
    <tr> <td>Bob</td> <td>Yellow</td> </tr>
    <tr> <td>Michelle</td> <td>Purple</td> </tr>
    <tr> <td>Bob</td> <td>Yellow</td> </tr>
    <tr> <td>Michelle</td> <td>Purple</td> </tr>
    <tr> <td>Bob</td> <td>Yellow</td> </tr>
    <tr> <td>Michelle</td> <td>Purple</td> </tr>
    <tr> <td>Bob</td> <td>Yellow</td> </tr>
    <tr> <td>Michelle</td> <td>Purple</td> </tr>
    <tr> <td>Bob</td> <td>Yellow</td> </tr>
    <tr> <td>Michelle</td> <td>Purple</td> </tr>
  </tbody>
</table>
```


css代码：
```css
th {
  position: sticky;
  background-color: black;
  color: white;
  top: 0;
}
```


需要注意的是，`sticky`必须设在`<th>`元素上面，不能设在`<thead>`和`<tr>`元素，因为这两个元素没有`reltive`定位，也就无法产生`sticky`效果。


（end）
