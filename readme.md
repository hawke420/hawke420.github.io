# 学习记录
## 这些npm操作都应该是项目的根目录操作！！！
1.npm run dev 可以看效果
2.npm run build 然后需要的是dist文件夹，同时可以先把其他文件删了【全删就可以，后续用http-server下载回来需要的】
3.在项目的文件下进行npm install http-server
(base) xiaoyu@yudeMacBook-Air ~/Documents/Docker/projects/hawke420.github.io ±main⚡ » npm run build
【当您运行 npm install http-server 命令时，npm 会从 npm registry 下载 http-server 包，并将其安装到项目的 node_modules 目录中。默认情况下，node_modules 目录位于您运行该命令的当前工作目录下。】
4.再上传整个项目文件

## 上述都是构建项目然后上传github可以显示，要是本地写的话还是先npm run dev 看效果。因为写的是vue文件，自动构建成css/js等文件的
npm run build 的目的是将项目从开发阶段转移到生产阶段。在开发阶段，您可能会使用 npm run dev 或类似的命令来启动本地开发服务器，以便实时查看和测试您的应用程序。这通常包括一些额外的调试和开发工具。

而当您准备将应用程序部署到生产环境时，您希望对代码进行优化、压缩，并删除不必要的调试信息和文件。这就是 npm run build 发挥作用的时候。

在 Vue.js 项目中，npm run build 会执行一系列操作，包括但不限于：

将 Vue 单文件组件编译成普通的 JavaScript、CSS 文件。
压缩和混淆 JavaScript 代码。
压缩 CSS。
复制静态资源，如图片和字体文件，到适当的目录。
生成一个用于部署的 dist 目录，其中包含了所有经过优化的文件。
这样，**您就可以将 dist 目录的内容部署到 Web 服务器上**，以提供给最终用户。最终生成的文件通常更小，加载速度更快，适用于生产环境。