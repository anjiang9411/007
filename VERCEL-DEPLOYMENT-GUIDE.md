# 🚀 Vercel 部署指南（5分钟完成）

超简单！跟着这个指南，5分钟内就能把应用部署到云端，然后在手机上安装！

---

## 📋 **准备工作**

### 需要的账号：
- ✅ **GitHub 账号**（免费注册：https://github.com）
- ✅ **Vercel 账号**（免费注册：https://vercel.com）

💡 **提示**：可以用 GitHub 账号直接登录 Vercel，超方便！

---

## 🎯 **部署步骤**

### **方法一：使用 Figma Make 导出功能（推荐）** ⭐

如果 Figma Make 支持导出或连接 GitHub：

1. **导出项目**
   - 在 Figma Make 中找到"Export"或"导出"按钮
   - 选择"Export to GitHub"或下载 ZIP 文件

2. **上传到 GitHub**（如果下载了 ZIP）
   - 登录 GitHub
   - 点击右上角 ➕ → "New repository"
   - 仓库名称：`smart-phone-app`（或任意名字）
   - 选择 "Public"
   - 点击 "Create repository"
   - 上传您的代码文件

3. **连接 Vercel**
   - 访问 https://vercel.com
   - 点击 "Add New" → "Project"
   - 选择 "Import Git Repository"
   - 选择您刚创建的 GitHub 仓库
   - 点击 "Import"

4. **配置项目**
   - Framework Preset: 选择 "Other"
   - Build Command: 留空或删除
   - Output Directory: `.`（一个点）
   - Install Command: 留空或删除

5. **添加环境变量**
   - 点击 "Environment Variables"
   - 添加以下变量（从您的 Supabase 项目获取）：
     ```
     VITE_SUPABASE_URL = https://你的项目ID.supabase.co
     VITE_SUPABASE_ANON_KEY = 你的匿名密钥
     ```

6. **部署！**
   - 点击 "Deploy" 按钮
   - 等待 1-2 分钟
   - 完成后会显示：🎉 **Congratulations!**

7. **获取链接**
   - 复制显示的链接，例如：`https://smart-phone-app.vercel.app`
   - 这就是您的应用网址！

---

### **方法二：手动部署（如果方法一不行）**

#### **步骤 1：准备代码**

1. **在 Figma Make 中导出代码**
   - 下载完整项目 ZIP 文件
   - 解压到电脑上

#### **步骤 2：上传到 GitHub**

1. **创建 GitHub 仓库**
   - 访问 https://github.com/new
   - 仓库名：`smart-phone-app`
   - 选择 "Public"
   - 点击 "Create repository"

2. **上传代码**
   
   **选项 A - 网页上传**（简单）：
   - 在 GitHub 仓库页面，点击 "uploading an existing file"
   - 将所有文件拖拽进去
   - 点击 "Commit changes"

   **选项 B - 命令行上传**（如果会用 Git）：
   ```bash
   cd 你的项目文件夹
   git init
   git add .
   git commit -m "Initial commit"
   git remote add origin https://github.com/你的用户名/smart-phone-app.git
   git push -u origin main
   ```

#### **步骤 3：连接 Vercel**

1. **登录 Vercel**
   - 访问 https://vercel.com
   - 用 GitHub 账号登录

2. **导入项目**
   - 点击 "Add New" → "Project"
   - 选择 `smart-phone-app` 仓库
   - 点击 "Import"

3. **配置设置**
   ```
   Framework Preset: Other
   Root Directory: ./
   Build Command: (留空)
   Output Directory: .
   Install Command: (留空)
   ```

4. **环境变量**
   - 点击展开 "Environment Variables"
   - 添加 Supabase 配置（见下方）

5. **点击 Deploy**
   - 等待部署完成（约 1-2 分钟）

---

## 🔑 **环境变量配置**

### 获取 Supabase 配置：

1. **访问 Supabase 控制台**
   - 登录 https://supabase.com
   - 选择您的项目

2. **获取配置信息**
   - 点击左侧 "Settings" → "API"
   - 复制以下内容：
     - **Project URL**：`https://xxxxx.supabase.co`
     - **Anon/Public Key**：`eyJhbG...` (很长的字符串)

3. **在 Vercel 中添加**
   ```
   Name: VITE_SUPABASE_URL
   Value: https://你的项目ID.supabase.co
   
   Name: VITE_SUPABASE_ANON_KEY
   Value: eyJhbG...你的密钥
   ```

