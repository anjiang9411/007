# ⚡ 5分钟快速部署清单

## 🎯 目标
让应用在 5 分钟内上线，可以在手机上安装使用！

---

## ✅ 第一步：准备账号（1分钟）

- [ ] **注册 GitHub**：https://github.com/signup
  - 已有账号？直接登录
  
- [ ] **注册 Vercel**：https://vercel.com/signup
  - 用 GitHub 账号登录即可（推荐）

---

## ✅ 第二步：上传代码到 GitHub（2分钟）

### 方式 A：Figma Make 直接导出到 GitHub
- [ ] 在 Figma Make 找到"Export"或"GitHub"按钮
- [ ] 连接您的 GitHub 账号
- [ ] 创建新仓库：`smart-phone-app`
- [ ] 导出完成！

### 方式 B：手动上传
- [ ] 在 Figma Make 下载 ZIP 文件
- [ ] 访问：https://github.com/new
- [ ] 仓库名：`smart-phone-app`
- [ ] 选择 "Public"
- [ ] 点击"Create repository"
- [ ] 点击"uploading an existing file"
- [ ] 拖拽所有文件进去
- [ ] 点击"Commit changes"
- [ ] 上传完成！

---

## ✅ 第三步：部署到 Vercel（1分钟）

- [ ] 访问：https://vercel.com/new
- [ ] 点击"Import Git Repository"
- [ ] 选择 `smart-phone-app` 仓库
- [ ] 点击"Import"
- [ ] **重要配置**：
  ```
  Framework Preset: Other
  Build Command: (删除/留空)
  Output Directory: .  (一个点)
  Install Command: (删除/留空)
  ```
- [ ] 先不点 Deploy！继续下一步 ↓

---

## ✅ 第四步：配置环境变量（1分钟）

### 获取 Supabase 配置：

- [ ] 打开新标签页访问：https://supabase.com
- [ ] 登录您的项目
- [ ] 点击左侧 **Settings** → **API**
- [ ] 复制两个值：
  
  **1. Project URL**（看起来像这样）：
  ```
  https://abcdefghijk.supabase.co
  ```
  
  **2. Anon/Public Key**（很长的字符串）：
  ```
  eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...
  ```

### 在 Vercel 中添加：

- [ ] 回到 Vercel 部署页面
- [ ] 展开 **Environment Variables**
- [ ] 添加第一个变量：
  ```
  Name: VITE_SUPABASE_URL
  Value: [粘贴您的 Project URL]
  ```
- [ ] 添加第二个变量：
  ```
  Name: VITE_SUPABASE_ANON_KEY
  Value: [粘贴您的 Anon Key]
  ```

---

## ✅ 第五步：部署！（等待 1-2 分钟）

- [ ] 点击 **Deploy** 按钮
- [ ] 等待进度条完成
- [ ] 看到 **🎉 Congratulations!**
- [ ] **复制部署链接**，例如：
  ```
  https://smart-phone-app.vercel.app
  ```

---

## 📱 第六步：在手机上安装

### iPhone 用户：

- [ ] 把链接发给自己（微信/QQ）
- [ ] **用 Safari 打开**链接
- [ ] 点击底部**分享按钮** ⬆️
- [ ] 选择"**添加到主屏幕**"
- [ ] 点击"**添加**"
- [ ] 完成！查看主屏幕图标

### Android 用户：

- [ ] 把链接发给自己（微信/QQ）
- [ ] **用 Chrome 打开**链接
- [ ] 使用 10 秒后会弹出安装提示
- [ ] 点击"**立即安装**"
- [ ] 完成！查看主屏幕图标

---

## 🎊 完成检查

- [ ] 应用能在浏览器打开
- [ ] 手机上成功安装
- [ ] 能看到主屏幕图标
- [ ] 点击图标能正常打开
- [ ] 功能正常工作

---

## ⚠️ 遇到问题？

### 问题：部署后打不开

**检查**：
- 环境变量是否正确？
- Supabase URL 和 Key 复制完整了吗？
- 变量名拼写正确吗？

**解决**：
- 去 Vercel 项目 Settings → Environment Variables
- 检查并修改变量
- 点击 Deployments → 最新部署 → Redeploy

### 问题：手机上安装不了

**iPhone**：
- 必须用 Safari！不能用 Chrome
- 确认链接是 https:// 开头

**Android**：
- 用 Chrome 浏览器
- 如果没弹出提示：菜单 ⋮ → "安装应用"

### 问题：功能不工作

**检查**：
- 打开浏览器控制台（F12）查看错误
- 确认 Supabase 后端正常运行
- 检查 API 密钥配置

---

## 📊 时间表

```
✅ 第1分钟：注册账号
✅ 第2-3分钟：上传代码到 GitHub  
✅ 第4分钟：连接 Vercel + 配置
✅ 第5分钟：部署完成！
✅ +1分钟：在手机上安装
━━━━━━━━━━━━━━━━━━━━━
🎉 总共 6 分钟搞定！
```

---

## 🔗 有用的链接

- GitHub：https://github.com
- Vercel：https://vercel.com
- Supabase：https://supabase.com
- 详细教程：查看 VERCEL-DEPLOYMENT-GUIDE.md

---

## 💡 小提示

1. **首次部署**可能需要 5-8 分钟，很正常
2. **保存好链接**！可以分享给朋友
3. **自定义域名**：在 Vercel 设置中可以绑定自己的域名
4. **自动更新**：修改 GitHub 代码后会自动重新部署

---

**准备好了吗？开始计时！⏱️**

现在就开始第一步吧！👆
