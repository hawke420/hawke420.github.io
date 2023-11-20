# 学习记录
## 这些npm操作都应该是项目的根目录操作！！！
1.npm run dev 可以看效果

2.npm run build 然后需要的是dist文件夹，同时可以先把其他文件删了【全删就可以，后续用http-server可以下载回来需要的node_modules下的一些文件】

3.在项目的文件**【现在项目就是dist文件夹（可以给disk重命名成自己的项目名称）】**下进行npm install http-server
(base) xiaoyu@yudeMacBook-Air ~/Documents/Docker/projects/hawke420.github.io ±main⚡ » npm run build

当您运行 npm install http-server 命令时，npm 会从 npm registry 下载 http-server 包，并将其安装到项目的 node_modules 目录中。默认情况下，node_modules 目录位于您运行该命令的当前工作目录下。

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

实现一个简单的父组件和子组件的通信
场景是这样的：父组件中有一个按钮，点击这个按钮，会控制子组件中的某一个<div></div>块是否显示。
这里我对问题是这么分解的：使用v-bind，简化就是: 。将父组件中的值传给子组件，子组件中设置prop的require=true（一定要接收这么个值），ref(*)表示响应性引用，提供.value来访问或者是修改值。在模板中使用 ref 创建的引用时，不需要使用 .value，Vue 会自动进行解包。但在 JavaScript 部分，你需要使用 .value 来访问和修改引用的值。要在模板中使用 v-bind 绑定一个 ref 创建的响应式引用，你不需要使用 .value。Vue 3 在模板中会自动解包引用，所以你可以直接在模板中使用 v-bind，就像你在绑定普通变量一样。
其次由于这里使用了 v-bind 实现了一个选择显示不同src来源图片的功能，发现有一个问题是在模版中使用默认的当前目录是项目，而在js中（没有用到模版功能？）默认是当前的文件目录。
在模板中，相对路径是相对于 public 文件夹的。而在 JavaScript 部分，相对路径是相对于当前文件所在的位置的。



把音乐播放器嵌入进去，还没有进行设计。当然也可以使用默认的`controls`参数。但是这里我就是隐藏了，父组件App中点击同时控制audio控件是否播放，运用了一个`watch`的命令，同时使用`onMounted`来在组件挂载后获取音频元素的引用。这是因为在组件挂载之前，DOM元素可能还不存在，所以我们需要等到组件挂载后才能安全地访问它。由于子组件中的props是一个只可读的内容，如果想要在内部修改就要使用`ref(props.xxx)`或者是`reactive`。如果只是访问但是又要作为引用在watch中，一般利用一个ref不能同步绑定父组件中的值更新【`watch` 函数只能观察响应式引用的值的变化。如果 `props.isPlaying` 不是一个响应式引用，你需要使用 `ref` 或 `reactive` 函数来创建一个响应式引用。】但直接用props.isPlaying不太行，所以这里利用了一个返回值【本质是执行了一个返回函数】。

```javascript
watch(()=>props.isPlaying,(newVal))=>{
  if(...){
     ...
     }else{
    ...
  }
}
```

