# Vue.js 开发与 GitHub Pages 部署指南

<style>
code, pre {
  font-size: 1.2em;
  line-height: 1.5;
}
</style>

## 项目初始化

### 创建 Vue.js 项目
```bash
npm create vite@latest [项目名称] -- --template vue
# 按提示完成项目创建

cd [项目名称]
npm install
npm run dev
```

## 项目配置

### 修改 Vite 配置文件 `vite.config.js`
```javascript
import { defineConfig } from 'vite'
import vue from '@vitejs/plugin-vue'

export default defineConfig({
  base: '/your-repo-name/', // 替换为你的 GitHub 仓库名，结尾斜杠必须
  plugins: [vue()],
})
```

### 构建项目
```bash
npm run build
```

## GitHub 仓库准备

### 创建 GitHub 仓库
1. 访问 GitHub 网站
2. 点击右上角 "+" 号，选择 "New repository"
3. 填写仓库名称（如 "blog"）
4. 选择公开仓库（public）
5. 点击 "Create repository" 创建

### 仓库 SSH 地址格式
```
git@github.com:[用户名]/[仓库名].git
```

## 本地部署流程

### 进入构建目录并初始化 Git
```bash
cd dist
git init
```

### 添加文件到暂存区
```bash
git add .
```

### 提交更改
```bash
git commit -m "[提交注释1]"
```

### 重命名主分支
```bash
git branch -m master main
```

### 配置远程仓库
```bash
git remote add origin [你的仓库链接]
```

### 首次推送到远程仓库
```bash
git push -u origin main
```

## 更新项目内容

### 修改项目文件后重新构建
1. 返回项目根目录编写代码
2. 重新构建项目：
```bash
npm run build
```

### 更新部署
```bash
cd dist
git add .
git commit -m "[提交注释2]"
git push -u origin main
```

## GitHub Pages 设置

### 启用 GitHub Pages
1. 进入 GitHub 仓库页面
2. 点击 "Settings" 选项卡
3. 在左侧菜单中找到 "Pages"
4. 在 "Source" 部分选择 "main" 分支
5. 点击 "Save"

### 等待部署完成
- GitHub 会自动构建并部署页面
- 部署完成后会在 Pages 设置页面显示访问链接
- 通常需要等待 1-2 分钟

## 注意事项
1. 确保 `base` 配置与仓库名完全一致
2. 每次更新代码后都需要重新执行构建和部署流程
3. 首次部署可能需要更长时间
4. 确保仓库设置为公开（public）状态