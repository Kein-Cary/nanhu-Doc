---
title: 不使用交大 VPN 登录南湖
parent: Examples
nav_order: 1
---

## 目的

在不连接交大 VPN 的情况下访问南湖服务器。首次配置仍需连接交大网络或交大 VPN。

> 请先确认服务器管理员允许使用远程隧道，并遵守南湖的访问与数据安全规定。隧道需要使用同一个 GitHub 或 Microsoft 账户在服务器端和客户端进行身份验证。

## 原理

通常，南湖服务器仅允许从交大网络或交大 VPN 访问。VS Code Tunnel 由南湖服务器主动连接到 VS Code 的中转服务，客户端再通过该服务连接南湖。

## 步骤

1. 安装并打开 [Visual Studio Code](https://code.visualstudio.com/)，然后安装微软官方的 **Remote Explorer** 和 **Remote - Tunnels** 扩展。
2. 连接交大 VPN，然后在 VS Code 中通过 SSH 首次登录南湖。请将 `<用户名>` 替换为你的南湖用户名：

   ```bash
   ssh <用户名>@111.186.40.90
   ```

3. 在南湖服务器上下载并解压 VS Code CLI：

   ```bash
   mkdir -p ~/vscode-cli
   cd ~/vscode-cli
   curl -L 'https://code.visualstudio.com/sha/download?build=stable&os=cli-alpine-x64' --output vscode_cli.tar.gz
   tar -xf vscode_cli.tar.gz
   ./code --version
   ```

   如果最后一条命令显示版本号，说明安装成功。

4. 将 Tunnel 安装为后台服务：

   ```bash
   ./code tunnel service install
   ```

   按终端提示完成身份验证。服务在服务器后台运行后，可以关闭当前远程连接。

5. 重新打开 VS Code，在 **Remote Explorer > Tunnels** 中确认 `nanhu` 正在运行。之后即可在不连接交大网络或 VPN 的情况下连接南湖服务器。

   ![VS Code Remote Explorer 中的 nanhu Tunnel 示例]({{ site.baseurl }}/_static/vscode_example.png)

更多信息及卸载方法请参阅 [VS Code Remote Tunnels 官方文档](https://code.visualstudio.com/docs/remote/tunnels)。
