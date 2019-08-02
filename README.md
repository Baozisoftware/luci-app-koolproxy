## luci-app-koolproxy modified
基于

[openwrt-develop/luci-app-koolproxy](https://github.com/openwrt-develop/luci-app-koolproxy)

整合了

[user1121114685/koolproxyR](https://github.com/user1121114685/koolproxyR)

的规则.

增加了内置规则和订阅规则一起更新

**增加IPv6支持(基于透明代理一刀切)**

**如果有可以去除副作用的方法,请提PR.**

```
ip6tables -t nat -I PREROUTING -p tcp -j REDIRECT --to-ports 3000
#已知副作用:
#一刀切劫持内网所以设备的IPv6 TCP流量.
#无法使用IPv6建立主动传入连接.
#如果未安装证书,打开启用HTTPS的网站会报错.
```

**NOTE:**

如果出现国外流量无法去广告(IPv4),请修改所使用代理的防火墙规则,必须让KP的规则在代理规则之上,检测命令:

``` bash
iptables -t nat -L PREROUTING
```

观察**KOOLPROXY**规则是否在所使用的代理的规则之上.

### 内置规则列表
[kp.dat](https://raw.githubusercontent.com/user1121114685/koolproxyR_rule_list/master/kp.dat)

[easylistchina](https://raw.githubusercontent.com/user1121114685/koolproxyR/master/koolproxyR/koolproxyR/data/rules/easylistchina.txt)

[yhosts](https://raw.githubusercontent.com/user1121114685/koolproxyR/master/koolproxyR/koolproxyR/data/rules/yhosts.txt)

[fanboy](https://raw.githubusercontent.com/user1121114685/koolproxyR/master/koolproxyR/koolproxyR/data/rules/fanboy-annoyance.txt)

### 订阅规则列表
[kpr_our_rule.txt](https://raw.githubusercontent.com/user1121114685/koolproxyR_rule_list/master/kpr_our_rule.txt)
