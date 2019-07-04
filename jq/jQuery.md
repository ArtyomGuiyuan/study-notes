# jQuery
 

## 入口函数 

    //原生js，入口函数。页面上所有内容加载完毕，会执行。
    //不仅文本加载完毕，而且图片也要加载完毕，在执行函数。
    window.onload = function () {
        alert(1);
    }
    //jquery的入口函数。  1.文档加载完毕，图片不加载的时候就可以执行这个函数。
    $(document).ready(function () {
        alert(1);
    })
    //jquery的入口函数。  2.文档加载完毕，图片不加载的时候就可以执行这个函数。一般使用这种
    $(function () {
        alert(1);
    });
    //jquery的入口函数。  3.文档加载完毕，图片加载完毕的时候在执行这个函数。
    $(window).ready(function () {
        alert(1);
    })

### 事件处理程序

#### Jquery:   click(function(){  });
#### 注意:jq中的事件处理都是方法 原生js的事件处理是属性


## jQuery基本选择器
### $("#demo") id选择器 
###	$(".d1") 类选择器
### $("div") 标签选择器
### $("*") 选择所有元素
### $(".arr,.arr-l) 选择多个指定的元素
### $(".box.inner") 选择box的子集元素

## jQuery的其他选择器
###  $("div span")   空格 后代选择器 选择所有的后代元素
###  $("div > span") > 子代选择器 选择所有的子代元素
### $("div + p") + 紧邻选择器 选择紧挨着的下一个元素
### $("div ~ p") ~ 兄弟选择器 选择后面所有的兄弟元素

## jQuery的过滤选择器
### $(“li:eq(1)”) 选择第一个匹配的元素
### $(“li:gt(2)”) 选择序号大于2的所有元素
### $(“li:lt(2)”) 选择序号小于2的所有元素
### :odd 选择所有序号为奇数行的元素
### :even 选择所有序号为偶数的元素
### :first  选择匹配的第一个元素
### :last 选择匹配的最后一个元素

## 属性选择器
### $(“a[href]”) 选择而所有包含href属性的元素

## 筛选选择器(方法)
### find(selector) 查找指定元素的所有后代元素
### children() 查找指定元素的直接子元素(亲儿子元素)
### siblings() 查找所有兄弟元素(不包括自己)
### parent() 查找父元素()亲的
### eq(index) 查找指定元素的第index个元素 index是索引


### mouseover事件和mouseenter事件的区别

#### mouseover/mouseout 鼠标经过的时候会触发多次 每遇到一个子元素就会触发一次
#### mouseenter/mouseleave 鼠标经过的时候只会触发有一次


## DOM对象 和jQuery对象相互转换

### jQ转dom $(“#btn”)[0]
### dom转jq $(btn)