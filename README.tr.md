# Cloudflare Worker 2 V'siz ve Alt

![rainbow](https://github.com/NiREvil/vless/assets/126243832/1aca7f5d-6495-44b7-aced-072bae52f256)

🇮🇷[Farsça](README.fa.md)

🇹🇷[Türkçe](README.tr.md)

🇬🇧[İngilizce](README.MD)

🇨🇳[Çince](README.zh-CN.md)

Bu, Cloudflare Worker platformunu temel alan bir komut dosyasıdır. Orijinal sürüme dayanarak, VLESS yapılandırma bilgilerini görüntüleyecek ve abonelik içeriğine dönüştürecek şekilde değiştirildi. Bu betiği kullanarak VLESS yapılandırma bilgilerini çevrimiçi yapılandırmayı kullanarak Clash veya Singbox gibi araçlara kolayca dönüştürebilirsiniz.

-   [Temel dağıtım video eğitimi](https://www.youtube.com/watch?v=LeT4jQUh8ok)
-   [Hızlı dağıtım video eğitimi](https://www.youtube.com/watch?v=59THrmJhmAw)**En iyi öneri!!!**
-   [Perspektifi kullanma konusunda ileri düzey eğitim](https://www.youtube.com/watch?v=s91zjpw3-P8)

[Telegram iletişim grubu](https://t.me/CMLiussss)

## risk uyarısı

-   Abonelik hizmetine yanlış düğüm yapılandırmaları göndererek düğüm yapılandırma bilgilerinin sızmasını önleyin.
-   Alternatif olarak, kendiniz dağıtmayı da seçebilirsiniz[WorkerVless2sub Abonelik Oluşturma Hizmeti](https://github.com/cmliu/WorkerVless2sub)Böylece abonelik oluşturucunun avantajlarından yararlanabilirsiniz.

![rainbow](https://github.com/NiREvil/vless/assets/126243832/1aca7f5d-6495-44b7-aced-072bae52f256)

## İşçi dağıtım yöntemi

[Video eğitimi](https://www.youtube.com/watch?v=LeT4jQUh8ok&t=83s)

1.  Cloudflare Worker'ı dağıtın:
    -   Cloudflare Worker konsolunda yeni bir Worker oluşturun.
    -   İrade[işçi.js](https://github.com/cmliu/edgetunnel/blob/main/_worker.js)İçeriği Worker düzenleyicisine yapıştırın.
    -   11\. satırı değiştir`userID`Kendinize göre değiştirin**UUID**。

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
<summary><code><strong>「I'm really, really not a newbie! I want to try some tricks! I want to start playing with advanced techniques! 」</strong></code></summary>

4.  kendininkini kullan`Preferred domain name`/`BestIP`Şunun için abonelikler:
    -   Kendi tercih ettiğiniz alan adını veya kendi tercih ettiğiniz IP'yi kullanmak istiyorsanız, şu adrese başvurabilirsiniz:[WorkerVless2sub GitHub deposu](https://github.com/cmliu/WorkerVless2sub)içindeki dağıtım talimatlarına göre kendiniz oluşturun.
    -   Açık[işçi.js](https://github.com/cmliu/edgetunnel/blob/main/_worker.js)dosya, 16. satırda bulundu`sub`değişkeni seçin ve konuşlandırılan abonelik oluşturucunuzun adresine göre değiştirin. Örneğin`let sub = 'sub.cmliussss.workers.dev';`, https gibi protokol bilgilerini ve simgeleri eklememeye dikkat edin.
    -   Kendi abonelik adresinizi kullanırsanız abonelik oluşturucunun`sub`alan adı ve`[YOUR-WORKER-URL]`Alan adı aynı üst düzey alan adına ait değil, aksi takdirde bir istisna oluşacaktır. Yapabilirsiniz`sub`Değişkene,workers.dev'e atanan alan adı atanır.

</details>

![rainbow](https://github.com/NiREvil/vless/assets/126243832/1aca7f5d-6495-44b7-aced-072bae52f256)

## Sayfa yükleme dağıtım yöntemi**En iyi öneri!!!**

[Video eğitimi](https://www.youtube.com/watch?v=59THrmJhmAw)

1.  Cloudflare Sayfalarını Dağıtın:
    -   indirmek[worker.zip](https://raw.githubusercontent.com/NiREvil/edgetunnel/main/worker.zip)dosyanızı açın ve Yıldız'a tıklayın!!!
    -   Cloudflare Sayfaları konsolunda seçin`Upload assets`Son olarak projenize bir isim verin ve tıklayın.`Create a project`ve ardından indirilenleri yükleyin[worker.zip](https://raw.githubusercontent.com/NiREvil/edgetunnel/main/worker.zip)Dosyadan sonra tıklayın`Deployment Site`.
    -   Dağıtım tamamlandıktan sonra tıklayın`Continue processing site`Bundan sonra seçin`set up`>`Environment variables`>**yapmak**Üretim için değişkenleri tanımlayın >`Add variables`, Değişken adını girin**UUID**değer UUID'nizdir, ardından tıklayın`keep`İşte bu.
    -   geri dönmek`Deploy`sekmesinde sağ alt köşedeki simgesine tıklayın`Create a New Deployment`Daha sonra yeniden yükleyin[worker.zip](https://raw.githubusercontent.com/cmliu/edgetunnel/main/worker.zip)Dosyadan sonra tıklayın`Save and deploy`İşte bu.

2.  Abonelik içeriğine erişin:
    -   erişim`https://[YOUR-PAGES-URL]/[YOUR-UUID]`Abonelik içeriği mevcuttur.
    -   Örneğin abonelik bağlantınız şöyle olacaktır:`https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10`Bu sizin evrensel uyarlanabilir abonelik adresinizdir.
    -   Base64 abonelik formatı:`https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?sub`PassWall, SSR+ vb. için uygundur.
    -   Clash abonelik formatı:`https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?clash`OpenClash vb. için uygundur.
    -   şarkı kutusu abonelik formatı`https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?sb`şarkı kutusu vb. için uygundur.

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

## Sayfalar GitHub dağıtım yöntemi.

[Video eğitimi](https://www.youtube.com/watch?v=LeT4jQUh8ok&t=560s)

1.  Cloudflare Sayfalarını Dağıtın:
    -   Bu projeyi Github'da çatallayın ve Yıldız'a tıklayın!!!
    -   Cloudflare Sayfaları konsolunda seçin`Connect to Git`Bundan sonra seçin`edgetunnel`Öğeden sonra tıklayın`Start setting up`.
    -   var olmak`Setting up build and deployment`Sayfanın alt kısmında`Environment variables (advanced)`daha sonra birleştir`Add variables`Değişken adını girin**UUID**değer UUID'nizdir, ardından tıklayın`Save and deploy`İşte bu.

2.  Abonelik içeriğine erişin:
    -   erişim`https://[YOUR-PAGES-URL]/[YOUR-UUID]`Abonelik içeriği mevcuttur.
    -   Örneğin`https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10`Bu sizin evrensel uyarlanabilir abonelik adresinizdir.
    -   Örneğin`https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?sub`Base64 abonelik formatı; PassWall, SSR+ vb. için uygundur.
    -   Örneğin`https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?clash`OpenClash vb. için uygun Clash abonelik formatı.
    -   Örneğin`https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?sb`singbox abonelik formatı, singbox vb. için uygundur.

3.  CNAME özel alan adını Sayfalara bağlayın:[Video eğitimi](https://www.youtube.com/watch?v=LeT4jQUh8ok&t=851s)
    -   Sayfalar konsolunda`custom domain`sekme, aşağıya tıklayın`Set up a custom domain`。
    -   Özel ikincil alan adınızı girin, kök alan adınızı kullanmamaya dikkat edin, örneğin:
        Size atanan alan adı`fuck.cloudns.biz`, ardından doldurulacak özel bir alan ekleyin`lizi.fuck.cloudns.biz`İşte bu;
    -   Cloudflare gereksinimlerine göre alan adı DNS servis sağlayıcınız iade edilecek ve özel alan adı eklenecektir.`lizi`CNAME kaydı`edgetunnel.pages.dev`Bundan sonra tıklayın`Activate Domain`İşte bu.
    -   **Eğer acemiyseniz, sayfalarınız bağlayıcıdır`Custom domains`Bundan sonra doğrudan yola çıkabilirsiniz, daha fazla bakmanıza gerek yok! ! !**

<details>
<summary><code><strong>「 I'm not a novice! I'm really not a novice！I want to play tricks! I want to start high-end gameplay！ 」</strong></code></summary>

4.  kendininkini kullan`Preferred domain name / Preferred IP`Şunun için abonelikler:
    -   Kendi tercih ettiğiniz alan adını veya kendi tercih ettiğiniz IP'yi kullanmak istiyorsanız, şu adrese başvurabilirsiniz:[WorkerVless2sub GitHub deposu](https://github.com/cmliu/WorkerVless2sub)içindeki dağıtım talimatlarına göre kendiniz oluşturun.
    -   Sayfalar konsolunda`set up`sekme, seç`set up`>`make`>`Edit variables`>`add variable`；
    -   Değişken adı şu şekilde ayarlandı:`SUB`karşılık gelen değer, dağıttığınız abonelik oluşturucunun adresidir. Örneğin`sub.cmliussss.workers.dev`, ardından tıklayın**kale**。
    -   Daha sonra Sayfalar konsolunda`deploy`sekme, seç`All deployments`>`The latest deployment is the rightmost ...`>`Retry deployment`, işte bu.
    -   Kendi abonelik adresinizi kullanırsanız abonelik oluşturucunun`SUB`alan adı ve`[YOUR-PAGES-URL]`Alan adı aynı üst düzey alan adına ait değil, aksi takdirde bir istisna oluşacaktır. Yapabilirsiniz`SUB`Değişkene Pages.dev'e atanan alan adı atanır.

</details>

![rainbow](https://github.com/NiREvil/vless/assets/126243832/1aca7f5d-6495-44b7-aced-072bae52f256)

## Değişken açıklaması

| Değişken Adı     | Örnek                                                                                                                                                              | Gerekli | Açıklama                                                                                                                                                                                                                                                                             | YouTube                                                      |
| ---------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------ |
| UUID             | `90cd4a77-141a-43c9-991b-08263cfe9c10`                                                                                                                             | ✅       | Kendi UUID'nizi nasıl oluşturabilirsiniz:<https://www.uuidgenerator.net/>                                                                                                                                                                                                            | [Video](https://www.youtube.com/watch?v=s91zjpw3-P8&t=72s)   |
| PROXYIP          | `bpb.radically.pro`                                                                                                                                                | ✅       | CloudFlareCDN sitesine erişim için bir proxy düğümü olarak alternatif (ProxyIP'ler arasında kullanılan birden fazla ProxyIP'yi veya aralık olarak satır beslemeyi destekler).[BURAYA ZİYARET EDİN](https://github.com/NiREvil/vless/blob/main/sub/ProxyIP.md)ProxyIP'yi bulmak için. | [Video](https://www.youtube.com/watch?v=s91zjpw3-P8&t=166s)  |
| ÇORAP5           | `user:password@127.0.0.1:1080`                                                                                                                                     | ❌       | CFCDN sitelerine erişim için SOCKS5 proxy olarak öncelik verin                                                                                                                                                                                                                       | [Video](https://www.youtube.com/watch?v=s91zjpw3-P8&t=826s)  |
| EKLEMEK          | `zula.ir:2053#preferred name`                                                                                                                                      | ❌       | Yerel tercih edilen TLS alan adı/tercih edilen IP (birden fazla öğeyi veya ayırıcı olarak satır sonlarını destekler)                                                                                                                                                                 |                                                              |
| EKLEMEK          | [https://raw.github.../addressesapi.txt](https://raw.githubusercontent.com/NiREvil/edgetunnel/main/addressesapi.txt)                                               | ❌       | Tercih edilen IP'nin API adresi (birden fazla öğeyi veya boşluk olarak satır sonlarını destekler)                                                                                                                                                                                    |                                                              |
| EK NOTLAR        | `zula.ir:8080#preferred name`                                                                                                                                      | ❌       | ocal tercih edilen noTLS alan adı/tercih edilen IP (birden fazla öğeyi veya ayırıcı olarak satır sonlarını destekler)                                                                                                                                                                |                                                              |
| ADDNOTLSAPI      | [https://raw.github.../addressesapi.txt](https://raw.githubusercontent.com/cmliu/CFcdnVmess2sub/main/addressesapi.txt)                                             | ❌       | Tercih edilen IP'nin API adresi (birden fazla öğeyi veya boşluk olarak satır sonlarını destekler)                                                                                                                                                                                    |                                                              |
| ADCCSV           | [https://raw.github.../addressescsv.csv](https://raw.githubusercontent.com/cmliu/WorkerVless2sub/main/addressescsv.csv)                                            | ❌       | iptest hız testi sonuçları (öğeler arasında aralıklar bulunan birden fazla öğeyi destekler)                                                                                                                                                                                          |                                                              |
| DLS              | `8`                                                                                                                                                                | ❌       | `ADDCSV`ADDCSVHız ölçüm sonucu alt hız sınırını karşılıyor                                                                                                                                                                                                                           |                                                              |
| TGTOKEN          | `6894123456:XXXXXXXXXX0qExVsBPUhHDAbXXX`                                                                                                                           | ❌       | TG bildirimlerini göndermek için robot belirteci                                                                                                                                                                                                                                     |                                                              |
| SİZ YAPIYORSUNUZ | `6946912345`                                                                                                                                                       | ❌       | TG bildirimlerini alan hesabın dijital kimliği                                                                                                                                                                                                                                       |                                                              |
| ALT              | `VLESS.fxxk.dedyn.io`                                                                                                                                              | ❌       | Yerleşik alan adının abonelik oluşturucu adresi ve IP düğümü bilgileri                                                                                                                                                                                                               | [Video](https://www.youtube.com/watch?v=s91zjpw3-P8&t=1193s) |
| SUBAPI           | `SUBAPI.fxxk.dedyn.io`                                                                                                                                             | ❌       | Clash, singbox vb. gibi abonelik dönüşümü arka uçları.                                                                                                                                                                                                                               | [Video](https://www.youtube.com/watch?v=s91zjpw3-P8&t=1446s) |
| ALT YAPILANDIRMA | [https://raw.github.../ACL4SSR_Online_Full_MultiMode.ini](https://raw.githubusercontent.com/ACL4SSR/ACL4SSR/master/Clash/config/ACL4SSR_Online_Mini_MultiMode.ini) | ❌       | Clash, singbox vb. için abonelik dönüştürme yapılandırma dosyaları.                                                                                                                                                                                                                  | [Video](https://www.youtube.com/watch?v=s91zjpw3-P8&t=1605s) |
| RPROXYIP         | `false`                                                                                                                                                            | ❌       | Abone tarafından atanan ProxyIP'nin alınmasını zorlamak için true olarak ayarlayın (abone desteği gereklidir))                                                                                                                                                                       | [Video](https://www.youtube.com/watch?v=s91zjpw3-P8&t=1816s) |
| CFEMAIL          | `admin@gmail.com`                                                                                                                                                  | ❌       | CF hesabı e-posta adresi (CFKEYHer ikisini de doldurduktan sonra abonelik bilgileri istenen kullanımı gösterecektir, dolayısıyla yeni başlayanlar bunu kullanmamalıdır)                                                                                                              |                                                              |
| CFKEY            | `c6a944b5c956b6c18c2352880952bced8b85e`                                                                                                                            | ❌       | CF hesabı Global API Anahtarı ( CFEMAILher ikisini de doldurduktan sonra abonelik bilgileri istenen kullanımı gösterecektir, dolayısıyla yeni başlayanlar bunu kullanmamalıdır)                                                                                                      |                                                              |

![rainbow](https://github.com/NiREvil/vless/assets/126243832/1aca7f5d-6495-44b7-aced-072bae52f256)

```url
- Note: fill in `SOCKS5` will no longer be enabled `PROXYIP` ！Please choose one of the two！！

- Note: fill in `SUB` will no longer be enabled `ADD` Subscription content generated by class variables! Please choose one of the two to use ！！

- Note: fill in `CFEMAIL` and` CFKEY` Display request usage will be enabled, but it is not recommended! No need to give 一个Worker The project has such high permissions! You are responsible for the consequences ！！！
```

## Pratik ipuçları

**Bu proje tarafından dağıtılan abonelikler, aşağıdakilerin eklenmesiyle hızlı bir şekilde değiştirilebilir:`sub`tercih edilen abonelik oluşturucunun anahtar değeri！**

> Örneğin`https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10`evrensel uyarlanabilir abonelik adresinizdir

-   Aboneyi hızla değiştirin`VLESS.fxxk.dedyn.io`Abonelik adresi

    ```url
    https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?sub=VLESS.fxxk.dedyn.io
    ```

**Bu proje tarafından dağıtılan düğümlere PATH (yol) düğümü aracılığıyla erişilebilir, Belirtilen yolu kullanın`PROXYIP`Veya`SOCKS5`！！！**

-   atama`PROXYIP`Dava
    ```url
    /proxyip=proxyip.fxxk.dedyn.io
    /?proxyip=proxyip.fxxk.dedyn.io
    /proxyip.fxxk.dedyn.io (Only domain names starting with 'proxyip.' domain name)
    ```

-   atama`SOCKS5`Dava
    ```url
    /socks5=user:password@127.0.0.1:1080
    /?socks5=user:password@127.0.0.1:1080
    /socks://dXNlcjpwYXNzd29yZA==@127.0.0.1:1080
    /socks5://user:password@127.0.0.1:1080
    ```

## Uyarlanmış uyarlanabilir abonelik içeriği

-   [Nick](https://github.com/mahsanet/NikaNG/releases)
-   [Android için NekoBox](https://github.com/Matsuridayo/NekoBoxForAndroid/releases)
-   [MahsaNG](https://github.com/GFW-knocker/MahsaNG/releases)
-   [Hiddify](https://github.com/hiddify/hiddify-next/releases)
-   [v2rayN](https://github.com/2dust/v2rayN)
-   Clash.meta（[çatışma eşiğinde devrim](https://github.com/clash-verge-rev/clash-verge-rev)
-   şarkı kutusu (SFI)

# minnettar

[zizifn](https://github.com/zizifn/edgetunnel)、[Hadi](https://github.com/cmliu/edgetunnel),[Sterilize et](https://github.com/3Kmfi6HP/EDtunnel)、[Stanley-bebek](https://github.com/Stanley-baby)、[ACL4SSR](https://github.com/ACL4SSR/ACL4SSR/tree/master/Clash/config)、[Shegs1999](https://github.com/SHIJS1999/cloudflare-worker-vless-ip)、<a href="https://alice.ws/aff.php?aff=15"><img src="https://alicenetworks.net/templates/lagom2/assets/img/logo/logo_big.194980063.png" width="150" height="75" alt="Alice Networks LTD"/></a>、
