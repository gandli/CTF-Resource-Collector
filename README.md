# CTF-Resource-Collector

本仓库使用 GitHub Actions 自动浅克隆（depth=1）CTF 相关的仓库资源，包括 writeups 和 wiki 资源，实现自动化收集和更新。

## 如何克隆本仓库

### 使用 Git 子模块（推荐）

```bash
# 克隆主仓库
git clone https://github.com/gandli/CTF-Resource-Collector.git
cd CTF-Resource-Collector

# 创建目录
mkdir -p writeups wiki

# 添加writeups资源作为子模块
git submodule add --depth=1 https://github.com/Jinmo/ctfs.git writeups/ctfs
git submodule add --depth=1 https://github.com/pwning/public-writeup.git writeups/public-writeup
git submodule add --depth=1 https://github.com/TryHackMyOffsecBox/Target-Machines-WriteUp.git writeups/Target-Machines-WriteUp
git submodule add --depth=1 https://github.com/Crypto-Cat/CTF.git writeups/CTF
git submodule add --depth=1 https://github.com/jon-brandy/hackthebox.git writeups/hackthebox
git submodule add --depth=1 https://github.com/ctf-wiki/ctf-challenges.git writeups/ctf-challenges
git submodule add --depth=1 https://github.com/b09780978/pwnable.kr-write-up.git writeups/pwnable.kr-write-up
git submodule add --depth=1 https://github.com/lifanxin/buuoj-challenges-pwn.git writeups/buuoj-challenges-pwn
git submodule add --depth=1 https://github.com/sajjadium/ctf-writeups.git writeups/ctf-writeups
git submodule add --depth=1 https://github.com/st424204/ctf_practice.git writeups/ctf_practice
git submodule add --depth=1 https://github.com/AravGarg/CTFarchives.git writeups/CTFarchives
git submodule add --depth=1 https://github.com/datajerk/ctf-write-ups.git writeups/ctf-write-ups
git submodule add --depth=1 https://github.com/JiaweiHawk/pwn.git writeups/pwn
git submodule add --depth=1 https://github.com/XDSEC/moeCTF_2021.git writeups/moeCTF_2021

# 添加wiki资源作为子模块
git submodule add --depth=1 https://github.com/ctf-wiki/ctf-wiki.git wiki/ctf-wiki
git submodule add --depth=1 https://github.com/Antel0p3/HITSZ-CTF-Wiki.git wiki/HITSZ-CTF-Wiki
git submodule add --depth=1 https://github.com/ReAbout/web-sec.git wiki/web-sec

# 初始化并更新所有子模块
git submodule update --init --recursive --depth=1
```

### Windows PowerShell 子模块版本

```powershell
# 克隆主仓库
git clone https://github.com/gandli/CTF-Resource-Collector.git
cd CTF-Resource-Collector

# 创建目录
New-Item -ItemType Directory -Force -Path writeups, wiki

# 添加writeups资源作为子模块
git submodule add --depth=1 https://github.com/Jinmo/ctfs.git writeups/ctfs
git submodule add --depth=1 https://github.com/pwning/public-writeup.git writeups/public-writeup
git submodule add --depth=1 https://github.com/TryHackMyOffsecBox/Target-Machines-WriteUp.git writeups/Target-Machines-WriteUp
git submodule add --depth=1 https://github.com/Crypto-Cat/CTF.git writeups/CTF
git submodule add --depth=1 https://github.com/jon-brandy/hackthebox.git writeups/hackthebox
git submodule add --depth=1 https://github.com/ctf-wiki/ctf-challenges.git writeups/ctf-challenges
git submodule add --depth=1 https://github.com/b09780978/pwnable.kr-write-up.git writeups/pwnable.kr-write-up
git submodule add --depth=1 https://github.com/lifanxin/buuoj-challenges-pwn.git writeups/buuoj-challenges-pwn
git submodule add --depth=1 https://github.com/sajjadium/ctf-writeups.git writeups/ctf-writeups
git submodule add --depth=1 https://github.com/st424204/ctf_practice.git writeups/ctf_practice
git submodule add --depth=1 https://github.com/AravGarg/CTFarchives.git writeups/CTFarchives
git submodule add --depth=1 https://github.com/datajerk/ctf-write-ups.git writeups/ctf-write-ups
git submodule add --depth=1 https://github.com/JiaweiHawk/pwn.git writeups/pwn
git submodule add --depth=1 https://github.com/XDSEC/moeCTF_2021.git writeups/moeCTF_2021

# 添加wiki资源作为子模块
git submodule add --depth=1 https://github.com/ctf-wiki/ctf-wiki.git wiki/ctf-wiki
git submodule add --depth=1 https://github.com/Antel0p3/HITSZ-CTF-Wiki.git wiki/HITSZ-CTF-Wiki
git submodule add --depth=1 https://github.com/ReAbout/web-sec.git wiki/web-sec

# 初始化并更新所有子模块
git submodule update --init --recursive --depth=1
```

