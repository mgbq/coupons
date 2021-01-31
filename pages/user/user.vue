<template>
	<view class="container">
		<view class="head">
			<block>
				<!-- <image :src="userInfo.avatarUrl" class="avatarUrl"></image> -->
				<view class="avatarUrl">
					<open-data type="userAvatarUrl"></open-data>
				</view>
				<view class="nickName">
					<open-data lang="zh_CN" type="userNickName"></open-data>
				</view>
			</block>
			<!-- <block v-else>
				<view class="loginBtn"><button open-type="getUserInfo" lang="zh_CN" @getuserinfo="onGotUserInfo" type="primary">授权登录</button></view>
			</block> -->
		</view>
		<view class="others">
			<view class="item">
				<image class="icon" src="/static/user_share.png"></image>
				<button class="content share" open-type="share">
					<view>分享好友</view>
					<image class="right" src="/static/right_h.png"></image>
				</button>
			</view>
			<view class="item">
				<image class="icon" src="/static/user_hezuo.png"></image>
				<button class="content share" @tap="chouqian">
					<view>抽签小程序</view>
					<image class="right" src="/static/right_h.png"></image>
				</button>
			</view>
			<view class="item">
				<button class="content share">
					<view>作者wx：nxmin68</view>
				</button>
			</view>
			<view class="item">
				<button class="content share">
					<view style="color: red;">例如你有一千个好友(四，五个微信群)，如果每个人一天吃一顿外卖20块，你拿5%
						1000*20*0.05 = 1000
						那就是一千啊！还上什么班？？？
						<br />
						需要小程序赚钱的联系作者QQ:392716797
					</view>
				</button>
			</view>
		</view>
		<view class="version">
			v3.0
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				userInfo: ''
			};
		},
		onLoad() {
			this.userInfo = getApp().globalData.userInfo
		},
		onShareAppMessage(res) {
			return getApp().shareConfig()
		},
		methods: {
			chouqian() {
				uni.navigateToMiniProgram({
					appId: 'wx84941c50415e1255',
					success(res) {
						// 打开成功
					}
				})

			},
			/*登录 */
			onGotUserInfo(e) {
				this.userInfo = e.detail.userInfo
				uni.setStorageSync('userInfo', e.detail.userInfo);
			}
		}
	};
</script>

<style lang="scss">
	page {
		background: #f8f8f8;
	}

	.container {
		padding-bottom: 20rpx;
	}

	.head {
		background: #fff;
		position: relative;
		text-align: center;
		flex-wrap: wrap;
		display: flex;
		align-items: center;
		justify-content: center;
		padding: 20px 0;
		height: 220rpx;
	}

	.head .avatarUrl {
		// width: 120rpx;
		// height: 120rpx;
		// display: block;
		// margin: auto;
		// border-radius: 50%;
		position: relative;
		display: flex;
		-webkit-box-pack: center;
		justify-content: center;
		overflow: hidden;
		width: 150rpx;
		height: 150rpx;
		border-radius: 50%;
		margin: 0 auto 10rpx;
	}

	.head .nickName {
		margin-top: 10rpx;
		text-align: center;
		font-size: 36rpx;
		color: #333;
		width: 100%;
	}

	.head .loginBtn {
		text-align: center;
	}

	.head .loginBtn button {
		display: inline-block;
		background: linear-gradient(90deg, #33cc33, #33bb33);
		font-size: 32rpx;
		height: 70rpx;
		line-height: 70rpx;
		border: none;
		padding: 0 20rpx;
		border-radius: 35rpx;
	}

	.head .loginBtn button::after {
		border: none;
	}

	.head .lot {
		position: absolute;
		bottom: 0;
		left: 0;
		display: flex;
		border-top: 1px solid #f8f8f8;
		width: 690rpx;
		padding: 30rpx;
	}

	.head .lot>view {
		width: 50%;
		text-align: center;
	}

	.head .lot .num {
		color: #333;
		font-size: 32rpx;
		font-weight: 700;
	}

	.head .lot .name {
		color: #666;
		font-size: 28rpx;
	}

	.head .lot .all {
		border-right: 1px solid #f8f8f8;
		box-sizing: border-box;
	}

	.others {
		margin: 20rpx 0;
		background: #fff;
	}

	.others .item {
		display: flex;
		align-items: center;
		width: 690rpx;
		padding: 0 30rpx;
		border-bottom: 1px solid #ededf0;
	}

	.others .item:last-child {
		border-bottom: none;
	}

	.others .item .icon {
		width: 50rpx;
		height: 50rpx;
		margin-right: 30rpx;
	}

	.others .item .content {
		width: 620rpx;
		padding: 30rpx 0;
		display: flex;
		align-items: center;
		font-size: 34rpx;
		color: #333;
	}

	.others .item .content.share {
		background: none;
		text-align: left;
		border: none;
		line-height: normal;
	}

	.others .item .content.share::after {
		border: none;
	}

	.others .item .content .right {
		width: 25rpx;
		height: 25rpx;
		margin-left: auto;
	}

	.version {
		position: fixed;
		bottom: 20rpx;
		display: block;
		width: 100%;
		text-align: center;
		font-size: 28rpx;
		color: #666;
	}
</style>