---

## 📱 **部署完成后在手机上安装**

### 🎉 **恭喜！您的应用已上线！**

1. **获取应用链接**
   - Vercel 会给您一个链接，例如：
     ```
     https://smart-phone-app.vercel.app
     ```

2. **发送到手机**
   - 通过微信/QQ 发给自己
   - 或在手机浏览器直接输入

3. **安装到手机**
   
   **iPhone (Safari)**：
   - 打开链接
   - 点击底部分享按钮 ⬆️
   - 选择"添加到主屏幕"
   - 点击"添加"
   
   **Android (Chrome)**：
   - 打开链接
   - 等待 10 秒，会弹出安装提示
   - 点击"立即安装"
   - 或手动：菜单 ⋮ → "安装应用"

4. **开始使用！** 🎊
   - 主屏幕会出现应用图标
   - 点击即可像 APP 一样使用！

---

## 🎨 **自定义域名（可选）**

如果您想要更好记的网址：

1. **在 Vercel 项目设置中**
   - Settings → Domains
   - 添加自定义域名，例如：`my-phone.com`

2. **配置 DNS**
   - 在您的域名服务商添加 CNAME 记录
   - 指向 `cname.vercel-dns.com`

---

## 🔄 **更新应用**

### 如何更新部署的应用？

**如果使用 GitHub**：
- 更新 GitHub 仓库的代码
- Vercel 会自动重新部署（约 1 分钟）

**如果直接在 Figma Make 修改**：
- 重新导出代码
- 上传到 GitHub 替换旧文件
- Vercel 自动更新

---

## ❓ **常见问题**

### **Q: 部署后打开是空白页面？**

**解决方法**：
1. 检查浏览器控制台是否有错误
2. 确认环境变量配置正确
3. 查看 Vercel 部署日志是否有错误

### **Q: Supabase 功能不工作？**

**检查清单**：
- ✅ 环境变量是否正确添加？
- ✅ Supabase URL 和 Key 是否正确？
- ✅ 变量名是否正确？(`VITE_` 前缀)

### **Q: 如何查看部署日志？**

1. 进入 Vercel 项目页面
2. 点击 "Deployments"
3. 点击最新的部署
4. 查看 "Build Logs" 和 "Function Logs"

### **Q: 部署失败怎么办？**

**常见原因**：
1. **缺少文件**：确保所有文件都上传了
2. **环境变量错误**：检查 Supabase 配置
3. **构建配置错误**：确保 Build Command 留空

**解决步骤**：
1. 查看错误日志
2. 修复问题
3. 在 Vercel 点击 "Redeploy"

---

## 📊 **部署时间线**

```
开始 ━━━━━━━━━━━━━━━━━━━━ 完成
│
├─ 0分钟：创建 GitHub 仓库
├─ 1分钟：上传代码
├─ 2分钟：连接 Vercel
├─ 3分钟：配置环境变量
├─ 4分钟：点击部署
└─ 5分钟：✅ 部署完成！获得链接！
```

---

## 🎁 **免费额度**

Vercel 免费版包括：
- ✅ 无限次部署
- ✅ 自动 HTTPS
- ✅ 全球 CDN 加速
- ✅ 100GB 带宽/月
- ✅ 自动重新部署

完全够个人使用！🎉

---

## 🆘 **需要帮助？**

如果遇到问题：

1. **查看 Vercel 文档**：https://vercel.com/docs
2. **查看部署日志**：找到具体错误信息
3. **检查 GitHub 仓库**：确保所有文件都在
4. **重新部署**：有时重新部署就能解决

---

## ✅ **快速检查清单**

部署前确认：
- [ ] 已注册 GitHub 账号
- [ ] 已注册 Vercel 账号
- [ ] 已从 Figma Make 导出代码
- [ ] 已创建 GitHub 仓库
- [ ] 已上传所有文件
- [ ] 已获取 Supabase 配置
- [ ] 已在 Vercel 添加环境变量

部署后确认：
- [ ] 网站能正常打开
- [ ] 功能正常工作
- [ ] 已复制部署链接
- [ ] 已在手机上测试
- [ ] 已成功安装到主屏幕

---

**准备好了吗？开始部署吧！** 🚀

如果遇到任何问题，随时告诉我具体的错误信息，我会帮您解决！
