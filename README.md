在模板  https://github.com/lin-xin/vue-manage-system   的基础上改造
# vue-houtai-moban
后台vue搭建好的模板

封装了token 拦截器

基于 Vue.js + Element UI + axios 的后台管理系统解决方案
本项目基于 vue-cli3 构建，

安装步骤:
git clone https://github.com/lin-xin/vue-manage-system.git      // 把模板下载到本地
cd vue-manage-system    // 进入模板目录
npm install         // 安装项目依赖，等待安装完成之后，安装失败可用 cnpm 或 yarn

// 开启服务器，浏览器访问 http://localhost:8080
npm run serve

// 执行构建命令，生成的dist文件夹放在服务器下即可访问
npm run build

其他注意事项:
一、如果我不想用到上面的某些组件呢，那我怎么在模板中删除掉不影响到其他功能呢？
举个栗子，我不想用 Vue-Quill-Editor 这个组件，那我需要分四步走。

第一步：删除该组件的路由，在目录 src/router/index.js 中，找到引入改组件的路由，删除下面这段代码。

{
    // 富文本编辑器组件
    path: '/editor',
    component: resolve => require(['../components/page/VueEditor.vue'], resolve)
},
第二步：删除引入该组件的文件。在目录 src/components/page/ 删除 VueEditor.vue 文件。

第三步：删除该页面的入口。在目录 src/components/common/Sidebar.vue 中，找到该入口，删除下面这段代码。

{
	index: 'editor',
	title: '富文本编辑器'
},
第四步：卸载该组件。执行以下命令： npm un vue-quill-editor -S

完成。

二、如何切换主题色呢？
第一步：打开 src/main.js 文件，找到引入 element 样式的地方，换成浅绿色主题。

import 'element-ui/lib/theme-default/index.css'; // 默认主题
// import './assets/css/theme-green/index.css';       // 浅绿色主题
第二步：打开 src/App.vue 文件，找到 style 标签引入样式的地方，切换成浅绿色主题。

@import "./assets/css/main.css";
@import "./assets/css/color-dark.css";     /*深色主题*/
/*@import "./assets/css/theme-green/color-green.css";   !*浅绿色主题*!*/
第三步：打开 src/components/common/Sidebar.vue 文件，找到 el-menu 标签，把 background-color/text-color/active-text-color 属性去掉即可。
