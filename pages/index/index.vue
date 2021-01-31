<template>
	<view class="container">
		<v-tabs v-model="current" :tabs="tabs" @change="changeTab" class="tab"></v-tabs>
		<view class="coupon" ref="coupon">
			<view class="item" v-for="(v, i) in couponList" @click="toCoupon(i)" :key="i">
				<view class="top">
					<view class="left">
						<view class="content">
							<image :src="v.icon" class="icon" mode="widthFix" />
							<view class="name">{{ v.name }}</view>
						</view>
						<view class="text" v-if="v.type == 1">天天可领</view>
						<view class="text" v-else-if="v.type == 2">限时秒杀</view>
					</view>
					<view class="right">免费领取</view>
				</view>
				<view class="bottom">
					<image :src="v.bannerPic" mode="widthFix" />
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				current: 0,
				tabs: [{
						"_id": {
							"$oid": "60155f5421a3040001350f96"
						},
						"icon": "/static/all.png",
						"tabId": 0,
						"text": "全部"
					},
					{
						"_id": {
							"$oid": "60155f5421a3040001350f98"
						},
						"icon": "/static/meituan.png",
						"tabId": 2,
						"text": "美团"
					},
					{
						"_id": {
							"$oid": "60155f5421a3040001350f99"
						},
						"icon": "/static/jd.png",
						"tabId": 3,
						"text": "京东"
					},
					{
						"_id": {
							"$oid": "60155f5421a3040001350f97"
						},
						"icon": "/static/ele.png",
						"tabId": 1,
						"text": "饿了么"
					},
					{
						"_id": {
							"$oid": "60163401665c3900014ea5ca"
						},
						"icon": "https://img-blog.csdnimg.cn/20210131123847141.png",
						"text": "橙心优选",
						"tabId": 4
					}

				],
				couponList: [],
				coupons: [{
						"_id": {
							"$oid": "5fe62b3eee98e30001cb59d0"
						},
						"bannerPic": "/static/coupon/meituan_banner.png",
						"icon": "/static/coupon/meituan.png",
						"minapp": {
							"appid": "wx2c348cf579062e56",
							"path": "outer_packages/r2xinvite/coupon/coupon?inviteCode=NnOIp-QOs8SiYF1dcSlL5r8phPrCf6qkH7evMyjIoup2NXxNCLYcBbd3bqpv2X2IWTcwWnu8FWalYrL6rB4nEogky0MwdrTa0OeltYyn2sIyfrnrBnlaeNLdKMNZBOGb82G3uByW5JEsf_XoD-_TdTyyKE2IlC762vKlLkkjfog"
						},
						"name": "美团外卖红包",
						"sort": 99,
						"tabId": 2,
						"type": 1,
						"url": "http://dpurl.cn/qWQQFhJ"
					}, {
						"_id": {
							"$oid": "5fe62b3eee98e30001cb59cf"
						},
						"bannerPic": "/static/coupon/ele_banner.png",
						"icon": "/static/coupon/ele.png",
						"minapp": {
							"appid": "wxece3a9a4c82f58c9",
							"path": "pages/sharePid/web/index?scene=https://s.click.ele.me/FXCJbru"
						},
						"name": "饿了么红包",
						"sort": 100,
						"tabId": 1,
						"type": 1,
						"url": "https://s.click.ele.me/frZOjvu"
					}, {
						"_id": {
							"$oid": "5fe62b3eee98e30001cb59d1"
						},
						"bannerPic": "/static/coupon/sanzhisongshu.png",
						"icon": "/static/coupon/jd.png",
						"minapp": {
							"appid": "wx91d27dbf599dff74",
							"path": "pages/union/proxy/proxy?spreadUrl=https%3a%2f%2funion-click.jd.com%2fjdc%3fe%3d%26p%3dAyIGZRhZFAIRAF0SXxMyEgZUGloTChEFUxlfJUZNXwtEa0xHV0YXEEULWUpYA0wPSh1JUkpJBUkcSkIBR0RMR05aW1kBUQ4SBlQaWhMKEQVTGV8CQh5zLGs%252BYnF1RiNiI3V2W2wWYy5ye3BdNRk7XQprZQ9nH2FnamE3Uh1edVoOPH8oYQBlX1x7OUxhV2Q3ZCJuYWVEImInd3VLbApjK35JRk4iWj1eeWpwD04MYl16Vyx4IFF0a3sGYDsBAGcTV25rbkJzTAATU3ZhckMFTwFLVnQPPWYCdQ4eN1QrWBQCEgNWHlwSBiI3VRxrQ2wSBlQaWhUGEQBcK1olAhUHVhpcFwEVAVAaUiUFEg5lQA57BxdSVB1YQVIXVVdOCSUyIgRlK2sVASIEZVk1FwdADlwaDhcKEg9QHg4WUUIGBh9SEgAWUlIbWEILQARlGVoUBhs%253D"
						},
						"name": "三只松鼠大礼包",
						"sort": 98,
						"tabId": 3,
						"type": 0,
						"url": "https://u.jd.com/wg5FOR5"
					}, {
						"_id": {
							"$oid": "601632c5157a0c000182ad15"
						},
						"bannerPic": "https://img-blog.csdnimg.cn/20210131124604470.png",
						"icon": "https://img-blog.csdnimg.cn/20210131123847141.png",
						"minapp": {
							"appid": "wxd7fa7df243b05aed",
							"path": "cx-cpc/views/index/index?trace_id=0a56473a601637b068f431b90bfa8f02&share_source_id=60052&biz_channel_id=666005&origin=&root_xpsid=951ba84b15894f4ab11ecaae334f31bf&xpsid=951ba84b15894f4ab11ecaae334f31bf&f_xpsid=951ba84b15894f4ab11ecaae334f31bf&page=invitee&share_code=bvqh43opqfrs8udvav1g00&dchn=nLAEd3"
						},
						"name": "橙心优选",
						"tabId": 4,
						"type": 0,
						"sort": 97
					}

				]
			};
		},
		onLoad(e) {
			// this.getHome()
			//#ifdef H5
			let tabId = this.$route.query.tabId ? parseInt(this.$route.query.tabId) : 0
			//#endif
			//#ifdef MP-WEIXIN
			let tabId = e.tabId ? parseInt(e.tabId) : 0
			//#endif
			for (let i in this.tabs) {
				if (tabId == this.tabs[i].tabId) {
					this.current = parseInt(i)
				}
			}
			this.changeTab(this.current)
		},
		onShareAppMessage(res) {
			return getApp().shareConfig()
		},

		onShareTimeline(res) {
			return getApp().shareConfig()
		},
		methods: {
			changeTab(index) {
				console.log('当前选中的项：' + index);
				this.couponList = []
				uni.showLoading({
					title: '获取优惠中'
				});
				if (index == 0) {
					this.couponList = this.coupons
				} else {
					for (let i in this.coupons) {
						if (this.coupons[i].tabId == this.tabs[index].tabId) {
							this.couponList.push(this.coupons[i])
						}
					}
				}
				//#ifdef H5
				this.$nextTick(() => {
					this.$refs.coupon.scrollTop = 0;
				})
				//#endif
				setTimeout(() => {
					uni.hideLoading()
				}, 500)
			},
			toCoupon(i) {
				console.log(this.couponList[i])
				//h5
				//#ifdef H5
				window.location.href = this.couponList[i].url
				//#endif
				//微信小程序
				//#ifdef MP-WEIXIN
				if (this.couponList[i].minapp) {
					wx.navigateToMiniProgram({
						appId: this.couponList[i].minapp.appid,
						path: this.couponList[i].minapp.path,
						success(res) {
							// 打开成功
						}
					})
				}
				//#endif
			},
			getHome() {
				uni.request({
					url: getApp().globalData.api.home,
					success: (res) => {
						this.tabs = res.data.data.tabs
						this.coupons = res.data.data.coupons
						this.changeTab(0)
					}
				});
			}
		}
	};
