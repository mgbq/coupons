<template>
	<view>
		<view :class="['mask',maskState===0?'none':maskState===1?'show':'']">
			<view class="mask-content">
				<view class="mask-content-topbar">
					<view class="left" @tap="cance">取消</view>
					<view class="right" @tap="confirm">确定</view>
				</view>
				<view class="mask-content-input">
					<textarea v-model="content" adjustPosition="true" class="textarea" cursorSpacing="50" :focus="focus" maxlength="1000" showConfirmBar="false"></textarea>
				</view>
				<view class="tips">想吃什么以空格分割输入，例如"面条 米饭 牛排"</view>
			</view>
		</view>


	</view>
</template>

<script>
	export default {
		data() {
			return {
				maskState: 0,
				content: "",
				focus: !1

			};
		},
		methods: {
			toggleMask(content) {
				this.maskState = 1; //显示弹窗
				this.content = content;
				this.focus = true;
			},
			cance() {
				this.maskState = 0;
			},
			confirm() {
				this.$emit('ok', this.content);
				this.cance();
			}

		}
	}
</script>

<style scoped>
	.mask {
		-webkit-box-align: end;
		align-items: flex-end;
		position: fixed;
		left: 0;
		top: 0;
		bottom: 0;
		background: transparent;
		z-index: 9995;
	}

	.mask,
	.mask .mask-content {
		display: flex;
		width: 100%;
		transition: .3s;
	}

	.mask .mask-content {
		background: #fff;
		transform: translateY(100%);
		-webkit-box-orient: vertical;
		-webkit-box-direction: normal;
		flex-direction: column;
	}

	.mask .mask-content .mask-content-topbar {
		display: flex;
		-webkit-box-orient: horizontal;
		-webkit-box-direction: normal;
		flex-direction: row;
		-webkit-box-pack: justify;
		justify-content: space-between;
		padding: 20rpx 30rpx 10rpx;
		font-size: 32rpx;
	}

	.mask .mask-content .mask-content-topbar .left {
		padding: 10rpx 0rpx;
		color: #606266;
	}

	.mask .mask-content .mask-content-topbar .right {
		padding: 10rpx 100rpx;
		border-radius: 6rpx;
		color: #fff;
		font-weight: 500;
		background-color: orange;
	}

	.mask .mask-content .mask-content-input {
		width: 718rpx;
		padding: 10rpx 16rpx 20rpx;
	}

	.mask .mask-content .mask-content-input .textarea {
		height: 100px;
		width: 686rpx;
		font-size: 25rpx;
		text-align: left;
		padding: 16rpx;
		border: 2rpx solid #d5d5d6;
		border-radius: 8rpx;
	}

	.mask.none {
		display: none;
	}

	.mask.show {
		background: rgba(0, 0, 0, .4);
	}

	.mask.show .mask-content {
		transform: translateY(0);
	}

	.mask .tips {
		font-size: 12px;
		color: grey;
	}
</style>
