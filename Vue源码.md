# Vue3源码阅读

### 回顾Vue & 分析源码

通过CDN形式引入Vue库文件

```javascript
<body>
	<div id="app"></div>

	<script src="./vue.js"></script>
	<script>
        debugger;
		Vue.createApp({
			template: `
				<h2>{{message}}</h2>
				<button @click="touchBtn">按钮</button>
			`,
			data: function() {
				return {
					message: '第一节课'
				}
			},
			methods: {
				touchBtn() {
					console.log('按钮被点击')
				}
			}
		}).mount('#app')
	</script>
</body>
```

##### 分析源码

1. 从github搜索vue-next, 拷贝最新的tag版本到本地文件夹
2. 通过yarn install安装依赖，yarn dev启动项目
3. 在packages/vue/examples文件夹下新建demo进行练习调试，查看源码是怎样实现的(debugger要加上)



##### 源码阅读：

methods中的方法是怎样与view层的函数名对应起来的，通过ctx这个对象实现的



v-model双向绑定原理

runtime-dom/directives/vModel.ts

