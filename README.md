Newbie-Gift
===========

新手大礼包。

这个包不仅仅是给新手用的一些简单工具。它会把Perl的复杂的不好的地方隐藏起来，让你快速地进行开发，不矫情。我期望看到以后 perler 们百分之九十的任务都可以通过这个包完成。

我的一些初步想法：
* 这个包是直接从网站上下载的，你不需要知道 CPAN 怎么使用。这个包里用到的所有非核心模块，都已含带在了下载包里。用户只要下载、解压、 use lib 之后就可以使用。未来可以加上更完善的安装程序，针对各个平台。
* 这个包缺省导出很多函数（不要跟我说污染命名空间什么的，那都是矫情）。这些函数都是常用的，比如获取一个网页的内容、把 Excel 变成二维数组、启动一个 http 服务器并处理请求、用回调函数处理切好的日志（拆行拆列兼容引号），这些功能都应该是一个函数就搞定了。这个想法主要是受 php 启发。
* CPAN 上有一些现有模块本身就很简单，那么我们直接包含进来就行了。
* 文档做成 cookbook 形式的，索引完备、一看就会。
* 把引用隐藏起来。提供面向对象基类： Object ，以及一个很重要的子类： Array 。基于基本标量类型（string、octets、int、float）和这两个类的子类来构建所有的 API 。另外提供定义类的简单函数，只要能定义属性和方法就行了，就像 java 刚出来的时候那样，或者 php4 的那样，不要那些 getter 、 setter 、私有、公有瞎矫情的东西。
* 养成用户异步编程的习惯。不管内部实际是异步实现的或同步实现的，公开的 API 接口都应该尽量是回调的形式，传入闭包参数。这样未来用户可以随时切换到异步引擎而不需要更改什么代码。这主要是受 node.js 的启发。
* 初始阶段实现的时候，不需要考虑性能，这些都可以留到以后再优化。不过要考虑到同步异步的兼容。面向对象这块的封装，刚开始可以用 bless hash 就行了，以后再改 glob 什么的。
* 在优化阶段，我们同样可以做很多省事的工作，比如你如果给 http_get 传很多 url 的话，自动就是并发下载了。
* 文档都写成中文的，慢慢再翻译成英文的，这样推进比较快。

希望大家广泛参与，会不断地有新的规范释出，大家只要按规范实现，添加代码即可。想要参与的请发邮件到 formalin14 at gmail dot com，或 perlchina 邮件列表， 或在 qq 群（552603）里招呼，或 github 私信。特别是欢迎国外高手参与。