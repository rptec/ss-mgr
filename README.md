[shadowsocks-manager是一个非常帅气的ss多用户管理程序，搭建起来稍微有点麻烦，因此写了本一键脚本。

---

# 效果

![](http://cdn.mmmxcc.cn/blog/20170513/135344468.png)
![](http://cdn.mmmxcc.cn/blog/20170513/135349156.png)
![](http://cdn.mmmxcc.cn/blog/20170513/135357497.png)
![](http://cdn.mmmxcc.cn/blog/20170513/140400232.png)

github： https://github.com/mmmwhy/ss-mgr

示例网站：https://wall.gyteng.com

# 特点
- 非常帅气，各种图表一上，是不是很牛逼的感觉。
- 支持支付宝付款对账，站长们多出来的vps可以不用再继续吃灰了。

# 要求
centos7 X64，在腾讯云，digitialocean,interserver,ethernetservers通过测试。
其他版本还没有测试，理论上可用。
# 安装脚本

## 安装ss-mgr
本脚本包括主控端和节点端，安装时，自动添加本vps作为一个节点。
```
wget -N --no-check-certificate https://raw.githubusercontent.com/rptec/ss-mgr/master/sm.sh && chmod +x sm.sh && bash sm.sh
```
坐等就可以了，没有什么需要做的东西。
打开ip地址，就可以看到ss-mgr了。

## 增加节点
本脚本为：已有**vps安装好主控端**，添加新节点时，在**新节点**使用的脚本。
```
wget -N --no-check-certificate https://raw.githubusercontent.com/rptec/ss-mgr/master/sm_node.sh && chmod +x sm_node.sh && bash sm_node.sh
```

- 输入密码
![](http://cdn.mmmxcc.cn/blog/20170514/135830856.png)
- 前端页面填入，刚才的密码，选择加密方式。
![](http://cdn.mmmxcc.cn/blog/20170514/140131877.png)

# 备注
- 注册的第一个用户就是管理员.
- 注册第二个账号，可以看到自己的剩余时间，一般来说是8个小时。可以点击续费，选择任意一个额度，支付后，可以看到时间会增长。
- 默认使用hotmail邮箱，因为邮箱在国外，所以如果服务器在国内的话，可能会timeout。
- 某些系统内核版本过老，因此可能会出现如下症状，按回车就可以了。
![](http://cdn.mmmxcc.cn/blog/20170513/135239354.png)
- 被墙掉的资源都换成国内的了。

鉴于很多小鸡可能带不动docker，因此这里使用传统方式安装，速度会慢一些。
其中，三条重要命令开启是通过`screen`完成的。
```
screen -dmS ss-manager ss-manager -m aes-256-cfb -u --manager-address 127.0.0.1:4000
cd /root/shadowsocks-manager/
screen -dmS ss node server.js -c /root/.ssmgr/ss.yml
screen -dmS webgui node server.js -c /root/.ssmgr/webgui.yml
```
---
因为本工具较难配置，因此如果有问题的话，可以通过tg联系我。https://t.me/feiyangss

---
参考以下链接：
https://code.momok.xyz/server/deploy-ss-manager.html
https://github.com/shadowsocks/shadowsocks-manager
