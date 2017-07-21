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
	