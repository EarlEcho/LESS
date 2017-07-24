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
# 匹配模式(类似于JS中的判断语句)
	

