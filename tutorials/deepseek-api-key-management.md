# 09. 创建 DeepSeek API

## 🎯 本课目标

注册 DeepSeek 开放平台账号，创建 DeepSeek API Key，了解 DeepSeek 模型家族。

> ⏱️ **预计时间**：15-30 分钟
> 💰 **费用**：注册免费，新用户赠送 500 万 Tokens

---

## 📝 第一步：注册 DeepSeek 账号

1. 打开浏览器，访问 **https://platform.deepseek.com**

2. 点击页面右上角的 **"Sign up"** 或 **"注册"**

3. 填写注册信息：
   - 邮箱地址
   - 设置密码
   - 验证码（发送到邮箱）

4. 去邮箱里找到 DeepSeek 发的验证邮件，点击验证链接

5. 登录后进入控制台主页（Dashboard）

> 💡 **提示**：DeepSeek 支持国内邮箱（QQ邮箱、163邮箱等），注册流程非常顺畅，无需海外手机号验证。

---

## 🔑 第二步：创建 API Key

1. 登录后，在左侧菜单找到 **"API Keys"**
   - 或直接访问：https://platform.deepseek.com/api_keys

2. 点击 **"创建 API Key"**（Create API Key）按钮

3. 填写密钥名称，比如 `tutorial-key`

4. 点击 **"创建"**，密钥会立即显示，格式类似：
   ```
   sk-xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
   ```

5. ⚠️ **关键一步**：API Key **只在创建时显示一次**，关掉弹窗后就看不到了。**立刻复制并保存！**

> 🔴 **重要**：不要公开、不要上传 GitHub、不要发给别人！建议为不同项目创建独立的 Key，并开启 IP 白名单。

---

## 🎓 第三步：了解 DeepSeek 模型家族

DeepSeek 的模型目前主要有以下几个：

| 模型名 | 特点 | 适合场景 |
|--------|------|---------|
| **deepseek-chat**（通用版） | 非思考模式，128K 上下文 | 日常对话、写作、翻译、通用编程 |
| **deepseek-reasoner**（推理版） | 思考模式，128K 上下文 | 数学推理、复杂逻辑、高难度编程 |
| **deepseek-v4-flash**（V4 快速版） | 1M 上下文，速度最快、价格最低 | 日常开发、批量任务、长文档处理 |
| **deepseek-v4-pro**（V4 专业版） | 1M 上下文，最强推理能力 | 复杂分析、高级编程、Agent 任务 |

> 📌 **记忆技巧**：
> - `-chat` = 聊天模式（快，不思考）
> - `-reasoner` = 推理模式（慢，会思考）
> - `-flash` = 闪电（最快最省）
> - `-pro` = 专业（最强最贵）

### ⚠️ 重要：模型命名变更

DeepSeek 官方已宣布，`deepseek-chat` 和 `deepseek-reasoner` 这两个旧模型名将于 **2026 年 7 月 24 日** 正式弃用，之后将自动映射到 `deepseek-v4-flash` 的对应模式（思考 / 非思考）。建议新项目直接使用新版模型名：

| 新名称 | 对应旧名称 | 模式 |
|--------|-----------|------|
| `deepseek-v4-flash` | `deepseek-chat` | 非思考模式 |
| `deepseek-v4-flash` | `deepseek-reasoner` | 思考模式 |
| `deepseek-v4-pro` | — | 支持思考/非思考切换 |

对于本教程的学习，使用 **`deepseek-v4-flash`** 就完全够用了，性价比最高。

---

## 🧪 第四步：测试你的 API Key

打开终端，用 curl 发一个测试请求：

```bash
curl https://api.deepseek.com/chat/completions \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer 你的API-Key粘贴到这里" \
  -d '{
    "model": "deepseek-v4-flash",
    "messages": [
      {"role": "user", "content": "你好！请用一句话打个招呼。"}
    ],
    "stream": false
  }'
```

> ⚠️ 把 `你的API-Key粘贴到这里` 替换成你刚才复制的 Key

如果成功，你会看到类似这样的返回：

```json
{
  "choices": [
    {
      "message": {
        "content": "你好！很高兴见到你，有什么我可以帮你的吗？"
      }
    }
  ]
}
```

看到回复内容就说明成功了！

### 用 jq 提取回复内容

如果你安装了 `jq` 工具，可以这样只提取 AI 说的话：

