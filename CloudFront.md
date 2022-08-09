<!--
 * @Author: Vincent Young
 * @Date: 2022-08-10 04:12:42
 * @LastEditors: Vincent Young
 * @LastEditTime: 2022-08-10 05:01:01
 * @FilePath: /XrayR-V2Board/CloudFront.md
 * @Telegram: https://t.me/missuo
 * 
 * Copyright © 2022 by Vincent, All Rights Reserved. 
-->
**_请不要在任何地方转载这篇教程_**

# 使用Amazon CDN (CloudFront) 加速你的节点

`CloudFront` 是 `AWS` 提供的 `CDN` 服务。但这并不是无限量免费的，具体的免费额度请查阅 `AWS` 官网的介绍，如产生大量费用，概不负责。使用 `CloudFront` 加速你的节点，可以让你的节点速度更快。原理是你的本地网络到你的节点IP之间的网络质量可能不是很好，但是使用了 `CloudFront` 后，可以保证的是 `CloudFront` 到你的节点源IP的质量一定是好的，你只需要找到你本地网络到 `CloudFront` 速度最快的 `自选IP`即可。

## 如何使用 `CloudFront`

1. 你应该使用 [XrayR-V2Board](https://github.com/missuo/XrayR-V2Board)正确安装 `XrayR`。请注意，必须选用 `WebSocket`。端口可以是常见的端口，例如80，8080，21，8443等等，不一定是80端口。无需开启TLS。

![2317c5710f133b74b0052](https://telegraph.eowo.us/file/2317c5710f133b74b0052.png)

2. 随意使用你的任何一个域名，并且解析到你的VPS的IP。原因是，当你使用 `CloudFront` 时，不可以填写源站IP，别问我为什么。。。

3. 注册 `AWS` 账号，这里不多赘述。打开 `CloudFront` 的管理页面，开始添加你的域名。将端口改成你刚才设定的节点的端口，如果提示端口不在范围内，请在 `V2Board` 管理后台更改为常见的端口。

![fe09b1fa5c2569a412080](https://telegraph.eowo.us/file/fe09b1fa5c2569a412080.png)

4. 关闭 `Compress objects automatically`，并且选择 `Legacy cache settings`，见下图，别的什么都不需要改。

![77a38b2d0489cc33f5184](https://telegraph.eowo.us/file/77a38b2d0489cc33f5184.png)

![accc59c4a1574df1a9288](https://telegraph.eowo.us/file/accc59c4a1574df1a9288.png)

5. 等待 `CDN` 部署完成，理论上速度非常快，大概1分钟左右 `Last modified` 就显示时间了，就说明部署完了。

6. 在 `V2Board` 添加一个全新的节点。这是最关键的一步，如果填错信息，你的 `CDN` 节点将无法访问。节点地址修改为 `CloudFront` 提供的域名，`连接端口` 修改为 **80**, 父节点选择你的原始没有CDN的节点。

![6235d8699ddfb2c92d073](https://telegraph.eowo.us/file/6235d8699ddfb2c92d073.png)

7. 到上一步完成，理论上你的节点已经成功使用 `CloudFront` CDN，并且已经可以开始正常使用了。如果你不需要自选IP，到这里就结束了。

8. 如果你想要获得到更快的速度，你需要使用 `自选IP`，而不是默认提供的域名。`自选IP` 的操作方式我会在下面说到。这里先讲拿到 `自选IP` 之后如何配置节点。你需要将你的节点地址改为 `自选IP`。

![9b137b2ed4c0af297722d](https://telegraph.eowo.us/file/9b137b2ed4c0af297722d.png)

9. 到上一步还不够，因为 `CloudFront` 的IP是很多人共用的，你只提供了IP地址和80端口，VPN客户端不知道你的源站地址是什么。所以最关键的一步，你需要配置 `WebSocket`，手动指定 `WebSocket` 的 `Headers` 的 `Host` 为 `CloudFront` 提供的域名。

~~~json
{
  "headers": {
    "Host": "xxxxx.cloudfront.net"
  }
}
~~~

![edc1389b6378a12270b2c](https://telegraph.eowo.us/file/edc1389b6378a12270b2c.png)

10. 到这里就结束了，你的节点可以正常使用，并且可以获得非常快的速度。并且我的方式，也保留了不使用 `CloudFront` 的原始节点，用户可以自行选择。

## 如何自选IP

1. 下载 [优选IP工具](https://github.com/XIU2/CloudflareSpeedTest/releases)。根据你的电脑自行选择对应版本。

2. 解压缩之后，仅保留 `CloudflareST` 和 `ip.txt` 两个文件，删除其余无用的文件。

3. 修改 `ip.txt` 文件为以下内容。

~~~
205.251.249.0/24
204.246.168.0/22
18.160.0.0/15
205.251.252.0/23
54.192.0.0/16
204.246.173.0/24
54.230.200.0/21
116.129.226.128/26
130.176.0.0/17
108.156.0.0/14
99.86.0.0/16
205.251.200.0/21
13.32.0.0/15
13.224.0.0/14
70.132.0.0/18
15.158.0.0/16
13.249.0.0/16
18.238.0.0/15
18.244.0.0/15
205.251.208.0/20
65.9.128.0/18
130.176.128.0/18
54.230.208.0/20
116.129.226.0/25
52.222.128.0/17
18.164.0.0/15
64.252.128.0/18
205.251.254.0/24
54.230.224.0/19
71.152.0.0/17
216.137.32.0/19
204.246.172.0/24
18.172.0.0/15
18.154.0.0/15
54.240.128.0/18
205.251.250.0/23
52.46.0.0/18
52.82.128.0/19
54.230.0.0/17
54.230.128.0/18
54.239.128.0/18
130.176.224.0/20
36.103.232.128/26
52.84.0.0/15
143.204.0.0/16
144.220.0.0/16
54.182.0.0/16
54.239.192.0/19
18.64.0.0/14
99.84.0.0/16
130.176.192.0/19
52.124.128.0/17
204.246.164.0/22
13.35.0.0/16
204.246.174.0/23
36.103.232.0/25
204.246.176.0/20
65.8.0.0/16
65.9.0.0/17
108.138.0.0/15
64.252.64.0/18
~~~

4. 在 `CloudFront` 添加一个新的 `域名`，用于测试速度。可以使用 `hnd-jp-ping.vultr.com` ，如图配置。同样关闭 `Compress objects automatically`，并且选择 `Legacy cache settings`，见下图，别的什么都不需要改。

![5b3bee4b4eef1b994547d](https://telegraph.eowo.us/file/5b3bee4b4eef1b994547d.png)

![77a38b2d0489cc33f5184](https://telegraph.eowo.us/file/77a38b2d0489cc33f5184.png)

![accc59c4a1574df1a9288](https://telegraph.eowo.us/file/accc59c4a1574df1a9288.png)

5. 你的 `测速URL` 为 `http://xxxxxx.cloudfront.net/vultr.com.100MB.bin`。请将 `xxxxxx.cloudfront.net` 替换为 `CloudFront` 提供的域名。

6. 运行 `CloudflareST`。设置测试延迟次数 `3`，指定URL为上面的地址。
~~~shell
./CloudflareST -t 3 -url http://xxxxxx.cloudfront.net/vultr.com.100MB.bin
~~~

7. 等待测试完成，会自动生成一个 `result.csv` 文件，找到最快的几个IP填入你的 `V2Board` 节点地址即可。

## 注意事项

- 无需指定 `WebSocket` 的 `Path`，如果你在别的教程看到设定了 `Path`，这与使用 `CDN` 没有任何影响。
- 请记住，使用 `CDN` 之后，你的连接端口一定是 `80`。
- 请确保原节点可以使用的情况下，再去配置 `CDN` 节点。
- 如何你有任何疑问，请带上问题截图联系 [Telegram](https://t.me/missuo)，我很乐意为你解答。