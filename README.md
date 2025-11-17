# 📱 智能社交手机模拟器

一个功能完整的手机模拟器，包含微信、微博、日历、音乐播放器等应用，支持 AI 对话、朋友圈、红包、视频通话等丰富功能。

## ✨ 主要功能

### 📱 核心应用
- **微信** - 完整的聊天、朋友圈、红包、转账、视频/语音通话
- **微博** - 发布动态、点赞评论、热搜榜单
- **日历** - 日程管理、AI 智能提醒
- **音乐** - 全网音乐搜索、歌单管理、桌面控制器
- **通讯录** - 联系人管理、分组功能
- **备忘录** - AI 辅助记录
- **钱包** - 余额管理、交易记录

### 🤖 AI 功能
- **智能对话** - 情绪化、口语化的 AI 角色
- **主动消息** - AI 可根据设置主动发送消息
- **日程提醒** - 智能分析并提醒重要事项
- **朋友圈互动** - AI 会点赞评论您的动态
- **视频通话场景** - 800-2000字的详细场景描写
- **换头像功能** - AI 可识别图片并更换头像

### 🎨 个性化
- **多主题** - 内置多种风格主题
- **自定义背景** - 渐变色或自定义图片
- **个人资料** - 完整的用户信息管理
- **应用图标** - 自定义应用图标和颜色

### 💬 社交功能
- **拍一拍** - 自定义拍一拍后缀
- **红包/转账** - 完整的金额交互
- **礼物系统** - 多种虚拟礼物
- **表情包** - 自定义表情管理
- **群聊** - 支持多人群组

## 🚀 快速开始

### 在线使用（PWA）

1. **访问部署链接**（见下方部署说明）
2. **在手机上安装**：
   - iPhone：Safari → 分享 → 添加到主屏幕
   - Android：Chrome → 菜单 → 安装应用
3. **像真实 APP 一样使用！**

### 本地开发

```bash
# 安装依赖
npm install

# 启动开发服务器
npm run dev

# 构建生产版本
npm run build
```

## 📦 部署指南

### 部署到 Vercel（推荐）

详细步骤请查看：[VERCEL-DEPLOYMENT-GUIDE.md](./VERCEL-DEPLOYMENT-GUIDE.md)

**快速步骤**：
1. Fork 或上传代码到 GitHub
2. 在 Vercel 导入 GitHub 仓库
3. 配置环境变量（Supabase）
4. 点击部署
5. 获得链接，在手机上安装！

### 环境变量配置

需要配置以下环境变量：

```env
VITE_SUPABASE_URL=https://你的项目ID.supabase.co
VITE_SUPABASE_ANON_KEY=你的匿名密钥
VITE_SUPABASE_SERVICE_ROLE_KEY=你的服务密钥
```

## 📱 PWA 功能

本应用支持渐进式网页应用（PWA）：

- ✅ 可安装到手机主屏幕
- ✅ 离线基础功能
- ✅ 全屏显示体验
- ✅ 快速启动
- ✅ 自动缓存更新

详细安装说明：[PWA-INSTALLATION-GUIDE.md](./PWA-INSTALLATION-GUIDE.md)

## 🛠️ 技术栈

- **前端框架**：React 18
- **样式**：Tailwind CSS 4.0
- **动画**：Motion (Framer Motion)
- **UI 组件**：shadcn/ui
- **图标**：Lucide React
- **后端**：Supabase (数据库 + Edge Functions)
- **部署**：Vercel

## 📂 项目结构

```
├── components/           # React 组件
│   ├── ui/              # shadcn/ui 组件
│   ├── WeChat.tsx       # 微信应用
│   ├── Weibo.tsx        # 微博应用
│   ├── Moments.tsx      # 朋友圈
│   ├── PwaInstaller.tsx # PWA 安装器
│   └── ...
├── utils/               # 工具函数
│   ├── aiDiaryGenerator.ts  # AI 日记生成
│   ├── groupChatAi.tsx      # 群聊 AI
│   └── ...
├── supabase/            # 后端代码
│   └── functions/
│       └── server/      # Edge Functions
├── styles/              # 全局样式
├── public/              # 静态资源
│   ├── manifest.json    # PWA 配置
│   └── service-worker.js # 离线支持
└── App.tsx              # 主应用入口
```

## 🎯 核心组件说明

### WeChat.tsx
完整的微信应用，包含：
- 聊天列表和对话界面
- AI 角色系统
- 红包、转账、礼物
- 视频/语音通话
- 拉黑功能
- 备忘录

### Moments.tsx
朋友圈功能：
- 发布动态（文字、图片、视频）
- 点赞评论
- AI 自动互动
- 分享功能

### Weibo.tsx
微博应用：
- 发布微博
- 热搜榜
- 点赞转发评论
- 个人主页

### PwaInstaller.tsx
PWA 安装提示组件：
- 智能检测安装条件
- 友好的安装引导
- 自动显示/隐藏

## 🔧 配置说明

### API 配置
支持多个 AI API 提供商：
- OpenAI
- Anthropic (Claude)
- DeepSeek
- 自定义 API

在设置中可以切换和配置不同的 API。

### 主题配置
内置主题：
- 🌸 樱花粉
- 💜 薰衣草
- 🌊 海洋蓝
- 🌅 日落橙
- 🌿 森林绿
- 🌙 午夜黑

可自定义渐变背景和上传自定义图片。

## 📝 开发说明

### 添加新应用

1. 在 `components/` 创建新组件
2. 在 `App.tsx` 中导入
3. 在 `socialApps` 数组添加应用配置
4. 在 `renderAppContent` 中添加渲染逻辑

### 添加新的 AI 功能

1. 在 `utils/` 创建工具函数
2. 调用后端 API：`/functions/v1/make-server-ae7aa30b/chat`
3. 处理返回的 AI 响应

### 数据存储

使用 Supabase KV Store：
```typescript
import * as kv from './supabase/functions/server/kv_store.tsx';

// 存储
await kv.set('key', value);

// 读取
const value = await kv.get('key');
```

## 🐛 问题排查

### 常见问题

**1. PWA 安装提示不显示**
- 确保使用 HTTPS 链接
- 确保使用支持的浏览器
- 清除缓存后重试

**2. AI 功能不工作**
- 检查 API 密钥配置
- 查看控制台错误信息
- 确认后端服务正常

**3. 图片加载失败**
- 检查图片 URL 是否正确
- 确认跨域配置
- 使用 ImageWithFallback 组件

### 调试工具

应用内置了调试工具：
- **服务器状态横幅** - 显示后端连接状态
- **API 诊断工具** - 测试 API 连接
- **服务器连接测试** - 检查后端健康状态

## 📄 许可证

MIT License

## 🤝 贡献

欢迎提交 Issue 和 Pull Request！

## 📮 联系方式

如有问题或建议，请通过 GitHub Issues 联系。

---

## 🎉 更新日志

### v1.0.0 (2024)
- ✅ 初始版本发布
- ✅ 微信、微博、日历等核心功能
- ✅ AI 对话和智能提醒
- ✅ PWA 支持
- ✅ 完整的社交功能
- ✅ 主题自定义

---

**享受使用吧！** 如有问题，查看 [部署指南](./VERCEL-DEPLOYMENT-GUIDE.md) 和 [PWA 安装指南](./PWA-INSTALLATION-GUIDE.md)。
