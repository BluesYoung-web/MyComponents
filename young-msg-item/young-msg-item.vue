<!-- 自定义消息组件 -->
<template>
	<view>
		<view class="m-item" :id="'message'+id">
			<!-- 时间 -->
			<view class="time width-750 flex flex-jc mg-tp20" v-if="message.time.length != 0">
				<text class="ft-26 color-666">{{message.time}}</text>
			</view>
			
			<!-- ------------文字消息-------------- -->
			<view class="" v-if="message.type == 0">
				<view class="flex flex-direction-row width-750 flex-as pd-lt30 mg-tp30" v-if="message.user == 'others'">
					<view class="">
						<image class="head_icon" :src="message.imgUrl" mode="aspectFill"></image>
					</view>
					<view class="left-Textcontent">
						<view class="">
							{{message.content}}
						</view>
					</view>
				</view>
				<view class="flex flex-direction-row width-750 flex-as pd-rt30 flex-je mg-tp30" v-if="message.user == 'myself'">
					<view class="right-Textcontent">
						<view class="">
							{{message.content}}
						</view>
					</view>
					<image class="head_icon" :src="message.imgUrl" mode="aspectFill"></image>
				</view>
			</view>

			<!-- ------------语音消息------------ -->
			<view class="" v-if="message.type == 1">
				<view class="flex flex-direction-row width-750 flex-as pd-lt30 mg-tp30" v-if="message.user == 'others'">
					<view class="">
						<image class="head_icon" :src="message.imgUrl" mode="aspectFill"></image>
					</view>
					<view class="left-Textcontent">
						<view class="">
							<span class="iconfont">&#xe743;</span>
							<text class="mg-lt10">{{message.voiceTime}}'</text>
						</view>
					</view>
				</view>
				<view class="flex flex-direction-row width-750 flex-as pd-rt30 flex-je mg-tp30" v-if="message.user == 'myself'">
					<view class="right-Textcontent">
						<view class="">
							<text class="mg-rt10">{{message.voiceTime}}'</text>
							<span class="iconfont">&#xe743;</span>
						</view>
					</view>
					<image class="head_icon" :src="message.imgUrl" mode="aspectFill"></image>
				</view>
			</view>

			<!-- ------------图片消息------------ -->
			<view class="" v-if="message.type == 2">
				<view class="flex flex-direction-row width-750 flex-as pd-lt30 mg-tp30" v-if="message.user == 'others'">
					<view class="">
						<image class="head_icon" :src="message.imgUrl" mode="aspectFill"></image>
					</view>
					<view class="leftImgMessage">
						<image :src="message.content"  @click="preImg(message.content)" mode="aspectFit"></image>
					</view>
				</view>
				<view class="flex flex-direction-row width-750 flex-as pd-rt30 flex-je mg-tp30" v-if="message.user == 'myself'">
					<view class="rightImgMessage">
						<image :src="message.content"  @click="preImg(message.content)" mode="aspectFit"></image>
					</view>
					<view class="">
						<image class="head_icon" :src="message.imgUrl"  mode="aspectFill"></image>
					</view>
				</view>
			</view>

			<!-- ------------系统消息------------ -->
			<view class="" v-if="message.type == 3">
				
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		name: 'msgItem',
		props: {
			message: {
				type: Object,
				default () {
					return {
						user: "others", //消息发送者： 包括myself-自己、others-其他人
						time: '2019-08-21 21:58', //如果time长度为0说明不显示时间
						type: 0, //消息类型： 包括0-文字消息、1-语音消息、2-图片、3-系统消息
						content: "/static/img/337C393466ABAB31425CE09E655515F9.png",
						imgUrl: "/static/img/finds_01.jpg"
					}
				}
			},
			id: {
				type: Number,
				default: 0
			}
		},
		methods: {
			preImg(imgUrl) {
				// 查看图片详情
				this.$emit('watchImg', imgUrl);
			}
		},
	}
</script>

<style lang="less">
    /* 引入公共样式 */
    @import '~@/common/common.less';
	.m-item {
		display: flex;
		flex-direction: column;
		width: 750upx;
	}

	.head_icon {
		width: 100upx;
		height: 100upx;
		border-radius: 10upx;
	}

	/* ------------文字消息样式------------- */
	.left-Textcontent {
		text-align: left;
		background: #FFFFFF;
		border-radius: 20upx;
		padding: 20upx;
		color: black;
		max-width: 400upx;
		word-break: break-all;
		margin-left: 30upx;
		position: relative;
		font-size: 30upx;
	}

	.left-Textcontent:before {
		border: 8px solid transparent;
		border-right: 8px solid #FFFFFF;
		left: -16px;
		top: 10px;
		width: 0;
		height: 0;
		position: absolute;
		content: ' '
	}

	.right-Textcontent {
		text-align: left;
		background: #03A7E4;
		border-radius: 20upx;
		padding: 20upx;
		color: white;
		max-width: 400upx;
		word-break: break-all;
		margin-right: 30upx;
		position: relative;
		font-size: 30upx;
	}

	.right-Textcontent:after {
		border: 8px solid transparent;
		border-left: 8px solid #03A7E4;
		right: -16px;
		top: 10px;
		width: 0;
		height: 0;
		position: absolute;
		content: ' '
	}

	/* ------------语音消息样式------------- */
	@font-face {
		font-family: 'iconfont';
		src: url('/static/ttf/voice/iconfont.eot');
		src: url('/static/ttf/voice/iconfont.eot?#iefix') format('embedded-opentype'),
			url('/static/ttf/voice/iconfont.woff2') format('woff2'),
			url('/static/ttf/voice/iconfont.woff') format('woff'),
			url('/static/ttf/voice/iconfont.ttf') format('truetype'),
			url('/static/ttf/voice/iconfont.svg#iconfont') format('svg');
	}

	.iconfont {
		font-family: "iconfont" !important;
		font-size: 16px;
		font-style: normal;
		-webkit-font-smoothing: antialiased;
		-moz-osx-font-smoothing: grayscale;
	}

	/* ------------图片消息样式------------- */
	.leftImgMessage image,
	.rightImgMessage image {
		max-width: 400upx;
	}

	.leftImgMessage,
	.rightImgMessage {
		border-radius: 10upx;
		overflow: hidden;
		background-color: #FFFFFF;
	}

	.leftImgMessage {
		margin-left: 20upx;
	}

	.rightImgMessage {
		margin-right: 20upx;
	}
</style>
