<template>
	<view class="container">
		<view class="top">
			<!-- <view class="adContainer">
	            <ad unitId="adunit-3cbbf95869b58c6c"></ad>
	        </view> -->
			<view class="avatar" style="margin-top: 200px;">
				<open-data type="userAvatarUrl"></open-data>
			</view>
			<view class="name">
				<open-data lang="zh_CN" type="userNickName"></open-data>
			</view>
		</view>
		<view class="bottom">
			<view class="eat">{{eatLabel}}</view>
			<view class="start">
				<label class="but _span" @tap="start">{{startLabel}}</label>
			</view>
			<view class="custom-dish" @tap="openSetMean">{ 自定义菜单 }</view>
		</view>
		<nx-set-means ref="setMean" @ok="setOk" />

	</view>

</template>

<script>
	export default {
		data() {
			return {
				startLabel: "开始",
				eatLabel: "今天吃什么?",
				cloudDishContent: "",
				defaultDishString: "盖浇饭 砂锅 大排档 米线 满汉全席 西餐 麻辣烫 自助餐 炒面 快餐 水果 西北风 馄饨 火锅 烧烤 泡面 速冻水饺 日本料理 涮羊肉 味千拉面 肯德基 面包 扬州炒饭 自助餐 茶餐厅 海底捞 咖啡 比萨 麦当劳 兰州拉面 沙县小吃 烤鱼 海鲜 铁板烧 韩国料理 粥 快餐 东南亚菜 甜点 农家菜 川菜 粤菜 湘菜 本帮菜 竹笋烤肉",

			}
		},
		methods: {
			setOk(content) {
				uni.setStorageSync('meanContent',content);
				this.cloudDishContent = content;
			},
			openSetMean() {
				this.$refs.setMean.toggleMask(this.cloudDishContent);
			},
			start() {
				"开始" == this.startLabel ? (this.startLabel = "停止", this.timer = setInterval(this.randEatLabel, 100)) : (this.startLabel =
					"开始",
					clearInterval(this.timer), this.timer = null, this.eatLabel = "今天吃" + this.dish + "吧!");
			},
			randEatLabel() {
				var t = this.dishs[Math.floor(Math.random() * this.dishs.length)];
				this.eatLabel = "今天吃" + t, this.dish = t;
			},
		},
		computed: {
			dishs: function() {
				return this.cloudDishContent.trim().split(/\s+/);
			}
		},
		onShow() {
			this.cloudDishContent = uni.getStorageSync('meanContent') || this.defaultDishString;
		}
	}
</script>

<style scoped>
	page {
		background-color: #f8f8f8;
	}

	.adContainer,
	page {
		width: 100%;
	}

	.container {
		width: 100%;
		text-align: center;
		position: absolute;
	}

	.container .top .avatar {
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

	.container .top .name {
		font-size: 12px;
	}

	.container .bottom {
		position: relative;
		margin-top: 50rpx;
	}

	.container .bottom .eat {
		font-size: 20px;
	}

	.container .bottom .start {
		margin-top: 64rpx;
	}

	.container .bottom .start .but {
		color: #fff;
		font-size: 16px;
		background-color: orange;
		padding: 12rpx 38rpx;
		border-radius: 40rpx;
	}

	.container .bottom .start .but:active {
		background-color: #bfbfbf;
	}

	.container .bottom .custom-dish {
		margin-top: 50rpx;
		font-size: 10px;
		color: grey;
	}

	.container .cu-form-group {
		background-color: #fff;
		font-size: 13px;
	}
</style>
