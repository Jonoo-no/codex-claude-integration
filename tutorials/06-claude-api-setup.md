# 06. 创建 Anthropic Claude API

## 🎯 本课目标

注册 Anthropic 账号，创建 Claude API Key，了解 Claude 模型家族。

> ⏱️ **预计时间**：30-45 分钟
> 💰 **费用**：注册免费，有试用额度

---

## 📝 第一步：注册 Anthropic 账号

1. 打开浏览器，访问 **https://console.anthropic.com**

2. 点击页面上的 **"Sign up"** 或 **"Get started"**

3. 你可以选择：
   - 用邮箱注册
   - 用 Google 账号登录

4. 填写注册信息：
   - 邮箱地址
   - 设置密码
   - 名字

5. 去邮箱里找到 Anthropic 发的验证邮件，点击验证链接

6. 首次登录可能会问几个问题：
   - **What are you building?**（你在做什么？）
     → 随便选一个，比如 "Personal project" 或 "Learning"
   - **How did you hear about us?**（怎么知道我们的？）
     → 随便选一个即可

---

## 🔑 第二步：创建 API Key

1. 登录后，在左侧菜单找到 **"API Keys"**
   - 或直接访问：https://console.anthropic.com/settings/keys

2. 点击 **"Create Key"** 按钮

3. 填写信息：
   - **Name**（名称）：随便写，比如 `tutorial-key`
   - **Workspace**（工作区）：选择默认的

4. 点击 **"Create Key"**

5. ⚠️ **关键一步**：API Key 会立即显示，格式类似：
   ```
   sk-ant-api03-abc123def456...
   ```
   **立刻复制并保存！** 关掉弹窗后就看不到完整的了。

> 🔴 **重要**：同样，不要公开、不要上传、不要发给别人！

---

## 🎓 第三步：了解 Claude 模型家族

Anthropic 的模型都以 **Claude** 命名，目前主要有三个系列：

| 模型 | 特点 | 适合场景 |
|------|------|---------|
| **Claude Opus** | 最强推理能力、最贵 | 复杂分析、数学推理、高难度编程 |
| **Claude Sonnet** | 平衡性能与速度、性价比高 | 日常编程、写作、一般任务 |
| **Claude Haiku** | 最快、最便宜 | 简单问答、批量处理、实时对话 |

> 📌 **记忆技巧**：
> - Opus = 巨作（最强）
> - Sonnet = 十四行诗（中等）
> - Haiku = 俳句（最简洁）

对于本教程的学习，使用 **Claude Sonnet** 就完全够用了，性价比最高。

---

## 🧪 第四步：测试你的 API Key

打开终端，用 curl 发一个测试请求：

```bash
curl https://api.anthropic.com/v1/messages \
  -H "Content-Type: application/json" \
  -H "x-api-key: 你的API-Key粘贴到这里" \
  -H "anthropic-version: 2023-06-01" \
  -d '{
    "model": "claude-sonnet-4-6",
    "max_tokens": 100,
    "messages": [
      {"role": "user", "content": "Hello! Say hello back in one sentence."}
    ]
  }'
```

> ⚠️ 把 `你的API-Key粘贴到这里` 替换成你刚才复制的 Key

如果成功，你会看到类似这样的返回：

```json
{
  "content": [
    {
      "text": "Hello! Great to meet you — how can I help you today?"
    }
  ]
}
```

看到回复内容就说明成功了！

---

## 🔍 第五步：两个平台 API 的差异

你已经看到 OpenAI 和 Anthropic 的 API 调用方式略有不同，这里做个对比：

| 对比项 | OpenAI | Anthropic |
|--------|--------|-----------|
| Endpoint | `/v1/chat/completions` | `/v1/messages` |
| 认证方式 | `Authorization: Bearer <key>` | `x-api-key: <key>` |
| Key 格式 | `sk-proj-...` | `sk-ant-api03-...` |
| 消息角色 | `user`, `assistant`, `system` | `user`, `assistant` |
| 额外参数 | 无需版本头 | 需要 `anthropic-version` 头 |

> 💡 现在知道为什么需要 CC-Switch 和 Echo Bird 这样的工具了吗？因为它们可以帮你统一这些差异，让你用一套方式调用所有模型。后面第三阶段会详细讲。

---

## 🆘 常见问题

### Q: Anthropic 的免费额度有多少？

Anthropic 会给新用户一定的试用额度，具体金额可能会变。可以在 Console → Usage 页面查看。

### Q: 我是小白，应该选哪个模型？

就选 **Claude Sonnet**。它又快又好，价格适中，学习阶段完全足够。

### Q: "anthropic-version" 是什么？

Anthropic 要求每个请求都带上 API 版本号，用来控制兼容性。目前用 `2023-06-01` 就行，后面的教程会一直用它。

### Q: 注册时手机号验证通不过？

Anthropic 目前对部分地区可能需要额外验证。如果遇到问题：
- 试试用 Google 账号登录
- 检查网络环境
- 联系 Anthropic 客服

---

## ✅ 检查清单

- [ ] 成功注册 Anthropic 账号
- [ ] 创建了一个 Claude API Key 并保存好
- [ ] 用 curl 成功测试了 API Key
- [ ] 知道 Opus / Sonnet / Haiku 的区别
- [ ] 能说出 OpenAI 和 Anthropic API 的两个主要差异

---

**上一篇**: [创建 OpenAI Codex API →](./05-codex-api-setup.md)
**下一篇**: [API Key 管理与安全 →](./07-api-key-management.md)

**最后更新**: 2026年6月12日
