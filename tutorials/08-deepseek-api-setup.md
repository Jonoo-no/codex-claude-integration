# DeepSeek API Key 获取与安全指南

本教程说明如何在 DeepSeek 平台（https://platform.deepseek.com）上注册、实名认证并创建 API Key。重点是一步步的操作指令，以及如何一次性保存和安全管理 Key，以便后续在 CC-Switch / Echo Bird 等工具中直接使用。

> 说明：本页只包含**获取 Key 与保护安全**的操作步骤，不包含 DeepSeek 的 API 调用示例。

---

## 先决条件

- 能上网的浏览器
- 可接收验证邮件 / 可进行实名认证的证件信息

---

## 一、注册账号

1. 打开浏览器，访问：https://platform.deepseek.com
2. 点击页面上的 "Sign up" / "Create account"（或类似按钮）
3. 按提示填写邮箱、密码等基本信息，并提交
4. 登录邮箱，点击验证链接完成邮箱验证

备注：部分地区/账号可能需要额外的信息或邀请码，按页面提示完成。

---

## 二、实名认证（必须步骤）

1. 登录 DeepSeek 后，进入用户设置或账户页面（Account / Profile / Settings）
2. 找到实名认证（Real-name verification / Identity verification）入口
3. 按页面要求上传证件照片或填写身份信息（身份证、护照等）
4. 提交并等待审核（通常几分钟到一天不等）

⚠️ 实名认证通过后才能创建 API Key，请耐心等待审核结果并留意邮箱或平台通知。

---

## 三、创建 API Key（只会显示一次）

1. 在 DeepSeek 控制台中找到 **API Keys** 或 **Access Keys** 页面
2. 点击 **Create Key** / **Generate API Key** 或类似按钮
3. 为密钥填写可识别的名称（例如：`cc-switch-key-2026`）
4. 点击确认生成
5. **重要：页面会只显示一次完整的 API Key**，立即复制并妥善保存

建议的保存方式（任选其一）：
- 将 Key 粘贴到本地受保护的密码管理器（推荐，如 1Password、Bitwarden）
- 将 Key 写入本地 `.env` 文件（同时确保 `.env` 被列入 `.gitignore`）
- 临时保存到安全的笔记应用并随后删除（不推荐长期保存）

示例 Key（请勿实际使用）：
```
sk-deep-xxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

---

## 四、将 Key 写入 .env（项目开发时推荐）

在你的项目根目录：

1. 创建或打开 `.env`：
```bash
# 在项目根目录
nano .env
```

2. 在 `.env` 中添加（一行一个）：
```env
DEEPSEEK_API_KEY=sk-deep-xxxxxxxxxxxxxxxxxxxxxxxxxxxx
OPENAI_API_KEY=sk-proj-xxxxxxxxxxxxxxxx
ANTHROPIC_API_KEY=sk-ant-xxxxxxxxxxxxxx
```

3. 确保 `.gitignore` 中包含 `.env`：
```
# .gitignore
.env
.env.local
```

4. 在 Node.js 中加载（示例）：
```javascript
require('dotenv').config();
const deepseekKey = process.env.DEEPSEEK_API_KEY;
```

或在 Shell 临时设置环境变量（当前终端会话有效）：

**macOS / Linux**：
```bash
export DEEPSEEK_API_KEY="sk-deep-xxxxxxxxxxxxxxxxxxxxxxxxxxxx"
```

**Windows (PowerShell)**：
```powershell
$env:DEEPSEEK_API_KEY = "sk-deep-xxxxxxxxxxxxxxxxxxxxxxxxxxxx"
```

---

## 五、在 CC-Switch / Echo Bird 中使用 DeepSeek Key

- CC-Switch 与 Echo Bird 都可以直接使用 DeepSeek 的 API Key 作为后端模型的凭证（前提是这两个工具支持将 DeepSeek 当作后端）。
- 常见做法：将 Key 写入 CC-Switch/Echo Bird 的配置文件或通过环境变量传入。

示例：在 `cc-switch` 的 `config.json`（伪示例）中：
```json
{
  "backends": {
    "deepseek": {
      "type": "deepseek",
      "api_key": "sk-deep-xxxxxxxxxxxxxxxxxxxxxxxxxxxx",
      "endpoint": "https://api.deepseek.com/v1"
    }
  }
}
```

示例：使用环境变量（更安全）
```bash
export DEEPSEEK_API_KEY="sk-deep-xxxxxxxxxxxxxxxxxxxxxxxxxxxx"
# 启动 cc-switch（示例）
npm run start -- --config ./config.json
```

注意：请参阅 CC-Switch / Echo Bird 的官方文档以确认配置字段名和支持的后端类型。你提供的仓库地址：
- https://github.com/farion1231/cc-switch
- https://github.com/edison7009/EchoBird

这些项目通常支持在配置文件或环境变量中注入第三方 API Key。

---

## 六、Key 的安全与应急处理

### 安全实践（必做）
1. 从不在公共仓库提交 Key（包括 Fork）
2. 使用 `.env` + `.gitignore` 保护开发环境 Key
3. 在生产环境使用托管的 Secrets 服务（例如：GitHub Secrets、AWS Secrets Manager、HashiCorp Vault）
4. 最小化权限：如果 DeepSeek 支持多权限 Key，请只授予所需权限
5. 为不同项目和环境使用不同 Key（开发/测试/生产分离）
6. 定期轮换 Key（例如每 3 个月）

### 如果 Key 泄露（应急步骤）
1. 立即登录 DeepSeek 控制台，撤销/删除该 Key
2. 在你的应用和服务中替换为新 Key（更新 `.env`、CI/CD Secrets 等）
3. 检查平台使用情况（是否有异常调用或高额消费）
4. 如果有异常消费，联系 DeepSeek 支持并说明情况
5. 如果 Key 被提交到 Git 历史，使用 BFG 或 git-filter-repo 从历史中清除，并强制推送（谨慎）

示例：用 BFG 删除 `.env` 并清理历史（仅在必要时）
```bash
# 安装 bfg（参考 BFG 官方文档）
# 删除包含敏感字符串的文件
bfg --delete-files .env

# 清理后强制推送
git reflog expire --expire=now --all
git gc --prune=now --aggressive
git push --force
```

---

## 七、验证与检查清单

- [ ] 已完成 DeepSeek 的注册并通过实名认证
- [ ] 已生成并复制 DeepSeek API Key（注意一次性显示）
- [ ] 已将 Key 存入安全的密码管理器或 `.env` 并加入 `.gitignore`
- [ ] 已在本地测试通过（环境变量或 `.env` 可读）
- [ ] 已在 CC-Switch / Echo Bird 配置或环境中注入 Key（按需）
- [ ] 已记录 Key 旋转和撤销流程

---

## 八、额外建议

- 在团队中使用集中化秘密管理系统，不要让每个人单独保管生产 Key
- 在 CI/CD 中通过加密 Secrets 注入运行环境，而不是在构建时写入文件
- 若 DeepSeek 提供 Webhook、Usage 或 Billing 报表，定期检查以发现异常

---

**本教程只包含获取 Key 与安全管理步骤**，如需我接着为你编写：
- CC-Switch / Echo Bird 的配置示例（针对 DeepSeek 后端）
- 使用 cc-switch 将 OpenAI 请求转发到 DeepSeek 的实战示例

请告诉我你想先写哪一篇，我会继续实现。
