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
				<text class="nav-link" @click="navigateTo('/pages/services/services')">应用场景</text>
				<text class="nav-link active">使用步骤</text>
			</view>
			<view class="nav-buttons">
				<button class="btn btn-outline">登录</button>
				<button class="btn btn-primary">立即注册</button>
			</view>
		</view>
		
		<!-- 使用步骤 -->
		<view class="section">
			<text class="section-title">使用流程</text>
			<text class="section-subtitle">简单几步，开启您的国际支付之旅</text>
			
			<view class="steps-container">
				<view class="step" v-for="(step, index) in steps" :key="index">
					<view class="step-number">{{index + 1}}</view>
					<text class="step-title">{{step.title}}</text>
					<text class="step-desc">{{step.description}}</text>
				</view>
			</view>
			
			<view class="steps-line"></view>
		</view>
		
		<!-- 详细说明 -->
		<view class="section steps-details">
			<text class="section-title">步骤详解</text>
			
			<view class="detail-steps">
				<view class="detail-step" v-for="(step, index) in detailSteps" :key="index">
					<view class="detail-step-header">
						<view class="detail-step-icon">{{index + 1}}</view>
						<text class="detail-step-title">{{step.title}}</text>
					</view>
					<text class="detail-step-desc">{{step.description}}</text>
					<view class="detail-step-tips" v-if="step.tips">
						<text class="tips-title">小贴士:</text>
						<text class="tips-content">{{step.tips}}</text>
					</view>
				</view>
			</view>
			
			<view class="start-button">
				<button class="btn btn-primary">立即开始</button>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				steps: [
					{
						title: '注册账号',
						description: '使用手机号或邮箱快速注册'
					},
					{
						title: '身份验证',
						description: '完成KYC身份验证'
					},
					{
						title: '支付开卡费',
						description: '支付一次性开卡费用'
					},
					{
						title: '充值卡片',
						description: '通过支付宝向虚拟卡充值'
					},
					{
						title: '绑定服务',
						description: '将卡信息绑定到目标服务'
					},
					{
						title: '使用/提现',
						description: '完成支付或将余额提现'
					}
				],
				detailSteps: [
					{
						title: '注册WildCard账号',
						description: '访问官网，点击"注册"按钮，使用您的手机号或电子邮箱地址进行注册。系统会向您发送验证码，输入后即可完成注册。整个过程不超过1分钟。',
						tips: '请确保使用真实有效的联系方式，这将用于接收重要通知和找回密码。'
					},
					{
						title: '完成身份验证',
						description: '根据监管要求，您需要完成简单的KYC身份验证流程。上传您的有效身份证件照片，并进行人脸识别验证，确保账户安全合规。',
						tips: '身份验证信息仅用于合规目的，我们采用金融级加密技术保护您的个人信息。'
					},
					{
						title: '支付开卡费并获取虚拟卡',
						description: '支付一次性开卡费用(¥9.9)，系统将为您生成一张虚拟VISA卡。支付成功后，您将立即收到卡片信息，包括卡号、有效期和CVV安全码。',
						tips: '开卡费是一次性费用，不会重复收取，您的卡片长期有效。'
					},
					{
						title: '为虚拟卡充值',
						description: '在"我的卡片"页面，选择"充值"选项，通过支付宝为您的虚拟卡充值。充值金额将实时到账，无需等待。',
						tips: '建议根据您的消费需求充值，支持小额多次充值，最低充值金额为¥10。'
					},
					{
						title: '绑定国际服务',
						description: '使用虚拟卡信息在您需要订阅的国际服务上完成支付。如需帮助，可参考我们提供的各服务详细教程，包括ChatGPT Plus、Claude Pro等常用服务的绑定流程。',
						tips: '首次绑定服务时，建议先使用小额测试，确认成功后再进行大额支付。'
					},
					{
						title: '管理卡片和提现',
						description: '在账户中心随时查看卡片交易记录和余额。如需提现，只需点击"提现"按钮，选择提现金额，资金将在1-3个工作日内退回您的支付宝账户。',
						tips: '提现手续费为1%，最低¥1，请在提现前确认余额足够支付手续费。'
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
	
	/* 步骤区域样式 */
	.section {
		padding: 20px;
		margin-bottom: 20px;
		position: relative;
	}
	
	.steps-details {
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
	
	.steps-container {
		display: flex;
		justify-content: space-around;
		flex-wrap: wrap;
		position: relative;
		z-index: 1;
		max-width: 1000px;
		margin: 0 auto;
		padding: 20px 0;
	}
	
	.steps-line {
		position: absolute;
		top: 50%;
		left: 10%;
		right: 10%;
		height: 2px;
		background-color: #e0e0e0;
		z-index: 0;
		margin-top: -60px;
		display: none;
	}
	
	@media (min-width: 768px) {
		.steps-line {
			display: block;
		}
	}
	
	.step {
		display: flex;
		flex-direction: column;
		align-items: center;
		width: 120px;
		margin-bottom: 30px;
		z-index: 1;
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
		font-size: 24px;
		font-weight: bold;
		margin-bottom: 15px;
	}
	
	.step-title {
		font-weight: 600;
		text-align: center;
		margin-bottom: 8px;
		display: block;
		color: #2c3e50;
	}
	
	.step-desc {
		font-size: 12px;
		color: #7f8c8d;
		text-align: center;
		display: block;
	}
	
	/* 详细步骤样式 */
	.detail-steps {
		display: flex;
		flex-direction: column;
		gap: 20px;
		margin-top: 30px;
	}
	
	.detail-step {
		background-color: #f8f9fa;
		padding: 20px;
		border-radius: 12px;
		box-shadow: 0 2px 10px rgba(0, 0, 0, 0.05);
	}
	
	.detail-step-header {
		display: flex;
		align-items: center;
		margin-bottom: 15px;
	}
	
	.detail-step-icon {
		width: 40px;
		height: 40px;
		border-radius: 50%;
		background-color: #3498db;
		color: white;
		display: flex;
		align-items: center;
		justify-content: center;
		font-weight: bold;
		margin-right: 15px;
	}
	
	.detail-step-title {
		font-size: 18px;
		font-weight: 600;
		color: #2c3e50;
	}
	
	.detail-step-desc {
		color: #7f8c8d;
		font-size: 14px;
		line-height: 1.6;
		margin-bottom: 15px;
		display: block;
	}
	
	.detail-step-tips {
		background-color: rgba(52, 152, 219, 0.1);
		padding: 15px;
		border-radius: 8px;
		border-left: 4px solid #3498db;
	}
	
	.tips-title {
		font-weight: 600;
		color: #3498db;
		margin-bottom: 5px;
		display: block;
	}
	
	.tips-content {
		font-size: 13px;
		color: #7f8c8d;
		display: block;
	}
	
	.start-button {
		margin-top: 40px;
		text-align: center;
	}
	
	/* 响应式调整 */
	@media (max-width: 768px) {
		.nav-links {
			display: none;
		}
		
		.steps-container {
			justify-content: center;
			gap: 20px;
		}
	}
</style> 