# 08. 创建智谱 GLM API

## 🎯 本课目标

注册智谱 AI（BigModel）开放平台账号，创建 GLM API Key，了解 GLM 模型家族。

> ⏱️ **预计时间**：15-30 分钟
> 💰 **费用**：注册免费，GLM-4-Flash 完全免费使用

---

## 📝 第一步：注册智谱 AI 账号

1. 打开浏览器，访问 **https://open.bigmodel.cn**（智谱 AI 开放平台）

2. 点击页面右上角的 **"注册"** 或 **"登录"**

3. 注册方式：
   - 使用 **手机号** 注册（国内用户推荐）
   - 也支持邮箱注册

4. 填写注册信息：
   - 手机号 / 邮箱
   - 设置密码
   - 输入短信 / 邮箱验证码

5. 登录后进入控制台主页

> 💡 **提示**：智谱开放平台由清华系 AI 公司"智谱 AI"运营，国内用户注册非常方便，无需海外手机号或特殊网络环境。

---

## 🔑 第二步：创建 API Key

智谱提供了两种使用方式，按需选择：

### 方式一：按量付费（通用 API）

1. 登录后，进入 **API Keys 管理页面**
   - 路径：控制台 → [用户中心](https://bigmodel.cn/usercenter/proj-mgmt/apikeys) → API Keys
   - 或直接访问：https://bigmodel.cn/usercenter/proj-mgmt/apikeys

2. 点击 **"创建 API Key"** 按钮

3. 填写密钥名称，比如 `tutorial-key`

4. 密钥会立即显示，格式类似：
   ```
   xxxxxxxx.xxxxxxxxxxxxxxxx
   ```
   （32 位十六进制 . 16 位字母数字）

5. ⚠️ **关键一步**：API Key **只在创建时显示一次**，关掉弹窗后就看不到了。**立刻复制并保存！**

#### 通用 API 端点

```
https://open.bigmodel.cn/api/paas/v4
```

### 方式二：Coding Plan（编程套餐，新用户推荐）

智谱提供了专门的 **Coding Plan（编程套餐）**，针对 AI 编程场景做了优化：

1. 访问 [编程套餐概览页](https://bigmodel.cn/coding-plan/personal/overview)
2. 选择订阅套餐（个人版 / 团队版）
3. 订阅后，在 **"套餐概览"** 页面新建 API Key
4. 此套餐下的 API Key 使用 **独立的 Coding 端点**：

#### Coding Plan API 端点

```
https://open.bigmodel.cn/api/coding/paas/v4
```

> ⚠️ **注意**：按量付费和 Coding Plan 使用的 API 端点不同，配置时请留意区分！

> 🔴 **重要**：无论哪种方式，不要公开、不要上传 GitHub、不要发给别人！

---

## 🎓 第三步：了解 GLM 模型家族

智谱的模型统称为 **GLM（General Language Model）**，目前已发展到 GLM-5 系列。以下是核心模型一览：

### 🆓 免费模型

| 模型 | 上下文 | 特点 |
|------|--------|------|
| **GLM-4-Flash** | 128K | 免费，通用对话、内容创作，入门首选 |
| **GLM-4.7-Flash** | 128K | 免费，混合思考模型，30B 参数 / 3B 激活 |
| **GLM-Z1-Flash** | 128K | 免费，推理模型，数学/代码/逻辑推理 |

### ⚡ 高性价比模型

| 模型 | 价格 | 上下文 | 特点 |
|------|------|--------|------|
| **GLM-4-FlashX** | ¥0.10 / 百万 tokens | 128K | Flash 增强版，超快推理 |
| **GLM-Z1-Air** | ¥0.50 / 百万 tokens | 128K | 性价比最高的推理模型，DeepSeek-R1 价格的 1/30 |
| **GLM-Z1-AirX** | ¥5.00 / 百万 tokens | 128K | 极速推理（200 tokens/s），速度快 8 倍 |

### 💪 主力模型

| 模型 | 上下文 | 特点 | 适合场景 |
|------|--------|------|---------|
| **GLM-4-Air** | 128K | 32B 参数，比肩 GPT-4o | 通用编程、指令遵循 |
| **GLM-4-AirX** | 128K | Air 高速版（145 tokens/s） | 低延时、高并发 |
| **GLM-4.5-Air** | 128K | 1060B 总参 / 120B 激活 | 推理、编码、Agent 任务 |
| **GLM-4.6** | **200K** | Token 效率提升 30% | 长文本、多语言、办公 |
| **GLM-4.7** | **200K** | 三种可控思考模式，SWE-bench 73.8% | **Agentic Coding 专精** |
| **GLM-4-Plus** | 128K | 旗舰基座模型 | 高智能通用任务 |

### 👑 旗舰模型

| 模型 | 上下文 | 输出上限 | 价格 | 特点 |
|------|--------|---------|------|------|
| **GLM-5** | 200K | 128K | ¥6/24（输入/输出 百万tokens） | 对标 Claude Opus 4.5 |
| **GLM-5.1** | 200K | 128K | 提价 10% | **8 小时级长程 Agent 任务** |
| **GLM-5.1 高速版** | 200K | 128K | — | 输出速度 **400 tokens/s** |

### 🧠 推理 / 沉思模型

| 模型 | 特点 |
|------|------|
| **GLM-Z1 系列** | 推理专用模型（Z1-Air / Z1-AirX / Z1-Flash），擅长数学、代码、逻辑深度推理 |
| **GLM-Z1-Rumination** | **沉思模型**，对标 OpenAI Deep Research，多轮深度思考 + 搜索工具，适合复杂开放问题 |

> 📌 **记忆技巧**：
> - `Flash` = 快速免费版
> - `Air` = 轻量高性价比版
> - `AirX` = Air 的极速版
> - `Z1` = 推理（Reasoning）系列
> - `Plus` = 旗舰版
> - 数字越大版本越新（4.5 → 4.6 → 4.7 → 5 → 5.1）

对于本教程的学习，使用 **GLM-4-Flash（免费）** 或 **GLM-4.7-Flash（免费）** 就完全够用了。

---

## 🧪 第四步：测试你的 API Key

打开终端，用 curl 发一个测试请求：

```bash
curl -X POST "https://open.bigmodel.cn/api/paas/v4/chat/completions" \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer 你的API-Key粘贴到这里" \
  -d '{
    "model": "glm-4-flash",
    "messages": [
      {"role": "user", "content": "你好！请用一句话打个招呼。"}
    ],
    "temperature": 0.7,
    "max_tokens": 200
  }'
```

> ⚠️ 把 `你的API-Key粘贴到这里` 替换成你刚才复制的 Key
>
> 如果你使用的是 Coding Plan 的 API Key，请把 URL 中的 `paas` 改为 `coding/paas`

如果成功，你会看到类似这样的返回：

```json
{
  "choices": [
    {
      "message": {
        "role": "assistant",
        "content": "你好！很高兴见到你，有什么我可以帮你的吗？"
      },
      "finish_reason": "stop"
    }
  ],
  "usage": {
    "prompt_tokens": 10,
    "completion_tokens": 16,
    "total_tokens": 26
  }
}
```

看到回复内容就说明成功了！

### 多轮对话测试

```bash
curl -X POST "https://open.bigmodel.cn/api/paas/v4/chat/completions" \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer 你的API-Key粘贴到这里" \
  -d '{
    "model": "glm-4-flash",
    "messages": [
      {"role": "system", "content": "你是一个专业的编程助手。"},
      {"role": "user", "content": "什么是递归？"}
    ]
  }'
```

---

## 🔍 第五步：OpenAI 与智谱 GLM API 的差异

智谱 GLM 的 API **高度兼容 OpenAI 格式**，但也有一些独特之处：

| 对比项 | OpenAI | 智谱 GLM |
|--------|--------|----------|
| Endpoint | `/v1/chat/completions` | `/api/paas/v4/chat/completions` |
| API Key 格式 | `sk-...` | 32位十六进制.16位字母数字 |
| 认证方式 | `Authorization: Bearer <key>` | `Authorization: Bearer <key>` ✅ 相同 |
| 消息格式 | `messages=[{role, content}]` | 完全一致 ✅ |
| 模型命名 | `gpt-4o`, `gpt-4o-mini` | `glm-4-flash`, `glm-4.7`, `glm-5.1` |
| 免费额度 | 付费为主 | **GLM-4-Flash / 4.7-Flash 完全免费** |
| 特有功能 | 无思考模式 | 支持 `thinking` 思考模式（独有） |
| 上下文长度 | GPT-4o 128K | GLM-4.6/4.7 达 **200K** |

### 用 OpenAI SDK 调用智谱 GLM

只需改 **两行代码**：

```python
from openai import OpenAI

client = OpenAI(
    api_key="你的智谱API-Key",                        # 换成智谱的 Key
    base_url="https://open.bigmodel.cn/api/paas/v4"   # 换成智谱的地址（注意结尾无斜杠）
)

response = client.chat.completions.create(
    model="glm-4-flash",                              # 换成智谱的模型
    messages=[
        {"role": "user", "content": "你好"}
    ]
)

print(response.choices[0].message.content)
```

> 💡 智谱是目前唯一同时提供 **OpenAI 兼容**、**Anthropic 兼容**和 **GLM 原生 SDK** 三套 API 的国产厂商，集成非常灵活。只改 base_url 和 api_key 就能无缝切换。

---

## 🆘 常见问题

### Q: 智谱有哪些免费模型？

**GLM-4-Flash** 和 **GLM-4.7-Flash** 完全免费使用，不限调用次数。另外 **GLM-Z1-Flash** 推理模型也是免费的。对于学习和个人项目，免费模型已经非常够用。

### Q: 我是小白，应该选哪个模型？

选 **`glm-4-flash`** —— 完全免费，128K 上下文，功能齐全，入门学习足够了。想要更强能力可以升级到 `glm-4.7`（200K 上下文，Agentic Coding 专精）。

### Q: 新用户有免费额度吗？

智谱的 **GLM-4-Flash 系列本身就是永久免费**的。新注册用户可能还会有额外的体验额度用于调用付费模型，具体以控制台显示为准。

### Q: 智谱支持中文吗？

**非常支持，而且是主打优势。** 智谱 AI 是清华大学孵化的大模型公司，对中文的理解和生成能力处于国内顶尖水平，中文编程场景表现出色。

### Q: API 端点的 `/paas/` 和 `/coding/paas/` 有什么区别？

- **`/api/paas/v4/`**：通用 API 端点，使用按量付费的 API Key
- **`/api/coding/paas/v4/`**：Coding Plan（编程套餐）专用端点，使用套餐内的 API Key

选错了会鉴权失败，配置时请留意。

### Q: API Key 丢了怎么办？

无法找回。去控制台 → API Keys 页面，把旧的删掉，重新创建一个新的 Key 即可。

### Q: 智谱 GLM 的价格贵吗？

**非常便宜，且有免费模型。** 以 GLM-4-Flash 为例，完全免费。GLM-4-FlashX 仅 ¥0.10/百万 tokens，GLM-4-Plus 降价后也只要 ¥5/百万 tokens。价格公开透明，详见官方定价页：https://docs.bigmodel.cn/cn/guide/start/model-overview

---

## ✅ 检查清单

- [ ] 成功注册智谱 AI 账号（open.bigmodel.cn）
- [ ] 创建了一个 API Key 并保存好
- [ ] 用 curl 成功测试了 API Key
- [ ] 知道 GLM 系列核心模型的区别（Flash / Air / Z1 / Plus / 5.1）
- [ ] 能说出 OpenAI 和智谱 GLM API 的主要差异
- [ ] 知道如何用 OpenAI SDK 调用智谱 GLM（改 base_url + api_key）
- [ ] 知道通用端点和 Coding Plan 端点的区别

---

**上一篇**: [创建 OpenAI Codex API →](./05-codex-api-setup.md)
**下一篇**: [API Key 管理与安全 →](./07-api-key-management.md)

**最后更新**: 2026年6月12日
