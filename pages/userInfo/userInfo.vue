<template>
	<view class="content">
		<view class="userImg"></view>
		<view class="tail">
			<view class="item">
				<view class="font">更改头像</view>
				<image src="../../static/svg/back_1.svg"></image>
			</view>
			<view class="item">
				<view class="font">修改密码</view>
				<image src="../../static/svg/back_1.svg"></image>
			</view>
			<view class="item">
				<view class="font">修改昵称</view>
				<image src="../../static/svg/back_1.svg"></image>
			</view> 
			<view class="item">
				<view class="font">个性签名</view>
				<image src="../../static/svg/back_1.svg"></image>
			</view>
			<view class="item">
				<view class="font">设置</view>
				<image src="../../static/svg/back_1.svg"></image>
			</view>
			<view class="item">
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
				Height:0
			}
		},
		methods: {
			
		},
		mounted() {
			uni.getSystemInfo({
			    success: function (res) {
					this.Height=res.windowHeight
			        console.log(res.windowWidth);
			        console.log(res.windowHeight);
			    }
			});
		}
	}
</script>

<style>
	.content{
		width: 100%;
		height:100vh;
		box-sizing: border-box;
		background-color: #f1f2f3;
	}
	.userImg{
		height: 30%;
		background-color: aquamarine;
	}
	.tail{
		width: 100%;
		height: 70%;
		margin: 0 auto;
		margin-top: 80rpx;
	}
	.item{
		width: 100%;
		height: 100rpx;
		border-radius: 6rpx;
		background-color: #fff;
		border-bottom: 2rpx solid #e2e3e4;
		display: flex;
		align-items: center;
		position: relative;
	}
	.font{
		margin-left: 100rpx;
		font-size: 32rpx;
	}
	
	.item image{
		width: 30rpx;
		height: 30rpx;
		transform: rotate(90deg);
		position: absolute;
		right: 30rpx;
	}
</style>
