# clash-subconfig

ACL4SSR 订阅转换模板的自定义副本，仅增加 Google Play / Microsoft Store 下载所需的规则前置。

在原有模板基础上，把以下域名在 `Ⓜ️ 微软服务` 规则之前显式指向代理组 `🚀 节点选择`：

- `delivery.mp.microsoft.com`（Store/DO 安装包 CDN）
- `mp.microsoft.com`
- `s-microsoft.com`
- `cdn.winget.microsoft.com`
- `live.com`

原因：这些域名的下载 CDN 在国内容易被解析到第三方节点（腾讯/百度云/Akamai 国内节点），
其返回的 TLS 证书与主机名不匹配，客户端握手直接失败。走代理可规避。

| 文件 | 对应上游模板 |
|---|---|
| msfix_AdblockPlus.ini | ACL4SSR_Online_AdblockPlus.ini |
| msfix_Full_MultiMode.ini | ACL4SSR_Online_Full_MultiMode.ini |
| msfix_Mini_AdblockPlus.ini | ACL4SSR_Online_Mini_AdblockPlus.ini |
