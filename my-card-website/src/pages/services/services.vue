<template>
	<view class="content">
		<!-- 导航栏 -->
		<view class="nav">
			<view class="logo" @click="goHome">
				<view class="logo-icon"></view>
				<view>Wild<text class="logo-span">Card</text></view>
			</view>
			<view class="nav-links">
				<text class="nav-link" @click="navigateTo('/pages/index/index')">首页</text>
				<text class="nav-link" @click="navigateTo('/pages/articles/articles')">文章资讯</text>
				<text class="nav-link active">应用场景</text>
				<text class="nav-link" @click="navigateTo('/pages/steps/steps')">使用步骤</text>
			</view>
			<view class="nav-buttons">
				<button class="btn btn-outline">登录</button>
				<button class="btn btn-primary">立即注册</button>
			</view>
		</view>
		
		<!-- 应用场景 -->
		<view class="section">
			<text class="section-title">应用场景</text>
			<text class="section-subtitle">满足您的各种国际服务订阅需求</text>
			
			<scroll-view scroll-x class="cases-container">
				<view class="case-card" v-for="(caseItem, index) in cases" :key="index">
					<view class="case-icon" :class="caseItem.iconClass">{{caseItem.icon}}</view>
					<text class="case-title">{{caseItem.title}}</text>
					<text class="case-desc">{{caseItem.description}}</text>
				</view>
			</scroll-view>
		</view>
		
		<!-- 服务介绍 -->
		<view class="section service-details">
			<text class="section-title">详细支持的服务</text>
			<text class="section-subtitle">WildCard虚拟信用卡支持多种国际服务，以下是一些常见应用</text>
			
			<view class="service-list">
				<view class="service-item" v-for="(service, index) in services" :key="index">
					<view class="service-header">
						<view class="service-icon" :class="service.iconClass">{{service.icon}}</view>
						<view class="service-info">
							<text class="service-name">{{service.name}}</text>
							<text class="service-price">{{service.price}}</text>
						</view>
					</view>
					<text class="service-desc">{{service.description}}</text>
					<button class="btn btn-outline service-btn">查看教程</button>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				cases: [
					{
						icon: 'GPT',
						iconClass: 'chatgpt',
						title: 'ChatGPT Plus',
						description: '支持美国IP环境和账单地址绑定，便于支付OpenAI的ChatGPT Plus订阅'
					},
					{
						icon: 'C',
						iconClass: 'claude',
						title: 'Claude Pro',
						description: '可用于支付Anthropic的Claude Pro服务，并支持绑定API密钥'
					},
					{
						icon: 'Cu',
						iconClass: 'cursor',
						title: 'Cursor Pro',
						description: '支持支付AI辅助编程工具Cursor Pro的订阅费用'
					},
					{
						icon: 'OF',
						iconClass: 'onlyfans',
						title: 'OnlyFans',
						description: '支持绑定OnlyFans账户，用于支付订阅费用'
					},
					{
						icon: '+',
						iconClass: 'other',
						title: '其他国际服务',
						description: '包括海外手机号、海外家庭网络、海外邮箱等服务'
					}
				],
				services: [
					{
						icon: 'GPT',
						iconClass: 'chatgpt',
						name: 'ChatGPT Plus',
						price: '$20/月',
						description: 'OpenAI开发的高级AI对话工具，订阅Plus服务可获得更快的响应速度和新功能优先体验。'
					},
					{
						icon: 'C',
						iconClass: 'claude',
						name: 'Claude Pro',
						price: '$20/月',
						description: 'Anthropic开发的对话AI助手，Pro版本提供更长的上下文窗口和更多的使用量。'
					},
					{
						icon: 'Cu',
						iconClass: 'cursor',
						name: 'Cursor Pro',
						price: '$20/月',
						description: 'AI辅助编程工具，帮助开发者更高效地编写和理解代码，Pro版本提供更多高级功能。'
					},
					{
						icon: 'OF',
						iconClass: 'onlyfans',
						name: 'OnlyFans',
						price: '按创作者定价',
						description: '内容创作者订阅平台，支持为喜欢的创作者付费订阅其独家内容。'
					}
				]
			}
		},
		methods: {
			goHome() {
				uni.navigateTo({
					url: '/pages/index/index'
				})
			},
			navigateTo(url) {
				uni.navigateTo({
					url: url
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
	
	.nav-link.active {
		color: #3498db;
		font-weight: 600;
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
	
	/* 应用场景样式 */
	.section {
		padding: 20px;
		margin-bottom: 20px;
	}
	
	.service-details {
		background-color: white;
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
	
	.cases-container {
		display: flex;
		white-space: nowrap;
		padding: 10px 0 30px;
	}
	
	.case-card {
		display: inline-block;
		min-width: 200px;
		background-color: white;
		border-radius: 12px;
		padding: 20px;
		margin-right: 15px;
		box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
		flex-direction: column;
		align-items: center;
		text-align: center;
	}
	
	.case-icon {
		width: 60px;
		height: 60px;
		border-radius: 15px;
		margin-bottom: 15px;
		display: flex;
		align-items: center;
		justify-content: center;
		font-size: 20px;
		font-weight: bold;
		margin-left: auto;
		margin-right: auto;
	}
	
	.case-icon.chatgpt {
		background-color: #74aa9c;
		color: white;
	}
	
	.case-icon.claude {
		background-color: #9b59b6;
		color: white;
	}
	
	.case-icon.cursor {
		background-color: #f1c40f;
		color: white;
	}
	
	.case-icon.onlyfans {
		background-color: #e74c3c;
		color: white;
	}
	
	.case-icon.other {
		background-color: #2ecc71;
		color: white;
	}
	
	.case-title {
		font-weight: 600;
		color: #2c3e50;
		margin-bottom: 10px;
		display: block;
	}
	
	.case-desc {
		font-size: 12px;
		color: #7f8c8d;
		display: block;
		white-space: normal;
	}
	
	/* 服务列表样式 */
	.service-list {
		display: flex;
		flex-direction: column;
		gap: 20px;
	}
	
	.service-item {
		background-color: #f8f9fa;
		padding: 20px;
		border-radius: 12px;
		box-shadow: 0 2px 10px rgba(0, 0, 0, 0.05);
	}
	
	.service-header {
		display: flex;
		align-items: center;
		margin-bottom: 15px;
	}
	
	.service-icon {
		width: 50px;
		height: 50px;
		border-radius: 10px;
		display: flex;
		align-items: center;
		justify-content: center;
		font-weight: bold;
		margin-right: 15px;
		font-size: 16px;
	}
	
	.service-info {
		flex: 1;
	}
	
	.service-name {
		font-size: 18px;
		font-weight: 600;
		color: #2c3e50;
		display: block;
	}
	
	.service-price {
		font-size: 14px;
		color: #3498db;
		display: block;
	}
	
	.service-desc {
		color: #7f8c8d;
		font-size: 14px;
		line-height: 1.5;
		margin-bottom: 15px;
		display: block;
	}
	
	.service-btn {
		width: 100%;
		margin-top: 10px;
	}
	
	/* 响应式调整 */
	@media (min-width: 768px) {
		.service-list {
			display: grid;
			grid-template-columns: repeat(2, 1fr);
			gap: 20px;
		}
	}
	
	@media (max-width: 768px) {
		.nav-links {
			display: none;
		}
	}
</style>