```bash
curl -s https://api.deepseek.com/chat/completions \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer 你的API-Key粘贴到这里" \
  -d '{
    "model": "deepseek-v4-flash",
    "messages": [
      {"role": "user", "content": "你好"}
    ]
  }' | jq -r '.choices[0].message.content'
```

---

## 🔍 第五步：OpenAI 与 DeepSeek API 的差异

DeepSeek 的 API **高度兼容 OpenAI 格式**，但有一些关键区别。这里做个对比：

| 对比项 | OpenAI | DeepSeek |
|--------|--------|----------|
| Endpoint | `https://api.openai.com/v1/chat/completions` | `https://api.deepseek.com/chat/completions` |
| API Key 格式 | `sk-proj-...` 或 `sk-...` | `sk-...`（OpenAI 兼容格式） |
| 认证方式 | `Authorization: Bearer <key>` | `Authorization: Bearer <key>` ✅ 相同 |
| 消息格式 | `messages=[{role, content}]` | 完全一致 ✅ |
| 支持的 SDK | OpenAI SDK / 任何 OpenAI 兼容客户端 | OpenAI SDK（改 base_url 即可） |
| 特有功能 | 无思考模式 | `thinking` 参数、`reasoning_effort` 参数 |
| 免费额度 | 付费为主 | 新用户赠送 500 万 Tokens |

### 用 OpenAI SDK 调用 DeepSeek

只需改 **两行代码**：

```python
from openai import OpenAI

client = OpenAI(
    api_key="你的DeepSeek-API-Key",          # 换成 DeepSeek 的 Key
    base_url="https://api.deepseek.com"      # 换成 DeepSeek 的地址
)

response = client.chat.completions.create(
    model="deepseek-v4-flash",               # 换成 DeepSeek 的模型
    messages=[
        {"role": "user", "content": "你好"}
    ]
)

print(response.choices[0].message.content)
```

> 💡 这就是为什么很多工具（如 CC-Switch）能同时支持多家模型 —— 因为它们都兼容 OpenAI 的 API 格式，只需要切换 base_url 和 API Key。

---

## 🆘 常见问题

### Q: DeepSeek 新用户有多少免费额度？

新用户注册后通常赠送 **500 万 Tokens**（有效期约 30 天），用于体验和测试基本够用。可以在控制台 → 用量页面查看剩余额度。

### Q: 我是小白，应该选哪个模型？

选 **`deepseek-v4-flash`**。它又快又便宜，1M 超长上下文，学习阶段完全足够。旧名称 `deepseek-chat` 也可以用，但建议直接上新的 `deepseek-v4-flash`。

### Q: 注册时需要手机号验证吗？

DeepSeek 主要使用邮箱注册，验证码发到邮箱即可。部分地区可能需要手机验证，但整体流程比 Anthropic/OpenAI 简单，国内用户友好。

### Q: DeepSeek 支持中文吗？

**非常支持。** DeepSeek 本身就是中国公司开发的模型，对中文的理解和生成能力在业界属于顶尖水平，中文编程场景表现尤其出色。

### Q: API Key 丢了怎么办？

无法找回。去控制台 → API Keys 页面，把旧的删掉，重新创建一个新的 Key 即可。

### Q: DeepSeek 的价格贵吗？

**非常便宜。** 以 `deepseek-v4-flash` 为例：
- 输入：1 元 / 百万 Tokens（缓存未命中）
- 输出：2 元 / 百万 Tokens
- 缓存命中仅 0.02 元 / 百万 Tokens

相比同类模型，性价比极高。详情见官方定价页：https://api-docs.deepseek.com/zh-cn/quick_start/pricing

---

## ✅ 检查清单

- [ ] 成功注册 DeepSeek 账号（platform.deepseek.com）
- [ ] 创建了一个 API Key 并保存好
- [ ] 用 curl 成功测试了 API Key
- [ ] 知道 `deepseek-chat` / `deepseek-reasoner` / `deepseek-v4-flash` / `deepseek-v4-pro` 的区别
- [ ] 能说出 OpenAI 和 DeepSeek API 的主要差异
- [ ] 知道如何用 OpenAI SDK 调用 DeepSeek（改 base_url + api_key）

---

**上一篇**: [创建 OpenAI Codex API →](./05-codex-api-setup.md)
**下一篇**: [API Key 管理与安全 →](./07-api-key-management.md)

**最后更新**: 2026年6月12日
