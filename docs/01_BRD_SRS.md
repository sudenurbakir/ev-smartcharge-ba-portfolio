# 01_BRD_SRS: Business Requirements & System Specification

## 1. Document Purpose & Scope 

Bu doküman, elektrikli araçlarda kullanılacak **EV-SmartCharge** yazılımının iş kurallarını, ne tür durumlarla karşılaşacağını ve sistemin vermesi gereken tepkileri tanımlar. 

Amacımız, sürücünün yolda kalmasını engellemek, batarya sağlığını korumak ve şarj sürecini en kolay hale getirmektir.

---

## 2. Business Rules 

Sistemin arka planında çalışan değişmez kurallar şunlardır:

* **BR-01 (Sıcaklık Eşiği):** Batarya sıcaklığı **55°C** ve üzerine çıktığında sistem bunu "Aşırı Isınma Risk Durumu" olarak kabul eder.
* **BR-02 (Şarj Eşiği):** Batarya şarj seviyesi **%15** ve altına düştüğünde sistem bunu "Kritik Şarj Seviyesi" olarak kabul eder.
* **BR-03 (Yakınlık Mesafesi):** Şarj istasyonu aramalarında araç konumunun en fazla **20 km** yarıçapındaki istasyonlar taranır.

---

## 3. Functional Requirements 

### A. Driver Notifications & Alerts (Sürücü Bilgilendirme ve Uyarılar)
* **FR-01:** Batarya sıcaklığı veya şarj seviyesi kritik eşiğe geldiğinde, araç içi ekranda görünecek şekilde **sesli ve görsel uyarı** mesajı verilmelidir.
* **FR-02:** Uyarı ekranında bataryanın güncel durumu (Örn: "Batarya Seviyesi: %12 - Aşırı Isınma: 58°C") açıkça yazmalıdır.

### B. Charging Station Discovery & Routing (Şarj İstasyonu Bulma ve Yönlendirme)
* **FR-03:** Sürücü ekrandaki "En Yakın İstasyonları Bul" butonuna bastığında, sistem aracın konumunu kullanarak yakındaki aktif şarj istasyonlarını listelemelidir.
* **FR-04:** Listelenen istasyonlarda; istasyon adı, araca olan mesafe (km) ve müsait (boş) şarj soketi sayısı gösterilmelidir.
* **FR-05:** Sürücü bir istasyon seçip "Rotayı Oluştur" dediğinde, navigasyon ekranı otomatik olarak o istasyona yönlendirme başlatmalıdır.

### C. Battery Thermal Pre-conditioning (Batarya Ön Hazırlığı)
* **FR-06:** Sürücü şarj istasyonu rotasını onayladığı an, sistem bataryayı hızlı şarja hazırlamak için otomatik olarak soğutma/ısıtma mekanizmasını çalıştırmalıdır.

---

## 4. Non-Functional Requirements 

* **NFR-01 (Performans):** Uyarılar, batarya riski tespit edildikten sonra **en geç 2 saniye içinde** ekranda görünmelidir.
* **NFR-02 (Kullanılabilirlik):** Sürücünün uyarılardan sonra istasyon seçip rotayı başlatması **en fazla 2 dokunuş (click)** ile tamamlanabilmelidir.
* **NFR-03 (Güvenilirlik):** Sürücüyü panikletmeyecek, anlaşılır ve sade bir uyarı dili kullanılmalıdır.
