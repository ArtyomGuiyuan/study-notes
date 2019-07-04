# 移动端web开发

## 适配问题 
#### 1.响应式 
#### 2.专门针对移动端开发页面


## 视口 viewport
#### 根据html的font-size 用px 转 rem 适配

		//页面初始化
		resetFontSize();
		//窗口大小变化时候执行	
		window.onresize = function(){
			resetFontSize();
		}
		// 如何获取浏览器宽度
		function resetFontSize(){
			var clientWidth = document.documentElement.clientWidth;
			//获取html对象
			document.documentElement.style.fontSize = clientWidth/10+'px';
		}
 
## 移动端事件

#### 1.touchstart 当手指触碰屏幕时发生.不管当前有多少手指
#### 2.touchmove 当手指在屏幕上滑动时连续触发.通常我们再滑屏页面，会调用event的preventDefault()可以阻止默认情况的发生：阻止页面滚动
#### 3.touchend 手指离开屏幕时触发.
#### 4.touchcancel 停止触摸.例如来电话.