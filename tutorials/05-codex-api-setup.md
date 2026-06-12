# 05. 创建 OpenAI Codex API

## 🎯 本课目标

注册 OpenAI 账号，创建你的第一个 API Key，了解 Codex 模型。

> ⏱️ **预计时间**：30-45 分钟
> 💰 **费用**：注册免费，有 $5 免费额度

---

## 📝 第一步：注册 OpenAI 账号

1. 打开浏览器，访问 **https://platform.openai.com**
2. 点击页面上的 **"Sign up"**（注册）
3. 你可以选择：
   - 用邮箱注册（输入邮箱、设置密码）
   - 用 Google 账号直接登录
   - 用 Microsoft 账号直接登录

4. 注册后会让你验证邮箱——去邮箱里找到 OpenAI 发的验证邮件，点击里面的链接

5. 验证完成后，可能会让你填写一些基本信息（名字、地区等）

6. 可能会要求**手机号验证**，输入你的手机号，收到验证码后填入即可

> 📱 **注意**：部分地区的手机号可能无法验证。如果遇到问题，可以参考本文末尾的常见问题。

---

## 🔑 第二步：创建 API Key

1. 登录后，在左侧菜单栏找到 **"API keys"**
   - 或者直接访问：https://platform.openai.com/api-keys

2. 点击 **"+ Create new secret key"** 按钮

3. 弹窗会让你填写：
   - **Name**（名称）：随便写，比如 `my-first-key` 或 `tutorial-key`
   - **Project**（项目）：选择默认的即可
   - **Permissions**（权限）：选择默认的即可

4. 点击 **"Create secret key"**

5. ⚠️ **关键一步**：API Key 会立即显示出来，格式类似：
   ```
   sk-proj-abc123def456...
   ```
   **现在就复制并保存！** 这个页面关掉后，你再也看不到完整的 Key 了。

6. 把 Key 保存到一个安全的地方，比如：
   - 新建一个文本文件，暂时存进去
   - 或者用密码管理器

> 🔴 **重要**：不要截图发朋友圈！不要传到 GitHub！不要发给别人！

---

## 🎓 第三步：了解 Codex 模型

OpenAI 提供多种模型，你不需要全部记住。先了解这几个：

| 模型 | 特点 | 适合场景 |
|------|------|---------|
| **GPT-4o** | 最新多模态模型，速度快 | 通用对话、代码、图片理解 |
| **GPT-4o-mini** | 轻量版，便宜 | 简单任务、批量处理 |
| **GPT-4** | 推理能力强 | 复杂问题分析 |
| **Codex** | 专门针对代码优化 | 代码生成、代码解释 |

在本教程中，我们主要关注 **Codex** 和 **GPT-4o**。

---

## 🧪 第四步：测试你的 API Key

打开终端（或 PowerShell），用 curl 发一个测试请求：

```bash
curl https://api.openai.com/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer 你的API-Key粘贴到这里" \
  -d '{
    "model": "gpt-4o-mini",
    "messages": [
      {"role": "user", "content": "Hello! Say hello back in one sentence."}
    ]
  }'
```

> ⚠️ 把 `你的API-Key粘贴到这里` 替换成你刚才复制的那串 Key

如果成功，你会看到类似这样的返回：

```json
{
  "choices": [
    {
      "message": {
        "content": "Hello! It's great to connect with you today."
      }
    }
  ]
}
```

看到 `"Hello! ..."` 就说明成功了！

---

## 📊 第五步：查看用量

1. 登录 OpenAI Platform：https://platform.openai.com
2. 左侧菜单 → **"Usage"**
3. 可以看到你的 API 调用次数和花费

免费额度用完后，需要充值才能继续使用。

---

## 🆘 常见问题

### Q: 手机号无法验证？

**解决方案**：
- 确保手机号前面选了正确的国家代码（中国大陆是 +86）
- 尝试用虚拟号码服务（不推荐，可能被封）
- 换一个网络环境试试

### Q: 注册后没有免费额度？

OpenAI 的政策可能会变化。如果新账号没有免费额度，最低充值一般是 $5。

### Q: API Key 不小心泄露了怎么办？

1. 马上去 OpenAI Platform → API Keys
2. 找到泄露的 Key，点击 **"Revoke"**（撤销）
3. 创建一个新的 Key

### Q: curl 命令在 Windows 上不能用？

Windows PowerShell 中 curl 的语法略有不同。你也可以用 Postman 或直接写一个 Node.js 脚本来测试——后面教程会教。

---

## ✅ 检查清单

- [ ] 成功注册 OpenAI 账号
- [ ] 创建了一个 API Key 并保存好
- [ ] 用 curl 成功测试了 API Key
- [ ] 知道 Codex 和 GPT-4o 的区别

---

**上一篇**: [API 基础概念 →](./04-api-basics.md)
**下一篇**: [创建 Anthropic Claude API →](./06-claude-api-setup.md)

**最后更新**: 2026年6月12日
