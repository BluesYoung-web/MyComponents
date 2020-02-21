# 使用说明

- 依赖/common/common.less

```js
friendsList:[{
"motto":"八极天一式-暴足",
"uid":15,
"avatar":"http://106.15.53.15:8808/data/head/15.jpg",
"tel":"15549451718",
"modifytime":1578968217,
"nick":"Mike"
},{
"motto":"夏夜的雨，秋日的阳。",
"uid":23,
"avatar":"http://106.15.53.15:8808/data/head/231579157407.jpg",
"tel":"",
"modifytime":1579069558,
"nick":"夏雨秋阳"
}]
```

```vue
<template>
	<view class="content">
		<view class="bg-fff pd-tp20">
			<address-item :friendsList="friendsList" @toFriendInfo="toFriendInfo"></address-item>
		</view>
	</view>
</template>

<script>
	import addressItem from '@/components/young-address-item/young-address-item.vue';
	import data from '@/data.js';
	export default {
		components: {
			addressItem
		},
		data() {
			return {
				/**
				 * 用于显示的好友列表
				 */
				friendsList: [],
			}
		},
		/**
		 * 下拉刷新
		 */
		onPullDownRefresh() {
			//请求好友列表数据
			data.user.get_address({
				force: true,
				success: (res) => {
					this.friendsList = res;
					setTimeout(() => {
						uni.stopPullDownRefresh();
					},500);
					console.log(JSON.stringify(this.friendsList));
				},
				fail: (code, err) => {
					console.log(code, err);
				}
			});
		},
		onLoad() {
			uni.startPullDownRefresh();
		},
		onShow() {
			// 从缓存拿数据
			data.user.get_address({
				success: (res) => {
					this.friendsList = res;
					this.allFriend = res;
				},
				fail: (code, err) => {
					console.log(code, err);
				}
			});
		},
		methods: {
			/**
			 * 点击某个好友项
			 */
			toFriendInfo(item){
				uni.navigateTo({
					url: `/pages/addressSubpackage/friendsInfo?uid=${item.uid}&isF=1`
				});
			}
		},
	}
</script>

<style>
</style>

```
