<!--
 * @Author: Vincent Young
 * @Date: 2022-07-26 02:18:54
 * @LastEditors: Vincent Young
 * @LastEditTime: 2022-08-10 05:00:32
 * @FilePath: /XrayR-V2Board/README_CN.md
 * @Telegram: https://t.me/missuo
 * 
 * Copyright © 2022 by Vincent, All Rights Reserved. 
-->
[English](https://github.com/missuo/XrayR-V2Board/blob/main/README.md) | 简体中文

[使用Amazon CDN (CloudFront) 加速你的节点](https://github.com/missuo/XrayR-V2Board/blob/main/CloudFront.md)

![muyI2Z](https://s3.missuo.me/images/muyI2Z.jpg)

## 说明
1. 感谢 `XrayR` 所有作者的贡献
2. 感谢 `XrayR-release` 提供的一键脚本
3. 本脚本是基于 `XrayR-release` 修改的
4. 适用于 `V2Board`
5. 本仓库默认使用最新版 `XrayR` 

## 更新
### 2022年5月19日
- 移除自主选择是否开启 `AEAD` 加密，强制开启 `AEAD`

### 2022年4月27日
- 作者删库，本脚本启用备份方案，不受影响 
- 我的 [XrayR备份](https://github.com/missuo/XrayR)

### 2022年4月13日
- 增加了 `ARM64` 的支持（例如Oracle ARM可以完美安装）

### 2022年2月28日
- 修改`AEAD`加密默认选择（不输入情况下默认开启）

### 2022年2月2日
- 可选择关闭`AEAD`加密(官方脚本默认开启，本脚本默认关闭)

### 2021年12月15日
- 可选择`V2ray`、`Shadowsocks`、`Trojan`(官方脚本默认V2ray，本脚本默认V2ray)

### 2021年5月31日
- 完成脚本

## 原项目
[XrayR-project/XrayR](https://github.com/XrayR-project/XrayR)

[XrayR-project/XrayR-release](https://github.com/XrayR-project/XrayR-release)

## 功能
1. 无需每次配置面板URL和TOKEN（一次永久生效）
2. 无需在配置文件中修改节点ID

## 使用指南
1. Fork本仓库，修改 `config.yml` 文件，仅需修改下面两行。
```shell
ApiHost: "YOUR_PANEL_URL" # 修改这里
ApiKey: "YOUR_TOKEN" # 修改这里
```


2. 修改 `install.sh` 文件的203行，将用户名 `missuo` 修改为你自己的GitHub用户名。
```
wget https://cdn.jsdelivr.net/gh/missuo/XrayR-V2Board/config.yml -O /etc/XrayR/config.yml
```

3. 修改下面链接的用户名 `missuo` 为你自己的GitHub用户名，完成配置一键安装脚本命令。
### x86_64
```
bash <(curl -Ls https://cdn.jsdelivr.net/gh/missuo/XrayR-V2Board/install.sh)
```
### ARM_64
```
bash <(curl -Ls https://cdn.jsdelivr.net/gh/missuo/XrayR-V2Board/install-arm.sh)
```

4. 在 `V2Board` 面板上完成基本节点信息的填写。
![截图](https://files.xiami.com/cpp/07d8ec1a38a5462c3afbfac41413b8af/1622434730321.png)

5. 记录一下你的节点ID。

6. 在VPS上执行上面的一键安装命令，会全自动安装，会提示你输入节点ID。

## 注意事项
由于你Fork本仓库之后，你的仓库可能会是公开的。直接修改配置文件可能会暴露你的面板关键信息。建议下载 `config.yml` ，修改完信息后，上传到你自己的服务器。并在 `install.sh` 中填写你自己的配置文件下载链接。最后上传 `install.sh` 到你自己的服务器，生成自己的一键安装命令。

[![Star History Chart](https://api.star-history.com/svg?repos=missuo/XrayR-V2Board&type=Date)](https://star-history.com/#fanux/missuo/XrayR-V2Board)
