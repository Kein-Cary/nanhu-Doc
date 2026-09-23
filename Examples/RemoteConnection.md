---
sort: 1
title: add files to the Nanhu-Doc groups
---

目的：实现可以不依赖交大VPN使用南湖服务器（但是第一次仍然需要借助交大VPN）
原理：正常情况下南湖服务器只允许交大网络或者交大VPN访问，但是使用vscode中的Tunnel可以绕开这个限制。因为Tunnel 是南湖服务器先主动连到外部中转服务（Vscode Tunnel），你再连这个中转服务。
步骤：
1.	安装并打开vscode安装微软官方Remote Explorer和Remote – Tunnels插件。
2.	使用交大VPN，在vscode中先用ssh登录南湖服务器：ssh 账户名@111.186.40.90
3.	下载并运行 VS Code Server，然后给这台服务器建立 tunnel：
```
mkdir -p ~/vscode-cli && cd ~/vscode-cli
curl -Lk 'https://code.visualstudio.com/sha/download?build=stable&os=cli-alpine-x64' --output vscode_cli.tar.gz
tar -xf vscode_cli.tar.gz
```
最后检查./code –version是否有显示版本号
4.	运行 Tunnel 变成后台服务：./code tunnel service install（只要保持在服务器后台运行即可，可以关闭当前远程连接）
5.	重新打开vscode检查在远程/Tunnels是否显示nanhu正在运行，如果是则可以在不依赖交大网络和VPN情况下点击图中的箭头即可连接南湖服务器

