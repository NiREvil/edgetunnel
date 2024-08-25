# Cloudflare Worker 2 Vless & Sub

🇮🇷[فارسی](README.fa.md)

🇹🇷[ترکی](README.tr.md)

🇬🇧[انگلیسی](README.MD)

🇨🇳[چینی](README.zh-CN.md)

این یک اسکریپت مبتنی بر پلتفرم Cloudflare Worker است. بر اساس نسخه اصلی، برای نمایش اطلاعات پیکربندی VLESS و تبدیل آن به محتوای اشتراک اصلاح شده است. با استفاده از این اسکریپت می توانید به راحتی اطلاعات پیکربندی VLESS را با استفاده از پیکربندی آنلاین به ابزارهایی مانند Clash یا Singbox تبدیل کنید.

-   آموزش تصویری استقرار اولیه:<https://www.youtube.com/watch?v=LeT4jQUh8ok>
-   آموزش تصویری استقرار سریع:<https://www.youtube.com/watch?v=59THrmJhmAw>**_بهترین توصیه!!!_**
-   آموزش پیشرفته استفاده از پرسپکتیو:<https://www.youtube.com/watch?v=s91zjpw3-P8>

گروه ارتباطی تلگرام:[@CMLiussss](https://t.me/CMLiussss)

## هشدار خطر

-   با ارسال تنظیمات نادرست گره به سرویس اشتراک، از افشای اطلاعات پیکربندی گره جلوگیری کنید.
-   از طرف دیگر، شما می توانید انتخاب کنید که آن را خودتان مستقر کنید[سرویس تولید اشتراک WorkerVless2sub](https://github.com/cmliu/WorkerVless2sub)، بنابراین می توانید از مزایای ایجاد کننده اشتراک استفاده کنید.

## روش استقرار کارگران[آموزش تصویری](https://www.youtube.com/watch?v=LeT4jQUh8ok&t=83s)

1.  استقرار Cloudflare Worker:
    -   یک Worker جدید در کنسول Cloudflare Worker ایجاد کنید.
    -   اراده[worker.js](https://github.com/cmliu/edgetunnel/blob/main/_worker.js)مطالب را در ویرایشگر Worker قرار دهید.
    -   تغییر خط 7`userID`آن را به خود تغییر دهید**UUID**。

2.  دسترسی به محتوای اشتراک:
    -   دسترسی داشته باشید`https://[YOUR-WORKERS-URL]/[UUID]`محتوای اشتراک در دسترس است.
    -   به عنوان مثال لینک اشتراک شما این خواهد بود:`https://vless.google.workers.dev/90cd4a77-141a-43c9-991b-08263cfe9c10`این آدرس اشتراک تطبیقی ​​جهانی شماست.
    -   فرمت اشتراک Base64:`https://vless.google.workers.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?sub`مناسب برای PassWall، SSR+ و غیره
    -   فرمت اشتراک کلش`https://vless.google.workers.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?clash`مناسب برای OpenClash و غیره
    -   فرمت اشتراک singbox`https://vless.google.workers.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?sb`مناسب برای singbox و غیره

3.  یک دامنه سفارشی را به کارگران متصل کنید:
    -   در کنسول کارگران`trigger`برگه، در زیر کلیک کنید`Add a custom domain`。
    -   نام دامنه ثانویه ای را که به سرویس حل نام دامنه CloudFlare منتقل کرده اید را وارد کنید، به عنوان مثال:`vless.google.com`بعد از کلیک`Add a custom domain`، فقط منتظر بمانید تا گواهی اجرا شود.
    -   **اگر تازه‌کار هستید، می‌توانید هم‌اکنون مستقیماً بدون نگاه کردن به زمین بلند شوید! ! !**

<details>
<summary><code><strong>「 I'm not a newbie! I'm really, really not a newbie! I want to try some tricks! I want to start playing with advanced techniques! 」</strong></code></summary>

4.  از خودت استفاده کن`Preferred domain name`/`BestIP`اشتراک برای:
    -   اگر می خواهید از نام دامنه دلخواه خود یا IP دلخواه خود استفاده کنید، می توانید به آن مراجعه کنید[مخزن WorkerVless2sub GitHub](https://github.com/cmliu/WorkerVless2sub)آن را خودتان طبق دستورالعمل‌های استقرار در بسازید.
    -   باز کنید[worker.js](https://github.com/cmliu/edgetunnel/blob/main/_worker.js)فایل، در خط 12 یافت شد`sub`متغیر و آن را به آدرس مولد اشتراک مستقر خود تغییر دهید. به عنوان مثال`let sub = 'sub.cmliussss.workers.dev';`، مراقب باشید اطلاعات پروتکل و نمادهایی مانند https را وارد نکنید.
    -   توجه داشته باشید که اگر از آدرس اشتراک خود استفاده می کنید، از آدرس مولد اشتراک`sub`نام دامنه و`[YOUR-WORKER-URL]`نام دامنه به همان نام دامنه سطح بالا تعلق ندارد، در غیر این صورت یک استثنا رخ خواهد داد. شما می توانید`sub`به متغیر، نام دامنه اختصاص داده شده به working.dev اختصاص داده شده است.

</details>

## روش استقرار آپلود صفحات**بهترین توصیه!!!**[آموزش تصویری](https://www.youtube.com/watch?v=59THrmJhmAw)

1.  استقرار صفحات Cloudflare:
    -   دانلود کنید[worker.zip](https://raw.githubusercontent.com/cmliu/edgetunnel/main/worker.zip)فایل و ستاره کلیک کنید!!!
    -   در کنسول Cloudflare Pages انتخاب کنید`Upload assets`در نهایت، نام پروژه خود را بگذارید و کلیک کنید`Create a project`و سپس فایل دانلود شده را آپلود کنید[worker.zip](https://raw.githubusercontent.com/cmliu/edgetunnel/main/worker.zip)بعد از فایل کلیک کنید`Deployment Site`。
    -   پس از اتمام استقرار، کلیک کنید`Continue processing site`پس از آن، را انتخاب کنید`set up`>`Environment variables`>**ساختن** Define variables for production > `Add variables`.
        نام متغیر را پر کنید**UUID**، مقدار UUID شما است، سپس کلیک کنید`keep`همین است.
    -   بازگشت`Deploy`برگه، در گوشه پایین سمت راست کلیک کنید`Create a New Deployment`سپس دوباره آپلود کنید[worker.zip](https://raw.githubusercontent.com/cmliu/edgetunnel/main/worker.zip)بعد از فایل کلیک کنید`Save and deploy`همین است.

2.  دسترسی به محتوای اشتراک:
    -   دسترسی داشته باشید`https://[YOUR-PAGES-URL]/[YOUR-UUID]`محتوای اشتراک در دسترس است.
    -   به عنوان مثال لینک اشتراک شما این خواهد بود:`https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10`این آدرس اشتراک تطبیقی ​​جهانی شماست.
    -   فرمت اشتراک Base64:`https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?sub`مناسب برای PassWall، SSR+ و غیره
    -   فرمت اشتراک کلش:`https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?clash`مناسب برای OpenClash و غیره
    -   فرمت اشتراک singbox`https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?sb`مناسب برای singbox و غیره

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

## روش استقرار GitHub صفحات[آموزش تصویری](https://www.youtube.com/watch?v=LeT4jQUh8ok&t=560s)

1.  استقرار صفحات Cloudflare:
    -   این پروژه را در Github فورک کنید و ستاره را کلیک کنید!!!
    -   در کنسول Cloudflare Pages انتخاب کنید`连接到 Git`پس از آن، را انتخاب کنید`edgetunnel`بعد از آیتم کلیک کنید`开始设置`。
    -   وجود داشته باشد`设置构建和部署`در پایین صفحه، را انتخاب کنید`环境变量（高级）`بعدا ادغام شوند`添加变量`نام متغیر را پر کنید**UUID**، مقدار UUID شما است، سپس کلیک کنید`保存并部署`همین است.

2.  دسترسی به محتوای اشتراک:
    -   دسترسی داشته باشید`https://[YOUR-PAGES-URL]/[YOUR-UUID]`محتوای اشتراک در دسترس است.
    -   به عنوان مثال`https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10`این آدرس اشتراک تطبیقی ​​جهانی شماست.
    -   به عنوان مثال`https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?sub`فرمت اشتراک Base64، مناسب برای PassWall، SSR+ و غیره.
    -   به عنوان مثال`https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?clash`فرمت اشتراک کلش، مناسب برای OpenClash و غیره.
    -   به عنوان مثال`https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?sb`فرمت اشتراک singbox، مناسب برای singbox و غیره.

3.  دامنه سفارشی CNAME را به صفحات متصل کنید:[آموزش تصویری](https://www.youtube.com/watch?v=LeT4jQUh8ok&t=851s)
    -   در کنسول Pages`自定义域`برگه، در زیر کلیک کنید`设置自定义域`。
    -   نام دامنه ثانویه سفارشی خود را وارد کنید، مراقب باشید از نام دامنه ریشه خود استفاده نکنید، به عنوان مثال:
        نام دامنه ای که به شما اختصاص داده شده است`fuck.cloudns.biz`، سپس یک فیلد سفارشی برای پر کردن اضافه کنید`lizi.fuck.cloudns.biz`همین است؛
    -   با توجه به الزامات Cloudflare، نام دامنه شما ارائه دهنده خدمات DNS بازگردانده خواهد شد و دامنه سفارشی اضافه خواهد شد.`lizi`رکورد CNAME از`edgetunnel.pages.dev`پس از آن، کلیک کنید`激活域`همین است.
    -   **اگر شما یک مبتدی هستید، پس صفحات خود را الزام آور`自定义域`شما می توانید بلافاصله پس از آن بلند شوید، نیازی به جستجوی بیشتر نیست! ! !**

<details>
<summary><code><strong>「 我不是小白！我真的真的不是小白！我要玩花活！我要开启高端玩法！ 」</strong></code></summary>

4.  از خودت استفاده کن`优选域名`/`优选IP`اشتراک برای:
    -   اگر می خواهید از نام دامنه دلخواه خود یا IP دلخواه خود استفاده کنید، می توانید به آن مراجعه کنید[مخزن WorkerVless2sub GitHub](https://github.com/cmliu/WorkerVless2sub)آن را خودتان طبق دستورالعمل‌های استقرار در بسازید.
    -   در کنسول Pages`设置`برگه، انتخاب کنید`环境变量`>`制作`>`编辑变量`>`添加变量`；
    -   نام متغیر تنظیم شده است`SUB`، مقدار مربوطه آدرس مولد اشتراکی است که شما مستقر کرده اید. به عنوان مثال`sub.cmliussss.workers.dev`، سپس کلیک کنید**نگه دارید**。
    -   سپس در کنسول Pages`部署`برگه، انتخاب کنید`所有部署`>`最新部署最右的 ...`>`重试部署`، همین است.
    -   توجه داشته باشید که اگر از آدرس اشتراک خود استفاده می کنید، از آدرس مولد اشتراک`SUB`نام دامنه و`[YOUR-PAGES-URL]`نام دامنه به همان نام دامنه سطح بالا تعلق ندارد، در غیر این صورت یک استثنا رخ خواهد داد. شما می توانید`SUB`متغیر به نام دامنه اختصاص داده شده به Pages.dev اختصاص داده می شود.

</details>

### توضیحات متغیر

| نام متغیر | مثال                                                                                                                                                           | تذکر دهید                                                                                                                                                                                 | YT                                                           |
| --------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------ |
| UUID      | 90SD4AH-141A-43SS-991B-08263SVISES10                                                                                                                           | Powershell -NoExit -Command "[راهنما]&#x3A;:NewGuid()"                                                                                                                                    | [ویدئو](https://www.youtube.com/watch?v=s91zjpw3-P8&t=72s)   |
| PROXYIP   | proxyip.fxxk.dedyn.io                                                                                                                                          | جایگزین به عنوان یک گره پروکسی برای دسترسی به سایت CloudFlareCDN (پشتیبانی از ProxyIP های متعدد، مورد استفاده بین ProxyIP ها`,`یا تغذیه خط به عنوان فاصله)                                | [ویدئو](https://www.youtube.com/watch?v=s91zjpw3-P8&t=166s)  |
| جوراب 5   | کاربر:[password@127.0.0.1](mailto:password@127.0.0.1):1080                                                                                                     | به عنوان یک پروکسی SOCKS5 برای دسترسی به سایت های CloudFlareCDN ترجیح داده می شود                                                                                                         | [ویدئو](https://www.youtube.com/watch?v=s91zjpw3-P8&t=826s)  |
| زیر       | sub.cmliussss.workers.dev                                                                                                                                      | آدرس مولد اشتراک با نام دامنه داخلی و اطلاعات گره IP                                                                                                                                      | [ویدئو](https://www.youtube.com/watch?v=s91zjpw3-P8&t=1193s) |
| subapi    | api.v1.mk                                                                                                                                                      | clash، singbox، و غیره باطن تبدیل اشتراک                                                                                                                                                  | [ویدئو](https://www.youtube.com/watch?v=s91zjpw3-P8&t=1446s) |
| SUBCONFIG | [https://raw.github.../ACL4SSR_Online_Full_MultiMode.ini](https://raw.githubusercontent.com/cmliu/ACL4SSR/main/Clash/config/ACL4SSR_Online_Full_MultiMode.ini) | clash، singbox، و غیره. پروفایل تبدیل اشتراک                                                                                                                                              | [ویدئو](https://www.youtube.com/watch?v=s91zjpw3-P8&t=1605s) |
| RPROXYIP  | نادرست                                                                                                                                                         | برای اجبار به دستیابی ProxyIP اختصاص داده شده توسط مشترک روی true تنظیم کنید (نیاز به پشتیبانی مشترک دارد)                                                                                | [ویدئو](https://www.youtube.com/watch?v=s91zjpw3-P8&t=1816s) |
| 02        | <https://t.me/CMLiussss>                                                                                                                                       | پرش صفحه اصلی 302 (از چندین URL پشتیبانی می کند، بین URL ها استفاده می شود)`,`یا تغذیه خط به‌عنوان فاصله‌گذار، اگر تازه کار هستید از آن استفاده نکنید)                                    |                                                              |
| URL       | <https://t.me/CMLiussss>                                                                                                                                       | پنهان کردن صفحه اصلی (از چندین URL پشتیبانی می کند، بین URL ها استفاده می شود)`,`یا خطوط به صورت فواصل زمانی شکسته می شوند، تنظیمات تصادفی به راحتی می توانند ضد تقلب را راه اندازی کنند) |                                                              |

## ستاره ها طلوع می کنند

[![Stargazers over time](https://starchart.cc/cmliu/edgetunnel.svg?variant=adaptive)](https://starchart.cc/cmliu/edgetunnel)

## محتوای اشتراک تطبیقی ​​تطبیقی

-   [v2rayN](https://github.com/2dust/v2rayN)
-   clash.meta ([clash-verge-rev](https://github.com/clash-verge-rev/clash-verge-rev)，[نیانپاسو را بزنید](https://github.com/keiko233/clash-nyanpasu)，~[درگیری](https://github.com/zzzgydi/clash-verge/tree/main)~(ClashX Meta)
-   sing-box (SFI)

# سپاسگزار

[zizifn](https://github.com/zizifn/edgetunnel)、[آن را استریل کنید](https://github.com/3Kmfi6HP/EDtunnel)、[استنلی عزیزم](https://github.com/Stanley-baby)、[ACL4SSR](https://github.com/ACL4SSR/ACL4SSR/tree/master/Clash/config)、[Shegs1999](https://github.com/SHIJS1999/cloudflare-worker-vless-ip)
