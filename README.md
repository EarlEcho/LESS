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
	    .triangle(left);
	    //如上，在使用时带个参数指明索要指向的方向
	    //要改变默认值时：.triangle(left);
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
	而匹配模式还有一个默认的值，就是无论匹配到上面哪一个，这一个都会被执{行：
	.triangle(@_, @width:10px , @color:pink){
		width: 0;
		height: 0;
		overflow: hidden;
	}
		
# 六：运算
	可以使用加减乘除的等运算
	例子：
	@test:200px;
	#box{
		width:(@test-20)*5;
		color:#ccc-10;
	}
	
# 嵌套规则
	在指定一个盒子中某些元素的样式时：
	比如说在这种情况下：
	<div id="box5">
		<a href="#">hello less</a>
		<span>这是一个span</span>
		<form>
			<input type="button" name="" id="" value="hello" />
		</form>
	</div>
	指定样式可以这样写：
	#box5{
    		height: 300px;
    		width: 400px;
    		border: solid 1px hotpink;
    		padding: 15px;
    		a{
    			text-decoration: none;
       			color: red; 
       			&:hover{
         	 		color: cornflowerblue;
       			}
    		}
	   	span{
	       		font-size: 18px;
	    	}
	    	form{
	        	border: solid 1px pink;
	        	padding: 20px;
	   	}
	}
	//嵌套在其中表示指定在#box5这个元素盒子里面的a，span，form等元素
	//而&符号表示其父级元素

