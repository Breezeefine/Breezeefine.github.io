# 虚拟信用卡支付服务网站

这是一个使用uni-app+Vue开发的信息型+转化型网站，专注于推广虚拟信用卡支付服务。

## 项目特点

- 响应式设计，适配各种设备
- 使用Vue3进行开发
- 基于uni-app实现多端适配
- 自动部署到GitHub Pages

## 本地开发

```bash
# 进入项目目录
cd my-card-website

# 安装依赖
npm install

# 启动开发服务器 (H5)
npm run dev:h5

# 打包构建
npm run build:h5
```

## 部署说明

该项目配置了GitHub Actions自动部署流程，每当代码推送到main或master分支时，会自动构建并部署到GitHub Pages。

访问地址: https://你的用户名.github.io/Breezeefine.github.io/

## 目录结构

```
my-card-website/
├── src/                  # 源代码
│   ├── pages/            # 页面
│   ├── static/           # 静态资源
│   ├── App.vue           # 主应用组件
│   └── main.js           # 入口文件
├── public/               # 公共资源
└── .github/workflows/    # GitHub Actions配置
    └── deploy.yml        # 部署配置
```
