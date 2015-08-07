
<!-- 启用360浏览器的极速模式(webkit) -->
<meta name="renderer" content="webkit">
<!-- 避免IE使用兼容模式 -->
<meta http-equiv="X-UA-Compatible" content="IE=edge">
<!-- 针对手持设备优化，主要是针对一些老的不识别viewport的浏览器，比如黑莓 -->
<meta name="HandheldFriendly" content="true">
<!-- 微软的老式浏览器 -->
<meta name="MobileOptimized" content="320">
<!-- uc强制竖屏 -->
<meta name="screen-orientation" content="portrait">
<!-- QQ强制竖屏 -->
<meta name="x5-orientation" content="portrait">
<!-- UC强制全屏 -->
<meta name="full-screen" content="yes">
<!-- QQ强制全屏 -->
<meta name="x5-fullscreen" content="true">
<!-- UC应用模式 -->
<meta name="browsermode" content="application">
<!-- QQ应用模式 -->
<meta name="x5-page-mode" content="app">
<!-- windows phone 点击无高光 -->
<meta name="msapplication-tap-highlight" content="no">


<link rel="apple-touch-icon" href="touch-icon-iphone.png">
<link rel="apple-touch-icon" sizes="76x76" href="touch-icon-ipad.png">
<link rel="apple-touch-icon" sizes="120x120" href="touch-icon-iphone-retina.png">
<link rel="apple-touch-icon" sizes="152x152" href="touch-icon-ipad-retina.png">

启动画面。

// iPhone
<link href="apple-touch-startup-image-320x460.png" media="(device-width: 320px)" rel="apple-touch-startup-image" />

// iPhone Retina
<link href="apple-touch-startup-image-640x920.png" media="(device-width: 320px) and (-webkit-device-pixel-ratio: 2)" rel="apple-touch-startup-image" />

// iPhone 5
<link rel="apple-touch-startup-image" media="(device-width: 320px) and (device-height: 568px) and (-webkit-device-pixel-ratio: 2)" href="apple-touch-startup-image-640x1096.png">

// iPad portrait
<link href="apple-touch-startup-image-768x1004.png" media="(device-width: 768px) and (orientation: portrait)" rel="apple-touch-startup-image" />

// iPad landscape
<link href="apple-touch-startup-image-748x1024.png" media="(device-width: 768px) and (orientation: landscape)" rel="apple-touch-startup-image" />

// iPad Retina portrait
<link href="apple-touch-startup-image-1536x2008.png" media="(device-width: 1536px) and (orientation: portrait) and (-webkit-device-pixel-ratio: 2)" rel="apple-touch-startup-image" />

// iPad Retina landscape
<link href="apple-touch-startup-image-1496x2048.png"media="(device-width: 1536px)  and (orientation: landscape) and (-webkit-device-pixel-ratio: 2)"rel="apple-touch-startup-image" />

transition与transform在safari下兼容问题，是因为transition-property没有工作，要改成transition:all可避免此问题。

表单提交autocomplete="off" 表单数据自动填写
safari下元素执行transform时，再给其动画暂停animation-play-state:paused;会导致safari崩溃。

###retina 下 1px 边框
>用background-image实现
>单边
>background:-webkit-gradient(linear, left top,left bottom, color-stop(0.5,red), color-stop(0.5,transparent));
	background-size:auto 1px;
	background-repeat:repeat-x;
}
>四边，圆角时，四角会空
>.border{
	background-image: -webkit-gradient(linear, left bottom, left top, color-stop(0.5, transparent), color-stop(0.5, red)), -webkit-gradient(linear, left top, right top, color-stop(0.5, transparent), color-stop(0.5, blue)), -webkit-gradient(linear, left top, left bottom, color-stop(0.5, transparent), color-stop(0.5, green)), -webkit-gradient(linear, right top, left top, color-stop(0.5, transparent), color-stop(0.5, black));
	-webkit-background-size: 100% 1px, 1px 100%, 100% 1px, 1px 100%;
	background-repeat: no-repeat;
	background-position: top, right, bottom, left;
}
>用transform: scale(0.5)
>利用伪元素实现
>.border-radius:before{
	content: '';
	position: absolute;
	top:0;
	left: 0;
	width: 200%;
	height: 200%;
	border: 1px solid #e0e0e0;
    -webkit-transform: scale(0.5);
    -webkit-transform-origin: 0 0;
    border-radius: 8px;
}

###box-shadow单边阴影 利用阴影扩展半径：spread-radius
>inset x-offset y-offset blur-radius spread-radius color
>投影方式 X轴偏移量 Y轴偏移量 阴影模糊半径 阴影扩展半径 阴影颜色
>box-shadow: 0 3px 2px -3px red;