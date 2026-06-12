# 17. 错误处理与故障排查

## 🎯 本课目标

在使用 CC-Switch / Echo Bird 时遇到问题，能快速定位并解决。

> ⏱️ **预计时间**：20-30 分钟
> 🔧 **类型**：参考手册，遇到问题时回来查

---

## 🚨 常见错误速查

### CC-Switch 软件相关

| 症状 | 可能原因 | 怎么解决 |
|------|---------|---------|
| 软件打不开 | 安装不完整 | 卸载后重新下载安装 |
| 软件闪退 | 版本不兼容 | 去 GitHub Releases 下载其他版本试试 |
| 界面卡死 | 内存不足 | 关掉其他不用的程序 |
| 添加模型后没反应 | 可能需要重启 | 关掉 CC-Switch 重新打开 |

### API Key 相关

| 症状 | 可能原因 | 怎么解决 |
|------|---------|---------|
| 连接失败 / 发不了消息 | Key 填错了 | 去 API Key 复制框重新粘贴，注意不要有空格 |
| 返回 "Invalid API Key" | Key 过期或被撤销 | 去 OpenAI/Anthropic 平台查看 Key 状态 |
| 返回 "Insufficient quota" | 没钱了 | 额度用完了，去平台充值 |
| 返回 "Rate limit exceeded" | 调太快了 | 等一分钟再试 |
| Key 是对的但连不上 | 网络问题 | 检查能不能访问 api.openai.com |

### 网络相关

| 症状 | 可能原因 | 怎么解决 |
|------|---------|---------|
| 一直转圈没回复 | 网络不通 | 检查 Wi-Fi，试试开网页 |
| 回复特别慢 | 网络不稳定 | 等一会儿，或者换个网络 |
| 间歇性连不上 | API 服务波动 | 正常现象，等几分钟再试 |
| 在国内连不上 OpenAI | 网络限制 | 需要使用合适的网络环境 |

---

## 🔍 通用排查步骤

遇到问题按顺序检查：

```
1. 重启 CC-Switch
   ↓ 不行？继续
2. 检查 API Key
   ↓ 去平台确认 Key 有效、有额度
3. 检查网络
   ↓ 能正常上网吗？能访问 api.openai.com 吗？
4. 重启电脑
   ↓ 很多问题重启就解决了
5. 重新安装 CC-Switch
   ↓ 去 GitHub Releases 下载最新版
6. 换 Echo Bird 试试
   ↓ 排除是不是软件本身的问题
7. 求助
   ↓ 带着错误截图去 GitHub Issues 提问
```

> 💡 80% 的问题出在前三步：重启、Key、网络。

---

## 📋 错误信息翻译（英文不好也能看懂）

| 英文提示 | 白话意思 |
|----------|---------|
| `Invalid API key` | "Key 填错了" |
| `Rate limit exceeded` | "你问太快了，慢一点" |
| `Insufficient quota` | "没钱了，去充值" |
| `Connection refused` | "连不上，检查网络" |
| `Model not found` | "没这个模型，名字写错了吧" |
| `Connection timed out` | "超时了，网络太慢" |
| `Authentication failed` | "认证失败，Key 不对" |

---

## 🛠️ 具体问题处理

### 问题：CC-Switch 添加模型后无法使用

1. 确认 API Key 完整粘贴（开头 `sk-` 部分没丢）
2. 确认 Key 来源正确（OpenAI Key 配 OpenAI 模型，Anthropic Key 配 Anthropic 模型）
3. 删除这个模型，重新添加
4. 重启 CC-Switch

### 问题：回复一半就断了

这是正常现象，AI 偶尔会生成到一半中断。刷新对话重新问一次即可。

### 问题：CC-Switch 和 Echo Bird 同时开，有一个连不上

- 两个工具共用同一个网络环境
- 如果只有一个连不上，可能是那个工具的配置问题
- 单独排查连不上的那个

### 问题：担心 Key 泄露

1. 立刻去平台撤销旧 Key
2. 创建新 Key
3. 在 CC-Switch 中删除旧模型，重新添加

---

## 📞 去哪求助？

| 问题类型 | 去哪问 |
|----------|--------|
| CC-Switch 软件 bug | https://github.com/farion1231/cc-switch/issues |
| Echo Bird 软件 bug | https://github.com/edison7009/EchoBird/issues |
| OpenAI API 问题 | https://platform.openai.com 帮助中心 |
| Anthropic API 问题 | https://console.anthropic.com 帮助中心 |

> 💡 提问时带上截图和具体错误信息，会更快得到回复。

---

## ✅ 检查清单

- [ ] 知道了"重启 → 查 Key → 查网络"三步排查法
- [ ] 能看懂常见英文错误提示
- [ ] 知道 Key 泄露后该怎么处理
- [ ] 知道去哪提交软件 bug

---

**上一篇**: [性能优化与成本控制 →](./16-performance-optimization.md)
**下一篇**: [第五阶段：项目案例 →](../phase/phase-5-cases.md)

**最后更新**: 2026年6月12日
