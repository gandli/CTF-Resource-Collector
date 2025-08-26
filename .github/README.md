# GitHub Actions 配置

## 自动克隆子模块

本目录包含GitHub Actions工作流配置，用于自动浅克隆（depth=1）CTF相关的仓库资源。

### 工作流文件

- `workflows/clone-submodules.yml`: 配置自动克隆CTF仓库的工作流

### 触发条件

工作流会在以下情况自动运行：
- 推送到main或master分支时
- 创建Pull Request时
- 每周一自动运行（使用cron表达式：`0 0 * * 1`）
- 可通过GitHub界面手动触发

### 工作流程

1. 检出当前仓库
2. 创建必要的目录结构（writeups和wiki）
3. 从README.md中提取仓库链接
4. 使用`git clone --depth=1`浅克隆所有仓库
   - writeups类仓库克隆到`writeups/`目录
   - wiki类仓库克隆到`wiki/`目录