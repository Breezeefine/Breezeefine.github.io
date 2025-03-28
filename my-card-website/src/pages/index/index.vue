<template>
	<view class="content">
		<!-- 头部横幅 -->
		<view class="banner">
			<text class="banner-title">虚拟信用卡支付解决方案</text>
			<text class="banner-subtitle">安全 · 便捷 · 全球支持</text>
			<button class="cta-button" @click="navigateToProducts">了解更多</button>
		</view>

		<!-- 简介部分 -->
		<view class="intro">
			<text class="section-title">为什么选择我们?</text>
			<text class="intro-text">我们提供专业的虚拟信用卡支付服务，帮助您轻松进行全球支付。无论是个人用户还是企业客户，都能找到适合的解决方案。</text>
		</view>

		<!-- 功能特点 -->
		<view class="features">
			<view class="feature-item" v-for="(feature, index) in features" :key="index">
				<text class="feature-title">{{ feature.title }}</text>
				<text class="feature-desc">{{ feature.description }}</text>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				features: [
					{
						title: '安全保障',
						description: '全方位的安全防护措施，保障您的资金安全'
					},
					{
						title: '全球支持',
						description: '支持多国货币和各类支付通道'
					},
					{
						title: '24/7支持',
						description: '全天候客户服务，随时解决您的问题'
					}
				]
			}
		},
		methods: {
			navigateToProducts() {
				uni.showToast({
					title: '功能开发中',
					icon: 'none'
				})
			}
		}
	}
</script>

<style>
	.content {
		padding: 20px;
	}

	.banner {
		background: linear-gradient(135deg, #6366F1, #3B82F6);
		padding: 40px 20px;
		border-radius: 16px;
		text-align: center;
		color: #fff;
		margin-bottom: 30px;
	}

	.banner-title {
		font-size: 24px;
		font-weight: bold;
		margin-bottom: 10px;
		display: block;
	}

	.banner-subtitle {
		font-size: 16px;
		opacity: 0.9;
		display: block;
		margin-bottom: 20px;
	}

	.cta-button {
		background-color: #fff;
		color: #3B82F6;
		border: none;
		padding: 10px 30px;
		border-radius: 25px;
		font-weight: bold;
	}

	.intro {
		margin-bottom: 30px;
	}

	.section-title {
		font-size: 20px;
		font-weight: bold;
		margin-bottom: 15px;
		display: block;
	}

	.intro-text {
		font-size: 16px;
		color: #666;
		line-height: 1.6;
		display: block;
	}

	.features {
		display: flex;
		flex-direction: column;
	}

	.feature-item {
		background: #fff;
		padding: 20px;
		border-radius: 12px;
		box-shadow: 0 2px 8px rgba(0,0,0,0.1);
		margin-bottom: 15px;
	}

	.feature-title {
		font-weight: bold;
		margin-bottom: 10px;
		font-size: 18px;
		display: block;
	}

	.feature-desc {
		font-size: 14px;
		color: #666;
		display: block;
	}
</style>
