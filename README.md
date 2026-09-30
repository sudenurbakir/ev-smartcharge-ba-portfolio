# EV-SmartCharge: Elektrikli Araç Akıllı Şarj ve Uyarı Sistemi

## Proje Hakkında

Bu proje, elektrikli araçlarda batarya durumunu takip eden ve sürücüye yardımcı olan bir araç içi yazılım fikridir. Araç sürüş esnasındayken batarya çok ısındığında veya şarjı kritik bir seviyeye düştüğünde sürücüyü uyarır ve en yakın uygun şarj istasyonunu haritada gösterir.

---

## Müşteri Problemi ve Çözüm

### Problem
Elektrikli araç sürücülerinin seyir halindeyken bataryanın aniden bitmesi, aşırı ısınması veya civardaki uygun şarj istasyonunu bulmakta zorlanması nedeniyle yaşadığı endişe.

### Çözüm
Sürücüye yardımcı olan akıllı yazılım sistemi:
1. **Güvenlik Uyarısı:** Batarya sıcaklığı veya şarj seviyesi kritik sınıra geldiğinde ekranda sesli ve görsel uyarı verir.
2. **Kolay İstasyon Bulma:** Sürücünün konumuna en yakın ve boş durumdaki şarj istasyonlarını otomatik olarak listeler.
3. **Akıllı Hazırlık:** Sürücü bir şarj istasyonu seçtiğinde, araba yoldayken bataryayı şarj olmaya en uygun sıcaklığa getirir (ön soğutma/ısıtma).

---

## Proje Adımları ve Klasör Yapısı

| Doküman | Açıklama |
| :--- | :--- |
| **İş ve Sistem Gereksinimleri** | Sistemde hangi kuralların geçerli olduğunu belirten ana liste. |
| **Kullanıcı Hikayeleri ve Kabul Kriterleri** | Sürücünün ve yazılımcının ne yapması gerektiğini anlatan basit senaryolar. |
| **Süreç Akış Şeması** | Adım adım sürücü ve sistem etkileşim şeması. |
| **Veri Yapısı** | Sistemde tutulacak basit bilgi başlıkları (Sıcaklık, Konum, Şarj Seviyesi vb.). |

---

## Adım Adım Çalışma Mantığı

1. Araç sensörleri batarya bilgilerini (Sıcaklık: 58°C, Şarj: %12) yazılıma iletir.
2. Yazılım bu değerlerin riskli olduğunu fark eder ve sürücü ekranına uyarı gönderir.
3. Ekran üzerinde en yakın şarj istasyonları listelenir.
4. Sürücü bir istasyon seçip "Rotayı Başlat" butonuna basar.
5. Yazılım, aracı hızlı şarja hazırlamak için batarya sıcaklığını ayarlamaya başlar.

---

## Bu Projede Öne Çıkan Analiz Yetkinlikleri

- **İhtiyaç Analizi:** Sürücü ve sistem ihtiyaçlarını net bir şekilde ortaya koyma.
- **Süreç Tasarımı:** Kullanıcının ekranla ve sistemin arka planıyla olan etkileşimini adım adım kurgulama.
- **Dokümantasyon:** Karmaşık konuları herkesin anlayabileceği sade ve düzenli bir dile dökme.
