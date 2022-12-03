**English** | [中文](https://p3terx.com/archives/build-openwrt-with-github-actions.html)

# Actions-OpenWrt

[![LICENSE](https://img.shields.io/github/license/mashape/apistatus.svg?style=flat-square&label=LICENSE)](https://github.com/P3TERX/Actions-OpenWrt/blob/master/LICENSE)
![GitHub Stars](https://img.shields.io/github/stars/P3TERX/Actions-OpenWrt.svg?style=flat-square&label=Stars&logo=github)
![GitHub Forks](https://img.shields.io/github/forks/P3TERX/Actions-OpenWrt.svg?style=flat-square&label=Forks&logo=github)

A template for building OpenWrt with GitHub Actions

## Usage

- Click the [Use this template](https://github.com/P3TERX/Actions-OpenWrt/generate) button to create a new repository.
- Generate `.config` files using [Lean's OpenWrt](https://github.com/coolsnowwolf/lede) source code. ( You can change it through environment variables in the workflow file. )
- Push `.config` file to the GitHub repository.
- Select `Build OpenWrt` on the Actions page.
- Click the `Run workflow` button.
- When the build is complete, click the `Artifacts` button in the upper right corner of the Actions page to download the binaries.

## Tips

- It may take a long time to create a `.config` file and build the OpenWrt firmware. Thus, before create repository to build your own firmware, you may check out if others have already built it which meet your needs by simply [search `Actions-Openwrt` in GitHub](https://github.com/search?q=Actions-openwrt).
- Add some meta info of your built firmware (such as firmware architecture and installed packages) to your repository introduction, this will save others' time.

## Credits

- [Microsoft Azure](https://azure.microsoft.com)
- [GitHub Actions](https://github.com/features/actions)
- [OpenWrt](https://github.com/openwrt/openwrt)
- [Lean's OpenWrt](https://github.com/coolsnowwolf/lede)
- [tmate](https://github.com/tmate-io/tmate)
- [mxschmitt/action-tmate](https://github.com/mxschmitt/action-tmate)
- [csexton/debugger-action](https://github.com/csexton/debugger-action)
- [Cowtransfer](https://cowtransfer.com)
- [WeTransfer](https://wetransfer.com/)

说明
本项目旨在使用Github的Actions功能实现OpenWrt的云编译，根本上解决本地编译的网络、环境配置问题。 同时大家也能通过配置来增、减插件，打造属于自己的OpenWrt固件，拒绝各种广告固件。 项目基于Lean的LEDE进行编译。

自动化用的是P3TERX项目，项目地址：https://github.com/P3TERX/Actions-OpenWrt
编译的OpenWrt源项目是Lean的LEDE，项目地址：https://github.com/coolsnowwolf/lede

云编译项目主要需修改俩个地方：
diy-part1.sh里面添加feeds源，可以使用 https://github.com/kenzok8/openwrt-packages
另一个是.config文件，可以本地自己通过make menuconfig来保存生成或者直接用别人的。
Windows环境下可以简单使用WSL（Windows Subsystem for Linux）来搭建Ubuntu环境（建议20版本以上），此环境的作用主要是用来配置config文件，然后将文件上传到github。

默认登陆IP 192.168.1.1 密码 password

附录：本地编译常见问题
fatal: unable to access 'https://github.com/coolsnowwolf/lede/': gnutls_handshake() failed: The TLS connection was non-properly terminated.
解决方式：

git config --global http.sslVerify "false"

error: RPC failed; curl 18 transfer closed with outstanding read data remaining
解决方案：

git config --global http.postBuffer 524288000

Can't exec "make": No such file or directory at ./scripts/feeds line 22.
解决方案：

sudo apt-get install build-essential subversion libncurses5-dev zlib1g-dev sudo apt-get install gawk gcc-multilib flex git-core gettext libssl-dev

Build dependency: Please install 'unzip'
解决方案：

sudo apt install unzip

fatal: unable to access 'https://git.openwrt.org/feed/telephony.git/': server certificate verification failed. CAfile: /etc/ssl/certs/ca-certificates.crt CRLfile: none
解决方案：

export GIT_SSL_NO_VERIFY=1

或者

sudo apt-get update sudo apt-get install ca-certificates

:1:10: fatal error: libelf.h: No such file or directory
解决方案：

sudo apt-get install libelf-dev

fatal error: gelf.h: No such file or directory
解决方案：

sudo apt-get install libelf-dev
- [Mikubill/transfer](https://github.com/Mikubill/transfer)
- [softprops/action-gh-release](https://github.com/softprops/action-gh-release)
- [ActionsRML/delete-workflow-runs](https://github.com/ActionsRML/delete-workflow-runs)
- [dev-drprasad/delete-older-releases](https://github.com/dev-drprasad/delete-older-releases)
- [peter-evans/repository-dispatch](https://github.com/peter-evans/repository-dispatch)

## License

[MIT](https://github.com/P3TERX/Actions-OpenWrt/blob/main/LICENSE) © [**P3TERX**](https://p3terx.com)
