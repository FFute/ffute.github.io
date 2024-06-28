今天装好FydeOS开始使用，体验还是很丝滑的。

不过发现一个问题，使用FydeOS时，默认情况下，Widevine是关闭状态。

这就导致打开Spotify时，提示无法播放受版权保护的内容，无法使用。

[此处应有图片]

‍

不过解决的办法很简单。

[FydeOS-开启Widevine](https://fydeos.com/docs/knowledge-base/recipes/widevine/)

> Widevine 是由谷歌发起的数字版权管理（DRM）技术，旨在为需要保障版权内容的网站提供安全的解密后播放办法。该技术用来保护数字流媒体内容免受盗版的威胁，确保只有授权用户可以在网上访问高清电影、电视节目和音乐等内容。简言之，Widevine 是一种「安全措施」，让内容提供商在为用户提供无缝的观看体验的同时，保护其应有的知识产权。现在全球主要的内容服务商都有在使用这项技术，包括 Google Play、YouTube、Netflix、Hulu、Amazon、Spotify 等。
>
> 若你想要在 FydeOS 使用有内容保护的流媒体服务，你需要在设置中开启 Widevine 功能：
>
> ### v17 及后续版本
>
> 1. 从你偏好的地方或供应商获取适应相应架构的必要的 Windevine 文件。如果找不到，可以尝试下面的文件：
>
>     * [X64](https://github.com/Twinaxeatk/WidevineCdm/releases/download/R114/WidevineCdm_X64.tar.gz)
>     * [ARM64](https://github.com/Twinaxeatk/WidevineCdm/releases/download/R114/WidevineCdm_ARM64.tar.gz)
> 2. 解压缩文件（如果需要），并获取 `libwidevinecdm.so`​ 文件。
> 3. 导航至 "设置" -> "FydeOS 设置"，找到并选择 "启用 Widevine" 选项，并选择 `libwidevinecdm.so`​ 文件。
> 4. 重启设备。

<!-- ##{"timestamp":1700275800}## -->