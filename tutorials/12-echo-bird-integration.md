# 12. Echo Bird 工具集成

## 🎯 本课目标

了解 Echo Bird、下载安装、并与 CC-Switch 对比。

> ⏱️ **预计时间**：20-30 分钟
> 📖 **类型**：动手操作

---

## 🤔 Echo Bird 是什么？

**Echo Bird** 和 CC-Switch 是同一类工具——都是桌面程序，通过 API Key 连接 AI 模型。

| 对比项 | CC-Switch | Echo Bird |
|--------|-----------|-----------|
| 开发者 | farion1231 | edison7009 |
| 仓库 | `farion1231/cc-switch` | `edison7009/EchoBird` |
| 使用方式 | 桌面程序，界面操作 | 桌面程序，界面操作 |
| 核心功能 | 通过 API Key 使用 Codex/Claude | 同 |
| 下载方式 | GitHub Releases | GitHub Releases |

> 💡 两个工具解决同一个问题。就像你有两部手机——都能打电话，但界面和操作略有不同。

---

## 📥 第一步：下载 Echo Bird

1. 打开浏览器，访问：
   ```
   https://github.com/edison7009/EchoBird/releases
   ```

2. 根据你的操作系统，下载对应的安装包：

| 操作系统 | 下载文件 |
|----------|---------|
| Windows | `EchoBird-Setup-x.x.x.exe` |
| macOS（Intel） | `EchoBird-x.x.x.dmg` |
| macOS（Apple Silicon） | `EchoBird-arm64.dmg` |

3. 下载完成后，安装方式与 CC-Switch 完全一样（参考教程 09）

---

## 🚀 第二步：启动与配置

1. 双击 Echo Bird 图标打开程序
2. 找到**模型管理**或**设置**界面
3. 添加模型并填入 API Key（和 CC-Switch 的操作流程一样）

Echo Bird 也支持同时添加多个模型——把你的 OpenAI Key 和 Anthropic Key 都填进去。

---

## 🔀 第三步：两个工具如何选择？

### 我应该用哪个？

| 你的情况 | 推荐 |
|----------|------|
| 第一次用这类工具 | **CC-Switch** 先入手 |
| 已经会了 CC-Switch | 试试 **Echo Bird**，看哪个更顺手 |
| 不确定 | 两个都下载，自己对比 |

### 两个可以同时装吗？

可以。它们是完全独立的程序，互不影响。就像你电脑上同时装了 QQ 和微信——都能聊天，但不冲突。

---

## 🆚 实用对比

| 使用维度 | CC-Switch | Echo Bird |
|----------|-----------|-----------|
| 上手难度 | 🟢 简单 | 🟢 简单 |
| 界面风格 | 取决于版本 | 取决于版本 |
| 稳定性 | 取决于版本 | 取决于版本 |

> 💡 由于两个工具都在持续更新，建议都试试，看哪个更符合你的使用习惯。

---

## 💡 为什么要了解两个工具？

1. **互为备份**：一个出问题，还能用一个
2. **功能互补**：不同版本可能有不同的特色功能
3. **多个选择**：你不被一个工具绑定

对于本教程的学习，**掌握 CC-Switch 就足够了**。Echo Bird 是加分项，你有时间再了解。

---

## 🆘 常见问题

### Q: Echo Bird 和 CC-Switch 能同时运行吗？

可以。它们是两个独立的程序，开着 CC-Switch 的同时也能开 Echo Bird。

### Q: 同一个 API Key 能用在两个工具上吗？

可以。API Key 是你的账户凭证，可以在多个地方使用——只要不超过 API 的频率限制。

### Q: Echo Bird 安装后打不开？

和 CC-Switch 遇到的问题一样。参考教程 09 中的"常见问题"部分。

---

## ✅ 检查清单

- [ ] 成功下载了 Echo Bird
- [ ] 安装了 Echo Bird 并能打开
- [ ] 在 Echo Bird 中添加了 API Key
- [ ] 理解了 CC-Switch 和 Echo Bird 的区别

---

**上一篇**: [CC-Switch 实战使用 →](./11-cc-switch-usage.md)
**下一篇**: [第四阶段：高级集成 →](../phase/phase-4-advanced.md)

**最后更新**: 2026年6月12日
