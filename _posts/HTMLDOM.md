---
title: HTMLDOM
date: 2021-01-02 19:10:00
tags: JavaScript
swiper: true
swiperImg: '/medias/2.jpg'
---
# HTML DOM 简介

**HTML DOM定义了访问和操作HTML文档标准**

如果想要学习该知识用该具备的知识：

- HTML
- CSS
- JavaScript

# 什么是DOM？

**DOM是W3C（万维网联盟）的标准。**

DOM定义了访问HTML和XML文档的标准：

“W3C文档对象模型（DOM）是中立于平台和语言的接口，它允许程序和脚本动态地访问和更新文档的内容、结构和样式。”

W3C DOM标准被分为3个不同的部分：

- 核心DOM - 针对任何结构化文档的标准模型
- XML DOM - 针对XML文档的标准模型
- HTML DOM - 针对HTML文档的标准模型

# 什么是HTML DOM？

HTML DOM是：

- HTML的标准对象模型
- HTML的标准编程接口
- W3C标准

HTML DOM定义了所有HTML元素的**对象**和**属性**，以及访问他们的**方法**。

**HTML DOM是关于如何获取、修改、添加或删除HTML元素的标准。**

# HTML DOM节点

**在HTML DOM中，所有事物都是节点。DOM是被视为节点树的HTML。**

## DOM节点

根据W3C的HTML DOM标准，HTML文档中的所有内容都是节点：

- 整个文档是一个文档节点
- 每个HTML元素是元素节点
- HTML元素内的文本是文本节点
- 每个HTML属性是属性节点
- 注释是注释节点

## HTML DOM节点树

HTML DOM将HTML文档视作树结构，这种接否被称为**节点树：**

**HTML DOM Tree实例**

![](https://www.w3school.com.cn/i/ct_htmltree.gif#alt=HTML%20DOM)

通过HTML DOM，树中的所有节点均可通过JavaScript进行访问。所有HTML元素（节点）均可被修改，也可以被创建和删除。

## 节点父、子和同胞

节点树中的节点彼此拥有层级关系。

父（parent）、子（child）和同胞（sibling）等术语用于描述这些关系。父节点拥有子节点。同级的子节点被称为同胞节点（兄弟或姐妹）。

- 在节点树中，顶端节点被称为根（root）
- 每个节点都有父节点、除了根节点（他没有父节点）
- 一个节点可拥有任意数量的子
- 同胞是拥有形同父节点的节点

树的一部分，以及节点之间的关系：

![](https://www.w3school.com.cn/i/dom_navigate.gif#alt=%E8%8A%82%E7%82%B9%20%E5%85%B3%E7%B3%BB)

**看下面的HTML代码片段：**

```html
<html>
	<head>
		<title>DOM 教程</title>
	</head>
	<body>
		<h1>第一课</h1>
		<p>Hello world!</P>
	</body>
</html>
```

上面的HTML中：

- 
节点没有父节点；它是根节点

- 
和的父节点是节点

- 文本节点"Hello world!"的父节点是节点

并且：
-  节点拥有两个子节点：和
- 节点拥有一个子节点：节点
- \<title>节点也拥有一个子节点：文本节点"DOM教程"
- \<h1>和节点是同胞节点，同时也是的子节点

# HTML DOM 方法

**方法是我们可以在节点（HTML元素）上执行的动作。**

## 编程接口

可以通过JavaScript（以及其他编程语言）对HTML DOM进行访问。

所有HTML元素被定义为对象，而编程接口则是对象方法和对象属性。

方法是您能够执行的动作（比如添加或修改元素）

属性是您能够获取或设置的值（比如节点的名称或内容）。

### getElementById()方法

getElementById()方法返回带有指定ID的元素：

**例子**

```javascript
 var element=document.getElementById("intro");
```

### HTML DOM对象 - 方法和属性

一些常用的HTML DOM方法：

- getElementById(id) - 获取带有指定ID的节点（元素）
- appendChild(node) - 插入新的子节点（元素）
- removeChild(node) - 删除子节点（元素）

一些常用的HTML DOM属性：
- innerHTML - 节点（元素）的文本值
- parentNode - 节点（元素）的父节点
- childNodes - 节点（元素）的子节点
- attribute - 节点（元素）的属性节点

## 一些DOM对象方法
| 方法 | 描述 |
| --- | --- |
| getElementById() | 返回带有指定ID的元素 |
| getElementByTagName() | 返回包含带有指定标签名称的所有元素的节点列表（集合/节点数组）。 |
| getElementByClassName() | 返回包含带有指定雷鸣的所有的节点列表 |
| appendChild() | 把新的子节点添加到指定节点。 |
| removeChild() | 删除子节点 。 |
| replaceChild() | 替换子节点 |
| insertBefore() | 在指定的子节点前面插入新的子节点 |
| createAttribute() | 创建属性节点 |
| createElement() | 创建元素节点 |
| createTextNode() | 创建文本节点 |
| getAttribute() | 返回指定属性值 |
| setAttribute() | 把指定属性设置或修改为指定的值 |

