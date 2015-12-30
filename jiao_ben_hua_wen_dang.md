# 脚本化文档

`Document Object Model`

![文档节点的部分层次结构](QQ20151230-0.png)


每个Window对象都有一个document属性指向`Document`

Document对象表示窗口的内容.

##1. 获取文档元素
```javascript
//ID
//返回`element`
document.getElementById('ID_K');

//Name
//返回NodeList
document.getElementsByName("name_K");

//根据标签 
//返回HTMLCollection 在<<JavaScript权威指南>>第六版第367页中写的是返回NodeList,但是查了官网API是返回HTMLCollection的.
//因为HTML不区分大小写,所以这个也不区分大小写.
var first_p = document.getElementTagName("p")[0];
first_p_span = first_p.getElementsTagName("span");

//通过Class
document.getElementsByClassName("K container");

//通过CSS选择器 返回NodeList
document.querySelectorAll("#K div");
document.querySelector("#K div"); //返回第一个匹配的.

```

`HtmlDocument`还定义了一些快捷的访问方式.

只读的`img`,`form`,`a(包含href属性的)`等元素的集合.(返回HTMLCollection)

因为在`Document`对象中为`form` `img` `iframe` `applet` `embed` `ojbect`元素设置name属性,既在Document对象中创建以此name属性值为名字的属性.

不太建议这样的使用方法,以下都返回的是`HTMLColection`
```javascript
document.images;

//假如women定义了一个ID/name属性为K_404的form 
document.forms.K_404;
//or
document.K_404;

document.links
```

##2. Node属性

1. parentNode : 该节点的父节点,类似Document对象此属性为null.
2. childNode : 只读的类数组对象(NodeList对象),实时表示
3. firstChild lastChild
4. nextSibling previoursSibling
5. nodeType : 节点类型
    1. 9表示Document节点
    2. 1表示Element节点
    3. 3表示Text节点
    4. 8表示Comment节点
    5. 11表示DcoumentFragment节点
6. nodeValue : Text节点/Commetn节点的文本内容.
7. nodeName : 元素的标签名,以大写形式表示


##3. HTML属性作为Element的属性

```javascript
var image = document.getElementByID("K_404");
var iamge_url = "../image/404_K.jpg";

///关键字 会默认前面加html 除class ,其他驼峰
document.getElementsByTagName('lable')[0].htmlFor = "404_K";
document.getElementById('K_404').className = "container";
```

##4. 获取和设置非标准HTML属性

Element定义的方法

1. setAttribute
2. getAttribute
3. hasAttribute
4. removeAttribute

```javascript
var image = document.images[0];
var width = parseInt("iamge.getAttribute('width')");
image.setAttribute('class',"container");

```