<template>
	<view class="page">

		<!-- 个人中心，反馈 -->
		<view class="userInfo">

			<image src="../../static/userDeafualt.png" class="icon" @click="toUserInfo"></image>
			<view style="font-size: 16rpx;" @click="toUserInfo">个人中心</view>

			<image src="../../static/routine.png" class="icon" @click="toRoutine"></image>
			<view style="font-size: 16rpx;" @click="toRoutine">推荐路线</view>
		</view>

		<!-- 地图 -->
		<web-view src="../../static/map.html"></web-view>

		<!-- 底部弹出层 -->
		<view :class="'tail '+(this.pop?'after_pop':'before_pop')">

			<!-- 搜索栏，拉起按钮 -->
			<view class="header">
				<uni-search-bar class="search" @confirm="confirm" @input="input" v-model="text" radius="25"
					@cancel="cancelSearch"></uni-search-bar>
				<image :class="'back '+ (this.rotate_pop?'after_r':'before_r')" src="../../static/svg/back_1.svg"
					@click="popUp">
				</image>
			</view>

			<!-- 折叠 -->
			<view class="fold" @click="foldUp">
				<image src="../../static/svg/back_1.svg" :class="this.rotate_fold?'after_r':'before_r'"></image>
			</view>
			<!-- 存放button的容器 -->
			<view :class="'main '+(this.fold?'after_fold':'before_fold')">
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
			<!-- 存放搜索结果 -->
			<view class="result" v-if="showResult">
				<view class="result_item" v-for="val,index in tabledata">
					<view class="title">{{val.title}}</view>
					<view class="content">
						<view class="location">{{val.content}}</view>
						<view class="comment">
							<view>
								<image src="../../static/svg/star.svg" style="width: 20rpx;height: 20rpx;"
									v-for="v in 5"></image>
							</view>

							<view>
								￥13
							</view>
							<view>
								特色菜
							</view>
							<view style="background-color: #68c5fe;border-radius: 6rpx;">
								<view class="font_2">连锁</view>
							</view>
						</view>
						<view class="time">
							<image src="../../static/svg/time.svg"></image>
							<view>10:00-22:00</view>
						</view>

					</view>
				</view>
			</view>
		</view>
	</view>

</template>

<script>
	export default {
		data() {
			return {
				rotate_pop: false,
				rotate_fold: false,
				pop: false,
				fold: false,
				showResult:false,
				text: "",
				tabledata: [{
						title: "烤鸭饭",
						content: "学一食堂"
					},
					{
						title: "烤鸭饭",
						content: "学一食堂"
					}, {
						title: "烤鸭饭",
						content: "学一食堂"
					}, {
						title: "烤鸭饭",
						content: "学一食堂"
					}, {
						title: "烤鸭饭",
						content: "学一食堂"
					}, {
						title: "烤鸭饭",
						content: "学一食堂"
					}, {
						title: "烤鸭饭",
						content: "学一食堂"
					}, {
						title: "烤鸭饭",
						content: "学一食堂"
					}, {
						title: "烤鸭饭",
						content: "学一食堂"
					}, {
						title: "烤鸭饭",
						content: "学一食堂"
					}
				]
			}
		},
		onLoad() {

		},
		methods: {
			confirm() {

			},
			toUserInfo() {
				uni.navigateTo({
					url: "/pages/userInfo/userInfo",

				})
			},
			toRoutine() {
				uni.navigateTo({
					url: "/pages/routine/routine",

				})
			},
			input() {
					this.pop = true;
					this.rotate_pop = true;
					this.fold = true;
					this.rotate_fold = true;
					this.showResult=true;
			},
			cancelSearch() {},
			popUp() {
				this.pop = !this.pop;
				this.rotate_pop = !this.rotate_pop;
			},
			foldUp() {
				this.fold = !this.fold;
				this.rotate_fold = !this.rotate_fold;
			}
		}
	}
</script>

<style>
	.page {
		height: 100%;
	}

	.userInfo {
		z-index: 10;
		width: 80rpx;
		height: 200rpx;
		padding: 10rpx;
		background-color: #fff;
		border-radius: 20rpx;
		box-shadow: 0px 0px 10rpx #c9c9c9;
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
		box-shadow: 0px 0px 25rpx #c9c9c9;
		position: fixed;
		bottom: -40%;
		background-color: #fff;
		display: flex;
		flex-direction: column;
		align-items: center;
	}

	.icon {
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

	.fold {
		width: 90%;
		height: 50rpx;
		display: flex;
		justify-content: center;
		border-top: 2rpx solid #e2e3e4;
	}

	.fold image {
		width: 40rpx;
		height: 40rpx;
	}

	.main {
		width: 700rpx;
		height: 400rpx;
		display: grid;
		grid-template-columns: repeat(4, 1fr);
		overflow: hidden;
		border-bottom: 2rpx solid #e2e3e4;
	}

	.button {
		width: 100rpx;
		height: 140rpx;
		margin: 30rpx;
		border-radius: 20rpx;
		display: flex;
		flex-direction: column;
		justify-content: space-around;
		align-items: center;
	}

	.button_img {
		width: 100rpx;
		height: 100rpx;
		border-radius: 15rpx;
	}

	.font {
		font-size: 24rpx;
	}

	.result {
		width: 90%;
		flex: 1;
		display: flex;
		flex-direction: column;
		align-items: center;
		overflow: scroll;
	}

	.result_item {
		width: 100%;
		min-height: 170rpx;
		box-sizing: border-box;
		border-bottom: 2rpx solid #e2e3e4;
		margin-top: 6rpx;
	}

	.result_item:active {
		background-color: #e2e3e4;
	}

	.title {
		height: 30%;
		margin-left: 20rpx;
		font-size: 36rpx;
	}

	.content {
		height: 70%;
		margin-left: 20rpx;
		margin-top: 10rpx;
		font-size: 26rpx;
	}

	.comment {
		width: 50%;
		display: flex;
		align-items: center;
		justify-content: space-between;
	}
	.font_2{
		color: #015ec8;
		margin: 3rpx;
		font-size: 20rpx;
	}
	.time{
		height: 30rpx;
		display: flex;
		align-items: center;
	}
	.time image{
		width: 30rpx;
		height: 30rpx;
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

	.before_fold {
		transition: 0.5s;
	}

	.after_fold {
		height: 0;
		transition: 0.5s;
	}

	.before_r {
		transition: .2s;
	}

	.after_r {
		transform: rotate(-180deg);
		transition: .2s;
	}
</style>