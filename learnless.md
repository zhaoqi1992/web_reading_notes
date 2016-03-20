#less
##注释
* //
	* 编译后不保留
* /**/
	* 编译后会保留
##变量
* 以@开头
##混合
* .class1{...}
* .class2{.class1,...}
* 带变量的.class(@width){width:@width}
	* 混合带括号的样式，必须加括号
		* 带括号的样式编译后会消失	
	* 默认参数.class(@width：5px){width:@width}
		* 不传递参数的时候，默认@width=5px;
##匹配模式
* 混合时判断传递的变量选择混合的样式
* .class(a,@width,@height){...}
* .class(b,@width,@height){...}
* .class2{.class(a,3px,5px),...}
	* 此时，混合第一个参数为a的样式
* .class(@_,@width,@height){...}
	* 不论选择哪个，该样式都会被添加进去
##运算
* 变量的加减乘除运算
##嵌套规则
* 标准css，尽量少用嵌套，一层一层的查找
* LESS嵌套
	* ul>li>a
	* ul{style1,li{style2,a{style3,$:hover{style4}}}}
		* 相当于 
			* ul{style1}
			* ul li{style2}
			* ul li a{style3}
			* ul li a:hover{style4}
				* &代表他的上一层选择器
##@arguments变量(用的很少）
* 包含了所有传递进来的参数
	* class(@a,@b,@c){border：@arguments}
		* @arguments表示@a,@b,@c
##避免编译，！important,总结
* width:~'calc(300px-30px)';
	* 编译到css后，保持为width:calc(300px-30px);而不是width:270px;
* !important(一般不用，最多用于调试）
	* 表示混合优先级
	* .class1{...}
	* .class2{class!important}
		* 编译后的css中，每一条对应的样式后面都有!important

* 清除浮动
	* .clearfix{&:after{content:'',display:block,clear:both}zoom:1}
		* less中伪类最好用嵌套写
			* zoom:1;是为了兼容IE，触发haslayout
			* img{border:none}
				* 也是为了兼容IE

* @import引入less和css
	* @import'style.less'
		* 可以不加扩展名，默认为less
	* @import 'style.css'
		* 想要让引入的css在编译后直接显示为具体样式指令
			* @import(less) 'style.css'
		* @import 'style.css'写在哪儿，编译后位置就在@import的位置