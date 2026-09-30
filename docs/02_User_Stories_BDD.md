# 02_User_Stories_BDD: User Stories & Acceptance Criteria

## Overview 

Bu doküman, EV-SmartCharge sisteminin yazılım ve test ekipleri tarafından geliştirebilmesi için hazırlanan Jira bilet formatındaki kullanıcı hikayelerini (User Stories) ve kabul kriterlerini (Acceptance Criteria) içerir.

---

## Story 1: Critical Battery & Overheat Warning (Kritik Şarj ve Isınma Uyarısı)

* **User Story:** 
  * **As a** Elektrikli araç sürücüsü,
  * **I want to** bataryam aşırı ısındığında veya şarjım kritik seviyeye düştüğünde ekranda net bir uyarı görmek,
  * **So that** yolda kalmadan veya araca zarar vermeden önlem alabilmek istiyorum.

* **Acceptance Criteria (BDD Format - Given / When / Then):**

  * **Scenario 1: Batarya sıcaklığı kritik sınırı aştığında uyarı verme**
    * **Given (Koşul):** Araç hareket halinde ve batarya sıcaklığı 55°C'nin altında iken,
    * **When (Eylem):** Batarya sıcaklığı 58°C seviyesine ulaştığında,
    * **Then (Sonuç):** Araç ekranında 2 saniye içinde "Aşırı Isınma Uyarısı" görünmeli ve hafif sesli ikaz çalmalıdır.

  * **Scenario 2: Şarj seviyesi %15'in altına düştüğünde uyarı verme**
    * **Given (Koşul):** Sürücü seyahat ederken,
    * **When (Eylem):** Şarj seviyesi (SoC) %12'ye düştüğünde,
    * **Then (Sonuç):** Ekranda "Kritik Şarj Seviyesi" uyarısı belirmeli ve altında "En Yakın İstasyonları Gör" butonu çıkmalıdır.

---

## Story 2: Charging Station Listing & Selection (İstasyon Listeleme ve Seçim)

* **User Story:**
  * **As a** Elektrikli araç sürücüsü,
  * **I want to** konumuma en yakın ve boş soketi olan şarj istasyonlarını ekranda listelemek,
  * **So that** zaman kaybetmeden şarj edebileceğim bir noktaya yönelebilmek istiyorum.

* **Acceptance Criteria (BDD Format - Given / When / Then):**

  * **Scenario 1: Yakındaki boş istasyonları listeleme**
    * **Given (Koşul):** Düşük şarj uyarısı ekranı açıkken,
    * **When (Eylem):** Sürücü "En Yakın İstasyonları Gör" butonuna bastığında,
    * **Then (Sonuç):** Sistem 20 km yarıçapındaki aktif istasyonları; mesafe ve boş soket sayısı bilgisiyle birlikte ekranda listelemelidir.

  * **Scenario 2: İstasyon seçimi ve rota başlatma**
    * **Given (Koşul):** İstasyon listesi ekrandayken,
    * **When (Eylem):** Sürücü bir istasyona dokunup "Rotayı Başlat" butonuna bastığında,
    * **Then (Sonuç):** Navigasyon seçilen istasyona doğru rotayı başlatmalı ve batarya ön soğutma/ısıtma süreci arka planda devreye girmelidir.
