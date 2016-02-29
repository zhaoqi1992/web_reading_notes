# 基本结构
## 1.基础部分
## 2.HTTP内容
* 报文
* 状态码
* 首部
* 追加协议
## 3.服务器
##4.安全
+ HTTPS
+ 身份认证
+ web攻击
##5.构建web  
***
#基础部分
* 客户端
* WWW构建技术
	* HTML
	* HTTP
	* URL
* TCP/IP
	* 含义
	* 分层
		* 应用层
		* 传输层
		* 网络层
		* 链路层
* TCP/IP传输流
	* 传输方向
	* 添加首部，删除首部
* IP协议
	* 网际协议
	* 网络层
	* 把各种数据包传送给对方
	* IP地址和mac地址
	* ARP
	* 路由选择
* TCP协议
	* 传输层
	* 大块数据分割成以报文段为单位的数据包
	* 三次握手
		* SYN
		* SYN/ACK
		* ACK
* DNS
	* 域名和IP地址之间的解析
		* www.abcd.com 到 192.168.1.1
* URI
	* 资源：非明确区别于其他类型的，需要标记的材料
	* URI具体到文件名，URL具体到文件的位置，URL属于URI
	* URI格式
		* 协议方案名
		* 登陆信息（用户名密码)(可选）
		* 服务器地址www.xxxx.com
		* 服务器端口号（可选）
		* 文件路径
		* 查询字符串（输入参数）（可选）
		* 片段标识符（已获取资源中的子资源）（可选）

* RFC
* 请求报文
	* GET /index.html http/1.1
	* 请求方法
	* 请求URI
	* 协议版本
	* 首部
	* 内容实体

* 响应报文
	* http/1.1 200 OK
	* 协议版本
	* 状态码
	* 状态码解释
	* 首部
	* 内容实体

* HTTP无状态
	* 不保存之前的交流记录

* 请求URI
	* 请求访问资源 URI
	* 访问服务器 *

* HTTP方法
	* GET 解析后响应
	* POST 传输实体
	* PUT传输文件
	* DELETE 删除文件按
	* HEAD获取首部信息
	* OPTIONS针对请求URI可用的方法
	* TRACE追踪路径
		* MAX-FORWARDS
	* CONNECT 隧道通信，加密

* 持久连接
	* 任意一方没有明确提出断开，则链接保持
	* HTTP默认使用

* 管线化
	* 不用等待响应即可发出下一个请求
	* 异步

* Cookie
	* 保存在客户端
	* 带Cookie的请求响应过程
	* Set-Cookie
***
##HTTP报文内容
* HTTP报文
	* 首部+空行+主体
	* 请求报文
		* 请求行
		* 通用首部
		* 请求首部
		* 实体首部
	* 响应报文
		* 响应行
		* 通用首部
		* 响应首部
		* 实体首部
* 编码提示传输速度
	* 报文
	* 实体
		* 实体压编码后与报文区别开，报文是基本的http传输单位
	* 内容编码
		* 应用在实体内容上，客户端负责解码
		* 常见编码：gzip compress  deflate identity（不编码）
	*分块传输编码
		* 把实体内容分块传输，在客户端重组
		* 每一块都用16进制来标注大小，最后一块用“0（空行）”表示

* 多部分对象集合
	* MIME 
		* 多用途因特网邮件扩展
	* 多部分对象集合
		* 一份报文主体内包含多个不同类型的实体
		* Content-Type
		* boundary：分割标记
		* 分割开始 --分割标记；分割结束 --分割标记--；
		* 每个部分的类型中，都可以包含首部
		* 多部分对象集合可以嵌套

* 获取部分内容的范围请求
	* 获取资源的一部分，可以从上次中断处继续下载
	* Range
		* 1000-10000；1000-；-2000；5000-10000  
	* Content-Type
		* multipart/byteranges
	* 206 Partital Content成功时返回
		* 不成功返回200 OK，然后会将整个资源发过来

* 内容协商
	* 服务器和客户端交涉，返回最合适的资源
	* 判断标准
		* Accept
		* Accept-Charset
		* Acccept-Encoding
		* Acccept-Language
		* Content-Language
	* 内容协商技术手段
		* 服务器驱动
		* 客户端驱动
		* 透明协商
			* 服务器和客户端各自协商

## 状态码
* 3位数字+原因短语
* 状态码有时和实际状态不一致
* 2XX成功
	* 200 OK
		* 表示正确处理完毕
	* 206 Partital Content
		* 范围请求
	* 204 No Content
		* 请求成功处理，响应不含有主体，浏览器页面不更新

* 3xx 重定向
	* 301 Moved Permanentaly
		* 请求的资源有了新的URI，书签引用要更改
	* 302 Found
		* 请求的资源有了临时新的URI，使用新的URI访问
	* 303 See Other
		* 请求的资源有别的URI，方法强制改成GET
	* 304 Not Modified
		* 条件请求因为没有满足条件的资源
	* 307 Temporay Redirect
		* 请求的资源有了临时的新URI，并不强制将方法改为GET

* 4xx 客户端错误
	* 400 Bad Request
		* 请求报文有语法错误
		* 浏览器会如同处理200 OK一样处理该响应
	* 401 Unauthorized
		* 发送的请求需要认证
		* 第一次请求返回401，要求发送用户名密码到服务器；第二次请求返回401表示认证失败
	* 403 Forbidden
		* 请求的资源拒绝访问
	* 404 Not found
		* 服务器上没有找到请求的资源

* 5xx 服务器错误
	* 500 Internal Server Error
		* 服务器内部出错
	* 503 Service Unavailable
		* 服务器服务现在不可用

## 与HTTP协作的WEB服务器
* 虚拟主机
	* 一个IP下面有多个主机名（域名）
	* HOST
		* www.shit.com
		* 访问到具体IP后，通过HOST指定的域名访问要访问的位置

* 代理
	* 客户端到服务器的中间人
	* 源服务器
	* Via首部
	* 分类
		* 缓存代理
		* 透明代理
			* 不对报文做任何的加工处理
* 网关
	* 转发别的服务器上的资源，收到请求时，如同自己有请求的资源那样做出响应
	* 可以给线路上的服务器提供非http的协议服务
* 隧道
	* 为相隔很远的客户端和服务器之间通信进行中转，安全
* 缓存
	* 保存资源副本
	* 有效期限
		* 向服务器确认资源的有效性
	* 客户端缓存
		* 临时网络文件
		* 向服务器确认有效性
## HTTP首部
* 为请求和响应提供额外信息
* 结构
	* 字段名：字段值1，字段值2
* 分类
	* 通用首部
	* 请求首部
	* 响应首部
	* 实体首部
* End-To-End
	* 端对端首部
	* 该类别首部会转发给最终的目标，且必须保存在缓存生成的响应中，必须被转发

* Hop-by-hop
	* 逐跳首部
	* 只对单次转发有效，通过缓存或代理后将不再转发
	* 标志
		* Connection
		* Keep-Alive
		* Proxy-Authorizate
		* Proxy-Authorization
		* Trailer
		* TE
		* Transfer-Encoding
		* Upgrade

* 通用首部字段
	* Cache-Control
		* 操作缓存的工作机制
		* Cache-Contral：指令
		* 指令
			* public
				* 所有人可以用该缓存
			* private
				* 特定客户端可以使用缓存
			* no-cache
				* 请求中，表示客户端不接受缓存中 的资源，请求被转发到源服务器
				* 响应中，表示缓存服务器不能缓存资源，也不能再进行有效性验证
				* 响应中，且no-cache有值，表示客户端不能再使用缓存
			* no-store
				* 缓存不能保存请求或者响应的任何部分
			* s-maxage
				* 功能和max-age相同
				* 应用在多人共享的缓存
				* 有他存在时，忽略Expire和max-age
			* max-age
				* 请求中，如果缓存时间小于指定时间，则返回该资源，否则将请求转发到源服务器
				* 响应中，表示缓存的有效期，该期间缓存不用再进行有效性检测
				* 有他存在时，忽略Expire
			* min-fresh
				* 在指定时间内没有过期，则返回该资源
			* max-stale
				* 即使过期了，没有超过该指令规定的时间，客户端也会接收到响应
			* only-if-cached
				* 只有缓存中存在请求的资源，才要求其返回
				* 无响应则返回504
			* must-revalidate
				* 代理会向源服务器确认即将返回的资源是否有效
				* 无响应则返回504
				* 他存在则忽略max-stale
			* proxy-revalidate
				* 所有的代理在接收到客户端的请求，在返回响应之前确认资源的有效性
			* no-transform
				* 不能对资源进行压缩编码等加工，不能改变媒体类型
			* 可以扩展指令，如果服务器不理解，则忽略该指令
	* Connection
		* 指令
			* 请求中，不再转发的首部
			* 响应中，close
				* 表示断开持久连接
				* http1.1默认为持久连接
	* Date
		* http报文创建的时间日期
	* Pragma
		* 为了向后兼容http1.0
		* 指令
			* 请求中，no-chache 不接受缓存中的资源
	* Trailer
		* 说明报文主体后面还有哪些首部
			* 出现在分块长度0之后
		*用于分块传输编码
	* Transfer-Encoding
		* 请求中，说明报文传输中用哪种编码方式
	* Warning
		* 告诉用户一些与缓存相关的警告
		* 格式：Warning：[警告码] [警告的主机：端口号] "[警告内容]" ([日期和时间])
	* Upgrade
		* 检测能否用更高级的协议进行通信
		* 同时，connection：upgrade
		* 只限于客户端和邻接的服务器之间使用
	* Via
		* 记录请求转发过程中都经过哪些服务器
		* 经常和TRACE方法一起使用

* 请求首部
	* Accept
		* 告诉服务器用户代理可以接受的媒体类型
		* 类型
			* 文本：text/html
			* 图片: image/jpg
			* 视频: video/mp4
			* 应用程序:application/zip
		* 优先级权重
			* text/html;q=0.8,text/txt;q=0.2
			* q范围0-1，精确到小数点后三位
			* 默认q为1
			* 服务器优先返回q最大的
	* Accept-Charset
		* 告诉服务器用户代理可接受的字符集
		* 可使用优先级q
	* Accept-Encoding
		* 告诉服务器用户代理可接受的内容编码
		* 可使用优先级q
		* 可以用通配符*
	* Accept-Language
		* 告诉服务器用户代理可接受的自然语言
		* 可使用优先级q
	* Authorization
		* 在需要认证的时候使用
		* 接收到服务器401（需要认证信息）的响应后，把Authorization首部字段加入到请求中，向服务器发送认证信息
		* 共用缓存在收到包含该字段的请求时的操作略有差异
	* Expect
		* 向服务器发送希望的扩展
	* From
		* 向服务器发送用户代理的邮件地址
		* 有时也放在User-Agent里
	* Host
		* 告诉服务器要访问的主机名/域名
		* 虚拟主机，相同IP不同域名
		* 必须包含在请求首部里
	* If-Match
		* If-Match：字段值
		* 服务器中的资源有自己的E-Tag值，类似于ID
		* 只有当字段值和E-Tag值一致时才返回资源
		* 可以使用通配符*作为字段值，这时，只要服务里有资源就返回
		* 这种情况下不能用弱E-Tag
	* If-Modified-Since
		* If-Modified-Since：字段值
		* 在字段值指定的日期后资源更新过，服务器接收请求
	* If-None-Match
		* 和If-Match反作用
	* If-Range
		* If-Range：字段值
		* 当字段值和服务器中资源的E-Tag或者资源更新时间相同，才可执行Range请求
		* 如果不匹配，则返回全体资源
	* If-Unmodified-Since
		* If-Modified-Since相反
	* Max-Forwards
		* TRACE
	* Proxy-Authorization
		* 客户端和代理之间需要认证
		* 过程和Authorization相同，不同在于Authorization用于和服务器之间的认证
	* Range
		* 范围请求
		* 不满足则返回资源的整体
	* Referer
		* 告诉服务器是从哪个链接过来的
	* TE
		* 告诉服务器客户端能处理的传输编码
		* TE:trailers   用于分块传输
	* User-Agent
		* 告诉服务器浏览器和用户代理的相关信息

* 响应首部
	* Accept-Ranges
		* 告诉客户端是否接受范围请求
		* Accept-Ranges：bytes 表示接受
		* Accept-Ranges：none 表示不接受
	* Age
	* ETag
	* Location
	* Proxy-Authenticate
	* Retry-After
	* Server
	* Vary
	* WWW-Authenticate