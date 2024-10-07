# Cloudflare Worker 2 Vless & Sub

![rainbow](https://github.com/NiREvil/vless/assets/126243832/1aca7f5d-6495-44b7-aced-072bae52f256)

🇮🇷[فارسی](README.fa.md)

🇹🇷[ترکی](README.tr.md)

🇬🇧[انگلیسی](README.MD)

🇨🇳[چینی](README.zh-CN.md)

این یک اسکریپت مبتنی بر پلتفرم Cloudflare Worker است. بر اساس نسخه اصلی، برای نمایش اطلاعات پیکربندی VLESS و تبدیل آن به محتوای اشتراک اصلاح شده است. با استفاده از این اسکریپت می توانید به راحتی اطلاعات پیکربندی VLESS را با استفاده از پیکربندی آنلاین به ابزارهایی مانند Clash یا Singbox تبدیل کنید.

-   [آموزش تصویری استقرار اولیه](https://www.youtube.com/watch?v=LeT4jQUh8ok)
-   [آموزش تصویری استقرار سریع](https://www.youtube.com/watch?v=59THrmJhmAw)**بهترین توصیه!!!**
-   [آموزش پیشرفته استفاده از پرسپکتیو](https://www.youtube.com/watch?v=s91zjpw3-P8)

[گروه ارتباطی تلگرام](https://t.me/CMLiussss)

## هشدار خطر

-   با ارسال تنظیمات نادرست گره به سرویس اشتراک، از افشای اطلاعات پیکربندی گره جلوگیری کنید.
-   از طرف دیگر، شما می توانید انتخاب کنید که آن را خودتان مستقر کنید[سرویس تولید اشتراک WorkerVless2sub](https://github.com/cmliu/WorkerVless2sub)، بنابراین می توانید از مزایای ایجاد کننده اشتراک استفاده کنید.

![rainbow](https://github.com/NiREvil/vless/assets/126243832/1aca7f5d-6495-44b7-aced-072bae52f256)

## روش استقرار کارگران

[آموزش تصویری](https://www.youtube.com/watch?v=LeT4jQUh8ok&t=83s)

1.  استقرار Cloudflare Worker:
    -   یک Worker جدید در کنسول Cloudflare Worker ایجاد کنید.
    -   اراده[worker.js](https://github.com/cmliu/edgetunnel/blob/main/_worker.js)مطالب را در ویرایشگر Worker قرار دهید.
    -   تغییر خط 11`userID`آن را به خود تغییر دهید**UUID**。

2.  دسترسی به محتوای اشتراک:
    -   دسترسی داشته باشید`https://[YOUR-WORKERS-URL]/[UUID]`محتوای اشتراک در دسترس است.
    -   به عنوان مثال لینک اشتراک شما این خواهد بود:`https://vless.google.workers.dev/90cd4a77-141a-43c9-991b-08263cfe9c10`این آدرس اشتراک تطبیقی ​​جهانی شماست.
    -   فرمت اشتراک Base64:`https://vless.google.workers.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?sub`مناسب برای PassWall، SSR+ و غیره
    -   فرمت اشتراک کلش`https://vless.google.workers.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?clash`مناسب برای OpenClash و غیره
    -   فرمت اشتراک singbox`https://vless.google.workers.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?sb`مناسب برای singbox و غیره

3.  یک دامنه سفارشی را به کارگران متصل کنید:
    -   در کنسول کارگران`trigger`برگه، در زیر کلیک کنید`Add a custom domain`。
    -   نام دامنه ثانویه را که به سرویس حل نام دامنه CloudFlare منتقل کرده اید را وارد کنید، به عنوان مثال:`vless.google.com`پس از کلیک`Add a custom domain`، فقط منتظر بمانید تا گواهی اجرا شود.
    -   **اگر تازه‌کار هستید، می‌توانید هم‌اکنون مستقیماً بدون نگاه کردن به زمین بلند شوید! ! !**

<details>
<summary><code><strong>「I'm really, really not a newbie! I want to try some tricks! I want to start playing with advanced techniques! 」</strong></code></summary>

4.  از خودت استفاده کن`Preferred domain name`/`BestIP`اشتراک برای:
    -   اگر می خواهید از نام دامنه دلخواه خود یا IP دلخواه خود استفاده کنید، می توانید به آن مراجعه کنید[مخزن WorkerVless2sub GitHub](https://github.com/cmliu/WorkerVless2sub)خودتان آن را مطابق دستورالعمل‌های استقرار در بسازید.
    -   باز کنید[worker.js](https://github.com/cmliu/edgetunnel/blob/main/_worker.js)فایل، در خط 16 یافت شد`sub`متغیر و آن را به آدرس مولد اشتراک مستقر خود تغییر دهید. به عنوان مثال`let sub = 'sub.cmliussss.workers.dev';`، مراقب باشید اطلاعات پروتکل و نمادهایی مانند https را وارد نکنید.
    -   توجه داشته باشید که اگر از آدرس اشتراک خود استفاده می کنید، از آدرس مولد اشتراک`sub`نام دامنه و`[YOUR-WORKER-URL]`نام دامنه به همان نام دامنه سطح بالا تعلق ندارد، در غیر این صورت یک استثنا رخ خواهد داد. شما می توانید`sub`به متغیر، نام دامنه اختصاص داده شده به working.dev اختصاص داده شده است.

</details>

![rainbow](https://github.com/NiREvil/vless/assets/126243832/1aca7f5d-6495-44b7-aced-072bae52f256)

## روش استقرار آپلود صفحات**بهترین توصیه!!!**

[آموزش تصویری](https://www.youtube.com/watch?v=59THrmJhmAw)

1.  استقرار صفحات Cloudflare:
    -   دانلود کنید[worker.zip](https://raw.githubusercontent.com/NiREvil/edgetunnel/main/worker.zip)فایل و ستاره کلیک کنید!!!
    -   در کنسول Cloudflare Pages انتخاب کنید`Upload assets`در نهایت، نام پروژه خود را بگذارید و کلیک کنید`Create a project`و سپس فایل دانلود شده را آپلود کنید[worker.zip](https://raw.githubusercontent.com/NiREvil/edgetunnel/main/worker.zip)بعد از فایل کلیک کنید`Deployment Site`.
    -   پس از اتمام استقرار، کلیک کنید`Continue processing site`پس از آن، را انتخاب کنید`set up`>`Environment variables`>**ساختن**تعریف متغیرهای تولید >`Add variables`، نام متغیر را وارد کنید**UUID**، مقدار UUID شما است، سپس کلیک کنید`keep`همین است.
    -   بازگشت`Deploy`برگه، در گوشه سمت راست پایین کلیک کنید`Create a New Deployment`سپس دوباره آپلود کنید[worker.zip](https://raw.githubusercontent.com/cmliu/edgetunnel/main/worker.zip)بعد از فایل کلیک کنید`Save and deploy`همین است.

2.  دسترسی به محتوای اشتراک:
    -   دسترسی داشته باشید`https://[YOUR-PAGES-URL]/[YOUR-UUID]`محتوای اشتراک در دسترس است.
    -   به عنوان مثال لینک اشتراک شما این خواهد بود:`https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10`این آدرس اشتراک تطبیقی ​​جهانی شماست.
    -   فرمت اشتراک Base64:`https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?sub`مناسب برای PassWall، SSR+ و غیره
    -   فرمت اشتراک کلش:`https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?clash`مناسب برای OpenClash و غیره
    -   فرمت اشتراک singbox`https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?sb`مناسب برای singbox و غیره

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

## روش استقرار GitHub صفحات.

[آموزش تصویری](https://www.youtube.com/watch?v=LeT4jQUh8ok&t=560s)

1.  استقرار صفحات Cloudflare:
    -   این پروژه را در Github فورک کنید و ستاره را کلیک کنید!!!
    -   در کنسول Cloudflare Pages انتخاب کنید`Connect to Git`پس از آن، را انتخاب کنید`edgetunnel`بعد از مورد کلیک کنید`Start setting up`.
    -   وجود داشته باشد`Setting up build and deployment`در پایین صفحه، را انتخاب کنید`Environment variables (advanced)`بعدا ادغام شوند`Add variables`نام متغیر را پر کنید**UUID**، مقدار UUID شما است، سپس کلیک کنید`Save and deploy`همین است.

2.  دسترسی به محتوای اشتراک:
    -   دسترسی داشته باشید`https://[YOUR-PAGES-URL]/[YOUR-UUID]`محتوای اشتراک در دسترس است.
    -   به عنوان مثال`https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10`این آدرس اشتراک تطبیقی ​​جهانی شماست.
    -   به عنوان مثال`https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?sub`فرمت اشتراک Base64، مناسب برای PassWall، SSR+ و غیره.
    -   به عنوان مثال`https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?clash`فرمت اشتراک کلش، مناسب برای OpenClash و غیره.
    -   به عنوان مثال`https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?sb`فرمت اشتراک singbox، مناسب برای singbox و غیره.

3.  دامنه سفارشی CNAME را به صفحات متصل کنید:[آموزش تصویری](https://www.youtube.com/watch?v=LeT4jQUh8ok&t=851s)
    -   در کنسول Pages`custom domain`برگه، در زیر کلیک کنید`Set up a custom domain`。
    -   نام دامنه ثانویه سفارشی خود را وارد کنید، مراقب باشید از نام دامنه ریشه خود استفاده نکنید، به عنوان مثال:
        نام دامنه ای که به شما اختصاص داده شده است`fuck.cloudns.biz`، سپس یک فیلد سفارشی برای پر کردن اضافه کنید`lizi.fuck.cloudns.biz`همین است؛
    -   با توجه به الزامات Cloudflare، نام دامنه شما ارائه دهنده خدمات DNS بازگردانده خواهد شد و دامنه سفارشی اضافه خواهد شد.`lizi`رکورد CNAME از`edgetunnel.pages.dev`پس از آن، کلیک کنید`Activate Domain`همین است.
    -   **اگر شما یک مبتدی هستید، پس صفحات خود را الزام آور`Custom domains`شما می توانید بلافاصله پس از آن بلند شوید، نیازی به جستجوی بیشتر نیست! ! !**

<details>
<summary><code><strong>「 I'm not a novice! I'm really not a novice！I want to play tricks! I want to start high-end gameplay！ 」</strong></code></summary>

4.  از خودت استفاده کن`Preferred domain name / Preferred IP`اشتراک برای:
    -   اگر می خواهید از نام دامنه دلخواه خود یا IP دلخواه خود استفاده کنید، می توانید به آن مراجعه کنید[مخزن WorkerVless2sub GitHub](https://github.com/cmliu/WorkerVless2sub)خودتان آن را مطابق دستورالعمل‌های استقرار در بسازید.
    -   در کنسول Pages`set up`برگه، انتخاب کنید`set up`>`make`>`Edit variables`>`add variable`；
    -   نام متغیر تنظیم شده است`SUB`، مقدار مربوطه آدرس مولد اشتراکی است که شما مستقر کرده اید. به عنوان مثال`sub.cmliussss.workers.dev`، سپس کلیک کنید**نگه دارید**。
    -   سپس در کنسول Pages`deploy`برگه، انتخاب کنید`All deployments`>`The latest deployment is the rightmost ...`>`Retry deployment`، همین است.
    -   توجه داشته باشید که اگر از آدرس اشتراک خود استفاده می کنید، از آدرس مولد اشتراک`SUB`نام دامنه و`[YOUR-PAGES-URL]`نام دامنه به همان نام دامنه سطح بالا تعلق ندارد، در غیر این صورت یک استثنا رخ خواهد داد. شما می توانید`SUB`متغیر به نام دامنه اختصاص داده شده به Pages.dev اختصاص داده می شود.

</details>

![rainbow](https://github.com/NiREvil/vless/assets/126243832/1aca7f5d-6495-44b7-aced-072bae52f256)

## توضیحات متغیر

| نام متغیر         | مثال                                                                                                                                                               | مورد نیاز | تذکر دهید                                                                                                                                                                                                                                                  | یوتیوب                                                       |
| ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ | --------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------ |
| UUID              | `90cd4a77-141a-43c9-991b-08263cfe9c10`                                                                                                                             | ✅         | چگونه UUID خود را تولید کنید:<https://www.uuidgenerator.net/>                                                                                                                                                                                              | [ویدئو](https://www.youtube.com/watch?v=s91zjpw3-P8&t=72s)   |
| PROXYIP           | `bpb.radically.pro`                                                                                                                                                | ✅         | جایگزین به عنوان یک گره پروکسی برای دسترسی به سایت CloudFlareCDN (پشتیبانی از ProxyIP های متعدد، مورد استفاده بین ProxyIP، یا تغذیه خط به عنوان فاصله).[از اینجا دیدن کنید](https://github.com/NiREvil/vless/blob/main/sub/ProxyIP.md)برای یافتن پروکسی IP | [ویدئو](https://www.youtube.com/watch?v=s91zjpw3-P8&t=166s)  |
| جوراب 5           | `user:password@127.0.0.1:1080`                                                                                                                                     | ❌         | به عنوان یک پروکسی SOCKS5 برای دسترسی به سایت های CFCDN اولویت بندی کنید                                                                                                                                                                                   | [ویدئو](https://www.youtube.com/watch?v=s91zjpw3-P8&t=826s)  |
| اضافه کنید        | `zula.ir:2053#preferred name`                                                                                                                                      | ❌         | نام دامنه ترجیحی محلی TLS/IP ترجیحی (از چندین عنصر پشتیبانی می‌کند، یا شکسته‌های خط به عنوان جداکننده)                                                                                                                                                     |                                                              |
| اضافه کنید        | [https://raw.github.../addressesapi.txt](https://raw.githubusercontent.com/NiREvil/edgetunnel/main/addressesapi.txt)                                               | ❌         | آدرس API IP ترجیحی (از چندین عنصر پشتیبانی می‌کند، یا شکست خط به عنوان فاصله)                                                                                                                                                                              |                                                              |
| اضافه کردن        | `zula.ir:8080#preferred name`                                                                                                                                      | ❌         | نام دامنه ترجیحی noTLS/IP ترجیحی ocal (از چندین عنصر پشتیبانی می کند، یا خط شکن به عنوان جداکننده)                                                                                                                                                         |                                                              |
| ADDNOTLSAPI       | [https://raw.github.../addressesapi.txt](https://raw.githubusercontent.com/cmliu/CFcdnVmess2sub/main/addressesapi.txt)                                             | ❌         | آدرس API IP ترجیحی (از چندین عنصر پشتیبانی می‌کند، یا شکست خط به عنوان فاصله)                                                                                                                                                                              |                                                              |
| ADDCSV            | [https://raw.github.../addressescsv.csv](https://raw.githubusercontent.com/cmliu/WorkerVless2sub/main/addressescsv.csv)                                            | ❌         | نتایج تست سرعت iptest (پشتیبانی از عناصر متعدد، با فواصل بین عناصر)                                                                                                                                                                                        |                                                              |
| DLS               | `8`                                                                                                                                                                | ❌         | `ADDCSV`ADDCSV نتیجه اندازه‌گیری سرعت با محدودیت سرعت پایین‌تر مطابقت دارد                                                                                                                                                                                 |                                                              |
| TGTOKEN           | `6894123456:XXXXXXXXXX0qExVsBPUhHDAbXXX`                                                                                                                           | ❌         | توکن ربات برای ارسال اعلان های TG                                                                                                                                                                                                                          |                                                              |
| شما انجام می دهید | `6946912345`                                                                                                                                                       | ❌         | شناسه دیجیتالی حسابی که اعلان‌های TG را دریافت می‌کند                                                                                                                                                                                                      |                                                              |
| زیر               | `VLESS.fxxk.dedyn.io`                                                                                                                                              | ❌         | آدرس مولد اشتراک نام دامنه داخلی و اطلاعات گره IP                                                                                                                                                                                                          | [ویدئو](https://www.youtube.com/watch?v=s91zjpw3-P8&t=1193s) |
| SUBAPI            | `SUBAPI.fxxk.dedyn.io`                                                                                                                                             | ❌         | باطن های تبدیل اشتراک مانند کلش، singbox و غیره.                                                                                                                                                                                                           | [ویدئو](https://www.youtube.com/watch?v=s91zjpw3-P8&t=1446s) |
| SUBCONFIG         | [https://raw.github.../ACL4SSR_Online_Full_MultiMode.ini](https://raw.githubusercontent.com/ACL4SSR/ACL4SSR/master/Clash/config/ACL4SSR_Online_Mini_MultiMode.ini) | ❌         | فایل های پیکربندی تبدیل اشتراک برای کلش، singbox و غیره.                                                                                                                                                                                                   | [ویدئو](https://www.youtube.com/watch?v=s91zjpw3-P8&t=1605s) |
| RPROXYIP          | `false`                                                                                                                                                            | ❌         | برای اجبار به دستیابی ProxyIP اختصاص داده شده توسط مشترک روی true تنظیم کنید (پشتیبانی مشترک مورد نیاز است))                                                                                                                                               | [ویدئو](https://www.youtube.com/watch?v=s91zjpw3-P8&t=1816s) |
| CFEMAIL           | `admin@gmail.com`                                                                                                                                                  | ❌         | آدرس ایمیل حساب CF (CFKEYپس از پر کردن هر دو، اطلاعات اشتراک میزان استفاده درخواستی را نشان می دهد، بنابراین افراد تازه کار نباید از این مورد استفاده کنند)                                                                                                |                                                              |
| CFKEY             | `c6a944b5c956b6c18c2352880952bced8b85e`                                                                                                                            | ❌         | کلید جهانی API حساب CF (CFEMAIL پس از پر کردن هر دو، اطلاعات اشتراک میزان استفاده درخواستی را نشان می دهد، بنابراین افراد تازه کار نباید از این مورد استفاده کنند)                                                                                         |                                                              |

![rainbow](https://github.com/NiREvil/vless/assets/126243832/1aca7f5d-6495-44b7-aced-072bae52f256)

```url
- Note: fill in `SOCKS5` will no longer be enabled `PROXYIP` ！Please choose one of the two！！

- Note: fill in `SUB` will no longer be enabled `ADD` Subscription content generated by class variables! Please choose one of the two to use ！！

- Note: fill in `CFEMAIL` and` CFKEY` Display request usage will be enabled, but it is not recommended! No need to give 一个Worker The project has such high permissions! You are responsible for the consequences ！！！
```

## نکات کاربردی

**اشتراک های مستقر شده توسط این پروژه را می توان به سرعت با اضافه کردن جایگزین کرد`sub`مقدار کلیدی برای تولید کننده اشتراک ترجیحی!**

> به عنوان مثال`https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10`آدرس اشتراک تطبیقی ​​جهانی شما است

-   به سرعت مشترک را تغییر دهید`VLESS.fxxk.dedyn.io`آدرس اشتراک

    ```url
    https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?sub=VLESS.fxxk.dedyn.io
    ```

**گره های مستقر شده توسط این پروژه از طریق گره PATH (مسیر) قابل دسترسی هستند. از مسیر مشخص شده استفاده کنید`PROXYIP`یا`SOCKS5`！！！**

-   تعیین`PROXYIP`مورد
    ```url
    /proxyip=proxyip.fxxk.dedyn.io
    /?proxyip=proxyip.fxxk.dedyn.io
    /proxyip.fxxk.dedyn.io (Only domain names starting with 'proxyip.' domain name)
    ```

-   تعیین`SOCKS5`مورد
    ```url
    /socks5=user:password@127.0.0.1:1080
    /?socks5=user:password@127.0.0.1:1080
    /socks://dXNlcjpwYXNzd29yZA==@127.0.0.1:1080
    /socks5://user:password@127.0.0.1:1080
    ```

## محتوای اشتراک تطبیقی ​​تطبیقی

-   [نیک](https://github.com/mahsanet/NikaNG/releases)
-   [NekoBox برای اندروید](https://github.com/Matsuridayo/NekoBoxForAndroid/releases)
-   [MahsaNG](https://github.com/GFW-knocker/MahsaNG/releases)
-   [Hiddify](https://github.com/hiddify/hiddify-next/releases)
-   [v2rayN](https://github.com/2dust/v2rayN)
-   clash.meta ([clash-verge-rev](https://github.com/clash-verge-rev/clash-verge-rev)
-   sing-box (SFI)

# سپاسگزار

[zizifn](https://github.com/zizifn/edgetunnel)、[بیا](https://github.com/cmliu/edgetunnel),[آن را استریل کنید](https://github.com/3Kmfi6HP/EDtunnel)、[استنلی عزیزم](https://github.com/Stanley-baby)、[ACL4SSR](https://github.com/ACL4SSR/ACL4SSR/tree/master/Clash/config)、[Shegs1999](https://github.com/SHIJS1999/cloudflare-worker-vless-ip)、<a href="https://alice.ws/aff.php?aff=15"><img src="https://alicenetworks.net/templates/lagom2/assets/img/logo/logo_big.194980063.png" width="150" height="75" alt="Alice Networks LTD"/></a>、
