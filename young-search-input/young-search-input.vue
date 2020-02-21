<!-- 输入框组件 可以设置背景色、宽度、圆角、边框、占位符 -->
<template>
	<view>
		<view class="search relative" :style="{width: width}">
			<image class="searchIcon absolute" src="/static/img/searchFriend.png" mode=""></image>
			<input v-model="inputMsg" type="text" @input="$emit('getInputMsg', $event.target.value)" class="input" value="" :placeholder="placeholder" :style="{'border-radius': bdRadius, border:border, 'background-color':backgroundColor}" />
			<image src="/static/img/delete.png" @tap="clear" v-show="inputMsg.length != 0" class="iconfont absolute clearIcon"></image>
		</view>
	</view>
</template>

<script>
	export default {
		name: 'searchInput',
		props: {
			//输入框宽度
			width: {
				type: String,
				default: "600upx"
			},
			//圆角
			bdRadius:{
				type: String,
				default: "10upx"
			},
			//边框
			border:{
				type: String,
				default: "1px solid #D5D5D6"
			},
			//占位符
			placeholder: {
				type: String,
				default: "搜索"
				// required: true
			},
			backgroundColor:{
				type: String,
				default: "#ffffff"
			}
		},
		data() {
			return {
				inputMsg:'',
			}
		},
		methods: {
			clear(){
				this.inputMsg = '';
				this.$emit('getInputMsg', this.inputMsg);
			},
		}
	}
</script>

<style lang="less">
	/* 引入公共样式 */
	@import '~@/common/common.less';
	.input {
		padding-left: 64upx;
		width: 100%;
		height: 80upx;
	}
	.searchIcon {
		top: 22upx;
		left: 22upx;
		width: 40upx;
		height:40upx;
	}
	.clearIcon {
		top: 24upx;
		right: 20upx;
		width: 36upx;
		height: 36upx;
	}
</style>
