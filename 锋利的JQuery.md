# 主体结构
# 1 选择器
# 2 DOM操作
# 3 事件和动画
# 4 表单表格
# 5 ajax
## 1.选择器  
* 基本选择器
	* #id
	* .class
	* element
	* *
	* selector1,selector2...
* 层次选择器
	* $('祖先 后代')
	* $('parent>child')
	* $('prev+next')
		* ('prev').next()
	* $('prev~siblings')
		* $('prev').nextAll()
* 过滤选择器
	* 基本过滤
	 * :first
		* :last
		* not(selector)
		* :even
		* :odd
		* eq(index)
			* 从0开始算index
		* :gt(index)
		* :lt(index)
		* :header
			* h1,h2...
		* :animated
		* :focus
	* 内容过滤
		* :contains(text)
		* :empty
		* :has(selector)
		* :parent
	* 可见性过滤
		* :hidden
		* :visible
	* 属性过滤
		* [attr]
		* [attr=value]
		* [attr!=value]
		* [attr^=value]
		* [attr$=value]
		* [attr*=value]
		* [attr|=value]
		* [attr~=value]
		* [attr1][attr2][attr3]
	* 子元素过滤
		* :first-child
			* 每个父元素的最后一个子元素
		* :last-child
			* 每个父元素的最后一个子元素
		* :nth-child（index/even/odd)
			* 与每一个父元素匹配
			* :nth-child（3n+1)
			* index从1开始算
		* :only-child
			* 所有父元素的唯一子元素
	* 表单对象属性
		* :enabled
		* :disabled
		* :checked
			* 单选框复选框
		* :selected
			* 下拉菜单
	
* 表单选择器
	* ：input
	* :text
	* :password
	* :radio
	* :checkbox
	* :submit
	* :image
		* 所有的图像按钮
	* :reset
	* :button
	* :file
		* 所有的上传域
	* :hidden
## 2.DOM操作
* 查找结点
	* 用选择器查找节点
	* attr（）得到元素属性节点
