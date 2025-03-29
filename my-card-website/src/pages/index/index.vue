<template>
	<view class="page-container">
		<!-- 导航栏 -->
		<view class="container">
			<view class="nav">
				<view class="logo">
					<view class="logo-icon"></view>
					<view>Wild<text class="logo-span">Card</text></view>
				</view>
				<view class="nav-links">
					<text @click="scrollToSection('features')" class="nav-link">功能特点</text>
					<text @click="scrollToSection('articles')" class="nav-link">文章资讯</text>
					<text @click="scrollToSection('services')" class="nav-link">应用场景</text>
					<text @click="scrollToSection('steps')" class="nav-link">使用步骤</text>
					<text @click="scrollToSection('pricing')" class="nav-link">定价</text>
				</view>
				<view class="nav-buttons">
					<button class="btn btn-outline" @click="login">登录</button>
					<button class="btn btn-primary" @click="register">立即注册</button>
				</view>
			</view>
        
			<!-- 英雄区域 -->
			<view class="hero">
				<view class="hero-content">
					<view class="hero-title">轻松实现国际支付<text>\n</text>一分钟开通虚拟信用卡</view>
					<view class="hero-desc">WildCard为您提供便捷的跨境支付解决方案，支持ChatGPT Plus、Claude Pro等国际服务订阅，支付宝直充，无需复杂流程。</view>
					<button class="btn btn-primary" @click="applyCard">立即开卡 (¥9.9)</button>
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
							<view class="card-holder">WILD CARD USER</view>
							<view class="card-expiry">09/28</view>
						</view>
					</view>
				</view>
			</view>
		</view>
		
		<!-- 特点区域 -->
		<view class="section" id="features">
			<view class="container">
				<view class="section-title">核心功能</view>
				<view class="section-subtitle">为您打造无缝的跨境支付体验</view>
				
				<view class="feature-grid">
					<view class="feature-card" v-for="(feature, index) in features" :key="index">
						<view class="feature-icon">{{feature.icon}}</view>
						<view class="feature-title">{{feature.title}}</view>
						<view class="feature-desc">{{feature.desc}}</view>
					</view>
				</view>
			</view>
		</view>
		
		<!-- 文章预览区域 -->
		<view class="section section-white" id="articles">
			<view class="container">
				<view class="section-title">最新资讯</view>
				<view class="section-subtitle">了解使用教程与平台动态</view>
				
				<view class="articles-grid">
					<view class="article-card" v-for="(article, index) in articles" :key="index" @click="viewArticle(article)">
						<view class="article-image" :style="{ backgroundImage: 'url(' + article.image + ')' }"></view>
						<view class="article-content">
							<view class="article-tag">{{article.tag}}</view>
							<view class="article-title">{{article.title}}</view>
							<view class="article-excerpt">{{article.excerpt}}</view>
							<view class="article-meta">
								<text class="article-date">{{article.date}}</text>
								<text class="article-read-time">{{article.readTime}}</text>
							</view>
						</view>
					</view>
				</view>
				
				<view class="text-center view-more">
					<button class="btn btn-outline" @click="viewAllArticles">查看全部文章</button>
				</view>
			</view>
		</view>
		
		<!-- 应用场景 -->
		<view class="section" id="services">
			<view class="container">
				<view class="section-title">应用场景</view>
				<view class="section-subtitle">满足您的各种国际服务订阅需求</view>
				
				<scroll-view scroll-x="true" class="cases-container" show-scrollbar="false">
					<view class="case-card" v-for="(caseItem, index) in cases" :key="index">
						<view class="case-icon" :class="caseItem.iconClass">{{caseItem.iconText}}</view>
						<view class="case-title">{{caseItem.title}}</view>
						<view class="case-desc">{{caseItem.desc}}</view>
					</view>
				</scroll-view>
			</view>
		</view>
		
		<!-- 使用步骤 -->
		<view class="section section-white" id="steps">
			<view class="container">
				<view class="section-title">使用流程</view>
				<view class="section-subtitle">简单几步，开启您的国际支付之旅</view>
				
				<view class="steps-container">
					<view class="steps-line"></view>
					<view class="steps">
						<view class="step" v-for="(step, index) in steps" :key="index">
							<view class="step-number">{{index + 1}}</view>
							<view class="step-title">{{step.title}}</view>
							<view class="step-desc">{{step.desc}}</view>
						</view>
					</view>
				</view>
			</view>
		</view>
		
		<!-- 底部简单版权 -->
		<view class="footer">
			<view class="container">
				<view class="copyright">© 2025 WildCard. 保留所有权利。</view>
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
						desc: '提供可用于国际支付的虚拟信用卡，全球通用，安全可靠。'
					},
					{
						icon: '⚡',
						title: '1分钟开卡',
						desc: '快速完成KYC身份验证，立即获得您的虚拟卡信息。'
					},
					{
						icon: '🇺🇸',
						title: '美国账单地址',
						desc: '提供美国账单地址，轻松订阅需要美国地址的国际服务。'
					},
					{
						icon: '💰',
						title: '支付宝充值',
						desc: '直接使用支付宝充值，无需通过复杂的稳定币兑换流程。'
					},
					{
						icon: '💸',
						title: '随时提现',
						desc: '卡内余额可随时提现至支付宝账户，资金灵活使用。'
					},
					{
						icon: '🔒',
						title: '安全可靠',
						desc: '经过在线安全检测，bewildcard.com被认为是合法安全的网站。'
					}
				],
				articles: [
					{
						image: '/static/images/article1.jpg',
						tag: '使用教程',
						title: '如何使用WildCard订阅ChatGPT Plus服务',
						excerpt: '本教程将详细介绍如何使用WildCard虚拟信用卡成功订阅OpenAI的ChatGPT Plus服务，包括美国IP环境设置、账单地址填写和支付流程等关键步骤。',
						date: '2025年3月15日',
						readTime: '5分钟阅读',
						id: 1
					},
					{
						image: '/static/images/article2.jpg',
						tag: '平台分析',
						title: 'WildCard虚拟信用卡服务平台详细分析',
						excerpt: 'WildCard是一个专注于提供虚拟信用卡服务的平台，主要面向有跨境支付需求的用户，特别是中国用户希望订阅和支付国际服务如ChatGPT Plus、Claude Pro、OnlyFans等。',
						date: '2025年3月10日',
						readTime: '8分钟阅读',
						id: 2
					},
					{
						image: '/static/images/article3.jpg',
						tag: '常见问题',
						title: 'WildCard常见问题解答：充值、提现与安全问题',
						excerpt: '本文整理了用户在使用WildCard虚拟信用卡过程中最常见的问题，包括充值限额、手续费、提现流程、账户安全等方面的详细解答，帮助您更顺畅地使用服务。',
						date: '2025年3月5日',
						readTime: '6分钟阅读',
						id: 3
					},
					{
						image: '/static/images/article4.jpg',
						tag: '新功能',
						title: 'WildCard新增功能：支持Cursor Pro和更多AI服务订阅',
						excerpt: 'WildCard平台最近更新了支持范围，现已完全兼容Cursor Pro等新兴AI辅助编程工具的订阅支付。本文详细介绍新增的服务支持及使用方法，助您开启AI辅助编程体验。',
						date: '2025年2月28日',
						readTime: '4分钟阅读',
						id: 4
					}
				],
				cases: [
					{
						iconClass: 'chatgpt',
						iconText: 'GPT',
						title: 'ChatGPT Plus',
						desc: '支持美国IP环境和账单地址绑定，便于支付OpenAI的ChatGPT Plus订阅'
					},
					{
						iconClass: 'claude',
						iconText: 'C',
						title: 'Claude Pro',
						desc: '可用于支付Anthropic的Claude Pro服务，并支持绑定API密钥'
					},
					{
						iconClass: 'cursor',
						iconText: 'Cu',
						title: 'Cursor Pro',
						desc: '支持支付AI辅助编程工具Cursor Pro的订阅费用'
					},
					{
						iconClass: 'onlyfans',
						iconText: 'OF',
						title: 'OnlyFans',
						desc: '支持绑定OnlyFans账户，用于支付订阅费用'
					},
					{
						iconClass: 'other',
						iconText: '+',
						title: '其他国际服务',
						desc: '包括海外手机号、海外家庭网络、海外邮箱等服务'
					}
				],
				steps: [
					{
						title: '注册账号',
						desc: '使用手机号或邮箱快速注册'
					},
					{
						title: '身份验证',
						desc: '完成KYC身份验证'
					},
					{
						title: '支付开卡费',
						desc: '支付一次性开卡费用'
					},
					{
						title: '充值卡片',
						desc: '通过支付宝向虚拟卡充值'
					},
					{
						title: '绑定服务',
						desc: '将卡信息绑定到目标服务'
					},
					{
						title: '使用/提现',
						desc: '完成支付或将余额提现'
					}
				]
			}
		},
		onLoad() {
			// 页面加载时创建临时目录
			this.createTempDirectories();
		},
		methods: {
			createTempDirectories() {
				// 在实际项目中，这些目录应该在项目构建时创建
				console.log('正在创建临时资源目录');
			},
			scrollToSection(sectionId) {
				// 在实际应用中，应使用uni.createSelectorQuery实现滚动
				uni.showToast({
					title: `前往${sectionId}部分`,
					icon: 'none'
				});
			},
			login() {
				uni.showToast({
					title: '登录功能开发中',
					icon: 'none'
				});
			},
			register() {
				uni.showToast({
					title: '注册功能开发中',
					icon: 'none'
				});
			},
			applyCard() {
				uni.showToast({
					title: '开卡功能开发中',
					icon: 'none'
				});
			},
			viewArticle(article) {
				uni.showToast({
					title: `查看文章: ${article.title}`,
					icon: 'none'
				});
			},
			viewAllArticles() {
				uni.showToast({
					title: '查看全部文章功能开发中',
					icon: 'none'
				});
			}
		}
	}
