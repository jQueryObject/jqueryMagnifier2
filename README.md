# jquery放大镜2jqueryMagnifier2
效果如下：
![](images/img.gif)

all code:
```
<!--文档声明为 html（最新html5）-->
<!Doctype html>
<html lang="en">
	<head>
		<!--声明当前页面编码格式为国际编码（utf-8）还有一种中文编码（gbk/gb2312）-->
		<meta charset="UTF-8">
		<!--网页三要素-->
		<meta name="Keywords" content="关键词,关键词">
		<meta name="Description" content="描述">
		<title>天猫放大镜特效-千凡老师</title>
		<!--css 层叠样式表 衣服 化妆品  修饰body页面-->
		<style>
		/*浏览器兼容 沉余*/
		*{margin:0;padding:0;}
		.box{/*以class命名 类选择器 .开头*/
			width:420px;
			height:420px;
			background:#ff0066;
			margin:100px;
			position:relative;/*相对定位 参照物*/
		}
		.box .simg{
			width:420px;
			height:420px;
		}
		.box .move{
			width:220px;
			height:220px;
			background:url('images/T12pdtXaldXXXXXXXX-2-2.png');/*背景图片*/
			position:absolute;/*绝对定位*/
			left:10px;
			top:10px;
			display:none;
		}
		.box .bimg{
			width:420px;
			height:420px;
			background:red;
			position:absolute;
			left: 450px;
			top:0;
			overflow:hidden;/*超出去的部分隐藏掉*/
			display:none;/*不显示*/
		}
		.box .bimg .b-img{
			width:800px;
			height:800px;
			position:absolute;
			left:0;
			top:0;
		}
		</style>
	</head>
	<body>
	<!--
		div 盒子模型，有宽度，高度 内容的长方形区域
		命名:区别个体与个体，添加样式 js控制对象
		id=""  身份证  唯一性
		class="" 名字  同名同姓 多个
		命名规范：

		定位：确定元素的位置
	-->
	<div class="box">
		<img class="simg" src="images/simg.jpg" width="430" height="430" alt=""/>
		<div class="move"></div>
		<div class="bimg">
			<img class="b-img" src="images/simg.jpg" width="430" height="430" alt=""/>
		</div>
	</div>
	</body>
</html>
<script src="js/jquery.js"></script>
<script>
	//验证jq引入成功了
	//alert($);//弹窗确定
	//hover 鼠标移入或者移出
	$('.box').hover(function(){
		//alert('移入')
		$('.move').show();
		$('.bimg').show();
	},function(){
		$('.move').hide();
		$('.bimg').hide();
	});
	var x=0,y=0,l=0,t=0;
	$('.move').mousemove(function(e){
		var ev = e||window.event;//解决ie和火狐兼容问题
		x = ev.clientX;//鼠标滑到坐标x
		y =	ev.clientY; //鼠标滑到坐标y
		l = $('.box').offset().left;
		t = $('.box').offset().top;
		//console.log(1)
		//改变move位置
		/*move坐标改变 = 鼠标滑到坐标- box原有的坐标
		 把改变的值给move坐标*/
		var nowLeft = x - l -$(this).width()/2;
		var nowTop =  y - t -$(this).height()/2;
		var max_w =$('.box').width()-$(this).width();
		var max_t =$('.box').height()-$(this).height();
		if(nowLeft<0){
			nowLeft=0;
		}else if(nowLeft>max_w){
			nowLeft=max_w;
		}
		if(nowTop<0){
			nowTop = 0;
		}else if(nowTop>max_t){
			nowTop =max_t;
		}
		$(this).css({
			left:nowLeft,
			top:nowTop
		});
		//
		var w = nowLeft/$('.box').width();
		var h = nowTop/$('.box').height();
		var _left = w*$('.b-img').width();
		var _top = h*$('.b-img').height();
		$('.b-img').css({
			left:-_left,
			top:-_top
		});
	})
</script>

```

