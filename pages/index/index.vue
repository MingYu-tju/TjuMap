<template>
	<view class="content">
		
		<!-- 个人中心，反馈 -->
		<view class="userInfo">
			<image src="../../static/svg/userCenter.svg" class="icon"></image>
			<view style="font-size: 16rpx;">个人中心</view>
			<image src="../../static/svg/callBack.svg" class="icon"></image>
			<view style="font-size: 16rpx;">反馈</view>
		</view>
		
		<!-- 地图 -->
		<web-view src="../../static/map.html"></web-view>
		
		<!-- 底部弹出层 -->
		<view :class="'tail '+(this.pop?'after_pop':'before_pop')">
			
			<!-- 搜索栏，拉起按钮 -->
			<view class="header">
				<uni-search-bar class="search" @confirm="confirm" @input="input" radius="25"></uni-search-bar>
				<image :class="'back '+ (this.rotate?'after_r':'before_r')" src="../../static/svg/back_1.svg"
					@click="popUp">
				</image>
			</view>
			
			<!-- 存放button的容器 -->
			<view class="main">
				<view class="button">
					<image src="../../static/logo.png" class="button_img"></image>
					<view class="font">美食</view>
				</view>
				<view class="button">
					<image src="../../static/logo.png" class="button_img"></image>
					<view class="font">路线</view>
				</view>
				<view class="button">
					<image src="../../static/logo.png" class="button_img"></image>
					<view class="font">猫猫</view>
				</view>
				<view class="button">
					<image src="../../static/logo.png" class="button_img"></image>
					<view class="font">推荐</view>
				</view>
				<view class="button">
					<image src="../../static/logo.png" class="button_img"></image>
					<view class="font">美食</view>
				</view>
				<view class="button">
					<image src="../../static/logo.png" class="button_img"></image>
					<view class="font">美食</view>
				</view>
				<view class="button">
					<image src="../../static/logo.png" class="button_img"></image>
					<view class="font">美食</view>
				</view>
			</view>
		</view>
	</view>

</template>

<script>
	export default {
		data() {
			return {
				rotate: false,
				pop: false,
				input: ""
			}
		},
		onLoad() {

		},
		methods: {
			confirm() {

			},
			popUp() {
				this.pop = !this.pop;
				this.rotate = !this.rotate;
			}
		}
	}
</script>

<style>
	.content {
		height: 100%;
	}
	.userInfo {
		z-index: 10;
		width: 65rpx;
		height: 200rpx;
		padding: 10rpx;
		background-color: #fff;
		border-radius: 20rpx;
		box-shadow:0px 0px 10rpx #c9c9c9;
		opacity: 0.9;
		position: fixed;
		right: 20rpx;
		top: 200rpx;
		display: flex;
		flex-direction: column;
		justify-content: space-around;
		align-items: center;
	}
	.tail {
		z-index: 1;
		width: 100%;
		height: 60%;
		border-radius: 50rpx 50rpx 0 0;
		box-shadow:0px 0px 25rpx #c9c9c9;
		position: fixed;
		bottom: -43%;
		background-color: #fff;
		display: flex;
		flex-direction: column;
		align-items: center;
	}

	.icon{
		width: 50rpx;
		height: 50rpx;
	}

	.header {
		width: 100%;
		display: flex;
		position: relative;
		align-items: center;
		justify-content: space-around;
	}
	.main{
		width: 90%;
		height: 30%;
		display: grid;
		grid-template-columns: repeat(4,1fr);
	}
	.button{
		width: 100rpx;
		height: 140rpx;
		margin: 30rpx;
		border-radius: 20rpx;
		display: flex;
		flex-direction: column;
		justify-content: space-around;
		align-items: center;
	}
	.button_img{
		width: 100rpx;
		height: 100rpx;
		border-radius: 15rpx;
	}
	.font{
		font-size: 24rpx;
	}
	.search {
		width: 70%;
	}

	.back {
		width: 40rpx;
		height: 40rpx;
		position: absolute;
		right: 40rpx;
	}


	/* 过渡动画 */
	.before_pop {
		transition: .3s;
	}

	.after_pop {
		bottom: 0;
		transition: .3s;
	}

	.before_r {
		transition: .2s;
	}

	.after_r {
		transform: rotate(-180deg);
		transition: .2s;
	}


</style>