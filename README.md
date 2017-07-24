# LESS的基本用法
# 一：变量
	语法：@变量名：值;
	例子：定义一个变量   @box-width-height: 200px;
	在盒子中使用它：
		#box1 {
			height: @box-width-height;
			width: @box-width-height;
		}

# 二：混合
	例子:定义一个混合:
		.box-style{
			width：200px;
			height:200px;
    	border: solid 3px pink;
    }
      在盒子中使用它：
    #box{
    	.box-style;
    	backgroud:gray;
    }

# 三：混合(带参数)
	例子：定义一个带参数的混合
		.boxAttr(@weight-height) {
    	width: @weight-height;
    	height: @weight-height;
    	border:solid 1px pink;
    }
	在盒子中使用它：
		#box2{
    	.boxAttr(300px);
    }
    
# 四：混合(参数可带默认值)
	例子:定义一个参数有默认值的混合
	.border_radius(@radius:5px){
		-webkit-border-radius: @radius;
    -moz-border-radius: @radius;
    border-radius: @radius;
	}
	在盒子中使用它：
		#box{
			.border_radius;
			//使用.border_radius，不带后面的括号那么默认的border-radius就是5px
			//如果在使用时想要改变border-radius的值，使用方法是：
			//.border_radius(10px);
			height:200px;
			width:200px;
			border:solid 1px pink;
		}
# 五：匹配模式(类似于JS中的判断语句)
	例子：画三角形，因为三角形有四个不同的朝向，所以我们可以在CSS中预定义4个不同的方向，在使用时指明要选用的方向就可以。
	通常画一个朝左的三角形是：
		#box4 {
	    width: 0;
	    height: 0;
	    overflow: hidden;
	    border-width:5px;
	    border-color: transparent pink transparent transparent;
	    border-style: dashed solid dashed dashed;
		}
	
	
	当要改变三角形的朝向时就必须重新复写样式，所以可以在less中庸匹配模式解决：
		#box4 {
	    width: 0;
	    height: 0;
	    overflow: hidden;
	    .triangle(left);
	    //如上，在使用时带个参数指明索要指向的方向
		}

		.triangle(top, @width: 10px, @color: pink) {
	    border-width: @width;
	    border-color: transparent transparent @color transparent;
	    border-style: dashed dashed solid dashed;
		}
	
		.triangle(bottom, @width: 10px, @color: pink) {
	    border-width: @width;
	    border-color: @color transparent transparent transparent;
	    border-style: solid dashed dashed dashed;
		}
	
		.triangle(right, @width: 10px, @color: pink) {
	    border-width: @width;
	    border-color: transparent transparent transparent @color;
	    border-style: dashed dashed dashed solid;
		}
	
		.triangle(left, @width: 10px, @color: pink) {
	    border-width: @width;
	    border-color: transparent @color transparent transparent;
	    border-style: dashed solid dashed dashed;
		}
	
	
	

