# try-vite

今天参考了大圣老师的文章，实现了一个山寨版的 Vite。<p>
https://mp.weixin.qq.com/s/yXGab8YQ8t3sxy4Qu5527A

Vite 是 Vue 3 的打包工具，其亮点是通过拦截import的http请求，来实现无需打包，自带按需加载；还未出正式版，但我们可以从 github 看到其雏形。

以下是 Vite 的山寨版实现：<p>
1.使用 KOA 来实现支持 HTML 和 JS 的文件请求。

2.实现第三方库的加载请求。<p>
a.遇到问题：浏览器报错：不是合法的相对路径<p>
解决方式：<p>
1）遇到绝对路径的模块加载，统一在路径前加前缀“/@module/”<p>
2）实现支持 “/@module/” 语法

b.遇到问题：浏览器报错<p>
browser: Uncaught ReferenceError: process is not defined<p>
解决方式：<p>
编译 HTML 时注入 window.process

3.实现 node 环境 Vue 单文件组件解析。<p>
a.实现解析 .vue 文件<p>
b.实现解析 template 文件<p>
c.实现解析 CSS 文件<p>