<template>
	<view class="content">
		<!-- 导航栏 -->
		<view class="nav">
			<view class="logo">
				<view class="logo-icon"></view>
				<view>Wild<text class="logo-span">Card</text></view>
			</view>
			<view class="nav-links">
				<text class="nav-link" @click="scrollTo('features')">功能特点</text>
				<text class="nav-link" @click="scrollTo('articles')">文章资讯</text>
				<text class="nav-link" @click="scrollTo('services')">应用场景</text>
				<text class="nav-link" @click="scrollTo('steps')">使用步骤</text>
			</view>
			<view class="nav-buttons">
				<button class="btn btn-outline">登录</button>
				<button class="btn btn-primary">立即注册</button>
			</view>
		</view>
		
		<!-- 英雄区域 -->
		<view class="hero">
			<view class="hero-content">
				<text class="hero-title">轻松实现国际支付\n一分钟开通虚拟信用卡</text>
				<text class="hero-desc">WildCard为您提供便捷的跨境支付解决方案，支持ChatGPT Plus、Claude Pro等国际服务订阅，支付宝直充，无需复杂流程。</text>
				<button class="btn btn-primary">立即开卡 (¥9.9)</button>
			</view>
			<view class="hero-image">
				<view class="card-visual">
					<view class="card-logo">
						<view class="card-chip"></view>
						<view class="card-network">VISA</view>
					</view>
					<view class="card-number">
						<text>4242</text>
						<text>••••</text>
						<text>••••</text>
						<text>••••</text>
					</view>
					<view class="card-details">
						<text class="card-holder">WILD CARD USER</text>
						<text class="card-expiry">09/28</text>
					</view>
				</view>
			</view>
		</view>
		
		<!-- 特点区域 -->
		<view class="section" id="features">
			<text class="section-title">核心功能</text>
			<text class="section-subtitle">为您打造无缝的跨境支付体验</text>
			
			<view class="feature-grid">
				<view class="feature-item" v-for="(feature, index) in features" :key="index">
					<view class="feature-icon">{{feature.icon}}</view>
					<text class="feature-title">{{ feature.title }}</text>
					<text class="feature-desc">{{ feature.description }}</text>
				</view>
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
						icon: '💳',
						title: '虚拟VISA卡',
						description: '提供可用于国际支付的虚拟信用卡，全球通用，安全可靠。'
					},
					{
						icon: '⚡',
						title: '1分钟开卡',
						description: '快速完成KYC身份验证，立即获得您的虚拟卡信息。'
					},
					{
						icon: '🇺🇸',
						title: '美国账单地址',
						description: '提供美国账单地址，轻松订阅需要美国地址的国际服务。'
					},
					{
						icon: '💰',
						title: '支付宝充值',
						description: '直接使用支付宝充值，无需通过复杂的稳定币兑换流程。'
					},
					{
						icon: '💸',
						title: '随时提现',
						description: '卡内余额可随时提现至支付宝账户，资金灵活使用。'
					},
					{
						icon: '🔒',
						title: '安全可靠',
						description: '经过在线安全检测，bewildcard.com被认为是合法安全的网站。'
					}
				]
			}
		},
		methods: {
			scrollTo(id) {
				// uni-app中的页面滚动方法
				uni.createSelectorQuery().select('#' + id).boundingClientRect(data => {
					uni.pageScrollTo({
						scrollTop: data.top,
						duration: 300
					})
				}).exec()
			},
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
	/* 基础样式 */
	.content {
		padding: 0;
		font-family: 'PingFang SC', 'Helvetica Neue', Arial, sans-serif;
		background-color: #f8f9fa;
		color: #2c3e50;
	}
	
	/* 导航栏样式 */
	.nav {
		display: flex;
		justify-content: space-between;
		align-items: center;
		padding: 20px;
	}
	
	.logo {
		display: flex;
		align-items: center;
		font-weight: bold;
		font-size: 24px;
		color: #3498db;
	}
	
	.logo-span {
		color: #2c3e50;
		margin-left: 5px;
	}
	
	.logo-icon {
		width: 32px;
		height: 32px;
		background-color: #3498db;
		border-radius: 8px;
		margin-right: 10px;
		position: relative;
	}
	
	.logo-icon:before {
		content: "W";
		position: absolute;
		top: 50%;
		left: 50%;
		transform: translate(-50%, -50%);
		color: white;
		font-weight: bold;
	}
	
	.nav-links {
		display: flex;
		gap: 25px;
	}
	
	.nav-link {
		color: #34495e;
		font-weight: 500;
	}
	
	.nav-buttons {
		display: flex;
		gap: 15px;
	}
	
	.btn {
		padding: 10px 20px;
		border-radius: 8px;
		border: none;
		font-weight: 500;
	}
	
	.btn-outline {
		background-color: transparent;
		border: 1px solid #3498db;
		color: #3498db;
	}
	
	.btn-primary {
		background-color: #3498db;
		color: white;
	}
	
	/* 英雄区样式 */
	.hero {
		display: flex;
		margin: 30px 20px;
		gap: 40px;
		align-items: center;
	}
	
	.hero-content {
		flex: 1;
	}
	
	.hero-title {
		font-size: 36px;
		font-weight: 700;
		color: #2c3e50;
		margin-bottom: 20px;
		line-height: 1.2;
		display: block;
	}
	
	.hero-desc {
		color: #7f8c8d;
		font-size: 16px;
		margin-bottom: 30px;
		line-height: 1.6;
		display: block;
	}
	
	.hero-image {
		flex: 1;
		display: flex;
		justify-content: center;
	}
	
	.card-visual {
		width: 80%;
		height: 220px;
		background: linear-gradient(135deg, #3498db, #9b59b6);
		border-radius: 16px;
		padding: 20px;
		position: relative;
		box-shadow: 0 20px 30px rgba(52, 152, 219, 0.2);
		color: white;
	}
	
	.card-logo {
		display: flex;
		align-items: center;
		margin-bottom: 30px;
	}
	
	.card-chip {
		width: 40px;
		height: 30px;
		background-color: rgba(255, 255, 255, 0.2);
		border-radius: 4px;
		margin-right: 15px;
	}
	
	.card-network {
		margin-left: auto;
		font-size: 20px;
		font-weight: bold;
	}
	
	.card-number {
		display: flex;
		gap: 15px;
		font-size: 20px;
		letter-spacing: 2px;
		margin-bottom: 25px;
	}
	
	.card-details {
		display: flex;
		justify-content: space-between;
		margin-top: auto;
		font-size: 14px;
	}
	
	.card-holder {
		text-transform: uppercase;
	}
	
	/* 特点区域样式 */
	.section {
		padding: 50px 20px;
		margin-bottom: 20px;
	}
	
	.section-title {
		text-align: center;
		font-size: 28px;
		color: #2c3e50;
		margin-bottom: 15px;
		display: block;
	}
	
	.section-subtitle {
		text-align: center;
		color: #7f8c8d;
		margin-bottom: 35px;
		display: block;
	}
	
	.feature-grid {
		display: flex;
		flex-direction: column;
		gap: 15px;
	}
	
	.feature-item {
		background: #fff;
		padding: 20px;
		border-radius: 12px;
		box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
	}
	
	.feature-icon {
		width: 50px;
		height: 50px;
		background-color: rgba(52, 152, 219, 0.1);
		border-radius: 10px;
		display: flex;
		align-items: center;
		justify-content: center;
		color: #3498db;
		font-size: 24px;
		margin-bottom: 15px;
	}
	
	.feature-title {
		font-size: 18px;
		font-weight: bold;
		color: #2c3e50;
		margin-bottom: 10px;
		display: block;
	}
	
	.feature-desc {
		color: #7f8c8d;
		font-size: 14px;
		line-height: 1.5;
		display: block;
	}
	
	/* 响应式调整 */
	@media (min-width: 768px) {
		.feature-grid {
			display: grid;
			grid-template-columns: repeat(2, 1fr);
			gap: 20px;
		}
	}
	
	@media (max-width: 768px) {
		.nav-links {
			display: none;
		}
		
		.hero {
			flex-direction: column;
		}
		
		.card-visual {
			width: 100%;
		}
	}
</style>
