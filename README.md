# CTF-Resource-Collector

本仓库使用 GitHub Actions 自动浅克隆（depth=1）CTF 相关的仓库资源，包括 writeups 和 wiki 资源，实现自动化收集和更新。

## 如何克隆本仓库

递归克隆（推荐）​

```
#使用 --recursive参数，一次性克隆主仓库及其所有子模块
git clone --recursive https://github.com/gandli/CTF-Resource-Collector.git
或者
# 浅克隆主仓库 + 子模块（仅最新提交）
git clone --recursive --depth 1 https://github.com/gandli/CTF-Resource-Collector.git
```

分步克隆

```
# 1. 克隆主仓库（不包含子模块）
git clone https://github.com/gandli/CTF-Resource-Collector.git
cd repo

# 2. 初始化并拉取所有子模块
git submodule init
git submodule update

# 或者只拉取特定子模块
git submodule update --init path/to/submodule
```

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