</script>

<style lang="scss">
	page {
		background-color: #f8f8f8;
	}

	.container {
		font-size: 14px;
		line-height: 24px;
		position: relative;

		.tab {
			position: fixed;
			top: var(--window-top);
			left: 0;
			z-index: 9999;
		}

		.coupon {
			padding-top: 200rpx;
			padding-bottom: 10rpx;

			.item {
				background-color: #ffffff;
				margin: 30rpx;
				border-radius: 10rpx;
				padding: 0 30rpx 30rpx 30rpx;

				.top {
					height: 116rpx;
					display: flex;
					align-items: center;
					justify-content: space-between;

					.left {
						height: 116rpx;
						width: 400rpx;
						display: flex;
						align-items: center;
						justify-content: space-between;

						.content {
							width: 100%;
						}

						.icon {
							display: inline-block;
							vertical-align: bottom;
							width: 52rpx;
							height: auto;
						}

						.name {
							text-align: left;
							display: inline-block;
							vertical-align: bottom;
							font-size: 34rpx;
							color: #000;
							line-height: 50rpx;
							font-weight: bold;
							margin-left: 15rpx;
						}

						.text {
							width: 150rpx;
							height: 38rpx;
							line-height: 38rpx;
							text-align: center;
							font-size: 24rpx;
							color: #61300e;
							background: linear-gradient(90deg, #f9db8d, #f8d98a);
							border-radius: 6rpx;
						}
					}

					.right {
						width: 170rpx;
						height: 60rpx;
						border-radius: 30rpx;
						background: linear-gradient(90deg, #ec6f43, #ea4a36);
						color: #fff;
						font-size: 28rpx;
						line-height: 60rpx;
						text-align: center;
					}
				}

				.bottom {
					height: auto;
					width: 100%;

					image {
						display: block;
						width: 100%;
						height: auto;
					}
				}
			}
		}
	}
</style>
