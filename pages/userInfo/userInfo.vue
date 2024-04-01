<template>
	<view class="content">
		<view class="userImg">
			<image src="../../static/userDeafualt.png"></image>
		</view>
		<view class="back"> <image src="../../static/userImg_back.png"></image> </view>
		<view class="tail">
			<view class="item" @click="toFuc(0)">
				<view class="font">更改头像</view>
				<image src="../../static/svg/back_1.svg"></image>
			</view>
			<view class="item" @click="toFuc(1)">
				<view class="font">修改密码</view>
				<image src="../../static/svg/back_1.svg"></image>
			</view>
			<view class="item" @click="toFuc(2)">
				<view class="font">修改昵称</view>
				<image src="../../static/svg/back_1.svg"></image>
			</view>
			<view class="item" @click="toFuc(3)">
				<view class="font">个性签名</view>
				<image src="../../static/svg/back_1.svg"></image>
			</view>
			<view class="item" @click="toFuc(4)">
				<view class="font">设置</view>
				<image src="../../static/svg/back_1.svg"></image>
			</view>
			<view class="item" @click="toFuc(5)">
				<view class="font">关于我们</view>
				<image src="../../static/svg/back_1.svg"></image>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				Height: 0
			}
		},
		methods: {
			toFuc(v){
				console.log(v);
			}
		},
		mounted() {
			uni.getSystemInfo({
				success: function(res) {
					this.Height = res.windowHeight
					console.log(res.windowWidth);
					console.log(res.windowHeight);
				}
			});
		}
	}
</script>

<style>
	.content {
		height: 100%;
		overflow: hidden;
		background-color: #f1f2f3;
	}

	.userImg {
		height: 20%;
		display: flex;
		justify-content: center;
		align-items: center;
		background-color:#F4FDFF ;
	}

	.userImg image {
		width: 200rpx;
		height: 200rpx;
		margin: 0 auto;
	}

	.back {
		width: 100%;
		height: 150rpx;
		
	}
	.back image{
		width: 100%;
		height: 100%;
	}
	.tail {
		width: 100%;
		height: 70%;
		margin: 0 auto;
		margin-top: 80rpx;
	}

	.item {
		width: 100%;
		height: 100rpx;
		border-radius: 6rpx;
		background-color: #fff;
		border-bottom: 2rpx solid #e2e3e4;
		display: flex;
		align-items: center;
		position: relative;
	}
	.item:active{
		background-color: #e2e3e4;
	}

	.font {
		margin-left: 100rpx;
		font-size: 32rpx;
	}

	.item image {
		width: 30rpx;
		height: 30rpx;
		transform: rotate(90deg);
		position: absolute;
		right: 30rpx;
	}
</style>