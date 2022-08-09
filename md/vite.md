## 定义变量
#### ref
    ref可以定义多种类型变量，使用时需要.value
#### reactive
    reactive只能定义数组或者对象，不能定义其他类型数据，使用不需要.value

## vue2和vue3区别
     vue3相对来说性能提升了，vue2采用数据劫持（Object.dobject.definrProperty）进行双向数据绑定，底层原理使用的是for循环了数据，而vue3使用的是new Proxy新特性，相对于vue2来说，不需要进行for循环，提高了性能。

## webpack  和  vite  区别  ：
    vite改变了数据，只更新改变的那个组件，而webpack改变了数据，会更新所有的组件，vite响应速度更快。

### vite 脚手架搭建
    npm create vite@latest

   #### vue3  setup语法糖插件：
      解决import { ref, reactive, ... }引入的问题
   #### 下载安装：  
      npm i unplugin-auto-import -D
   #### 在vite.config.js文件中配置

      import vue from '@vitejs/plugin-vue';
      //引入插件
      import AutoImport from 'unplugin-auto-import/vite';
      
      const path = requier('path');
      export default defineConfig({
         plugins: [
            vue(),
            AutoImport({
                imports:['vue','vue-router']
            })
         ],
         resolve:{
            //配置路径别名
            alias:{
               '@':path.resolve(_dirname, './src'),
            },
          },
      });
## 安装router
    npm install vue-router@4 -S
## 安装vuex 
    npm install vuex
#### 1.项目根目录，新建router目录
#### 2.在router目录中新建index.js文件
###### 内容：
    import { createRouter,createWebHistory } from "vue-router";
    import Home from "../views/Home.vue";

    const routes =[
       {
           path:"/",
           name:"Home",
           component: Home,
       },
       {
           path:"/about",
           name:"About",
           component: ()=>import("../views/About.vue")
       },
    ];

    const router = createRouter({
       history:createWebHistory(),
       routes,
    });

    export default router;

#### 路由index.js文件配置完成，查照路由新建views文件夹，文件夹内新建Home和About文件
#### 使用，常规使用方法是App.vue文件，<template>内使用<router-view>
<template>
   <router-view></router-view>
</template>

#### main.js文件挂载路由
    import { createApp } from 'vue'
    import App from './App.vue'

    import router from './router'

    createApp(App).use(router).mount('#app')