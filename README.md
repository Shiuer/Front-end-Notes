Front-end-Notes
===============
##移动web
###position相对于父元素定位，高度问题
absolute相对于bottom定位时，切记要设置父元素的高度。尤其不要忘记body

###retina 下 1px 边框
用background-image实现


单边

background:-webkit-gradient(linear, left top,left bottom, color-stop(0.5,red), color-stop(0.5,transparent));
	background-size:auto 1px;
	background-repeat:repeat-x;
}


四边，圆角时，四角会空

.border{
	background-image: -webkit-gradient(linear, left bottom, left top, color-stop(0.5, transparent), color-stop(0.5, red)), -webkit-gradient(linear, left top, right top, color-stop(0.5, transparent), color-stop(0.5, blue)), -webkit-gradient(linear, left top, left bottom, color-stop(0.5, transparent), color-stop(0.5, green)), -webkit-gradient(linear, right top, left top, color-stop(0.5, transparent), color-stop(0.5, black));
	-webkit-background-size: 100% 1px, 1px 100%, 100% 1px, 1px 100%;
	background-repeat: no-repeat;
	background-position: top, right, bottom, left;
}

用transform: scale(0.5)

利用伪元素实现

.border-radius:before{
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

inset x-offset y-offset blur-radius spread-radius color

投影方式 X轴偏移量 Y轴偏移量 阴影模糊半径 阴影扩展半径 阴影颜色

box-shadow: 0 3px 2px -3px red;