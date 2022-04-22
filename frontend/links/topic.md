
**1.Node**

Node.js 就是运行在服务端的 JavaScript。Node.js 是一个基于Chrome JavaScript
运行时建立的一个平台。Node.js是一个事件驱动I/O服务端JavaScript环境，基于Google的V8引擎。相当与JDK。

Github:

<https://github.com/nodejs/node>

官网教程：

<https://nodejs.org/en/>

其他教程：

* [七天学会NodeJS](http://nqdeng.github.io/7-days-nodejs)

**2.Npm**

NPM（node package manager）是Node.js的包管理和分发工具。它类似于PHP的Composer，Ruby的gem，Python的pip，Java的Maven……它可以让JavaScript开发者能够更加轻松的共享代码和共用代码片段，并且通过npm管理你分享的代码也很方便快捷和简单。

Github:

<https://github.com/npm/npm>

官方网站：

<https://docs.npmjs.com/>


其他教程：

* [npm入门文档](https://segmentfault.com/a/1190000005799797)
* [你所需要的npm知识储备都在这了](https://juejin.im/post/5d08d3d3f265da1b7e103a4d)

**3.Gulp**

gulp是基于Nodejs的自动任务运行器， 能自动化地完成javascript、coffee、sass、less、html/image、css等文件的测试、检查、合并、压缩、格式化、浏览器自动刷新、部署文件生成，并监听文件在改动后重复指定的这些步骤。在实现上，它借鉴了Unix操作系统的管道（pipe）思想，前一级的输出，直接变成后一级的输入，使得在操作上非常简单。

Github:

<https://github.com/gulpjs/gulp>

官方网站：

<http://gulpjs.com/>

官方文档：

<https://github.com/gulpjs/gulp/blob/master/docs/API.md>

其他教程：

* [前端构建工具gulpjs的使用介绍及技巧](http://www.cnblogs.com/2050/p/4198792.html)
* [前端构建工具gulp入门教程](http://www.tuicool.com/articles/FJVNZf)
* [gulp使用小结](https://www.cnblogs.com/Darren_code/p/gulp.html)

**4.Bower**

Bower是一个客户端技术的软件包管理器，它可用于搜索、安装和卸载如JavaScript、HTML、CSS之类的网络资源。其他一些建立在Bower基础之上的开发工具，如YeoMan和Grunt。

Bower与Npm：

简单的说，npm是进行后端开发中，使用的模块安装工具，而bower，是前端的模块安装工具。比如，在安装express，socket.io时，当然使用的是npm，那么比如bootstrap，jquery等前端框架，需要使用bower，npm
是伴随 Node.js 出现的一个包管理器，最开始只能支持 Node.js 的模块管理，但是后来，
npm 官网经过一次改版，打出的口号是，javascript
的包管理器，所以，其已经不在局限于是Node.js 的模块管理了，已经通用到了所有 js
的包管理工具了，可以说，前后通吃了。bower
的话，从一开始，就是专门为前端表现设计的包管理器，一切全部为前端考虑的。npm 和
bower 的最大区别，就是 npm 支持嵌套地依赖管理，而
bower只能支持扁平的依赖（嵌套的依赖，由程序员自己解决）。嵌套依赖，指的就是，你依赖的软件包，还有它自己的依赖，好像摘葡萄，一摘一大串。在服务器环境的时候，这并没什么关系，因为存储空间够大，一切代码都是本地运行，只要解决完依赖就行了，但是到了用户产品的浏览器里，就很成问题了，你不能让用户去下载好几M的js代码，那就太糟糕了。在这个情况下，就需要程序员自己手动解决用到的类库的嵌套依赖问题。比如确保各种各样的插件都依赖同一个版本的jQuery。为什么有很多项目
bower 和 npm 都用呢，那是因为要用 bower 管理前端的包，而用 npm
去管理一些后端的包和构建工具，例如，yeoman，grunt，gulp，jshint
等等等等。所有的包管理器，都有自己的弊端，要视需要选用对自己的项目最合适的。

最新更新于2018年1月17日：

Bower已经过时，作者也不在进行维护，包管理工具已经是npm的天下，不过yarn也在快速崛起，值得研究。

Github:

<https://github.com/bower/bower>

官方网站：

<https://bower.io/>

官方教程：

<https://bower.io/#getting-started>

其他教程：

* [bower简明入门教程](https://segmentfault.com/a/1190000002971135)

**5.Browserify­**

browserify是一个编译工具,通过它可以在浏览器环境下像nodejs一样使用遵循commonjs规范的模块化编程。你可以使用browserify来组织代码,也可以使用第三方模块,不需要会nodejs,只需要用到node来编译,用到npm来安装包.browserify模块化的用法和node是一样的,所以npm上那些原本仅仅用于node环境的包,在浏览器环境里也一样能用。

Github:

<https://github.com/browserify/browserify>

官方网站：

<http://browserify.org/>

官方教程：

<https://github.com/substack/node-browserify#usage>

学习资料

* [browserify使用手册](http://www.tuicool.com/articles/IFvQ3qv)
* [前端模块及依赖管理的新选择：Browserify](https://segmentfault.com/a/1190000002941361)
* [browserify使用手册](http://www.cnblogs.com/liulangmao/p/4920534.html)

**6.Browsersync**

Browsersync能让浏览器实时、快速响应您的文件更改（html、js、css、sass、less等）并自动刷新页面。更重要的是
Browsersync可以同时在PC、平板、手机等设备下进项调试。您可以想象一下：“假设您的桌子上有pc、ipad、iphone、android等设备，同时打开了您需要调试的页面，当您使用browsersync后，您的任何一次代码保存，以上的设备都会同时显示您的改动”。无论您是前端还是后端工程师，使用它将提高您30%的工作效率。

Github:

<https://github.com/BrowserSync/browser-sync>

教程：

* [Browsersync中文网](http://www.browsersync.cn/)

**7.Less-.less,Saas-.scss**

Sass,Less 是一门 CSS 预处理语言，它扩展了 CSS
语言，增加了变量、Mixin、函数等特性，使 CSS 更易维护和扩展。Less 可以运行在 Node
或浏览器端。

less 官网：

<http://lesscss.org/>

less中文网：

<http://lesscss.cn/>

sass官网：

<http://sass-lang.com/>

sass中文网：

<https://www.sass.hk/>

**8.Es6**

ECMAScript 6
（以下简称ES6）是JavaScript语言的下一代标准。因为当前版本的ES6是在2015年发布的，所以又称ECMAScript
2015.也就是说，ES6就是ES2015。

站内资源：

* [ECMAScript 6 笔记](https://github.com/liuyuqin1991/polaris/blob/master/frontend/note/ES6%E7%AC%94%E8%AE%B0.md)

站外资源：

* [深入实践 ES6 Proxy & Reflect](https://zhuanlan.zhihu.com/p/60126477)

教程：

* [阮一峰ECMAScript 6 入门](http://es6.ruanyifeng.com)

**9.Babel**

Babel是一个广泛使用的转码器，可以将ES6代码转为ES5代码，从而在现有环境执行。

Github:

<https://github.com/babel/babel>

官方网站：

<http://babeljs.io/>

教程：

<http://babeljs.cn/>

其他：

* [babel7使用手册](https://mp.weixin.qq.com/s/AURDiWwspdfRExopNf4YLQ) 
* [一口(很长的)气了解 Babel](https://github.com/easonyq/easonyq.github.io/blob/master/%E5%AD%A6%E4%B9%A0%E8%AE%B0%E5%BD%95/others/babel.md)

**10.promise**

Promise是抽象异步处理对象以及对其进行各种操作的组件。JavaScript的异步执行都是以回调函数来执行的。Promise可以简化回调并提供链式异步调用。

教程：

<http://liubin.org/promises-book/>

相关资料：

* [从 filter 聊到 Promise](https://juejin.im/post/5c91afdcf265da60fe7c2613)

**11.Express.js**

基于Node.js平台，快速、开放、极简的 web 后端开发框架。

Github:

<https://github.com/expressjs/express>

官方网站：

<http://expressjs.com/>

中文网：

<http://www.expressjs.com.cn/>

**12.Fontawesome**

Font Awesome 字体为您提供可缩放矢量图标,它可以被定制大小、颜色、阴影以及任何可以用CSS的样式。

Github:

<https://github.com/FortAwesome/Font-Awesome>

官方地址：

<http://www.fontawesome.com.cn/>

**13.yarn**

Yarn 是一个依赖管理工具。它能够管理你的代码，并与全世界的开发者分享代码。Yarn
是高效、安全和可靠的，你完全可以安心使用，与npm属于同一类型的库

中文官方教程：

<https://yarn.bootcss.com/docs/getting-started.html>

其他教程：

* [Yarn：一个新的JavaScript包管理器](http://mp.weixin.qq.com/s/FnCa0wqdHKQN4syrPIPSAA)

**14.ESLint**

提供一个插件化的javascript代码检测工具

Github：

<https://github.com/eslint/eslint>

官网：

<https://eslint.org/>

中文网教程：

<http://eslint.cn/>

其他教程：
* [搞懂 ESLint 和 Prettier](https://zhuanlan.zhihu.com/p/80574300)

**15.typescript**

TypeScript 是 JavaScript 的类型的超集，它可以编译成纯 JavaScript。编译出来的
JavaScript 可以运行在任何浏览器上。TypeScript
编译工具可以运行在任何服务器和任何系统上。TypeScript 是开源的。

Github：

<https://github.com/Microsoft/TypeScript>

教程：

<https://www.tslang.cn/>

<https://ts.xcatliu.com/introduction/what-is-typescript.html>

相关资源：

* [从 JavaScript 到 TypeScript](http://muyunyun.cn/posts/66a54fc2/index.html)
* [TypeScript 实践分享](https://juejin.im/post/5a9c004a6fb9a028b92c9e91)
* [TypeScript 和 Babel：一场美丽的结合](https://juejin.im/post/5c822e426fb9a04a0a5ffb49)
* [TypeScript - 一种思维方式](https://zhuanlan.zhihu.com/p/63346965)
* [TypeScript简介全集](http://blog.ayqy.net/)
* [TypeScript —— 面向编辑器编程](https://zhuanlan.zhihu.com/p/62292091)

**16.PWA**

PWA（Progressive Web App）是一种理念，使用多种技术来增强web app的功能，可以让网站的体验变得更好，能够模拟一些原生功能，比如通知推送。在移动端利用标准化框架，让网页应用呈现和原生应用相似的体验。

相关资料：

* [什么是 PWA](https://juejin.im/post/5a9e8ad5f265da23a40456d4)
* [关于PWA，你需要注意这9点](https://mp.weixin.qq.com/s/3JgScJUbEPWL0wRDn28kkA)
* [为什么我们应该关注下 PWA?](https://mp.weixin.qq.com/s/6b479imf6UdIo1H7AC2PTw)
* [企鹅辅导课程详情页毫秒开的秘密 - PWA 直出](https://mp.weixin.qq.com/s/A6B7lyo_VrElJAiHNctDkA)
* [带你走进PWA在业务中的实践方案](https://mp.weixin.qq.com/s/KYTAUVuP1Jd0BukOjT_z7Q)

**17.Flutter**

Flutter是谷歌的移动UI框架，可以快速在iOS和Android上构建高质量的原生用户界面。 Flutter可以与现有的代码一起工作。在全世界，Flutter正在被越来越多的开发者和组织使用，并且Flutter是完全免费、开源的。

相关资料：

* [我看完掘金上的227篇文章，总结出一份Flutter入门教程](https://juejin.im/post/5b3c8a4be51d4519935860d5)