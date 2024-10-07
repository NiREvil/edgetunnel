# Cloudflare Worker 2 Vless 和 Sub

![rainbow](https://github.com/NiREvil/vless/assets/126243832/1aca7f5d-6495-44b7-aced-072bae52f256)

🇮🇷[波斯语](README.fa.md)

🇹🇷[土耳其](README.tr.md)

🇬🇧[英语](README.MD)

🇨🇳[中国人](README.zh-CN.md)

这是一个基于 Cloudflare Worker 平台的脚本。在原版本的基础上修改为显示VLESS配置信息并转换为订阅内容。使用此脚本，您可以轻松地将VLESS配置信息转换为使用在线配置的Clash或Singbox等工具。

-   [基本部署视频教程](https://www.youtube.com/watch?v=LeT4jQUh8ok)
-   [快速部署视频教程](https://www.youtube.com/watch?v=59THrmJhmAw)**最好推荐！！！**
-   [使用透视的高级教程](https://www.youtube.com/watch?v=s91zjpw3-P8)

[Telegram 交流群](https://t.me/CMLiussss)

## 风险提示

-   通过向订阅服务提交错误的节点配置来避免泄漏节点配置信息。
-   或者，您可以选择自行部署[WorkerVless2sub订阅生成服务](https://github.com/cmliu/WorkerVless2sub)，这样您就可以利用订阅生成器。

![rainbow](https://github.com/NiREvil/vless/assets/126243832/1aca7f5d-6495-44b7-aced-072bae52f256)

## 工人调配方法

[视频教程](https://www.youtube.com/watch?v=LeT4jQUh8ok&t=83s)

1.  部署 Cloudflare Worker：
    -   在 Cloudflare Worker 控制台中创建一个新 Worker。
    -   将要[工人.js](https://github.com/cmliu/edgetunnel/blob/main/_worker.js)将内容粘贴到 Worker 编辑器中。
    -   换乘11号线`userID`修改为你自己的**通用唯一识别码**。

2.  访问订阅内容：
    -   使用权`https://[YOUR-WORKERS-URL]/[UUID]`订阅内容可用。
    -   例如，您的订阅链接将是：`https://vless.google.workers.dev/90cd4a77-141a-43c9-991b-08263cfe9c10`这是您的通用自适应订阅地址。
    -   Base64订阅格式：`https://vless.google.workers.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?sub`适用于PassWall、SSR+等。
    -   冲突订阅格式`https://vless.google.workers.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?clash`适用于OpenClash等
    -   单盒订阅格式`https://vless.google.workers.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?sb`适用于singbox等

3.  将自定义域绑定到工作人员：
    -   在工人控制台中`trigger`选项卡，单击下面`Add a custom domain`。
    -   填写您已转入CloudFlare域名解析服务的二级域名，例如：`vless.google.com`点击后`Add a custom domain`，只需等待证书生效即可。
    -   **如果你是新手，现在就可以直接起飞，不用再看了！ ！ ！**

<details>
<summary><code><strong>「I'm really, really not a newbie! I want to try some tricks! I want to start playing with advanced techniques! 」</strong></code></summary>

4.  用你自己的`Preferred domain name`/`BestIP`订阅：
    -   如果您想使用自己喜欢的域名或者自己喜欢的IP，可以参考[WorkerVless2sub GitHub 存储库](https://github.com/cmliu/WorkerVless2sub)按照 中的部署说明自行构建。
    -   打开[工人.js](https://github.com/cmliu/edgetunnel/blob/main/_worker.js)文件，在第 16 行找到`sub`变量并将其修改为您部署的订阅生成器的地址。例如`let sub = 'sub.cmliussss.workers.dev';`，注意不要包含协议信息和https等符号。
    -   请注意，如果您使用自己的订阅地址，则订阅生成器的`sub`域名和`[YOUR-WORKER-URL]`域名不能属于同一个顶级域名，否则会出现异常。你可以`sub`该变量被分配了分配给workers.dev 的域名。

</details>

![rainbow](https://github.com/NiREvil/vless/assets/126243832/1aca7f5d-6495-44b7-aced-072bae52f256)

## 页面上传部署方法**最好推荐！！！**

[视频教程](https://www.youtube.com/watch?v=59THrmJhmAw)

1.  部署 Cloudflare 页面：
    -   下载[worker.zip](https://raw.githubusercontent.com/NiREvil/edgetunnel/main/worker.zip)文件并点击星标！！！
    -   在 Cloudflare Pages 控制台中选择`Upload assets`最后，为您的项目命名并单击`Create a project`，然后上传下载的[worker.zip](https://raw.githubusercontent.com/NiREvil/edgetunnel/main/worker.zip)单击文件后`Deployment Site`.
    -   部署完成后，点击`Continue processing site`之后，选择`set up`>`Environment variables`>**制作**定义生产变量 >`Add variables`,填写变量名**通用唯一识别码**，值为你的UUID，然后点击`keep`就是这样。
    -   返回`Deploy`选项卡，单击右下角`Create a New Deployment`然后重新上传[worker.zip](https://raw.githubusercontent.com/cmliu/edgetunnel/main/worker.zip)单击文件后`Save and deploy`就是这样。

2.  访问订阅内容：
    -   使用权`https://[YOUR-PAGES-URL]/[YOUR-UUID]`订阅内容可用。
    -   例如，您的订阅链接将是：`https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10`这是您的通用自适应订阅地址。
    -   Base64订阅格式：`https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?sub`适用于PassWall、SSR+等。
    -   冲突订阅格式：`https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?clash`适用于OpenClash等
    -   单盒订阅格式`https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?sb`适用于singbox等

<details>
<summary><code><strong>「I have my own domain name! I want to bind my own domain name! I have mastered domain name resolution! 」</strong></code></summary>
   
3. Bind a CNAME custom domain to Pages: [Video Tutorial](https://www.youtube.com/watch?v=LeT4jQUh8ok&t=851s)
   - In the Pages console `Custom domains` tab, click below `Set up a custom domain` 。
   - Fill in your custom subdomain name, be careful not to use your root domain name, for example：
     The domain name you are assigned is `fuck.cloudns.biz` ，Add a custom field to fill in `lizi.fuck.cloudns.biz` You can；
   - According to Cloudflare's requirements, your domain name DNS service provider will be returned, and the custom domain will be added `lizi` CNAME record for `edgetunnel.pages.dev` Then click on `Activate Domain` You can。
   - **If you are new, then your pages binding `Custom domains` After that, you can take off directly without looking down.！！！**

</details>
<details>
<summary><code><strong>「I'm really not a newbie! I want to play tricks! I want to open up high-end gameplay！ 」</strong></code></summary>
   
4. Use your own `Preferred domain name`/`BestIP` Subscriptions：
   - If you want to use your own preferred domain name or your own preferred IP, you can refer to [WorkerVless2sub GitHub storehouse](https://github.com/cmliu/WorkerVless2sub) Build it yourself using the deployment instructions in 。
   - In the Pages console `set up` tab, select `Environment variables` > `Production` > `Editing variables` > `Add variables`；
   - The variable name is set to `SUB`，The corresponding value is the address of the subscription generator you deployed. 。For Example: `sub.cmliussss.workers.dev`，Then click **Save**。
   - Then in the Pages console `Deploy` tab, select `All deployments` > `The latest deployment is the rightmost ...` > `Retry Deployment`，You can。
   - Note that if you use your own subscription address, ask the subscription generator `SUB` domain name and  `[YOUR-PAGES-URL]` Domain names of different 一个 Top level domain，Otherwise an exception will occur。You can `SUB` assign the domain name assigned to Pages.dev to the variable.
</details>

![rainbow](https://github.com/NiREvil/vless/assets/126243832/1aca7f5d-6495-44b7-aced-072bae52f256)

## Pages GitHub 部署方法。

[视频教程](https://www.youtube.com/watch?v=LeT4jQUh8ok&t=560s)

1.  部署 Cloudflare 页面：
    -   在 Github 上分叉这个项目并点击 Star！
    -   在 Cloudflare Pages 控制台中选择`Connect to Git`之后，选择`edgetunnel`单击该项目后`Start setting up`.
    -   存在`Setting up build and deployment`在页面底部，选择`Environment variables (advanced)`稍后合并`Add variables`填写变量名**通用唯一识别码**，值为你的UUID，然后点击`Save and deploy`就是这样。

2.  访问订阅内容：
    -   使用权`https://[YOUR-PAGES-URL]/[YOUR-UUID]`订阅内容可用。
    -   例如`https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10`这是您的通用自适应订阅地址。
    -   例如`https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?sub`Base64订阅格式，适用于PassWall、SSR+等。
    -   例如`https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?clash`Clash订阅格式，适用于OpenClash等。
    -   例如`https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?sb`singbox订阅格式，适用于singbox等

3.  将 CNAME 自定义域绑定到页面：[视频教程](https://www.youtube.com/watch?v=LeT4jQUh8ok&t=851s)
    -   在页面控制台中`custom domain`选项卡，单击下面`Set up a custom domain`。
    -   填写您的自定义二级域名，注意不要使用您的根域名，例如：
        您分配的域名是`fuck.cloudns.biz`，然后添加自定义字段来填写`lizi.fuck.cloudns.biz`就是这样;
    -   根据Cloudflare的要求，将返回您的域名DNS服务商并添加自定义域名。`lizi`CNAME 记录`edgetunnel.pages.dev`之后，单击`Activate Domain`就是这样。
    -   **如果你是新手，那么你的页面绑定`Custom domains`之后就可以直接起飞，无需再寻找！ ！ ！**

<details>
<summary><code><strong>「 I'm not a novice! I'm really not a novice！I want to play tricks! I want to start high-end gameplay！ 」</strong></code></summary>

4.  用你自己的`Preferred domain name / Preferred IP`订阅：
    -   如果您想使用自己喜欢的域名或者自己喜欢的IP，可以参考[WorkerVless2sub GitHub 存储库](https://github.com/cmliu/WorkerVless2sub)按照 中的部署说明自行构建。
    -   在页面控制台中`set up`选项卡，选择`set up`>`make`>`Edit variables`>`add variable`；
    -   变量名称设置为`SUB`，对应的值为您部署的订阅生成器的地址。例如`sub.cmliussss.workers.dev`，然后单击**保持**。
    -   然后在页面控制台中`deploy`选项卡，选择`All deployments`>`The latest deployment is the rightmost ...`>`Retry deployment`， 就是这样。
    -   请注意，如果您使用自己的订阅地址，则订阅生成器的`SUB`域名和`[YOUR-PAGES-URL]`域名不能属于同一个顶级域名，否则会出现异常。你可以`SUB`该变量被分配给 Pages.dev 的域名。

</details>

![rainbow](https://github.com/NiREvil/vless/assets/126243832/1aca7f5d-6495-44b7-aced-072bae52f256)

## 变量描述

| 变量名         | 例子                                                                                                                                                                 | 必需的 | 评论                                                                                                                                    | YouTube                                                   |
| ----------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ | --- | ------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------- |
| 通用唯一识别码     | `90cd4a77-141a-43c9-991b-08263cfe9c10`                                                                                                                             | ✅   | 如何生成自己的UUID：<https://www.uuidgenerator.net/>                                                                                          | [视频](https://www.youtube.com/watch?v=s91zjpw3-P8&t=72s)   |
| 代理IP        | `bpb.radically.pro`                                                                                                                                                | ✅   | 替代作为访问CloudFlareCDN站点的代理节点（支持多个ProxyIP，在ProxyIP之间使用，或换行作为间隔）。[访问这里](https://github.com/NiREvil/vless/blob/main/sub/ProxyIP.md)查找代理IP。 | [视频](https://www.youtube.com/watch?v=s91zjpw3-P8&t=166s)  |
| 袜子5         | `user:password@127.0.0.1:1080`                                                                                                                                     | ❌   | 优先作为 SOCKS5 代理访问 CFCDN 站点                                                                                                             | [视频](https://www.youtube.com/watch?v=s91zjpw3-P8&t=826s)  |
| 添加          | `zula.ir:2053#preferred name`                                                                                                                                      | ❌   | 本地首选TLS域名/首选IP（支持多个元素，或换行符作为分隔符）                                                                                                      |                                                           |
| 添加          | [https://raw.github.../addressesapi.txt](https://raw.githubusercontent.com/NiREvil/edgetunnel/main/addressesapi.txt)                                               | ❌   | 首选IP的API地址（支持多个元素，或换行符作为间距）                                                                                                           |                                                           |
| 添加NOTLS     | `zula.ir:8080#preferred name`                                                                                                                                      | ❌   | 本地首选noTLS域名/首选IP（支持多个元素，或换行符作为分隔符）                                                                                                    |                                                           |
| 添加NOTLS API | [https://raw.github.../addressesapi.txt](https://raw.githubusercontent.com/cmliu/CFcdnVmess2sub/main/addressesapi.txt)                                             | ❌   | 首选IP的API地址（支持多个元素，或换行符作为间距）                                                                                                           |                                                           |
| ADDCSV      | [https://raw.github.../addressescsv.csv](https://raw.githubusercontent.com/cmliu/WorkerVless2sub/main/addressescsv.csv)                                            | ❌   | iptest速度测试结果（支持多个元素，元素之间有 ,间隔）                                                                                                        |                                                           |
| 动态LS        | `8`                                                                                                                                                                | ❌   | `ADDCSV`ADDCSV测速结果满足速度下限                                                                                                              |                                                           |
| TGToken     | `6894123456:XXXXXXXXXX0qExVsBPUhHDAbXXX`                                                                                                                           | ❌   | 用于发送 TG 通知的机器人令牌                                                                                                                      |                                                           |
| 你做          | `6946912345`                                                                                                                                                       | ❌   | 接收TG通知的账户的数字ID                                                                                                                        |                                                           |
| 子系统         | `VLESS.fxxk.dedyn.io`                                                                                                                                              | ❌   | 内置域名和IP节点信息的订阅生成器地址                                                                                                                   | [视频](https://www.youtube.com/watch?v=s91zjpw3-P8&t=1193s) |
| 子API        | `SUBAPI.fxxk.dedyn.io`                                                                                                                                             | ❌   | 订阅转换后端，例如clash、singbox等。                                                                                                              | [视频](https://www.youtube.com/watch?v=s91zjpw3-P8&t=1446s) |
| 子配置         | [https://raw.github.../ACL4SSR_Online_Full_MultiMode.ini](https://raw.githubusercontent.com/ACL4SSR/ACL4SSR/master/Clash/config/ACL4SSR_Online_Mini_MultiMode.ini) | ❌   | crash、singbox 等的订阅转换配置文件。                                                                                                             | [视频](https://www.youtube.com/watch?v=s91zjpw3-P8&t=1605s) |
| 代理IP        | `false`                                                                                                                                                            | ❌   | 设置为true强制获取订阅者分配的ProxyIP（需要订阅者支持））                                                                                                    | [视频](https://www.youtube.com/watch?v=s91zjpw3-P8&t=1816s) |
| 电子邮件        | `admin@gmail.com`                                                                                                                                                  | ❌   | CF账户邮箱地址（CFKEY两者填写后，订阅信息会显示请求的用途，新手请勿使用）                                                                                              |                                                           |
| CFKEY       | `c6a944b5c956b6c18c2352880952bced8b85e`                                                                                                                            | ❌   | CF账户 Global API Key ( CFEMAIL 两者填写后，订阅信息会显示请求的用途，新手请勿使用)                                                                              |                                                           |

![rainbow](https://github.com/NiREvil/vless/assets/126243832/1aca7f5d-6495-44b7-aced-072bae52f256)

```url
- Note: fill in `SOCKS5` will no longer be enabled `PROXYIP` ！Please choose one of the two！！

- Note: fill in `SUB` will no longer be enabled `ADD` Subscription content generated by class variables! Please choose one of the two to use ！！

- Note: fill in `CFEMAIL` and` CFKEY` Display request usage will be enabled, but it is not recommended! No need to give 一个Worker The project has such high permissions! You are responsible for the consequences ！！！
```

## 实用技巧

**通过添加以下内容可以快速替换该项目部署的订阅`sub`键值对首选订阅生成器！**

> 例如`https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10`是您的通用自适应订阅地址

-   快速将订阅者更改为`VLESS.fxxk.dedyn.io`订阅地址

    ```url
    https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?sub=VLESS.fxxk.dedyn.io
    ```

**本项目部署的节点可以通过节点PATH（路径）访问，使用指定`PROXYIP`或者`SOCKS5`！！！**

-   指定`PROXYIP`案件
    ```url
    /proxyip=proxyip.fxxk.dedyn.io
    /?proxyip=proxyip.fxxk.dedyn.io
    /proxyip.fxxk.dedyn.io (Only domain names starting with 'proxyip.' domain name)
    ```

-   指定`SOCKS5`案件
    ```url
    /socks5=user:password@127.0.0.1:1080
    /?socks5=user:password@127.0.0.1:1080
    /socks://dXNlcjpwYXNzd29yZA==@127.0.0.1:1080
    /socks5://user:password@127.0.0.1:1080
    ```

## 改编后的自适应订阅内容

-   [缺口](https://github.com/mahsanet/NikaNG/releases)
-   [Android 版 NekoBox](https://github.com/Matsuridayo/NekoBoxForAndroid/releases)
-   [玛莎NG](https://github.com/GFW-knocker/MahsaNG/releases)
-   [希迪菲](https://github.com/hiddify/hiddify-next/releases)
-   [v2rayN](https://github.com/2dust/v2rayN)
-   冲突.元（[冲突边缘修订版](https://github.com/clash-verge-rev/clash-verge-rev)
-   唱盒（SFI）

# 感激的

[紫菀](https://github.com/zizifn/edgetunnel)、[快点](https://github.com/cmliu/edgetunnel),[对其进行消毒](https://github.com/3Kmfi6HP/EDtunnel)、[斯坦利宝贝](https://github.com/Stanley-baby)、[ACL4SSR](https://github.com/ACL4SSR/ACL4SSR/tree/master/Clash/config)、[谢格斯1999](https://github.com/SHIJS1999/cloudflare-worker-vless-ip)、<a href="https://alice.ws/aff.php?aff=15"><img src="https://alicenetworks.net/templates/lagom2/assets/img/logo/logo_big.194980063.png" width="150" height="75" alt="Alice Networks LTD"/></a>、