### 子模块的优势

使用 Git 子模块有以下优势：

- 可以将每个 CTF 资源库作为独立的子模块管理
- 方便更新：只需运行 `git submodule update --remote` 即可更新所有子模块
- 可以选择性克隆特定的子模块
- 保持原始仓库的 Git 历史记录
- 可以轻松切换到特定的提交或分支

### 完整克隆（不使用子模块）

```bash
# 克隆仓库
git clone https://github.com/gandli/CTF-Resource-Collector.git
cd CTF-Resource-Collector

# 手动运行克隆脚本（可选）
mkdir -p writeups wiki
# 克隆 writeups 资源
cat README.md | grep -A 100 "1. Writeups" | grep -B 100 "2. Wiki" | grep "https://github.com" | while read -r repo; do
  if [ ! -z "$repo" ]; then
    repo_name=$(echo $repo | awk -F'/' '{print $NF}' | sed 's/.git$//')
    echo "Cloning $repo_name from $repo"
    git clone --depth=1 $repo writeups/$repo_name
  fi
done

# 克隆 wiki 资源
cat README.md | grep -A 100 "2. Wiki" | grep "https://github.com" | while read -r repo; do
  if [ ! -z "$repo" ]; then
    repo_name=$(echo $repo | awk -F'/' '{print $NF}' | sed 's/.git$//')
    echo "Cloning $repo_name from $repo"
    git clone --depth=1 $repo wiki/$repo_name
  fi
done
```

### 浅克隆（节省空间和时间）

```bash
# 浅克隆仓库
git clone --depth=1 https://github.com/gandli/CTF-Resource-Collector.git
cd CTF-Resource-Collector

# 后续步骤同上
```

### Windows PowerShell 用户

```powershell
# 克隆仓库
git clone https://github.com/gandli/CTF-Resource-Collector.git
cd CTF-Resource-Collector

# 手动运行克隆脚本（可选）
New-Item -ItemType Directory -Force -Path writeups, wiki

# 克隆 writeups 资源
$content = Get-Content README.md -Raw
$writeupSection = $content -split "## 2. Wiki" | Select-Object -First 1
$writeupUrls = $writeupSection | Select-String -Pattern "https://github.com.*\.git" -AllMatches | ForEach-Object { $_.Matches } | ForEach-Object { $_.Value }

foreach ($repo in $writeupUrls) {
    $repoName = $repo -split "/" | Select-Object -Last 1
    $repoName = $repoName -replace "\.git$", ""
    Write-Host "Cloning $repoName from $repo"
    git clone --depth=1 $repo writeups/$repoName
}

# 克隆 wiki 资源
$wikiSection = $content -split "## 2. Wiki" | Select-Object -Last 1
$wikiUrls = $wikiSection | Select-String -Pattern "https://github.com.*" -AllMatches | ForEach-Object { $_.Matches } | ForEach-Object { $_.Value }

foreach ($repo in $wikiUrls) {
    $repoName = $repo -split "/" | Select-Object -Last 1
    $repoName = $repoName -replace "\.git$", ""
    Write-Host "Cloning $repoName from $repo"
    git clone --depth=1 $repo wiki/$repoName
}
```

## 自动克隆

> **注意**：浅克隆（`--depth=1`）只获取最新的提交，大大减少下载时间和磁盘空间占用，非常适合这种资源收集仓库。

仓库配置了 GitHub Actions 工作流，会在以下情况自动运行：

- 推送到 main 或 master 分支时
- 创建 Pull Request 时
- 每周一自动运行
- 可手动触发

## 1. Writeups 资源

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
```

## 2. Wiki 资源

```
https://github.com/ctf-wiki/ctf-wiki
https://github.com/Antel0p3/HITSZ-CTF-Wiki/
https://github.com/ReAbout/web-sec
```
