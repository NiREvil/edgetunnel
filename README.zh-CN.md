# Cloudflare Worker 2 Vless 和 Sub

🇮🇷[波斯语](README.fa.md)

🇹🇷[土耳其](README.tr.md)

🇬🇧[英语](README.MD)

🇨🇳[中国人](README.zh-CN.md)

这是一个基于 Cloudflare Worker 平台的脚本。在原版本的基础上修改为显示VLESS配置信息并转换为订阅内容。使用此脚本，您可以轻松地将VLESS配置信息转换为使用在线配置的Clash或Singbox等工具。

-   基本部署视频教程：[HTTPS://呜呜呜.YouTube.com/watch?V=let4JQ U和8OK](https://www.youtube.com/watch?v=LeT4jQUh8ok)
-   快速部署视频教程：[HTTPS://呜呜呜.YouTube.com/watch?V=59T HR MJ HM AW](https://www.youtube.com/watch?v=59THrmJhmAw)**_最好推荐！！！_**
-   使用透视的高级教程：[HTTPS://呜呜呜.YouTube.com/watch?V=是91专家评委3-P8](https://www.youtube.com/watch?v=s91zjpw3-P8)

Telegram交流群：[@CMLiussss](https://t.me/CMLiussss)

## 风险提示

-   通过向订阅服务提交错误的节点配置来避免泄漏节点配置信息。
-   或者，您可以选择自行部署[WorkerVless2sub订阅生成服务](https://github.com/cmliu/WorkerVless2sub)，这样您就可以利用订阅生成器。

## 工人调配方法[视频教程](https://www.youtube.com/watch?v=LeT4jQUh8ok&t=83s)

1.  部署 Cloudflare Worker：
    -   在 Cloudflare Worker 控制台中创建一个新 Worker。
    -   将要[工人.js](https://github.com/cmliu/edgetunnel/blob/main/_worker.js)将内容粘贴到 Worker 编辑器中。
    -   换乘7号线`userID`修改为你自己的**通用唯一识别码**。

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
<summary><code><strong>「 I'm not a newbie! I'm really, really not a newbie! I want to try some tricks! I want to start playing with advanced techniques! 」</strong></code></summary>

4.  用你自己的`Preferred domain name`/`BestIP`订阅：
    -   如果您想使用自己喜欢的域名或者自己喜欢的IP，可以参考[WorkerVless2sub GitHub 存储库](https://github.com/cmliu/WorkerVless2sub)按照 中的部署说明自行构建。
    -   打开[工人.js](https://github.com/cmliu/edgetunnel/blob/main/_worker.js)文件，在第 12 行找到`sub`变量并将其修改为您部署的订阅生成器的地址。例如`let sub = 'sub.cmliussss.workers.dev';`，注意不要包含协议信息和https等符号。
    -   请注意，如果您使用自己的订阅地址，则订阅生成器的`sub`域名和`[YOUR-WORKER-URL]`域名不能属于同一个顶级域名，否则会出现异常。你可以`sub`该变量被分配给workers.dev 的域名。

</details>

## 页面上传部署方法**最好推荐！！！**[视频教程](https://www.youtube.com/watch?v=59THrmJhmAw)

1.  部署 Cloudflare 页面：
    -   下载[worker.zip](https://raw.githubusercontent.com/cmliu/edgetunnel/main/worker.zip)文件并点击星标！！！
    -   在 Cloudflare Pages 控制台中选择`Upload assets`最后，为您的项目命名并单击`Create a project`，然后上传下载的[worker.zip](https://raw.githubusercontent.com/cmliu/edgetunnel/main/worker.zip)单击文件后`Deployment Site`。
    -   部署完成后，点击`Continue processing site`之后，选择`set up`>`Environment variables`>**制作**定义生产变量 >`Add variables`。
        填写变量名**通用唯一识别码**，值为你的UUID，然后点击`keep`就是这样。
    -   返回`Deploy`选项卡，单击右下角`Create a New Deployment`然后重新上传[worker.zip](https://raw.githubusercontent.com/cmliu/edgetunnel/main/worker.zip)单击文件后`Save and deploy`就是这样。

2.  访问订阅内容：
    -   使用权`https://[YOUR-PAGES-URL]/[YOUR-UUID]`订阅内容可用。
    -   例如，您的订阅链接将是：`https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10`这是您的通用自适应订阅地址。
    -   Base64订阅格式：`https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?sub`适用于PassWall、SSR+等。
    -   冲突订阅格式：`https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?clash`适用于OpenClash等
    -   单盒订阅格式`https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?sb`适用于singbox等

<details>
<summary><code><strong>「 I have my own domain name! I want to bind my own domain name! I have mastered domain name resolution! 」</strong></code></summary>
   
3. Bind a CNAME custom domain to Pages: [Video Tutorial](https://www.youtube.com/watch?v=LeT4jQUh8ok&t=851s)
   - In the Pages console `Custom domains` tab, click below `Set up a custom domain` 。
   - Fill in your custom subdomain name, be careful not to use your root domain name, for example：
     The domain name you are assigned is `fuck.cloudns.biz` ，Add a custom field to fill in `lizi.fuck.cloudns.biz` You can；
   - According to Cloudflare's requirements, your domain name DNS service provider will be returned, and the custom domain will be added `lizi` CNAME record for `edgetunnel.pages.dev` Then click on `Activate Domain` You can。
   - **If you are new, then your pages binding `Custom domains` After that, you can take off directly without looking down.！！！**
   - 
</details>
<details>
<summary><code><strong>「 I'm not a newbie! I'm really not a newbie! I want to play tricks! I want to open up high-end gameplay！ 」</strong></code></summary>
   
4. Use your own `Preferred domain name`/`BestIP` Subscriptions：
   - If you want to use your own preferred domain name or your own preferred IP, you can refer to [WorkerVless2sub GitHub storehouse](https://github.com/cmliu/WorkerVless2sub) Build it yourself using the deployment instructions in 。
   - In the Pages console `set up` tab, select `Environment variables` > `Production` > `Editing variables` > `Add variables`；
   - The variable name is set to `SUB`，The corresponding value is the address of the subscription generator you deployed. 。For Example: `sub.cmliussss.workers.dev`，Then click **Save**。
   - Then in the Pages console `Deploy` tab, select `All deployments` > `The latest deployment is the rightmost ...`> `重试部署`，You can。
   - 注意，如果您使用了自己的订阅地址，要求订阅生成器的 `SUB`域名 和 `[YOUR-PAGES-URL]`的域名 不同属一个顶级域名，否则会出现异常。您可以在 `SUB` 变量赋值为 Pages.dev 分配到的域名。

</details>

## Pages GitHub 部署方法[视频教程](https://www.youtube.com/watch?v=LeT4jQUh8ok&t=560s)

1.  部署 Cloudflare 页面：
    -   在 Github 上分叉这个项目并点击 Star！
    -   在 Cloudflare Pages 控制台中选择`连接到 Git`之后，选择`edgetunnel`单击该项目后`开始设置`。
    -   存在`设置构建和部署`在页面底部，选择`环境变量（高级）`稍后合并`添加变量`填写变量名**通用唯一识别码**，值为你的UUID，然后点击`保存并部署`就是这样。

2.  访问订阅内容：
    -   使用权`https://[YOUR-PAGES-URL]/[YOUR-UUID]`订阅内容可用。
    -   例如`https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10`这是您的通用自适应订阅地址。
    -   例如`https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?sub`Base64订阅格式，适用于PassWall、SSR+等。
    -   例如`https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?clash`Clash订阅格式，适用于OpenClash等。
    -   例如`https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?sb`singbox订阅格式，适用于singbox等

3.  将 CNAME 自定义域绑定到页面：[视频教程](https://www.youtube.com/watch?v=LeT4jQUh8ok&t=851s)
    -   在页面控制台中`自定义域`选项卡，单击下面`设置自定义域`。
    -   填写您的自定义二级域名，注意不要使用您的根域名，例如：
        您分配的域名是`fuck.cloudns.biz`，然后添加自定义字段来填写`lizi.fuck.cloudns.biz`就是这样;
    -   根据Cloudflare的要求，将返回您的域名DNS服务商并添加自定义域名。`lizi`CNAME 记录`edgetunnel.pages.dev`之后，单击`激活域`就是这样。
    -   **如果你是新手，那么你的页面绑定`自定义域`之后就可以直接起飞，无需再寻找！ ！ ！**

<details>
<summary><code><strong>「 我不是小白！我真的真的不是小白！我要玩花活！我要开启高端玩法！ 」</strong></code></summary>

4.  用你自己的`优选域名`/`优选IP`订阅：
    -   如果您想使用自己喜欢的域名或者自己喜欢的IP，可以参考[WorkerVless2sub GitHub 存储库](https://github.com/cmliu/WorkerVless2sub)按照 中的部署说明自行构建。
    -   在页面控制台中`设置`选项卡，选择`环境变量`>`制作`>`编辑变量`>`添加变量`；
    -   变量名称设置为`SUB`，对应的值为您部署的订阅生成器的地址。例如`sub.cmliussss.workers.dev`，然后单击**保持**。
    -   然后在页面控制台中`部署`选项卡，选择`所有部署`>`最新部署最右的 ...`>`重试部署`， 就是这样。
    -   请注意，如果您使用自己的订阅地址，则订阅生成器的`SUB`域名和`[YOUR-PAGES-URL]`域名不能属于同一个顶级域名，否则会出现异常。你可以`SUB`该变量被分配给 Pages.dev 的域名。

</details>

### 变量说明

| 变量名     | 例子                                                                                                                                                             | 评论                                                             | 油田                                                        |
| ------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------- | --------------------------------------------------------- |
| 通用唯一识别码 | 90SD4AH-141A-43SS-991B-08263SVISES10                                                                                                                           | Powershell -NoExit -命令“[指导]&#x3A;:NewGuid()"                   | [视频](https://www.youtube.com/watch?v=s91zjpw3-P8&t=72s)   |
| 代理IP    | proxy IP.法学学科.的第一年.IO                                                                                                                                          | 替代作为访问CloudFlareCDN站点的代理节点（支持多个ProxyIP，在ProxyIP之间使用`,`或换行作为间隔） | [视频](https://www.youtube.com/watch?v=s91zjpw3-P8&t=166s)  |
| 袜子5     | 用户：[password@127.0.0.1](mailto:password@127.0.0.1):1080                                                                                                        | 首选作为访问 CloudFlareCDN 站点的 SOCKS5 代理                             | [视频](https://www.youtube.com/watch?v=s91zjpw3-P8&t=826s)  |
| 子系统     | sub.cmliussss.workers.dev                                                                                                                                      | 内置域名和IP节点信息的订阅生成器地址                                            | [视频](https://www.youtube.com/watch?v=s91zjpw3-P8&t=1193s) |
| 子API    | API.V1.门口                                                                                                                                                      | clang、singbox等订阅转化后端                                           | [视频](https://www.youtube.com/watch?v=s91zjpw3-P8&t=1446s) |
| 子配置     | [https://raw.github.../ACL4SSR_Online_Full_MultiMode.ini](https://raw.githubusercontent.com/cmliu/ACL4SSR/main/Clash/config/ACL4SSR_Online_Full_MultiMode.ini) | crash、singbox 等订阅转化配置文件                                        | [视频](https://www.youtube.com/watch?v=s91zjpw3-P8&t=1605s) |
| 代理IP    | 错误的                                                                                                                                                            | 设置为true强制获取订阅者分配的ProxyIP（需要订阅者支持）                              | [视频](https://www.youtube.com/watch?v=s91zjpw3-P8&t=1816s) |
| 02      | [HTTPS://他.么/C ml IU SSSS](https://t.me/CMLiussss)                                                                                                             | 首页302跳转（支持多个URL，用于URL之间）`,`或者换行作为间隔符，如果您是新手，请不要使用它）            |                                                           |
| 网址      | <https://t.me/CMLiussss>                                                                                                                                       | 主页伪装（支持多个URL，在URL之间使用）`,`或者换行作为间隔，随机设置很容易触发反欺诈）                |                                                           |

## 星星星星升起

[![Stargazers over time](https://starchart.cc/cmliu/edgetunnel.svg?variant=adaptive)](https://starchart.cc/cmliu/edgetunnel)

## 改编后的自适应订阅内容

-   [v2rayN](https://github.com/2dust/v2rayN)
-   冲突.元（[冲突边缘修订版](https://github.com/clash-verge-rev/clash-verge-rev)，[冲突尼安帕苏](https://github.com/keiko233/clash-nyanpasu)，~[冲突边缘](https://github.com/zzzgydi/clash-verge/tree/main)~，ClashX元）
-   唱箱（SFI）

# 感激的

[紫菀](https://github.com/zizifn/edgetunnel)、[对其进行消毒](https://github.com/3Kmfi6HP/EDtunnel)、[斯坦利宝贝](https://github.com/Stanley-baby)、[ACL4SSR](https://github.com/ACL4SSR/ACL4SSR/tree/master/Clash/config)、[谢格斯1999](https://github.com/SHIJS1999/cloudflare-worker-vless-ip)
