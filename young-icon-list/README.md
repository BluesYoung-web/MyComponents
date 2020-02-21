# 使用说明

- 依赖/common/common.less
- 示例依赖/static/img/my/*

```vue
<template>
	<view class="content">
		<view class="topInfo flex flex-jc relative">
		<icon-list class="mg-tp20" :iconUrl="listMsg[0].iconUrl" :title="listMsg[0].title"></icon-list>
		<icon-list class="mg-tp20" :iconUrl="listMsg[1].iconUrl" :title="listMsg[1].title"></icon-list>
		<icon-list class="mg-tp20" :iconUrl="listMsg[2].iconUrl" :title="listMsg[2].title"></icon-list>
		<icon-list @click="toSetting" class="mg-tp20" :iconUrl="listMsg[3].iconUrl" :title="listMsg[3].title"></icon-list>
	</view>
</template>

<script>
	import iconList from '@/components/young-icon-list/young-icon-list.vue';
	export default {
		components: {
			iconList
		},
		data() {
			return {
				/**
				 * 标签信息
				 */
				listMsg: [{
						iconUrl: "/static/img/my/store.png",
						title: "商店"
					},
					{
						iconUrl: "/static/img/my/score.png",
						title: "战绩"
					},
					{
						iconUrl: "/static/img/my/card.png",
						title: "名片"
					},
					{
						iconUrl: "/static/img/my/setting.png",
						title: "设置"
					},
				],
			}
		},
		methods: {
			/**
			 * 点击设置
			 */
			toSetting() {
				uni.navigateTo({
					url:"../mySubpackage/setting/setting"
				})
			},
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

	.topInfo {
		width: 100%;
		height: 300upx;
		position: relative;
		background: -webkit-linear-gradient(top, #1ccfcf, #ffffff);
		border-bottom-left-radius: 58upx;
		border-bottom-right-radius: 58upx;
	}

	.topTitle {
		height: 70upx;
		width: 690upx;
		border-bottom-right-radius: 10upx;
		border-bottom-left-radius: 10upx;
		background-color: rgba(255, 255, 255, 0.4);
		border: 0.5px solid #fff;
		z-index: 10;
		left: 50%;
		transform: translateX(-50%);
		/* overflow: hidden; */
		top: -10upx;
	}
</style>

```
