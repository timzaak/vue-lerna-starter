本项目主要是 timzaak 为了尽量复用以前写的零碎 js 代码而做的尝试性项目，其次想是尽量将前端工程化一些。
至于为什么是现在做这种事情，主要前提是：前端的框架目前发展的基本稳定了，在尝试了多种框架后，决定以 Vue 为核心（移动端还是 react-native）。

目前项目的思路比较初级，不适合大中型公司，只适合小型或个人。还有很多脚本等需要写。

项目结构如下:
1. 在 packages 目录下存放基础常用的开发工具类封装。根据实际功能划分，拆分成多个 monorepo， 可用 gitmodule 进行 package 链接。

2. 在 app 目录下存放多个应用，这些应用需要另开代码仓库，本项目会把 app 目录添加进 .gitignore 中去。

3. .template 存放模版代码，方便自己开新项目时，进行拷贝，解决格式化代码、 .eslint 配置不一致问题。

4. lerna package.json 配置整个项目的开发环境包。


模版和开发环境配置改自于 [PanJiaChen/vue-admin-template](https://github.com/PanJiaChen/vue-admin-template)，以后应该也会随着它更新而更新。

相关 Lerno 的实践可参考:
* [Babel monorepo design doc](https://github.com/babel/babel/blob/master/doc/design/monorepo.md)
