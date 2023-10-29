# 在Milkv-duo上访问互联网

### 在开发板上：
#### 配置默认路由（ip：电脑端的地址，如192.168.42.254）
```bash
ip r add default via ip
```

#### 配置域名解析
```bash
 echo 'nameserver 8.8.8.8' >> /etc/resolv.conf
```

### 在电脑上：
#### 开启流量转发
```bash
sysctl net.ipv4.ip_forward
```

#### 配置iptables规则（outgoing_if：出口的网络设备，通过ip addr或ifconfig查询，如：wlp4s0）
```bash
iptables -P FORWARD ACCEPT
iptables -t nat -A POSTROUTING -o outgoing_if -j MASQUERADE
```

---

至此开发板已经可以访问互联网，可以通过`ping www.baidu.com`来测试。



