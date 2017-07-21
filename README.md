# LESS的基本用法
# 一：变量
	语法：@变量名：值;
	例子：
	定义一个变量   @box-width-height: 200px;
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
		#box2{
		.boxAttr(300px);
		}

