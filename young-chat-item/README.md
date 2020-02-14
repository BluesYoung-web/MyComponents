- 使用示例：

```js
dataList:[{
  "imgUrl":"http://106.15.53.15:8808/data/head/15.jpg",
  "nick":"Mike",
  "ot":1581644776000,
  "isTop":0,
  "time":"09:46",
  "content":"凉凉",
  "msgNum":1,
  "roomId":"47",
  "conversation":[{
    "time":"09:46",
    "user":"others",
    "content":"凉凉",
    "ot":1581644776000,
    "imgUrl":"http://106.15.53.15:8808/data/head/15.jpg",
    "type":0
  }]
}]
```

```vue
<template>
	<!-- 消息页面，可通过:options 和 :options1 改变滑动开关的样式 -->
	<view>
		<!-- 聊天列表组件 -->
		<chat-item :dataList = "dataList" @clickInto = "onClickInto" @clickChoice = "onClickChoice"></chat-item>
	</view>
</template>

<script>
	import chatItem from '@/components/young-chat-item/young-chat-item.vue';
	export default {
		components: {
			chatItem
		},
		data() {
			return {
				/**
				 * 对话列表
				 */
				dataList: [],
			}
		},
		methods: {
			/**
			 * 直接进入某个聊天室
			 */
			onClickInto(item){
				// ...
			},
			/**
			 * 点击滑动开关
			 */
			onClickChoice(event, item, index){
				switch (event.index){
					case 0:
						//...
						break;
					case 1:
						// ...
						break;
					case 2:
						// ...
						break;
				}
			}
		},
</script>

<style>

</style>
```
