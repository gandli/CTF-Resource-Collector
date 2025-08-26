# CTF-Resource-Collector [![Collect CTF Resources](https://github.com/gandli/CTF-Resource-Collector/actions/workflows/clone-submodules.yml/badge.svg)](https://github.com/gandli/CTF-Resource-Collector/actions/workflows/clone-submodules.yml)

本仓库使用 GitHub Actions 自动浅克隆（depth=1）CTF 相关的仓库资源，包括 writeups 和 wiki 资源，实现自动化收集和更新。

## 如何克隆本仓库

### 递归克隆（推荐）

```bash
# 使用 --recursive参数，一次性克隆主仓库及其所有子模块
git clone --recursive https://github.com/gandli/CTF-Resource-Collector.git

# 或者浅克隆主仓库 + 子模块（仅最新提交）
git clone --recursive --depth 1 https://github.com/gandli/CTF-Resource-Collector.git
```

### 分步克隆

```bash
# 1. 克隆主仓库（不包含子模块）
git clone https://github.com/gandli/CTF-Resource-Collector.git
cd CTF-Resource-Collector

# 2. 初始化并拉取所有子模块
git submodule init
git submodule update

# 或者只拉取特定子模块
git submodule update --init path/to/submodule
```

### 子模块管理

```bash
# 更新所有子模块到最新版本
git submodule update --remote

# 更新特定子模块
git submodule update --remote writeups/ctfs

# 查看子模块状态
git submodule status
```

### 子模块的优势

使用 Git 子模块有以下优势：

- 可以将每个 CTF 资源库作为独立的子模块管理
- 方便更新：只需运行 `git submodule update --remote` 即可更新所有子模块
- 可以选择性克隆特定的子模块，节省空间和时间
- 保持原始仓库的 Git 历史记录
- 可以轻松切换到特定的提交或分支

> 注意：仓库链接支持多种格式，如 `https://github.com/username/repo.git`、`https://github.com/username/repo` 或 `git@github.com:username/repo.git`（SSH 格式），系统会自动处理。

## 1. Wiki 资源

```
https://github.com/ctf-wiki/ctf-wiki.git
https://github.com/Antel0p3/HITSZ-CTF-Wiki.git
https://github.com/ReAbout/web-sec.git
https://github.com/ProbiusOfficial/Hello-CTF.git
```

## 2. Writeups 资源

```
https://github.com/Jinmo/ctfs.git
https://github.com/pwning/public-writeup.git
https://github.com/TryHackMyOffsecBox/Target-Machines-WriteUp.git
https://github.com/Crypto-Cat/CTF.git
https://github.com/jon-brandy/hackthebox.git
https://github.com/ctf-wiki/ctf-challenges.git
https://github.com/b09780978/pwnable.kr-write-up.git
https://github.com/lifanxin/buuoj-challenges-pwn.git
https://github.com/sajjadium/ctf-writeups.git
https://github.com/st424204/ctf_practice.git
https://github.com/AravGarg/CTFarchives.git
https://github.com/datajerk/ctf-write-ups.git
https://github.com/JiaweiHawk/pwn.git
https://github.com/XDSEC/moeCTF_2021.git
https://github.com/Ignitetechnologies/HackTheBox-CTF-Writeups.git
https://github.com/susers/Writeups.git
https://github.com/bl4de/ctf.git
https://github.com/testert1ng/hacker101-ctf.git
https://github.com/balsn/ctf_writeup.git
https://github.com/shiltemann/CTF-writeups-public.git
https://github.com/USTC-Hackergame/hackergame2020-writeups.git
https://github.com/USTC-Hackergame/hackergame2021-writeups.git
https://github.com/USTC-Hackergame/hackergame2022-writeups.git
https://github.com/USTC-Hackergame/hackergame2023-writeups.git
https://github.com/USTC-Hackergame/hackergame2024-writeups.git
https://github.com/sixstars/ctf.git
https://github.com/hongriSec/CTF-Training.git
https://github.com/david942j/ctf-writeups.git
```

## 3. Tools 工具

```
https://github.com/Puliczek/awesome-mcp-security.git
```
