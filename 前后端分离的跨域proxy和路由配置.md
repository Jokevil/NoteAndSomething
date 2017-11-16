---
title: 前后端分离的跨域proxy和路由配置
tags: proxy,vue-router,前后端分离
grammar_cjkRuby: true
---


### 项目初始化
1.首先是用vue-cli脚手架搭建了一个webpack模板项目

#### 配置proxy
作用：为了前端能访问后台thinkphp的数据库

配置config文件里的 index.js
	proxyTable:{}
	=>
```markdown
config/index.js
	proxyTable: {
      '/api/*':{
	  //target设置你想要请求的后台完整路径
        target: 'http://localhost/files/VueTP/public/',
		//是否跨域 true
        changeOrigin:true,
		//是否路径替换 
        pathRewrite: {
          '^/api': '/'   //相当于是 你前端请求的路径  http://localhost:8080/api/... 
		  				  //=>会被替换为  http://localhost/files/VueTP/public/
        }
      }
    }
```
#### 配置路由
```markdown
router/index.js

import Vue from 'vue'     -->
import Router from 'vue-router'   -->导入vue-router.js
import Login from '@/components/Login'   -->导入组件
import Index from '@/components/index/index'

Vue.use(Router);     //!!!!一定要调用

export default new Router({
  mode: 'history',        // 注意事项：！mode不为history 则默认为hash 路径会自带#开头
  routes: [
    {
      path: '/',
      name: 'Login',
      component: Login,

    },
    {
		//告诉路由路径为 /index的组件是Index
      path: '/index',
      name: 'Index',
      component: Index,
      meta: { requiresAuth: true}     //在访问该路径的时候是否需要验证 
    }

  ]
})
```

```markdown
main.js

import Vue from 'vue'
import App from './App.vue'
import router from './router'                --->导入上面配置好的路由文件
import './assets/css/bootstrap.css'
import './assets/js/bootstrap'
import axios from 'axios'
import sweetalert from 'sweetalert'


Vue.config.productionTip = false;
Vue.prototype.$axios = axios;

/* eslint-disable no-new */
new Vue({
  el: '#app',
  router,                                        --->一定要注入到父组件 
  template: '<App/>',
  components: { App }
})

```

