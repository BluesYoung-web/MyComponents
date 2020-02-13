# MyComponents

我的vue组件

## 聊天对话项组件 young-chat-item.vue
- 依赖uni-swipe-action 和 uni-swipe-action-item
- 使用示例：

```vue
<template>
	<!-- 消息页面  -->
	<view>
		<!-- 聊天列表组件 -->
		<chat-item :dataList = "dataList" @clickInto = "onClickInto" @clickChoice = "onClickChoice"></chat-item>
    <!-- 可通过:options 和 :options1 改变滑动开关的样式 -->
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