</script>

<style>
	/* 基础样式 */
	.page-container {
		background-color: #f8f9fa;
		color: #2c3e50;
		line-height: 1.6;
	}
	
	.container {
		max-width: 1200px;
		margin: 0 auto;
		padding: 0 20px;
	}
	
	/* 导航栏样式 */
	.nav {
		display: flex;
		justify-content: space-between;
		align-items: center;
		padding: 20px 0;
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
	
	.logo-icon::before {
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
		transition: color 0.3s;
	}
	
	.nav-link:active {
		color: #3498db;
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
		cursor: pointer;
		transition: all 0.3s;
	}
	
	.btn-outline {
		background-color: transparent;
		border: 1px solid #3498db;
		color: #3498db;
	}
	
	.btn-outline:active {
		background-color: #3498db;
		color: white;
	}
	
	.btn-primary {
		background-color: #3498db;
		color: white;
	}
	
	.btn-primary:active {
		background-color: #2980b9;
	}
	
	/* 英雄区样式 */
	.hero {
		display: flex;
		margin-top: 30px;
		gap: 40px;
		align-items: center;
		padding-bottom: 50px;
	}
	
	.hero-content {
		flex: 1;
	}
	
	.hero-title {
		font-size: 2.6rem;
		font-weight: 700;
		color: #2c3e50;
		margin-bottom: 20px;
		line-height: 1.2;
	}
	
	.hero-desc {
		color: #7f8c8d;
		font-size: 1.1rem;
		margin-bottom: 30px;
		line-height: 1.6;
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
		font-size: 1.2rem;
		font-weight: bold;
	}
	
	.card-number {
		display: flex;
		gap: 15px;
		font-size: 1.3rem;
		letter-spacing: 2px;
		margin-bottom: 25px;
	}
	
	.card-details {
		display: flex;
		justify-content: space-between;
		margin-top: auto;
		font-size: 0.9rem;
	}
	
	.card-holder {
		text-transform: uppercase;
	}
	
	/* 通用样式 */
	.section {
		padding: 50px 0;
	}
	
	.section-white {
		background-color: white;
	}
	
	.section-title {
		text-align: center;
		font-size: 1.8rem;
		color: #2c3e50;
		margin-bottom: 15px;
		font-weight: bold;
	}
	
	.section-subtitle {
		text-align: center;
		color: #7f8c8d;
		margin-bottom: 35px;
		max-width: 700px;
		margin-left: auto;
		margin-right: auto;
	}
	
	.text-center {
		text-align: center;
	}
	
	/* 特点区域 */
	.feature-grid {
		display: grid;
		grid-template-columns: repeat(3, 1fr);
		gap: 25px;
	}
	
	.feature-card {
		background-color: white;
		border-radius: 12px;
		padding: 25px;
		box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
		transition: transform 0.3s, box-shadow 0.3s;
	}
	
	.feature-card:active {
		transform: translateY(-5px);
		box-shadow: 0 15px 30px rgba(0, 0, 0, 0.1);
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
		font-size: 1.5rem;
		margin-bottom: 15px;
	}
	
	.feature-title {
		font-size: 1.2rem;
		color: #2c3e50;
		margin-bottom: 10px;
		font-weight: bold;
	}
	
	.feature-desc {
		color: #7f8c8d;
		font-size: 0.9rem;
		line-height: 1.5;
	}
	
	/* 文章预览区域 */
	.articles-grid {
		display: grid;
		grid-template-columns: repeat(2, 1fr);
		gap: 25px;
	}
	
	.article-card {
		background-color: white;
		border-radius: 12px;
		overflow: hidden;
		box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
		transition: transform 0.3s, box-shadow 0.3s;
	}
	
	.article-card:active {
		transform: translateY(-5px);
		box-shadow: 0 15px 30px rgba(0, 0, 0, 0.1);
	}
	
	.article-image {
		height: 180px;
		background-size: cover;
		background-position: center;
		background-color: #e0e0e0;
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
		font-size: 0.8rem;
		margin-bottom: 10px;
	}
	
	.article-title {
		font-size: 1.3rem;
		font-weight: 600;
		color: #2c3e50;
		margin-bottom: 10px;
		line-height: 1.4;
	}
	
	.article-excerpt {
		color: #7f8c8d;
		font-size: 0.9rem;
		line-height: 1.5;
		margin-bottom: 15px;
		display: -webkit-box;
		-webkit-line-clamp: 3;
		-webkit-box-orient: vertical;
		overflow: hidden;
	}
	
	.article-meta {
		display: flex;
		align-items: center;
		font-size: 0.8rem;
		color: #95a5a6;
	}
	
	.article-date {
		margin-right: 15px;
	}
	
	.article-read-time::before {
		content: "•";
		margin-right: 15px;
	}
	
	.view-more {
		margin-top: 30px;
	}
	
	/* 应用场景 */
	.cases-container {
		display: flex;
		white-space: nowrap;
		padding: 10px 0 30px;
		margin: 0 -10px;
	}
	
	.case-card {
		min-width: 200px;
		background-color: white;
		border-radius: 12px;
		padding: 20px;
		margin: 0 10px;
		box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
		display: inline-flex;
		flex-direction: column;
		align-items: center;
		text-align: center;
		transition: transform 0.3s;
	}
	
	.case-card:active {
		transform: translateY(-5px);
	}
	
	.case-icon {
		width: 60px;
		height: 60px;
		border-radius: 15px;
		margin-bottom: 15px;
		display: flex;
		align-items: center;
		justify-content: center;
		font-size: 1.8rem;
		color: white;
	}
	
	.case-icon.chatgpt {
		background-color: #74aa9c;
	}
	
	.case-icon.claude {
		background-color: #9b59b6;
	}
	
	.case-icon.cursor {
		background-color: #f1c40f;
	}
	
	.case-icon.onlyfans {
		background-color: #e74c3c;
	}
	
	.case-icon.other {
		background-color: #2ecc71;
	}
	
	.case-title {
		font-weight: 600;
		color: #2c3e50;
		margin-bottom: 10px;
	}
	
	.case-desc {
		font-size: 0.8rem;
		color: #7f8c8d;
	}
	
	/* 使用流程 */
	.steps-container {
		position: relative;
		max-width: 900px;
		margin: 40px auto 0;
	}
	
	.steps-line {
		position: absolute;
		top: 40px;
		left: 10%;
		right: 10%;
		height: 2px;
		background-color: #e0e0e0;
		z-index: 0;
	}
	
	.steps {
		display: flex;
		justify-content: space-between;
		position: relative;
		z-index: 1;
	}
	
	.step {
		display: flex;
		flex-direction: column;
		align-items: center;
		width: 120px;
	}
	
	.step-number {
		width: 60px;
		height: 60px;
		border-radius: 50%;
		background-color: #3498db;
		color: white;
		display: flex;
		align-items: center;
		justify-content: center;
		font-size: 1.5rem;
		font-weight: bold;
		margin-bottom: 15px;
	}
	
	.step-title {
		font-weight: 600;
		text-align: center;
		margin-bottom: 8px;
	}
	
	.step-desc {
		font-size: 0.8rem;
		color: #7f8c8d;
		text-align: center;
	}
	
	/* 底部版权 */
	.footer {
		background-color: #2c3e50;
		color: white;
		padding: 20px 0;
		margin-top: 30px;
	}
	
	.copyright {
		text-align: center;
		font-size: 0.9rem;
		color: #95a5a6;
	}
	
	/* 响应式调整 */
	@media (max-width: 1000px) {
		.feature-grid {
			grid-template-columns: repeat(2, 1fr);
		}
		
		.articles-grid {
			grid-template-columns: 1fr;
		}
		
		.hero {
			flex-direction: column;
		}
		
		.steps {
			flex-wrap: wrap;
			justify-content: center;
			gap: 30px 60px;
		}
		
		.steps-line {
			display: none;
		}
	}
	
	@media (max-width: 768px) {
		.nav-links {
			display: none;
		}
		
		.feature-grid {
			grid-template-columns: 1fr;
		}
		
		.card-visual {
			width: 100%;
		}
		
		.step {
			width: 40%;
			margin-bottom: 30px;
		}
	}
</style>
