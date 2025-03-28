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
				<text class="nav-link active">文章资讯</text>
				<text class="nav-link" @click="navigateTo('/pages/services/services')">应用场景</text>
				<text class="nav-link" @click="navigateTo('/pages/steps/steps')">使用步骤</text>
			</view>
			<view class="nav-buttons">
				<button class="btn btn-outline">登录</button>
				<button class="btn btn-primary">立即注册</button>
			</view>
		</view>
		
		<!-- 文章预览区域 -->
		<view class="section">
			<text class="section-title">最新资讯</text>
			<text class="section-subtitle">了解使用教程与平台动态</text>
			
			<view class="articles-grid">
				<view class="article-card" v-for="(article, index) in articles" :key="index">
					<view class="article-image" :style="{ backgroundImage: 'url(' + article.image + ')' }"></view>
					<view class="article-content">
						<text class="article-tag">{{article.tag}}</text>
						<text class="article-title">{{article.title}}</text>
						<text class="article-excerpt">{{article.excerpt}}</text>
						<view class="article-meta">
							<text class="article-date">{{article.date}}</text>
							<text class="article-read-time">{{article.readTime}}</text>
						</view>
					</view>
				</view>
			</view>
			
			<view class="text-center view-more">
				<button class="btn btn-outline">查看全部文章</button>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				articles: [
					{
						image: '/static/placeholder.jpg',
						tag: '使用教程',
						title: '如何使用WildCard订阅ChatGPT Plus服务',
						excerpt: '本教程将详细介绍如何使用WildCard虚拟信用卡成功订阅OpenAI的ChatGPT Plus服务，包括美国IP环境设置、账单地址填写和支付流程等关键步骤。',
						date: '2025年3月15日',
						readTime: '5分钟阅读'
					},
					{
						image: '/static/placeholder.jpg',
						tag: '平台分析',
						title: 'WildCard虚拟信用卡服务平台详细分析',
						excerpt: 'WildCard是一个专注于提供虚拟信用卡服务的平台，主要面向有跨境支付需求的用户，特别是中国用户希望订阅和支付国际服务如ChatGPT Plus、Claude Pro、OnlyFans等。',
						date: '2025年3月10日',
						readTime: '8分钟阅读'
					},
					{
						image: '/static/placeholder.jpg',
						tag: '常见问题',
						title: 'WildCard常见问题解答：充值、提现与安全问题',
						excerpt: '本文整理了用户在使用WildCard虚拟信用卡过程中最常见的问题，包括充值限额、手续费、提现流程、账户安全等方面的详细解答，帮助您更顺畅地使用服务。',
						date: '2025年3月5日',
						readTime: '6分钟阅读'
					},
					{
						image: '/static/placeholder.jpg',
						tag: '新功能',
						title: 'WildCard新增功能：支持Cursor Pro和更多AI服务订阅',
						excerpt: 'WildCard平台最近更新了支持范围，现已完全兼容Cursor Pro等新兴AI辅助编程工具的订阅支付。本文详细介绍新增的服务支持及使用方法，助您开启AI辅助编程体验。',
						date: '2025年2月28日',
						readTime: '4分钟阅读'
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
	
	/* 文章区域样式 */
	.section {
		padding: 20px;
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
	
	.articles-grid {
		display: flex;
		flex-direction: column;
		gap: 20px;
	}
	
	.article-card {
		background-color: white;
		border-radius: 12px;
		overflow: hidden;
		box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
	}
	
	.article-image {
		height: 180px;
		background-size: cover;
		background-position: center;
		background-color: #eee;
	}
	
	.article-content {
		padding: 20px;
	}
	
	.article-tag {
		display: inline-block;
		background-color: rgba(52, 152, 219, 0.1);
		color: #3498db;
		padding: 5px 10px;
		border-radius: 50px;
		font-size: 12px;
		margin-bottom: 10px;
	}
	
	.article-title {
		font-size: 18px;
		font-weight: 600;
		color: #2c3e50;
		margin-bottom: 10px;
		line-height: 1.4;
		display: block;
	}
	
	.article-excerpt {
		color: #7f8c8d;
		font-size: 14px;
		line-height: 1.5;
		margin-bottom: 15px;
		display: block;
		overflow: hidden;
		text-overflow: ellipsis;
		display: -webkit-box;
		-webkit-line-clamp: 3;
		-webkit-box-orient: vertical;
	}
	
	.article-meta {
		display: flex;
		align-items: center;
		font-size: 12px;
		color: #95a5a6;
	}
	
	.article-date {
		margin-right: 15px;
	}
	
	.view-more {
		margin-top: 30px;
		text-align: center;
	}
	
	/* 响应式调整 */
	@media (min-width: 768px) {
		.articles-grid {
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