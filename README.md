<!--
 * @Author: Vincent Young
 * @Date: 2022-07-26 02:19:56
 * @LastEditors: Vincent Young
 * @LastEditTime: 2022-10-07 05:55:53
 * @FilePath: /XrayR-V2Board/README.md
 * @Telegram: https://t.me/missuo
 * 
 * Copyright © 2022 by Vincent, All Rights Reserved. 
-->
English | [简体中文](https://github.com/missuo/XrayR-V2Board/blob/main/README_CN.md)

[Speed up your nodes with Amazon CDN (CloudFront)](https://github.com/missuo/XrayR-V2Board/blob/main/CloudFront.md)

## Description
1. Thanks to `XrayR` all authors for their contributions
2. Thanks to `XrayR-release` for the one-click script
3. This script is based on `XrayR-release`.
4. Only For `V2Board`.
5. Only For `Shadowsocks` `V2Ray-TCP` `V2Ray-WebSocket`.
6. This repository uses the latest version of `XrayR` by default

## Update
### Oct 7, 2022
- Switch to the latest official version.
### May 19, 2022
- Remove the autonomy to choose whether to enable `AEAD` encryption and force `AEAD` to be enabled
### April 27, 2022
- Author delete library, this script enable backup solution, not affected
- My [XrayR backup](https://github.com/missuo/XrayR)
### April 13, 2022
- Added `ARM64` support (e.g. Oracle ARM can be installed perfectly)
### February 28, 2022
- Modified `AEAD` encryption default selection (on by default if not entered)
### February 2, 2022
- Option to turn off `AEAD` encryption (on by default in official script, off by default in this script)
### December 15, 2021
- Optionally `V2ray`, `Shadowsocks`, `Trojan` (official script default V2ray, this script default V2ray)
### May 31, 2021
- Complete the script

## Original project
[XrayR-project/XrayR](https://github.com/XrayR-project/XrayR)

[XrayR-project/XrayR-release](https://github.com/XrayR-project/XrayR-release)

## Features
1. No need to configure panel URL and TOKEN each time (permanent once)
2. No need to change the node ID in the configuration file

## Guide
1. Fork this repository and modify the `config.yml` file, only the following two lines need to be modified.
```shell
ApiHost: "YOUR_PANEL_URL" # Modify here
ApiKey: "YOUR_TOKEN" # Modify here
```
2. Modify line 213 of the `install.sh` file to change the username `missuo` to your own GitHub username.
```
wget https://cdn.jsdelivr.net/gh/missuo/XrayR-V2Board/config.yml -O /etc/XrayR/config.yml
```
3. Change the username `missuo` in the link below to your own GitHub username to complete the configuration of the one-click install script command.
### Install Command
```
bash <(curl -Ls https://cdn.jsdelivr.net/gh/missuo/XrayR-V2Board/install.sh)
```
4. Complete the basic node information on the `V2Board` panel.
![Screenshot](https://files.xiami.com/cpp/07d8ec1a38a5462c3afbfac41413b8af/1622434730321.png)
5. Record your node ID.
6. Execute the above one-click install command on your VPS, it will install fully automatically and you will be prompted to enter your node ID.

## Caution
Since your repository may be public after you Fork this repository. Modifying the configuration file directly may expose your panel's key information. We recommend downloading `config.yml` and uploading it to your own server after modifying the information. And fill in the `install.sh` with your own config file download link. Finally, upload `install.sh` to your own server to generate your own one-click installation command.

[![Star History Chart](https://api.star-history.com/svg?repos=missuo/XrayR-V2Board&type=Date)](https://star-history.com/#fanux/missuo/XrayR-V2Board)