* 创建节点
	* 直接在$('')里面把元素，属性，文本写好
	* 创建元素节点
	* 创建属性节点
	* 创建文本节点
	* $('<li class="abc">hello</li>")
* 插入节点
	* append()
	* appendTo()
	* prepend()
	* prependTo()
	* after()
	* insertAfter()
	* before()
	* insertBefore()
* 删除节点
	* remove()
		* 可以传参选择性删除
		* 重新追加删除的节点，原来保留绑定的事件不在
	* detach()
		* 重新追加删除的节点，原来保留绑定的事件还在
	* empty()
		* 清除节点
* 复制节点
	* clone()
		* 被复制的节点不含原节点绑定的事件
		* clone（true）包含绑定的事件
* 替换节点
	* replaceWith()
	* replaceAll()
* 包裹节点
	* wrap()
		* 所有匹配的元素单独包裹
	* wrapAll()
		* 匹配的元素用一个元素包裹
		* 匹配元素中间的元素会被放到包裹元素后面
	* wrapInner()
		* 匹配元素的子内容（包括文本节点）包裹起来
* 属性操作
	* attr()
	* removeAttr()
* 样式操作
	* 对class属性进行操作
	* addClass()
	* removeClass()
	* toggleClass()
	* hasClass()
* 设置HTML TEXT VALUE
	* html()
	* text()
	* val()
		* defaultValue 包含表单元素的初始值
		* val（）应用于表单，表单的value属性表示表单选中的内容；表单的selected属性，true表示选中
* 遍历节点
	* children()
	* next()
	* prev()
	* siblings()
	* closet()
	* parent()
	* parents()
* CSS的DOM操作
	* 用css()函数来获取或设置css，类似设置属性
	* css({"color":"red","backgroundColor":"blue")
	* css('height')得到的是css中设置的值，height()表示元素在页面中实际的值；width同理
	* style属性不能读取外部CSS设置的样式
	* offSet()
		* 应用于position:relative的元素
		* top，left属性为设置的top和left的值
	* position()
		* 应用于pisition:absolute的元素
		* top，left属性为设置的top和left的值
	* scrollTop()
		* 竖直滚动条距顶端滚动距离
	* scrollLeft()
		* 水平滚动条距左端滚动距离

##3 JQuery中的事件和动画
* 事件
	* 加载DOM
		* $('document').ready()
		* window.onload
		* 差别
			* window.onload所有的元素加载到浏览器后才能执行，redy()在DOM就绪的时候网页所有的元素就可以访问到，不过有些关联文件可能没有下载完，相关属性无法调用
			* windown.load一次只能保存对一个函数的引用，后面的会覆盖前面的；redy()会在现有的行为上追加新的行为
		* load()
			* 绑定在window上，所有内容加载完后触发
			* 绑定在元素上，元素加载完后触发
		* $('document').ready()简写方式：$(function(){..})
	* 事件绑定
		* bind(type,data,fn)
		* $("P").click(fn)
	* 合成事件
		* hover(fn1,fn2)
		* toggle(fn1,fn2,...)
	* 事件冒泡
		* 绑定同一个事件的嵌套元素组，从最内层到最外层
		* 阻止事件冒泡
			* event.stopPropagation()：阻止事件冒泡
			* event.stopDefault():阻止默认行为
			* return false:阻止事件冒泡，阻止默认行为
		* 事件捕获：与事件冒泡相反，JQuery不支持
	* 事件对象属性
		* event
		* event.target
		* event.relatedTarget
		* event.pageX,event.pageY
		* event.whcih
		* event.metaKey
		* 
	* 移除事件
		* unbind()
		* one():处理函数触发一次后，立即被删除，用法和bind()一样
	* 模拟操作
		* trigger('click')
		* trigger('click',data):传一个参数给回调函数，区分是用户行为还是模拟操作
		* 阻止浏览器默认 行为：triggerHandler('focus')：禁止浏览器的默认focus行为
	* 其他用法
		* bind()的扩展用法
		* bind('mouseover mouseout',fn)
		* 命名空间
			* bind('click',fn1)   bind('click.plugin',fn2)
			* unbind('.plugin')
			* trigger('click!'):不包含在命名空间的事件触发
* 动画
	* 说白了就是在一定的时间内改变元素的CSS
	* 任何动画都可以设置速度参数：slow(600),normal(400),fast(200);数字：毫秒
	* show()，hide()
		* 设置css：display
		* 同时改变高度，宽度，透明度
	* fadeIn()，fadeOut()
		* 只改变透明度
	* slideUp()，slideDown()
		* 只改变元素高度，达到隐藏和显示的效果
	* animate()
		* animate({left:"500px",height:"+=100px"},3000,fn)
		* 用链式的方式依次执行多个动画
		* 在animate()下，css值可以是"show","hide","toggle"
	* 回调函数
		* 所有的动画效果方法都可以添加回调函数，动画执行完后执行该函数
		* 直接链式方式把css()放到最后是无效的，css()会立即执行
		* 非动画方法会插队
	* 停止动画
		* stop([clearQueue],[gotoEnd])
			* clearQueue 为true 表示停止当前动画，清空当前动画队列
			* gotoEnd 为true，表示直接将正在执行的动画跳到末状态
		* stop():立即停止当前的动画，以当前状态开始执行下一个动画
	* 判断元素是否处于动画状态
		* is(':animated')
		* 使用动画的时候都要进行该判断，防止动画队列累积
	* 延迟动画
		* 队列中使用delay(200)
	* 其他动画方法
		* toggle()
			* 切换 hide(),show()
		* slideToggle()
			* 切换 slideUp(),slideDown()
		* fadeTo()
			* 把元素透明度以渐进方式调整到指定值 fadeTo(600,0.2)
		* fadeToggler()
			* 切换 fadeIn(),fadeOut()


## 4 JQuery对表单表格的操作和更多应用
* JQuery的实际应用
* 表单
	* 对表单的CSS操作：height（）,scrollTop(),background等
	* 全选/全不选 按钮
		* checked属性来控制
		* 全选按钮和选项的同步
		* prop():只添加属性名该属性就产生效应；只存在true/false属性值的属性时代替attr()
	* 下拉菜单
		* 取得节点，appendTo
		* appendTo()可以同时完成删除和追加
	* 表单验证
		* 正则表达式
		* 判断是否可提交：看是否存在错误提示信息，给错误信息添加class，用length判断
		* 实时提醒，添加keyup和focus事件
* 表格
	* 表格变色
		* 普通的隔行变色：选行，addClass()
		* 单选框控制表格行高亮：选中行添加高亮，去除兄弟行的高亮，当前行的单选框设置为选中checked=true
		* end()的用法：$('p').addClass('class1').siblings.removeClass('class1').end().find('li')
		* parents（）获取祖先节点：$('table').parent().parent().addClass('class1')相当于$('table').parents().addClass('class1')
		* $(this)['removeClass']('selected')相当于$(this).removClass('selected')
	* 表格展开关闭
		* toggle(),toggleClass()
		* $('p').click(function(){..}).click() 表示执行点击操作从而执行那个函数,立即触发
	* 表格内容筛选
		* 	filter(':contain('lee')')	
* 更多应用
	* 网页字体大小
		* font-size
		* parseInt(string,10):把string转换为Int型数字10进制
		* slice()
	* 网页选项卡
		* 隐藏显示指定内容
		* 通过<li>的索引显示对应的<div>
	* 网页换肤
		* 调用不同的样式表：操作link的href属性
		* 存入cookie：cookie插件，
		* 存入cookie：$.cookie('mycssskin',this.id,{path:'/'.expires:10})
		* 从cookie调用 $.cookie('myscsskin')

## 5 AJAX
* ajax用js最基本实现
	* XMLHttpRequest对象
	* 按需发送，无刷新（影响后退键的使用）
	* 创建XHR
		* IE $request = new Active Object('Microsoft.XMLHTTP')
		* 非IE： $request = new XMLHttpRequest();
	* open()
		* $request.open('GET','请求地址的url',true)true表示异步
	* send()
	* onreadystatechange
		* $request.readyState == 4,$request.status == 200
* JQuery实现ajax
	* load()
	* $.get()
	* $.post()
	* $.getScript()
	* $.getJson
	* $.ajax
* 序列化元素
* jquery中ajax的全局时间