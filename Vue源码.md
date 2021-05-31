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

##### 调试源码

1. 从github搜索vue-next, 拷贝最新的tag版本到本地文件夹
2. 通过yarn install安装依赖，yarn dev启动项目
3. 在packages/vue/examples文件夹下新建demo进行练习调试，查看源码是怎样实现的(debugger要加上)



## 源码阅读

### Vue 2.x options

课程：源码阅读-5/14日课

位置：`runtime-core/src/component.ts`  & `componentOptions.ts`

关于opitons这些选项在Vue源码中的处理，以及是怎样和template中元素绑定的事件对应起来的(通过ctx这个对象实现的)

1. methods
2. computed

### 虚拟DOM、diff算法

课程：源码阅读-5/17课

位置：`runtime-core/src/renderer.ts`  & `componentOptions.ts`

### v-model双向绑定原理

课程：源码阅读-5/21课

位置：`runtime-dom/directives/vModel.ts`

>  v-model的双向绑定原理其实很简单，就是将当前input框的输入的值，赋值给input框绑定的变量，这样实现双向绑定
>
> `<input v-model="searchText">`
>
> 相当于@input="searchText = $event.target.value"
