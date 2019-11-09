本项目主要是 timzaak 为了尽量复用以前写的零碎 js 代码而做的尝试性项目，其次想是尽量将前端工程化一些。
至于为什么是现在做这种事情，主要前提是：前端的框架目前发展的基本稳定了，在尝试了多种框架后，决定以 Vue 为核心（移动端还是 react-native）。


项目结构如下:
1. 在 packages 目录下存放基础常用的开发工具类封装。根据实际功能划分，拆分成多个 monorepo， 可用 git submodule 进行 package 链接。

2. 在 app 目录下存放多个应用，这些应用需要另开代码仓库，本项目会把 app 目录添加进 .gitignore 中去。

3. 用 lerna bootstrap/lerna link 进行package 之间的链接


模版和开发环境配置改自于 [PanJiaChen/vue-admin-template](https://github.com/PanJiaChen/vue-admin-template)，以后应该也会随着它更新而更新。

相关 Lerno 的实践可参考:
* [Babel monorepo design doc](https://github.com/babel/babel/blob/master/doc/design/monorepo.md)
* [pixari/component-library-monorepo](https://github.com/pixari/component-library-monorepo)

这种开发模式有个问题，就是 lerna 总包和子包的关联关系没法在 GIT 中体现出来。这就很麻烦了。一种临时的解决方案是， 上面的第二步进行变化：用 git submodule 管理子项目。

另外还有另外一种前端开发模式可供参考：[npm 私有包依赖 本地开发调试频繁更新解决方案](https://www.jianshu.com/p/d0c887cf730e), 这种方式也不是很完美，需要多个版本提交。

### 优化版本

1. 在 packages 目录下存放基础常用的开发工具类封装。根据实际功能划分，拆分成多个 monorepo， 用 git submodule 进行 package 管理。

2. 在 app 目录下存放个应用

3. 用 lerna bootstrap/lerna link 进行package 之间的链接

为了方便管理，前期的话，约定： git submodule 会管理 package 的分支，默认该管理分支的最新代码是可用的。`git pull && git submodule update --remote && git submodule foreach -q --recursive 'branch="$(git config -f $toplevel/.gitmodules submodule.$name.branch)"; git checkout $branch;'` 来解决代码更新的问题。

优化版本和前面的解决方案，只有一个差别： app 目录下只会有一个项目。
