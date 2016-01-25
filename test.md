| 主机记录 | 记录类型 | 记录值                                | 权重 | MX优先级 | TTL | 用途备注       |
| :------: | :------: | ------------------------------------- | :--: | :------: | :-: | -------------- |
| *        | MX       | mx.sendcloud.org.                     | -    | 5        | 600 | SendCloud验证  |
| *        | TXT      | sendcloud-site-verification=XXXXX     | -    | -        | 600 | SendCloud验证  |
| *        | TXT      | v=spf1 include:spf.sendcloud.org ~all | -    | -        | 600 | SendCloud验证  |
| 1hquulsug0 | CNAME  | zz.baidu.com.                         | 0    | -        | 10  | Baidu推广验证  |
| @        | A        | `SLB主机IP地址`                       | 0    | -        | 10  | 主域名         |
| @        | MX       | mxbiz1.qq.com                         | -    | 5        | 600 | 腾讯企业邮箱   |
| @        | MX       | mxbiz2.qq.com                         | -    | 10       | 600 | 腾讯企业邮箱   |
| @        | NS       | ns4.dnsv3.com.                        | -    | -        | 86400 | DNSPod系统   |
| @        | NS       | ns3.dnsv3.com.                        | -    | -        | 86400 | DNSPod系统   |
| alicdn   | CNAME    | alicdn.yangcong345.com.w.kunlungr.com. | 0   | -        | 10  | 阿里云CDN用    |
| android  | CNAME    | yangcong345.com.                      | 0    | -        | 600 | 安卓客户端用   |
| bd       | A        | `Backoor的IP地址`                     | 0    | -        | 10  | 方便访问后门   |
| cb       | CNAME    | yangcong345.com.                      | 0    | -      | 10 | 课程后台（暂无用）|
| design   | A        | 139.129.128.228                       | 0    | -        | 10  | `设计`         |
| hackthon | A        | 112.124.41.118                        | 0    | -        | 600 | 微信公众号     |
| ios      | CNAME    | yangcong345.com.                      | 0    | -        | 600 | 苹果客户端用   |
| m        | A        | 120.26.100.245                        | 10   | -        | 10  | 手机端         |
| mail._domainkey.info | TXT | k=rsa;p=MXXXXXXXXXXXXXX        | -    | -        | 600 | SendCloud验证  |
