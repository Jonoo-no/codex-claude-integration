# 09. CC-Switch 下载与安装

## 🎯 本课目标

从 GitHub Releases 页面下载 CC-Switch 并安装到你的电脑上。

> ⏱️ **预计时间**：15-20 分钟
> 💻 **类型**：动手操作

---

## 📥 第一步：打开 GitHub Releases 页面

1. 打开浏览器，访问：
   ```
   https://github.com/farion1231/cc-switch/releases
   ```

2. 在 Releases 页面，你会看到最新版本的 CC-Switch

3. 找到 **Assets**（资源文件）部分，根据你的操作系统选择下载：

| 操作系统 | 下载文件 |
|----------|---------|
| **Windows** | `CC-Switch-Setup-x.x.x.exe` 或 `CC-Switch-win-x64.exe` |
| **macOS（Intel）** | `CC-Switch-x.x.x.dmg` 或 `CC-Switch-darwin-x64.dmg` |
| **macOS（Apple Silicon M1/M2/M3）** | `CC-Switch-darwin-arm64.dmg` |

> 💡 如果你不确定自己的 Mac 是 Intel 还是 Apple Silicon，点击屏幕左上角  → "关于本机" → 看"处理器"或"芯片"一栏。

---

## 📦 第二步：安装

### Windows

1. 双击下载的 `.exe` 文件
2. 如果弹出"Windows 已保护你的电脑"提示，点击"更多信息"→"仍要运行"
3. 按照安装向导的提示操作：
   - 选择安装位置（默认即可）
   - 是否创建桌面快捷方式（建议勾选）
4. 点击"安装"，等待完成
5. 安装完成后，桌面上会出现 CC-Switch 的图标

### macOS

1. 双击下载的 `.dmg` 文件
2. 在弹出的窗口中，把 CC-Switch 图标**拖到**"Applications"（应用程序）文件夹
3. 等待复制完成
4. 如果第一次打开时提示"无法验证开发者"：
   - 打开"系统设置"→"隐私与安全性"
   - 找到 CC-Switch，点击"仍要打开"
   - 或者：按住 Control 键点击应用图标 → 选择"打开"

---

## 🚀 第三步：首次启动

1. 双击 CC-Switch 图标打开程序
2. 程序启动后，你会看到 CC-Switch 的主界面

> 📸 第一次启动可能需要几秒钟，耐心等待。

---

## 🆘 常见问题

### Q: GitHub Releases 页面打不开？

**解决方案**：
- 检查网络连接
- 尝试用手机热点
- 如果在学校或公司网络，可能需要 VPN

### Q: 下载速度很慢？

**解决方案**：
- 这是 GitHub 的服务器在国外，国内下载可能慢
- 耐心等待，文件通常不大
- 尝试换一个时间段下载

### Q: Windows 提示"无法验证发布者"？

**解决方案**：
- 这是正常现象，因为是个人开发者的开源软件
- 点击"更多信息"→"仍要运行"即可

### Q: macOS 提示"应用已损坏"？

**解决方案**：
- 这是 macOS 的安全机制
- 打开终端，输入：`sudo spctl --master-disable`
- 然后重新打开应用
- 安装完成后可以改回来：`sudo spctl --master-enable`

### Q: 安装后找不到图标？

**解决方案**：
- Windows：在开始菜单搜索"CC-Switch"
- macOS：在 Launchpad 或"应用程序"文件夹中查找

---

## ✅ 检查清单

- [ ] 成功打开 GitHub Releases 页面
- [ ] 根据操作系统下载了正确的安装包
- [ ] 完成了安装
- [ ] 成功打开了 CC-Switch，看到主界面

---

**上一篇**: [CC-Switch 工具介绍 →](./08-cc-switch-intro.md)
**下一篇**: [CC-Switch 界面与模型配置 →](./10-cc-switch-config.md)

**最后更新**: 2026年6月12日
