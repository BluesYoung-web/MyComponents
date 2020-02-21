# 使用说明

- 依赖/common/common.less

```vue
<template>
	<view class=" flex flex-direction-column">
		<!-- 消息面板 -->
		<view class="content" id="content">
			<scroll-view scroll-y="true" :scroll-with-animation="true" :style="{height: style.scrollHeight + 'px'}"
			 :scroll-top="scrollTop" id="sc">
			 <view class="scrollview">
			 	<msg-item v-for="(item, index) in messages" :message="item" :id="index" :key="index+'l1'"></msg-item>
			 </view>
			</scroll-view>
		</view>
	</view>
</template>

<script>
	import msgItem from '@/components/young-msg-item/young-msg-item.vue';
	export default {
		components: {
			  msgItem
		},
		data() {
			return {
                messages
			}
		},
	}
</script>

<style>
	page{
		background-color: #F6F6F6;
	}
	.content {
		display: flex;
		/* flex: 1; */
		/* margin-bottom: 100px; */
	}
```
