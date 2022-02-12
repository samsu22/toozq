# toozq
支持多协议多用户的 xray 面板

# 功能介绍
- 系统状态监控
- 支持多用户多协议，网页可视化操作
- 支持的协议：vmess、vless、trojan、shadowsocks、dokodemo-door、socks、http
- 支持配置更多传输配置
- 流量统计，限制流量，限制到期时间
- 可自定义 xray 配置模板
- 支持 https 访问面板（自备域名 + ssl 证书）
- 更多高级配置项，详见面板

# 安装&升级
```
bash <(curl -Ls https://raw.githubusercontent.com/samsu22/toozq/master/install.sh)
```

## 手动安装&升级
1. 首先从 https://github.com/samsu22/toozq/releases 下载最新的压缩包，一般选择`amd64`架构
2. 然后将这个压缩包上传到服务器的`/root/`目录下，并使用`root`用户登录服务器

> 如果你的服务器 cpu 架构不是`amd64`，自行将命令中的`amd64`替换为其他架构

```
cd /root/
rm toozq/ /usr/local/toozq/ /usr/bin/toozq -rf
tar zxvf toozq-linux-amd64.tar.gz
chmod +x toozq/toozq toozq/bin/xray-linux-* toozq/toozq.sh
cp toozq/toozq.sh /usr/bin/toozq
cp -f toozq/toozq.service /etc/systemd/system/
mv toozq/ /usr/local/
systemctl daemon-reload
systemctl enable toozq
systemctl restart toozq
```

## 建议系统
- CentOS 7+
- Ubuntu 16+
- Debian 8+

# 常见问题

## 从 v2-ui 迁移
首先在安装了 v2-ui 的服务器上安装最新版 toozq，然后使用以下命令进行迁移，将迁移本机 v2-ui 的`所有 inbound 账号数据`至 toozq，`面板设置和用户名密码不会迁移`
> 迁移成功后请`关闭 v2-ui`并且`重启 toozq`，否则 v2-ui 的 inbound 会与 toozq 的 inbound 会产生`端口冲突`
```
toozq v2-ui
```

## Stargazers over time

[![Stargazers over time](https://starchart.cc/samsu22/toozq.svg)](https://starchart.cc/samsu22/toozq)
