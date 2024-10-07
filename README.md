# Cloudflare Worker 2 Vless & Sub  
![rainbow](https://github.com/NiREvil/vless/assets/126243832/1aca7f5d-6495-44b7-aced-072bae52f256)


🇮🇷 [Persian](README.fa.md)  


🇹🇷 [Turkish](README.tr.md)  


🇬🇧 [English](README.MD)  


🇨🇳[ Chinese](README.zh-CN.md)  


This is a script based on the Cloudflare Worker platform. Based on the original version, it is modified to display VLESS configuration information and convert it into subscription content. Using this script, you can easily convert VLESS configuration information into tools such as Clash or Singbox using online configuration.

- [Basic deployment video tutorial](https://www.youtube.com/watch?v=LeT4jQUh8ok)
- [Quick deployment video tutorial](https://www.youtube.com/watch?v=59THrmJhmAw)    __Best recommendation!!!__
- [Advanced tutorial on using perspective](https://www.youtube.com/watch?v=s91zjpw3-P8)

[Telegram communication group](https://t.me/CMLiussss)

## risk warning

- Avoid leaking node configuration information by submitting false node configurations to the subscription service.
- Alternatively, you can choose to deploy it yourself [WorkerVless2sub Subscription Generation Service](https://github.com/cmliu/WorkerVless2sub), so you can take advantage of the subscription generator.

![rainbow](https://github.com/NiREvil/vless/assets/126243832/1aca7f5d-6495-44b7-aced-072bae52f256)


## Workers deployment method  

[Video tutorial](https://www.youtube.com/watch?v=LeT4jQUh8ok&t=83s)

1.  Deploy Cloudflare Worker:
    - Create a new Worker in the Cloudflare Worker console.
    - Will [worker.js](https://github.com/cmliu/edgetunnel/blob/main/_worker.js) Paste the contents into the Worker editor.
    - Change line 11 `userID` Modify it to your own **UUID** 。

2.  Access subscription content:
    - access `https://[YOUR-WORKERS-URL]/[UUID]` Subscription content is available.
    - For example your subscription link will be: `https://vless.google.workers.dev/90cd4a77-141a-43c9-991b-08263cfe9c10` This is your universal adaptive subscription address.
    - Base64 subscription format: `https://vless.google.workers.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?sub` suitable for PassWall, SSR+, etc.
    - Clash subscription format `https://vless.google.workers.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?clash` suitable for OpenClash, etc.
    - singbox subscription format `https://vless.google.workers.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?sb` suitable for singbox, etc.

3.  Bind a custom domain to workers:
    - In the workers console `trigger` tab, click below `Add a custom domain` 。
    - Fill in the secondary domain name that you have transferred to the CloudFlare domain name resolution service, for example: `vless.google.com` After click `Add a custom domain` , just wait for the certificate to take effect.
    - **If you are a novice, you can take off directly now without looking further! ! !**

<details>
<summary><code><strong>「I'm really, really not a newbie! I want to try some tricks! I want to start playing with advanced techniques! 」</strong></code></summary>

4.  use your own `Preferred domain name`/`BestIP` Subscriptions for:
    - If you want to use your own preferred domain name or your own preferred IP, you can refer to [WorkerVless2sub GitHub repository](https://github.com/cmliu/WorkerVless2sub)Build it yourself according to the deployment instructions in .
    - Open [worker.js](https://github.com/cmliu/edgetunnel/blob/main/_worker.js) file, found on line 16 `sub` variable and modify it to the address of your deployed subscription generator. For example `let sub = 'sub.cmliussss.workers.dev';` , be careful not to include protocol information and symbols such as https.
    - Note that if you use your own subscription address, the subscription generator's `sub` domain name and `[YOUR-WORKER-URL]` The domain name does not belong to the same top-level domain name, otherwise an exception will occur. You can `sub` The variable is assigned the domain name assigned to workers.dev.

</details>

![rainbow](https://github.com/NiREvil/vless/assets/126243832/1aca7f5d-6495-44b7-aced-072bae52f256)

## Pages upload deployment method     __Best recommendation!!!__  


[Video tutorial](https://www.youtube.com/watch?v=59THrmJhmAw)  

1.  Deploy Cloudflare Pages:
    - download [worker.zip](https://raw.githubusercontent.com/NiREvil/edgetunnel/main/worker.zip) file and click Star!!!
    - Select in the Cloudflare Pages console `Upload assets` Finally, give your project a name and click `Create a project`, and then upload the downloaded [worker.zip](https://raw.githubusercontent.com/NiREvil/edgetunnel/main/worker.zip) Click after the file `Deployment Site`.
    -   After deployment is complete, click `Continue processing site` After that, select `set up` > `Environment variables` > **make** Define variables for production > `Add variables`,  Fill in the variable name **UUID**, the value is your UUID, then click `keep` That’s it.
    -  return `Deploy` tab, click in the lower right corner `Create a New Deployment` Then re-upload [worker.zip](https://raw.githubusercontent.com/cmliu/edgetunnel/main/worker.zip) Click after the file `Save and deploy` That’s it.

2.  Access subscription content:
    - access `https://[YOUR-PAGES-URL]/[YOUR-UUID]` Subscription content is available.
    - For example your subscription link will be:  `https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10` This is your universal adaptive subscription address.
    - Base64 subscription format: `https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?sub` suitable for PassWall, SSR+, etc.
    - Clash subscription format: `https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?clash` suitable for OpenClash, etc.
    - singbox subscription format `https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?sb` suitable for singbox, etc.

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


## Pages GitHub deployment method.  

[Video tutorial](https://www.youtube.com/watch?v=LeT4jQUh8ok&t=560s)

1.  Deploy Cloudflare Pages:
    - Fork this project on Github and click Star!!!
    - Select in the Cloudflare Pages console `Connect to Git` After that, select `edgetunnel` Click after the item `Start setting up`.
    - exist `Setting up build and deployment` At the bottom of the page, select `Environment variables (advanced)` merge later `Add variables` Fill in the variable name**UUID**, the value is your UUID, then click `Save and deploy` That’s it.

2.  Access subscription content:
    - access `https://[YOUR-PAGES-URL]/[YOUR-UUID]` Subscription content is available.
    - For example `https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10` This is your universal adaptive subscription address.
    - For example `https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?sub` Base64 subscription format, suitable for PassWall, SSR+, etc.
    - For example `https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?clash` Clash subscription format, suitable for OpenClash, etc.
    - For example `https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?sb` singbox subscription format, suitable for singbox, etc.

3.  Bind CNAME custom domain to Pages:  [Video tutorial](https://www.youtube.com/watch?v=LeT4jQUh8ok&t=851s)
    - In the Pages console `custom domain` tab, click below `Set up a custom domain`。
    -  Fill in your custom secondary domain name, be careful not to use your root domain name, for example:
       The domain name you are assigned is `fuck.cloudns.biz` , then add a custom field to fill in `lizi.fuck.cloudns.biz` That’s it;
    - According to Cloudflare's requirements, your domain name DNS service provider will be returned and the custom domain will be added. `lizi` CNAME record of `edgetunnel.pages.dev` After that, click `Activate Domain` That’s it.
    - **If you are a novice, then your pages binding `Custom domains` You can take off directly after that, no need to look further! ! !**

<details>
<summary><code><strong>「 I'm not a novice! I'm really not a novice！I want to play tricks! I want to start high-end gameplay！ 」</strong></code></summary>

4.  use your own`Preferred domain name / Preferred IP`Subscriptions for:
    -   If you want to use your own preferred domain name or your own preferred IP, you can refer to[WorkerVless2sub GitHub repository](https://github.com/cmliu/WorkerVless2sub)Build it yourself according to the deployment instructions in .
    -   In the Pages console `set up` tab, select `set up` > `make` > `Edit variables` > `add variable` ；
    -   The variable name is set to `SUB`, the corresponding value is the address of the subscription generator you deployed. For example `sub.cmliussss.workers.dev` , then click **keep**。
    -   Then in the Pages console `deploy` tab, select `All deployments` > `The latest deployment is the rightmost ...` > `Retry deployment` , that’s it.
    -   Note that if you use your own subscription address, the subscription generator's `SUB` domain name and `[YOUR-PAGES-URL]` The domain name does not belong to the same top-level domain name, otherwise an exception will occur. You can `SUB` The variable is assigned the domain name assigned to Pages.dev.

</details>


![rainbow](https://github.com/NiREvil/vless/assets/126243832/1aca7f5d-6495-44b7-aced-072bae52f256)
## Variable description

| Variable Name | Example | Required | Remark | YouTube |
|--------|---------|-|-----|-----|
| UUID | `90cd4a77-141a-43c9-991b-08263cfe9c10` |✅| How to generate your own UUID: https://www.uuidgenerator.net/ | [Video](https://www.youtube.com/watch?v=s91zjpw3-P8&t=72s) |
| PROXYIP | `bpb.radically.pro` |✅| Alternative as a proxy node for accessing CloudFlareCDN site (supports multiple ProxyIPs, used between ProxyIPs,or line feed as interval).  [VISIT  HERE ](https://github.com/NiREvil/vless/blob/main/sub/ProxyIP.md) to Find proxyIP. | [Video](https://www.youtube.com/watch?v=s91zjpw3-P8&t=166s) |
| SOCKS5  | `user:password@127.0.0.1:1080` |❌| Prioritize as a SOCKS5 proxy for accessing CFCDN sites | [Video](https://www.youtube.com/watch?v=s91zjpw3-P8&t=826s) |
| ADD | `zula.ir:2053#preferred name` |❌| Local preferred TLS domain name/preferred IP (supports multiple elements ,or line breaks as separators) ||
| ADDAPI | [https://raw.github.../addressesapi.txt](https://raw.githubusercontent.com/NiREvil/edgetunnel/main/addressesapi.txt) |❌| API address of the preferred IP (supports multiple elements ,or line breaks as spacing) ||
| ADDNOTLS | `zula.ir:8080#preferred name` |❌| ocal preferred noTLS domain name/preferred IP (supports multiple elements ,or line breaks as separators) ||
| ADDNOTLSAPI | [https://raw.github.../addressesapi.txt](https://raw.githubusercontent.com/cmliu/CFcdnVmess2sub/main/addressesapi.txt) |❌| API address of the preferred IP (supports multiple elements ,or line breaks as spacing) ||
| ADDCSV | [https://raw.github.../addressescsv.csv](https://raw.githubusercontent.com/cmliu/WorkerVless2sub/main/addressescsv.csv) |❌| iptest speed test results (supports multiple elements, with ,intervals between elements) ||
| DLS | `8` |❌| `ADDCSV`ADDCSVThe speed measurement result meets the lower speed limit ||
| TGTOKEN | `6894123456:XXXXXXXXXX0qExVsBPUhHDAbXXX` |❌| Robot token for sending TG notifications | 
| TGID | `6946912345` |❌| The digital ID of the account that receives TG notifications | 
| SUB | `VLESS.fxxk.dedyn.io` | ❌ | Subscription generator address of built-in domain name and IP node information | [Video](https://www.youtube.com/watch?v=s91zjpw3-P8&t=1193s) |
| SUBAPI | `SUBAPI.fxxk.dedyn.io` |❌| Subscription conversion backends such as clash, singbox, etc. | [Video](https://www.youtube.com/watch?v=s91zjpw3-P8&t=1446s) |
| SUBCONFIG | [https://raw.github.../ACL4SSR_Online_Full_MultiMode.ini](https://raw.githubusercontent.com/ACL4SSR/ACL4SSR/master/Clash/config/ACL4SSR_Online_Mini_MultiMode.ini) |❌| Subscription conversion configuration files for clash, singbox, etc. | [Video](https://www.youtube.com/watch?v=s91zjpw3-P8&t=1605s) |
| RPROXYIP | `false` |❌| Set to true to force the acquisition of the ProxyIP assigned by the subscriber (subscriber support required))| [Video](https://www.youtube.com/watch?v=s91zjpw3-P8&t=1816s) |
| CFEMAIL | `admin@gmail.com` |❌| CF account email address ( CFKEYafter filling in both, the subscription information will show the requested usage, so newbies should not use this) |  |
| CFKEY | `c6a944b5c956b6c18c2352880952bced8b85e` |❌| CF account Global API Key ( CFEMAILafter filling in both, the subscription information will show the requested usage, so newbies should not use this) |  |

![rainbow](https://github.com/NiREvil/vless/assets/126243832/1aca7f5d-6495-44b7-aced-072bae52f256)



   ```url
  - Note: fill in `SOCKS5` will no longer be enabled `PROXYIP` ！Please choose one of the two！！

  - Note: fill in `SUB` will no longer be enabled `ADD` Subscription content generated by class variables! Please choose one of the two to use ！！

  - Note: fill in `CFEMAIL` and` CFKEY` Display request usage will be enabled, but it is not recommended! No need to give 一个Worker The project has such high permissions! You are responsible for the consequences ！！！
```


## Practical tips

**The subscriptions deployed by this project can be quickly replaced by adding the `sub` key value to the preferred subscription generator！** 
> For example `https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10` is your universal adaptive subscription address

- Quickly change the subscriber to `VLESS.fxxk.dedyn.io` Subscription address
  
   ```url
   https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?sub=VLESS.fxxk.dedyn.io
   ```
   
**The nodes deployed by this project can be accessed through the node PATH (path)，Use the specified `PROXYIP` Or `SOCKS5`！！！**

- designation `PROXYIP` Case
   ```url
   /proxyip=proxyip.fxxk.dedyn.io
   /?proxyip=proxyip.fxxk.dedyn.io
   /proxyip.fxxk.dedyn.io (Only domain names starting with 'proxyip.' domain name)
   ```

- designation `SOCKS5` Case
   ```url
   /socks5=user:password@127.0.0.1:1080
   /?socks5=user:password@127.0.0.1:1080
   /socks://dXNlcjpwYXNzd29yZA==@127.0.0.1:1080
   /socks5://user:password@127.0.0.1:1080
   ```


## Adapted adaptive subscription content
   - [NikaNG](https://github.com/mahsanet/NikaNG/releases)
   - [NekoBoxForAndroid](https://github.com/Matsuridayo/NekoBoxForAndroid/releases)
   - [MahsaNG](https://github.com/GFW-knocker/MahsaNG/releases)
   - [Hiddify](https://github.com/hiddify/hiddify-next/releases)
   - [v2rayN](https://github.com/2dust/v2rayN)
   - clash.meta（[clash-verge-rev](https://github.com/clash-verge-rev/clash-verge-rev)
   - sing-box（SFI）



# grateful 
[zizifn](https://github.com/zizifn/edgetunnel)、[Cmliu](https://github.com/cmliu/edgetunnel), [3Kmfi6HP](https://github.com/3Kmfi6HP/EDtunnel)、[Stanley-baby](https://github.com/Stanley-baby)、[ACL4SSR](https://github.com/ACL4SSR/ACL4SSR/tree/master/Clash/config)、[SHIJS1999](https://github.com/SHIJS1999/cloudflare-worker-vless-ip)、<a href="https://alice.ws/aff.php?aff=15"><img src="https://alicenetworks.net/templates/lagom2/assets/img/logo/logo_big.194980063.png" width="150" height="75" alt="Alice Networks LTD"/></a>、
