<p align="center"><img src="assets/covers/18-internal-chat.jpg" alt="局域网聊天 项目封面" width="100%"></p>

<h1 align="center">internal-chat · 发个东西</h1>

<p align="center">WebRTC 点对点的局域网聊天与文件传输，无需登录</p>

<p align="center">
  <a href="LICENSE">MIT 许可</a>
</p>

## 简介

浏览器打开就能用：文字和文件走 WebRTC 直连，服务器只负责把两个端点连起来，不接触传输内容。适合局域网内部互发文件、临时沟通。

## 功能

- **P2P 聊天**：基于 WebRTC DataChannel 的即时消息
- **文件传输**：拖拽发送，8 KB 分块 + 缺失重传，进度与速度可见
- **房间密码**：可创建加密房间，MD5 校验
- **昵称持久化**：写入 Cookie，下次打开还在
- **零安装**：浏览器即用，手机端也适配
- **连接恢复**：断线后自动重建 WebRTC 连接
- **小细节**：自动识别消息里的 URL 并转为可点链接，消息可一键复制

## 技术栈

WebRTC（DataChannel）｜ WebSocket（`ws`）信令 ｜ Node.js 16+ ｜ STUN / TURN 可自定义

## 部署

```bash
git clone https://github.com/aiyangdie/internal-chat.git
cd internal-chat
cd server
npm install
npm start            # 默认 8081，可用 npm run start 8082 指定端口
```

前端：把 `www/index.js` 第一行的 `wsUrl` 改成你的信令地址，再把 `www/` 交给 Nginx 做静态托管（HTTPS 与反代参考 `nginxvhost.conf`）。

## 项目结构

```
server/        信令服务（index.js、data.js、房间密码配置）
www/           前端（index.html、index.js、xchatuser.js、style.css）
nginxvhost.conf  Nginx 反代示例
```

## 免责声明

仅用于学习交流，请勿用于非法用途。

## 许可证

[MIT](LICENSE)
