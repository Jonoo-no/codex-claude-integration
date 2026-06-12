# 🔧 第一阶段：环境搭建完全指南

欢迎来到第一阶段！本章节会从零开始详细说明如何安装和配置 Git、Node.js 和 Python。

> ⏱️ **预计时间**：2-3 小时  
> 🎯 **目标**：成功安装并配置所有开发工具

---

## 📖 目录

1. [Git 安装与环境配置](#git-安装与环境配置)
2. [Node.js 下载与环境搭建](#nodejs-下载与环境搭建)
3. [Python 环境配置](#python-环境配置)
4. [验证安装](#验证安装)

---

# Git 安装与环境配置

## 🎯 什么是 Git？

Git 是一个版本控制系统，用来管理代码版本、跟踪文件变化。我们需要它来：
- 克隆项目代码
- 提交和推送代码更改
- 与其他开发者协作

## 📥 安装步骤

### Windows 系统

**第 1 步：下载 Git**

1. 访问 [Git 官方网站](https://git-scm.com/)
2. 点击 "Download for Windows"
3. 选择你的系统版本（32-bit 或 64-bit）
4. 文件会自动下载（通常是 `Git-2.x.x-64-bit.exe`）

**第 2 步：安装 Git**

1. 打开下载的 `.exe` 文件
2. 选择安装路径（默认通常是 `C:\Program Files\Git`）
3. 选择组件：
   - ✅ Git Bash Here
   - ✅ Git GUI Here
   - ✅ Associate .git* configuration files with the default text editor
4. 继续点击 "Next"，直到完成安装

**第 3 步：配置 Git**

1. 打开 **Git Bash**（右键点击文件夹 → "Git Bash Here"）
2. 输入以下命令配置用户名：

```bash
git config --global user.name "你的名字"
```

例如：
```bash
git config --global user.name "Jonoo-no"
```

3. 输入以下命令配置邮箱：

```bash
git config --global user.email "你的邮箱@example.com"
```

4. 验证配置：

```bash
git config --global --list
```



✅ **Windows 安装完成！**

---

### macOS 系统

**第 1 步：使用 Homebrew 安装（推荐）**

1. 首先确保你已安装 Homebrew，如果没有，打开终端输入：

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

2. 使用 Homebrew 安装 Git：

```bash
brew install git
```

**或者：第 1 步（替代方案）：直接下载安装**

1. 访问 [Git 官方网站](https://git-scm.com/)
2. 点击 "Download for macOS"
3. 根据你的 Mac 芯片选择：
   - Apple Silicon（M1/M2/M3）→ 选择 "Apple Silicon" 版本
   - Intel → 选择 "Intel x86_64" 版本
4. 下载并打开 `.dmg` 文件
5. 双击 `Git Installer` 按照提示安装

**第 2 步：配置 Git**

1. 打开终端（应用程序 → 实用工具 → 终端）
2. 输入以下命令配置用户名：

```bash
git config --global user.name "你的名字"
```

3. 输入以下命令配置邮箱：

```bash
git config --global user.email "你的邮箱@example.com"
```

4. 验证配置：

```bash
git config --global --list
```

✅ **macOS 安装完成！**

---

### Linux 系统

**第 1 步：使用包管理器安装**

**Ubuntu / Debian：**

```bash
sudo apt update
sudo apt install git
```

**CentOS / RHEL / Fedora：**

```bash
sudo yum install git
```

**Arch Linux：**

```bash
sudo pacman -S git
```

**第 2 步：配置 Git**

1. 打开终端
2. 输入以下命令配置用户名：

```bash
git config --global user.name "你的名字"
```

3. 输入以下命令配置邮箱：

```bash
git config --global user.email "你的邮箱@example.com"
```

4. 验证配置：

```bash
git config --global --list
```

✅ **Linux 安装完成！**

---

## ✅ Git 安装验证

无论你使用哪个系统，都可以运行以下命令验证安装：

```bash
git --version
```

你应该看到类似的输出：
```
git version 2.40.0
```

如果看到版本号，说明安装成功！

---

# Node.js 下载与环境搭建

## 🎯 什么是 Node.js？

Node.js 是一个 JavaScript 运行环境，让我们可以在服务器端运行 JavaScript 代码。我们需要它来：
- 运行 JavaScript 项目
- 使用 npm 包管理器
- 运行 CC-Switch 等工具

npm 是 Node.js 的包管理器，会自动随 Node.js 一起安装。

## 📥 安装步骤

### Windows 系统

**第 1 步：下载 Node.js**

1. 访问 [Node.js 官方网站](https://nodejs.org/)
2. 你会看到两个版本：
   - **LTS**（长期稳定版）→ 推荐选择
   - **Current**（最新版）
3. 点击 LTS 下载 Windows 版本（`.msi` 文件）

**第 2 步：安装 Node.js**

1. 打开下载的 `.msi` 文件
2. 点击 "Next" 接受许可条款
3. 选择安装路径（默认即可）：`C:\Program Files\nodejs`
4. 在 "Tools for Native Modules" 选项，选择 "Automatically install tools..."（可选但推荐）
5. 继续点击 "Next" 完成安装

**第 3 步：验证安装**

1. 打开 **命令提示符** 或 **PowerShell**
2. 输入以下命令检查 Node.js 版本：

```bash
node --version
```

你应该看到：
```
v18.17.0  (或更新版本)
```

3. 检查 npm 版本：

```bash
npm --version
```

你应该看到：
```
9.6.7  (或更新版本)
```

✅ **Windows 安装完成！**

---

### macOS 系统

**第 1 步（推荐）：使用 Homebrew 安装**

1. 打开终端
2. 输入以下命令：

```bash
brew install node
```

Homebrew 会自动安装 Node.js 和 npm

**第 1 步（替代方案）：直接下载安装**

1. 访问 [Node.js 官方网站](https://nodejs.org/)
2. 点击 LTS 版本下载 macOS 版本
3. 选择正确的架构：
   - Apple Silicon（M1/M2/M3）→ 选择 "ARM64" 版本
   - Intel → 选择 "x64" 版本
4. 下载 `.pkg` 文件
5. 打开文件按照提示安装

**第 2 步：验证安装**

1. 打开终端
2. 检查 Node.js 版本：

```bash
node --version
```

3. 检查 npm 版本：

```bash
npm --version
```

✅ **macOS 安装完成！**

---

### Linux 系统

**第 1 步：使用包管理器安装**

**Ubuntu / Debian：**

```bash
curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -
sudo apt-get install -y nodejs
```

**CentOS / RHEL / Fedora：**

```bash
curl -fsSL https://rpm.nodesource.com/setup_18.x | sudo bash -
sudo yum install nodejs
```

**Arch Linux：**

```bash
sudo pacman -S nodejs npm
```

**第 2 步：验证安装**

1. 打开终端
2. 检查 Node.js 版本：

```bash
node --version
```

3. 检查 npm 版本：

```bash
npm --version
```

✅ **Linux 安装完成！**

---

## 🔄 npm 基础配置

Node.js 安装完成后，建议进行一些 npm 配置：

### 更新 npm 到最新版本

```bash
npm install -g npm@latest
```

### 配置 npm 默认初始化值

```bash
npm config set init-author-name "你的名字"
npm config set init-author-email "你的邮箱@example.com"
npm config set init-author-url "https://github.com/yourusername"
```

### 验证 npm 配置

```bash
npm config list
```

---

## ✅ Node.js 安装验证

运行以下命令创建第一个 Node.js 项目：

```bash
# 创建一个新文件夹
mkdir my-first-node-project
cd my-first-node-project

# 初始化 npm 项目
npm init -y

# 运行一个简单的 JavaScript 代码
node -e "console.log('Hello from Node.js!')"
```

你应该看到输出：
```
Hello from Node.js!
```

---

# Python 环境配置

## 🎯 什么是 Python？

Python 是一种编程语言。虽然本教程主要使用 JavaScript/Node.js，但某些 AI 工具和库可能需要 Python。

## 📥 安装步骤

### Windows 系统

**第 1 步：下载 Python**

1. 访问 [Python 官方网站](https://www.python.org/)
2. 点击 "Downloads"
3. 下载 Python 3.11 或更新版本（`.exe` 文件）

**第 2 步：安装 Python**

1. 打开下载的 `.exe` 文件
2. ⚠️ **重要**：勾选 "Add Python to PATH"
3. 点击 "Install Now"
4. 安装完成后，点击 "Disable path length limit"（可选）

**第 3 步：验证安装**

1. 打开 **命令提示符** 或 **PowerShell**
2. 输入以下命令：

```bash
python --version
```

或者：

```bash
python3 --version
```

你应该看到：
```
Python 3.11.0  (或更新版本)
```

3. 验证 pip（Python 包管理器）：

```bash
pip --version
```

你应该看到：
```
pip 23.0.1 from C:\Users\...\Python311\lib\site-packages ...
```

✅ **Windows 安装完成！**

---

### macOS 系统

**第 1 步（推荐）：使用 Homebrew 安装**

1. 打开终端
2. 输入以下命令：

```bash
brew install python3
```

**第 1 步（替代方案）：直接下载安装**

1. 访问 [Python 官方网站](https://www.python.org/)
2. 点击 "Downloads"
3. 下载 macOS 版本
4. 打开 `.pkg` 文件按照提示安装

**第 2 步：验证安装**

1. 打开终端
2. 输入以下命令：

```bash
python3 --version
```

你应该看到：
```
Python 3.11.0  (或更新版本)
```

3. 验证 pip：

```bash
pip3 --version
```

✅ **macOS 安装完成！**

---

### Linux 系统

**第 1 步：使用包管理器安装**

**Ubuntu / Debian：**

```bash
sudo apt update
sudo apt install python3 python3-pip python3-venv
```

**CentOS / RHEL / Fedora：**

```bash
sudo yum install python3 python3-pip
```

**Arch Linux：**

```bash
sudo pacman -S python python-pip
```

**第 2 步：验证安装**

1. 打开终端
2. 输入以下命令：

```bash
python3 --version
```

3. 验证 pip：

```bash
pip3 --version
```

✅ **Linux 安装完成！**

---

## 🔄 Python 虚拟环境配置

虚拟环境用来隔离不同项目的依赖，强烈推荐使用。

### 创建虚拟环境

```bash
# 创建一个新文件夹
mkdir my-python-project
cd my-python-project

# 创建虚拟环境
python -m venv venv
# 或者
python3 -m venv venv
```

### 激活虚拟环境

**Windows：**

```bash
venv\Scripts\activate
```

**macOS / Linux：**

```bash
source venv/bin/activate
```

成功激活后，你会看到终端提示符前出现 `(venv)`

### 停用虚拟环境

```bash
deactivate
```

### 在虚拟环境中安装包

```bash
# 激活虚拟环境
source venv/bin/activate  # macOS/Linux
# 或
venv\Scripts\activate  # Windows

# 安装包
pip install package-name

# 查看已安装的包
pip list
```

---

# ✅ 验证安装

## 完整验证清单

运行以下所有命令，确保所有工具都正确安装：

```bash
# 1. 验证 Git
git --version
git config user.name
git config user.email

# 2. 验证 Node.js
node --version
npm --version

# 3. 验证 Python（可选）
python3 --version
pip3 --version
```

你应该看到类似的输出：

```
git version 2.40.0
Jonoo-no
1627854419@qq.com

v18.17.0
9.6.7

Python 3.11.0
pip 23.0.1 from /usr/local/lib/python3.11/site-packages/pip (python 3.11)
```

---

## 🎯 快速测试项目

### 1. 测试 Git

```bash
# 克隆一个示例项目
git clone https://github.com/Jonoo-no/codex-claude-integration.git
cd codex-claude-integration

# 查看项目状态
git status
```

### 2. 测试 Node.js

```bash
# 创建项目
mkdir test-node
cd test-node

# 初始化 npm
npm init -y

# 创建一个简单的 JavaScript 文件
echo "console.log('Node.js works!');" > test.js

# 运行文件
node test.js
```

### 3. 测试 Python

```bash
# 创建项目
mkdir test-python
cd test-python

# 创建虚拟环境
python3 -m venv venv

# 激活虚拟环境
source venv/bin/activate  # macOS/Linux
# 或
venv\Scripts\activate  # Windows

# 创建一个简单的 Python 文件
echo "print('Python works!')" > test.py

# 运行文件
python test.py
```

---

## 🆘 常见问题解决

### 问题 1：Git 命令找不到

**解决方案：**
- Windows：重新启动电脑或重启命令提示符
- macOS/Linux：重新启动终端

### 问题 2：npm install 速度很慢

**解决方案 1：更改 npm 源**

```bash
# 使用淘宝源（如果在中国）
npm config set registry https://registry.npmmirror.com

# 查看当前源
npm config get registry
```

**解决方案 2：使用 yarn（替代包管理器）**

```bash
npm install -g yarn
yarn install
```

### 问题 3：Python 命令不识别

**解决方案：**
- Windows：确保安装时勾选了 "Add Python to PATH"
- macOS/Linux：使用 `python3` 代替 `python`

### 问题 4：权限错误（Linux/macOS）

**解决方案：**

```bash
# 使用 sudo
sudo npm install -g package-name

# 或更改 npm 默认目录
mkdir ~/.npm-global
npm config set prefix '~/.npm-global'
```

### 问题 5：虚拟环境激活失败

**解决方案：**

```bash
# Windows 如果 activate 失败，尝试
python -m venv venv
.\venv\Scripts\python.exe -m pip install --upgrade pip

# macOS/Linux
python3 -m venv venv --upgrade-deps
source venv/bin/activate
```

---

## 🎉 环境搭建完成！

恭喜！你现在已经完成了第一阶段的所有配置。

### 下一步

现在你可以进入 **第二阶段：API 基础知识**

在下一阶段中，你将学到：
- 📚 API 基础概念
- 🔑 创建 OpenAI Codex API
- 🤖 创建 Anthropic Claude API
- 🔐 API 密钥管理与安全

👉 **[前往第二阶段 →](./phase-2-api.md)**

---

**上一步**: [返回主 README →](../../README.md)  
**下一步**: [第二阶段：API 基础知识 →](./phase-2-api.md)

**最后更新**: 2026年6月12日
