### CSS 的顶层样式表由两种规则组成的规则列表构成，一种被称为at-rule，也就是 at 规则，另一种是 qualified rule,也就是普通规则.

## 1.at规则

### @charset 用于提示CSS文件所使用的字符编码方式,例如

	@charset = "utf-8"

### @import 用于引入一个css文件,除了@charset规则不会被引入,@import可以引入另一个文件的全部内容.

	@import "mystyle.css";
	@import url("mystyle.css");

### @media 就是media query,他能够对设备的类型做一定的判断.在media的区块内,就是普通规则列表.
	@media(max-width: 768px){

	} 

### @key-frames 定义动画关键帧
	@keyframes diagonal-slide {

 		 from {
   		 	left: 0;
   			 top: 0;
 		 }

		to {
    		left: 100px;
    		top: 100px;
 		 }

	}

### @page 用于分页媒体访问网页时的表现设置,页面是一种特殊的盒模型,除了页面本身,还可以设置它周围的盒.

	@page {
  		size: 8.5in 11in;
 		margin: 10%;

  		@top-left {
    	content: "Hamlet";
  		}
  		@top-right {
    	content: "Page " counter(page);
  		}
	}

### counter-style 产生一种数据，用于定义列表项的表现。
	@counter-style triangle {
  		system: cyclic;
  		symbols: ‣;
  		suffix: " ";
	}

### @fontface 用于定义一种字体,icon font就是利用这个特性实现的
	@font-face {
  		font-family: Gentium;
  		src: url(http://example.com/fonts/Gentium.woff);
	}

	p { font-family: Gentium, serif; }


### @support 检查环境的特性 和@media类似
