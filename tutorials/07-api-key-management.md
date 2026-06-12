# 07. API Key 管理与安全

## 🎯 本课目标

学会安全地管理 API Key，避免泄露，避免不必要的花费。

> ⏱️ **预计时间**：20-30 分钟
> 🛡️ **核心原则**：像保护银行卡密码一样保护 API Key

---

## 🚨 为什么 API Key 安全很重要？

先看一个真实案例（简化版）：

> 小明把 API Key 写在了代码里，然后上传到了 GitHub。第二天醒来发现，他的 OpenAI 账户被扣了 **$5000**——因为有人用爬虫扫到了他的 Key，拿去挖矿了。

这不是危言耸听，这种事情**每天都在发生**。GitHub 上有专门的机器人 24 小时扫描公开仓库里的 API Key。

记住三条铁律：

1. **API Key 绝不写死在代码里**
2. **API Key 绝不上传到 GitHub**
3. **万一泄露，第一时间去平台撤销**

---

## 📂 方法一：用 .env 文件（推荐）

### 什么是 .env？

`.env` 是一个存放敏感配置的文件，你的程序从这里读取 API Key，但它**不会被上传到 GitHub**。

### 创建 .env 文件

在你的项目根目录下创建一个 `.env` 文件：

```bash
# 在项目目录下
touch .env
```

然后用记事本（或任何编辑器）打开它，写入：

```
# OpenAI
OPENAI_API_KEY=sk-proj-你的key粘贴到这里

# Anthropic
ANTHROPIC_API_KEY=sk-ant-api03-你的key粘贴到这里
```

### 创建 .gitignore 文件

`.gitignore` 文件告诉 Git："这些文件不要上传"。这是保护 Key 最关键的一步！

在项目根目录创建 `.gitignore`，写入：

```
# 环境变量文件 - 包含 API Key
.env

# Node.js
node_modules/

# Python
venv/
__pycache__/
```

这样 `.env` 文件就永远不会被上传到 GitHub 了。

---

## 📂 方法二：用系统环境变量

### Windows

打开 PowerShell：

```powershell
# 设置环境变量（当前会话）
$env:OPENAI_API_KEY="sk-proj-你的key"
$env:ANTHROPIC_API_KEY="sk-ant-api03-你的key"

# 永久设置（所有新会话都生效）
[System.Environment]::SetEnvironmentVariable('OPENAI_API_KEY', 'sk-proj-你的key', 'User')
[System.Environment]::SetEnvironmentVariable('ANTHROPIC_API_KEY', 'sk-ant-api03-你的key', 'User')
```

设置后需要重新打开终端才能生效。

### macOS / Linux

打开终端：

```bash
# 编辑配置文件
nano ~/.zshrc    # 如果用 zsh（macOS 默认）
# 或
nano ~/.bashrc   # 如果用 bash（Linux 默认）
```

在文件末尾添加：

```bash
export OPENAI_API_KEY="sk-proj-你的key"
export ANTHROPIC_API_KEY="sk-ant-api03-你的key"
```

保存后执行：

```bash
source ~/.zshrc   # 让配置立即生效
```

---

## 💡 最佳实践总结

### ✅ 要做的

| 做法 | 为什么 |
|------|--------|
| Key 存在 `.env` 文件里 | 代码和配置分离 |
| `.env` 加入 `.gitignore` | 不会被上传到 GitHub |
| 创建一个 `.env.example` | 告诉别人需要哪些配置项 |
| 定期检查 API 用量 | 发现异常及时处理 |

### ❌ 不要做的

| 做法 | 后果 |
|------|------|
| Key 写在代码里 | 一上传就泄露 |
| 截图包含 Key 发社交媒体 | 被公开传播 |
| 在公共电脑上存 Key | 下一个人能看到 |
| 把 Key 发给陌生人 | 对方能花你的钱 |

---

## 📄 .env.example 文件

`.env.example` 是一个模板文件——它**不包含真实的 Key**，只是告诉别人你的项目需要哪些配置。这个文件可以上传到 GitHub。

创建 `.env.example`：

```
# OpenAI API Key - 在这里注册: https://platform.openai.com/api-keys
OPENAI_API_KEY=your-openai-api-key-here

# Anthropic API Key - 在这里注册: https://console.anthropic.com/settings/keys
ANTHROPIC_API_KEY=your-anthropic-api-key-here
```

当别人克隆你的项目时，他们看到这个文件就知道："哦，我需要配置这两个 Key"，然后把 `.env.example` 复制为 `.env`，填入自己的 Key。

---

## 🔍 如何检查用量

### OpenAI

1. 访问 https://platform.openai.com/usage
2. 可以按日期查看每天的调用次数和花费
3. 设置 **Usage limits**（用量上限），防止意外超支：
   - 左侧菜单 → Billing → Usage limits
   - 设置每月硬上限（Hard limit）和软上限（Soft limit）

### Anthropic

1. 访问 https://console.anthropic.com/settings/usage
2. 查看当前用量和剩余额度
3. 同样可以设置用量上限

---

## 🚨 紧急情况：Key 泄露了怎么办？

1. **立刻撤销 Key**
   - OpenAI：https://platform.openai.com/api-keys → 找到该 Key → 点击 🗑️ 或 Revoke
   - Anthropic：https://console.anthropic.com/settings/keys → 找到该 Key → 删除

2. **创建一个新的 Key**

3. **检查用量记录**——看看有没有异常消费

4. **如果造成了财务损失**——联系平台客服说明情况

---

## 🧪 动手练习

来，实际做一遍：

1. 在你的项目目录下创建 `.env` 文件
2. 把两个 Key 写进去
3. 创建 `.gitignore` 文件
4. 创建 `.env.example` 模板文件
5. 运行 `git status`，确认 `.env` 不在待上传列表中

```bash
# 你的目录结构应该像这样：
your-project/
├── .env          ← 包含真实 Key，被 gitignore 了
├── .env.example  ← 模板文件，可以上传
├── .gitignore    ← 告诉 Git 忽略哪些文件
└── README.md
```

---

## ✅ 检查清单

- [ ] 创建了 `.env` 文件并写入了 API Key
- [ ] 创建了 `.gitignore` 并加入了 `.env`
- [ ] 创建了 `.env.example` 模板文件
- [ ] 知道 Key 泄露后该怎么处理
- [ ] 在 OpenAI 和 Anthropic 上查看了用量页面

---

**上一篇**: [创建 Anthropic Claude API →](./06-claude-api-setup.md)
**下一篇**: [第三阶段：模型转接工具 →](./phase/phase-3-tools.md)

**最后更新**: 2026年6月12日
