# 使用说明

- 依赖/common/common.less
- 依赖/static/img/searchFriend.png
- 依赖/static/img/delete.png

```vue
<template>
	<view class="content">
		<view class="search flex flex-jc bg-fff pd-tp20 pd-bt20">
			<search-input width="600upx" border="none" backgroundColor="#efeff4" bdRadius="50upx" placeholder="输入好友名称"  @getInputMsg="input"></search-input>
		</view>
	</view>
</template>

<script>
	import searchInput from '@/components/young-search-input/young-search-input.vue';
	export default {
		components: {
			searchInput,
		},
		data() {
			return {
			}
		},
		methods: {
			/**
			 * e为输入的值
			 */
			input(e){
				//
			},
	}
</script>

<style>
	page {
		display: flex;
		flex-direction: column;
		box-sizing: border-box;
		background-color: #efeff4;
		min-height: 100%;
		height: auto;
	}
	.search{
		width: 750upx;
		background-color: #FFFFFF;
	}
</style>

```
