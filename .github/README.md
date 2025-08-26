# CTF-Resource-Collector GitHub Actions 配置

## 自动资源收集

本目录包含GitHub Actions工作流配置，用于自动将CTF相关的仓库资源作为Git子模块添加，实现资源的自动化收集和更新。

### 工作流文件

- `workflows/clone-submodules.yml`: 配置自动添加CTF仓库作为子模块的工作流

### 触发条件

工作流会在以下情况自动运行：
- 推送到main或master分支时
- 创建Pull Request时
- 每周一自动运行（使用cron表达式：`0 0 * * 1`）
- 可通过GitHub界面手动触发

### 工作流程

1. 检出当前仓库（配置了写入权限）
2. 配置Git用户信息
3. 创建必要的目录结构（writeups和wiki）
4. 从README.md中提取仓库链接
5. 使用`git submodule add --depth=1`将仓库添加为子模块
   - writeups类仓库添加到`writeups/`目录
   - wiki类仓库添加到`wiki/`目录
6. 初始化并更新所有子模块
7. 提交并推送子模块更改（如有）