# Cloudflare Worker 2 V'siz ve Alt

🇮🇷[Farsça](README.fa.md)

🇹🇷[Türkçe](README.tr.md)

🇬🇧[İngilizce](README.MD)

🇨🇳[Çince](README.zh-CN.md)

Bu, Cloudflare Worker platformunu temel alan bir komut dosyasıdır. Orijinal sürüme dayanarak, VLESS yapılandırma bilgilerini görüntüleyecek ve abonelik içeriğine dönüştürecek şekilde değiştirildi. Bu betiği kullanarak VLESS yapılandırma bilgilerini çevrimiçi yapılandırmayı kullanarak Clash veya Singbox gibi araçlara kolayca dönüştürebilirsiniz.

-   Temel dağıtım video eğitimi:<https://www.youtube.com/watch?v=LeT4jQUh8ok>
-   Hızlı dağıtım video eğitimi:<https://www.youtube.com/watch?v=59THrmJhmAw>**_En iyi öneri!!!_**
-   Perspektifi kullanma konusunda ileri düzey eğitim:<https://www.youtube.com/watch?v=s91zjpw3-P8>

Telegram iletişim grubu:[@CMLiussss](https://t.me/CMLiussss)

## risk uyarısı

-   Abonelik hizmetine yanlış düğüm yapılandırmaları göndererek düğüm yapılandırma bilgilerinin sızmasını önleyin.
-   Alternatif olarak, kendiniz dağıtmayı da seçebilirsiniz[WorkerVless2sub Abonelik Oluşturma Hizmeti](https://github.com/cmliu/WorkerVless2sub)Böylece abonelik oluşturucunun avantajlarından yararlanabilirsiniz.

## İşçi dağıtım yöntemi[Video eğitimi](https://www.youtube.com/watch?v=LeT4jQUh8ok&t=83s)

1.  Cloudflare Worker'ı dağıtın:
    -   Cloudflare Worker konsolunda yeni bir Worker oluşturun.
    -   İrade[işçi.js](https://github.com/cmliu/edgetunnel/blob/main/_worker.js)İçeriği Worker düzenleyicisine yapıştırın.
    -   7\. satırı değiştir`userID`Kendinize göre değiştirin**UUID**。

2.  Abonelik içeriğine erişin:
    -   erişim`https://[YOUR-WORKERS-URL]/[UUID]`Abonelik içeriği mevcuttur.
    -   Örneğin abonelik bağlantınız şöyle olacaktır:`https://vless.google.workers.dev/90cd4a77-141a-43c9-991b-08263cfe9c10`Bu sizin evrensel uyarlanabilir abonelik adresinizdir.
    -   Base64 abonelik formatı:`https://vless.google.workers.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?sub`PassWall, SSR+ vb. için uygundur.
    -   Clash abonelik biçimi`https://vless.google.workers.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?clash`OpenClash vb. için uygundur.
    -   şarkı kutusu abonelik formatı`https://vless.google.workers.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?sb`şarkı kutusu vb. için uygundur.

3.  Çalışanlara özel bir alan adı bağlayın:
    -   İşçi konsolunda`trigger`sekme, aşağıya tıklayın`Add a custom domain`。
    -   CloudFlare alan adı çözümleme hizmetine aktardığınız ikincil alan adını girin, örneğin:`vless.google.com`Tıkladıktan sonra`Add a custom domain`, sertifikanın geçerli olmasını bekleyin.
    -   **Eğer acemiyseniz, daha fazla bakmanıza gerek kalmadan hemen şimdi yola çıkabilirsiniz! ! !**

<details>
<summary><code><strong>「 I'm not a newbie! I'm really, really not a newbie! I want to try some tricks! I want to start playing with advanced techniques! 」</strong></code></summary>

4.  kendininkini kullan`Preferred domain name`/`BestIP`Şunun için abonelikler:
    -   Kendi tercih ettiğiniz alan adını veya kendi tercih ettiğiniz IP'yi kullanmak istiyorsanız, şu adrese başvurabilirsiniz:[WorkerVless2sub GitHub deposu](https://github.com/cmliu/WorkerVless2sub).txt dosyasındaki dağıtım talimatlarına göre kendiniz oluşturun.
    -   Açık[işçi.js](https://github.com/cmliu/edgetunnel/blob/main/_worker.js)dosya, 12. satırda bulundu`sub`değişkeni seçin ve bunu dağıtılan abonelik oluşturucunuzun adresine göre değiştirin. Örneğin`let sub = 'sub.cmliussss.workers.dev';`, https gibi protokol bilgilerini ve simgeleri eklememeye dikkat edin.
    -   Kendi abonelik adresinizi kullanırsanız abonelik oluşturucunun`sub`alan adı ve`[YOUR-WORKER-URL]`Alan adı aynı üst düzey alan adına ait değil, aksi takdirde bir istisna oluşacaktır. Yapabilirsiniz`sub`Değişkene,workers.dev'e atanan alan adı atanır.

</details>

## Sayfa yükleme dağıtım yöntemi**En iyi öneri!!!**[Video eğitimi](https://www.youtube.com/watch?v=59THrmJhmAw)

1.  Cloudflare Sayfalarını Dağıtın:
    -   indirmek[worker.zip](https://raw.githubusercontent.com/cmliu/edgetunnel/main/worker.zip)dosyanızı açın ve Yıldız'a tıklayın!!!
    -   Cloudflare Sayfaları konsolunda seçin`Upload assets`Son olarak projenize bir isim verin ve tıklayın.`Create a project`ve ardından indirilenleri yükleyin[worker.zip](https://raw.githubusercontent.com/cmliu/edgetunnel/main/worker.zip)Dosyadan sonra tıklayın`Deployment Site`。
    -   Dağıtım tamamlandıktan sonra tıklayın`Continue processing site`Bundan sonra seçin`set up`>`Environment variables`>**yapmak**Üretim için değişkenleri tanımlayın >`Add variables`.
        Değişken adını girin**UUID**değer UUID'nizdir, ardından tıklayın`keep`İşte bu.
    -   geri dönmek`Deploy`sekmesinde sağ alt köşedeki simgesine tıklayın`Create a New Deployment`Daha sonra yeniden yükleyin[worker.zip](https://raw.githubusercontent.com/cmliu/edgetunnel/main/worker.zip)Dosyadan sonra tıklayın`Save and deploy`İşte bu.

2.  Abonelik içeriğine erişin:
    -   erişim`https://[YOUR-PAGES-URL]/[YOUR-UUID]`Abonelik içeriği mevcuttur.
    -   Örneğin abonelik bağlantınız şöyle olacaktır:`https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10`Bu sizin evrensel uyarlanabilir abonelik adresinizdir.
    -   Base64 abonelik formatı:`https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?sub`PassWall, SSR+ vb. için uygundur.
    -   Clash abonelik formatı:`https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?clash`OpenClash vb. için uygundur.
    -   şarkı kutusu abonelik formatı`https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?sb`şarkı kutusu vb. için uygundur.

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

## Sayfalar GitHub dağıtım yöntemi[Video eğitimi](https://www.youtube.com/watch?v=LeT4jQUh8ok&t=560s)

1.  Cloudflare Sayfalarını Dağıtın:
    -   Bu projeyi Github'da çatallayın ve Yıldız'a tıklayın!!!
    -   Cloudflare Sayfaları konsolunda seçin`连接到 Git`Bundan sonra seçin`edgetunnel`Öğeden sonra tıklayın`开始设置`。
    -   var olmak`设置构建和部署`Sayfanın alt kısmında`环境变量（高级）`daha sonra birleştir`添加变量`Değişken adını girin**UUID**değer UUID'nizdir, ardından tıklayın`保存并部署`İşte bu.

2.  Abonelik içeriğine erişin:
    -   erişim`https://[YOUR-PAGES-URL]/[YOUR-UUID]`Abonelik içeriği mevcuttur.
    -   Örneğin`https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10`Bu sizin evrensel uyarlanabilir abonelik adresinizdir.
    -   Örneğin`https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?sub`Base64 abonelik formatı; PassWall, SSR+ vb. için uygundur.
    -   Örneğin`https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?clash`OpenClash vb. için uygun Clash abonelik formatı.
    -   Örneğin`https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?sb`singbox abonelik formatı, singbox vb. için uygundur.

3.  CNAME özel alan adını Sayfalara bağlayın:[Video eğitimi](https://www.youtube.com/watch?v=LeT4jQUh8ok&t=851s)
    -   Sayfalar konsolunda`自定义域`sekme, aşağıya tıklayın`设置自定义域`。
    -   Özel ikincil alan adınızı girin, kök alan adınızı kullanmamaya dikkat edin, örneğin:
        Size atanan alan adı`fuck.cloudns.biz`, ardından doldurulacak özel bir alan ekleyin`lizi.fuck.cloudns.biz`İşte bu kadar;
    -   Cloudflare gereksinimlerine göre alan adı DNS servis sağlayıcınız iade edilecek ve özel alan adı eklenecektir.`lizi`CNAME kaydı`edgetunnel.pages.dev`Bundan sonra tıklayın`激活域`İşte bu.
    -   **Eğer acemiyseniz, sayfalarınız bağlayıcıdır`自定义域`Bundan sonra doğrudan yola çıkabilirsiniz, daha fazla bakmanıza gerek yok! ! !**

<details>
<summary><code><strong>「 我不是小白！我真的真的不是小白！我要玩花活！我要开启高端玩法！ 」</strong></code></summary>

4.  kendininkini kullan`优选域名`/`优选IP`Şunun için abonelikler:
    -   Kendi tercih ettiğiniz alan adını veya kendi tercih ettiğiniz IP'yi kullanmak istiyorsanız, şu adrese başvurabilirsiniz:[WorkerVless2sub GitHub deposu](https://github.com/cmliu/WorkerVless2sub).txt dosyasındaki dağıtım talimatlarına göre kendiniz oluşturun.
    -   Sayfalar konsolunda`设置`sekme, seç`环境变量`>`制作`>`编辑变量`>`添加变量`；
    -   Değişken adı şu şekilde ayarlandı:`SUB`karşılık gelen değer, dağıttığınız abonelik oluşturucunun adresidir. Örneğin`sub.cmliussss.workers.dev`, ardından tıklayın**kale**。
    -   Daha sonra Sayfalar konsolunda`部署`sekme, seç`所有部署`>`最新部署最右的 ...`>`重试部署`, işte bu.
    -   Kendi abonelik adresinizi kullanırsanız abonelik oluşturucunun`SUB`alan adı ve`[YOUR-PAGES-URL]`Alan adı aynı üst düzey alan adına ait değil, aksi takdirde bir istisna oluşacaktır. Yapabilirsiniz`SUB`Değişkene Pages.dev'e atanan alan adı atanır.

</details>

### Değişken açıklaması

| değişken adı     | Örnek                                                                                                                                                          | Açıklama                                                                                                                                                                           | YT                                                           |
| ---------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------ |
| UUID             | 90SD4AH-141A-43SS-991B-08263SVISES10                                                                                                                           | Powershell -Çıkış Yok -Komut "[rehber]&#x3A;:YeniGuid()"                                                                                                                           | [Video](https://www.youtube.com/watch?v=s91zjpw3-P8&t=72s)   |
| PROXYIP          | proxyip.fxxk.dedyn.io                                                                                                                                          | CloudFlareCDN sitesine erişim için proxy düğümü olarak alternatif (ProxyIP'ler arasında kullanılan birden fazla ProxyIP'yi destekler)`,`veya aralık olarak satır besleme)          | [Video](https://www.youtube.com/watch?v=s91zjpw3-P8&t=166s)  |
| ÇORAP5           | kullanıcı:[password@127.0.0.1](mailto:password@127.0.0.1):1080                                                                                                 | CloudFlareCDN sitelerine erişim için SOCKS5 proxy'si olarak tercih edilir                                                                                                          | [Video](https://www.youtube.com/watch?v=s91zjpw3-P8&t=826s)  |
| ALT              | sub.cmliussss.workers.dev                                                                                                                                      | Yerleşik alan adı ve IP düğümü bilgileriyle birlikte abonelik oluşturucu adresi                                                                                                    | [Video](https://www.youtube.com/watch?v=s91zjpw3-P8&t=1193s) |
| subapi           | api.v1.mk                                                                                                                                                      | Clash, singbox vb. abonelik dönüşümü arka ucu                                                                                                                                      | [Video](https://www.youtube.com/watch?v=s91zjpw3-P8&t=1446s) |
| ALT YAPILANDIRMA | [https://raw.github.../ACL4SSR_Online_Full_MultiMode.ini](https://raw.githubusercontent.com/cmliu/ACL4SSR/main/Clash/config/ACL4SSR_Online_Full_MultiMode.ini) | Clash, singbox vb. Abonelik dönüşüm profili                                                                                                                                        | [Video](https://www.youtube.com/watch?v=s91zjpw3-P8&t=1605s) |
| RPROXYIP         | YANLIŞ                                                                                                                                                         | Abone tarafından atanan ProxyIP'nin alınmasını zorlamak için true olarak ayarlayın (abone desteği gerektirir)                                                                      | [Video](https://www.youtube.com/watch?v=s91zjpw3-P8&t=1816s) |
| 02               | <https://t.me/CMLiussss>                                                                                                                                       | Ana sayfa 302 atlaması (URL'ler arasında kullanılan birden fazla URL'yi destekler)`,`Veya satır beslemeyi aralayıcı olarak kullanın, eğer bu konuda yeniyseniz kullanmayın)        |                                                              |
| URL'si           | <https://t.me/CMLiussss>                                                                                                                                       | Ana sayfa gizleme (URL'ler arasında kullanılan birden fazla URL'yi destekler)`,`Veya aralıklı satır kesintileri, rastgele ayarlar dolandırıcılığı önlemeyi kolayca tetikleyebilir) |                                                              |

## Yıldız yıldızlar yükseliyor

[![Stargazers over time](https://starchart.cc/cmliu/edgetunnel.svg?variant=adaptive)](https://starchart.cc/cmliu/edgetunnel)

## Uyarlanmış uyarlanabilir abonelik içeriği

-   [v2rayN](https://github.com/2dust/v2rayN)
-   Clash.meta（[çatışma eşiğinde devrim](https://github.com/clash-verge-rev/clash-verge-rev)，[Nyanpasu'da çatışma](https://github.com/keiko233/clash-nyanpasu)，~[çatışma eşiği](https://github.com/zzzgydi/clash-verge/tree/main)~，ClashX Metası）
-   şarkı kutusu (SFI)

# minnettar

[zizifn](https://github.com/zizifn/edgetunnel)、[Sterilize et](https://github.com/3Kmfi6HP/EDtunnel)、[Stanley-bebek](https://github.com/Stanley-baby)、[ACL4SSR](https://github.com/ACL4SSR/ACL4SSR/tree/master/Clash/config)、[Shegs1999](https://github.com/SHIJS1999/cloudflare-worker-vless-ip)
