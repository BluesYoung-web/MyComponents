# 使用示例

## 属性

- type 对应的类型

type | des
--- | ---
0 | 左边标题，右边图片和右箭头
1 | 左边标题，右边内容和右箭头（默认值）
2 | 左边标题，右边内容
3 | 中间内容

- title 标题，当type=3时无效

- content 内容，当type=0时无效

- avatar 图片url，仅当type=0时有效

```vue
<!-- 编辑资料 -->
<template>
	<view class="body">
		<view class="content flex flex-direction-column">
			<edit-item type="0" title="用户头像" :avatar="user.avatar" @poupChange="openPopup"></edit-item>
			<edit-item type="1" title="昵称" :content="user.nick" @toChange="toChangeName"></edit-item>
			<edit-item type="2" title="来聊账号" :content="user.uid" @cpoy="accountCopy"></edit-item>
			<edit-item type="3" :content="清空聊天记录" @poupChange="showPopup('clearChatLogPopup')"></edit-item>
		</view>
	</view>	
</template>

<script>
	import editItem from '@/components/young-edit-item/young-edit-item.vue';
	import data from '@/data.js';
	export default {
		data() {
			return {
				user:{},
				showPopup: false, //控制弹出框是否显示
				tempFilePath: '',//要裁剪图片的路径
				cropFilePath: '',//裁剪后图片的路径
			}
		},
		onShow() {
			data.user.get_info({
				success: (res) => {
					this.user = res;
				}
			});
		},
		methods: {
			
		},
		components: {
			editItem
		},
	}
</script>

<style lang="less">
	// 引入预先定义好的less
	@import "~@/common/common.less";
	/* 设置页面背景色 */
	page{
		width: @p100;
		height: @p100;
		background-color: @bgcolor;
	}
</style>

```
