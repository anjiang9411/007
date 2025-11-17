# 故障排除指南

## ❌ "Failed to fetch" 错误

### 问题描述
在使用AI聊天功能时，遇到 `TypeError: Failed to fetch` 错误，无法连接到后端服务器。

### 可能的原因

1. **Supabase Edge Function 冷启动** ⏱️
   - Edge Functions 在闲置一段时间后会进入休眠状态
   - 首次请求时需要10-30秒来启动
   - 这是Supabase的正常行为

2. **网络连接问题** 🌐
   - 本地网络不稳定
   - 防火墙阻止访问
   - VPN或代理设置问题

3. **CORS配置问题** 🔒
   - 浏览器阻止跨域请求
   - 服务器CORS配置不正确

4. **Edge Function未部署** 🚀
   - Supabase项目中的Edge Function未正确部署
   - 项目ID配置错误

### 解决方法

#### 方法1: 等待服务器预热（推荐） ⏰

应用已内置自动预热功能：
1. **刷新页面** - 应用会自动预热后端服务器
2. **等待30秒** - 观察浏览器控制台的预热日志
3. **查看预热状态**：
   ```
   ✅ [Server Warmup] 预热成功 - 服务器已就绪
   ❌ [Server Warmup] 预热失败 - 需要进一步诊断
   ```
4. **重试操作** - 预热成功后再次尝试AI聊天

#### 方法2: 手动测试连接 🔧

1. 打开**微信设置** > **AI配置**
2. 点击**服务器连接测试**按钮
3. 查看5项测试结果：
   - ✅ 所有通过 = 后端正常
   - ❌ 部分失败 = 查看具体错误提示

#### 方法3: 检查浏览器控制台 🔍

打开浏览器开发者工具（F12），查看控制台日志：

**成功的预热日志示例：**
```
🔥 [Server Warmup] 开始预热服务器...
🔥 [Server Warmup] Project ID: ufquykfrqpstdjgkykcq
🔥 [Server Warmup] 预热URL: https://ufquykfrqpstdjgkykcq.supabase.co/functions/v1/make-server-ae7aa30b/health
🔥 [Server Warmup] 响应状态: 200 OK
✅ [Server Warmup] 预热成功！耗时 2543ms
```

**失败的预热日志示例：**
```
❌ [Server Warmup] 网络连接失败
❌ [Server Warmup] 可能原因：1) CORS问题 2) Edge Function未部署 3) 网络不可达
```

#### 方法4: 验证Edge Function部署 📦

1. 在浏览器中直接访问（替换你的项目ID）：
   ```
   https://YOUR_PROJECT_ID.supabase.co/functions/v1/make-server-ae7aa30b/health
   ```
2. 应该看到JSON响应：
   ```json
   {
     "status": "ok",
     "timestamp": "2024-11-16T04:24:28.527Z",
     "environment": {
       "hasSupabaseUrl": true,
       "hasSupabaseServiceKey": true,
       "hasAnonKey": true
     }
   }
   ```
3. 如果看到404错误，说明Edge Function未部署

#### 方法5: 检查网络设置 🌐

1. **关闭VPN/代理**
2. **尝试不同的网络环境**（Wi-Fi / 移动数据）
3. **检查防火墙设置**
4. **清除浏览器缓存**

---

## ❌ "API key expired" 错误

### 问题描述
在聊天测试中看到：`API key expired. Please renew the API key`

### 原因
这是**外部AI服务商**（如Gemini、Claude、OpenAI）的API密钥过期了，不是Supabase的问题。

### 解决方法

1. **打开微信** > **设置** > **AI配置**
2. **选择对应的API配置**
3. **更新API密钥**：
   - 如果使用的是代理服务（如997128.xyz），去代理网站更新密钥
   - 如果使用官方API，去官方网站获取新密钥：
     - Gemini: https://ai.google.dev/
     - OpenAI: https://platform.openai.com/
     - Claude: https://console.anthropic.com/
4. **保存配置**
5. **重新测试**

---

## 📊 诊断工具使用

### 服务器连接测试

**位置**：微信 > 设置 > AI配置 > 服务器连接测试

**测试项目**：
1. ✅ 根路径连接 - 测试基础网络连通性
2. ✅ 健康检查端点 - 验证服务器状态和环境变量
3. ✅ CORS预检请求 - 检查跨域配置
4. ✅ POST请求（回声测试）- 测试数据传输
5. ✅ API配置端点 - 验证API端点可访问性

### API诊断工具

**位置**：微信 > 设置 > AI配置 > 诊断

**功能**：
- 测试AI API连接
- 验证API密钥有效性
- 检查模型可用性
- 查看详细错误信息

---

## 🆘 常见问题解答

### Q: 为什么首次使用时总是出错？
**A**: Edge Function冷启动需要时间。刷新页面后等待30秒，让预热功能完成。

### Q: 预热成功但聊天还是失败？
**A**: 
1. 检查是否配置了AI API
2. 验证API密钥是否有效
3. 使用API诊断工具测试

### Q: 如何知道是哪个环节出了问题？
**A**: 按顺序检查：
1. 服务器预热日志 → 后端连接
2. 服务器连接测试 → 具体端点
3. API诊断工具 → AI服务商连接

### Q: 所有测试都通过，但功能还是不工作？
**A**: 
1. 刷新页面
2. 清除浏览器缓存
3. 尝试无痕模式
4. 检查浏览器控制台的具体错误

---

## 📞 获取帮助

如果以上方法都无法解决问题：

1. **导出诊断日志**：
   - 打开服务器连接测试
   - 点击"导出日志到控制台"
   - 复制控制台内容

2. **查看详细错误**：
   - 打开浏览器开发者工具（F12）
   - 切换到"Console"标签
   - 找到红色的错误信息
   - 复制完整的错误堆栈

3. **提供以下信息**：
   - 浏览器类型和版本
   - 网络环境（Wi-Fi / 移动数据 / VPN）
   - 错误发生的具体步骤
   - 诊断日志和错误信息

---

## ✅ 最佳实践

1. **定期检查API密钥有效期**
2. **保持浏览器和应用更新**
3. **使用稳定的网络环境**
4. **首次使用时给予足够的预热时间**
5. **遇到问题时先查看浏览器控制台**

---

**更新日期**: 2024-11-16
**版本**: v1.0
