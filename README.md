# Clash and Dashboard
- 这是一个基于[Dreamacro/clash-dashboard](https://github.com/Dreamacro/clash-dashboard)修改的仓库
- 项目用于将Dashboard管理页面直接打包进clash的docker镜像中，**实现一个容器同时启动Clash和Dashboard**
- 修改了后台接口部分代码，使后台只会连接到同一docker容器中clash的9090端口，不再需要配置即可直接管理。
- 当然，因为去除了后台接口配置功能，所以此页面只能一对一了。

## 打包
```sh
npm install -g pnpm
pnpm i
pnpm build
docker build -f ./build/Dockerfile -t clash-and-dashboard:latest .
```

## 启动
```sh
docker run -d \
  --name clash \
  -v clash.yaml:/root/.config/clash/config.yaml \
  -p 8080:8080 -p 7890:7890 \
  -e SERVER_PORT=8080
  clash-and-dashboard:latest
```

- 8080为管理界面端口
- 7890为http端口
- 7891为socks端口
- 注意勾选允许局域网连接

## LICENSE
MIT License
