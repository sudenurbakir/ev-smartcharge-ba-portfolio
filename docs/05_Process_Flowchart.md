# 05_Process_Flowchart: System & User Interaction Workflow

## Overview (Genel Bakış)

Bu doküman, EV-SmartCharge sisteminde bir uyarı tetiklendiğinde sürücü ile sistem arasındaki etkileşim adımlarını gösteren süreç akış şemasını (Flowchart) içerir.

---

## Process Flowchart (Süreç Akış Şeması)

Aşağıdaki şema, araç sensörlerinden gelen verinin işlenmesinden sürücünün rota başlatmasına kadar geçen süreci görselleştirir.

flowchart TD
    A([Başla: Araç Seyir Halinde]) --> B[Sensör Verileri Okunur]
    B --> C{Sıcaklık >= 55°C VEYA Şarj <= %15 mi?}
    
    C -- Hayır --> B
    C -- Evet --> D[Ekranda Sesli ve Görsel Uyarı Göster]
    
    D --> E[Sürücüye Yakındaki İstasyonları Arama Seçeneği Sun]
    E --> F{Sürücü 'İstasyon Bul' Butonuna Bastı mı?}
    
    F -- Hayır --> G[Uyarı Ekranı Arka Plana Alınır]
    F -- Evet --> H[Konuma Göre 20 km Yarıçaptaki İstasyonlar Listelenir]
    
    H --> I[Sürücü Bir İstasyon Seçer ve 'Rotayı Başlat' Der]
    I --> J[Navigasyon Yönlendirmesi Başlatılır]
    J --> K[Batarya Ön Soğutma / Isıtma Mekanizması Çalıştırılır]
    K --> L([Bitiş: Güvenli Şarj Rotalaması Tamamlandı])

---

## Process Steps & Logic (Süreç Adımları ve Mantığı)

### 1. Veri Toplama

Aracın arka planındaki sistem, batarya sıcaklığını ve şarj seviyesini belirli aralıklarla kontrol eder.

### 2. Karar Mekanizması

Batarya sıcaklığı belirlenen kritik eşik değerine ulaştığında veya şarj seviyesi kritik seviyenin altına düştüğünde uyarı senaryosu tetiklenir.

### 3. Kullanıcı Etkileşimi

Sürücü, uyarı ekranındaki **"İstasyon Bul"** seçeneğini seçtiğinde sistem konum bilgisine göre uygun şarj istasyonlarını API aracılığıyla sorgular ve sonuçları ekranda listeler.

### 4. Rota Başlatma ve Otomatik Aksiyon

Sürücü bir istasyon seçip **"Rotayı Başlat"** seçeneğini onayladığında navigasyon yönlendirmesi başlatılır. Desteklenen araçlarda bataryanın şarj için uygun sıcaklığa getirilmesine yönelik ön koşullandırma süreci arka planda başlatılır.

---

## Business Logic Summary

| Adım                  | Sistem Davranışı                                                                    |
| --------------------- | ----------------------------------------------------------------------------------- |
| Sensör kontrolü       | Batarya sıcaklığı ve şarj seviyesi izlenir.                                         |
| Kritik değer kontrolü | Belirlenen eşik değerleri kontrol edilir.                                           |
| Uyarı                 | Kritik durumda sesli ve görsel uyarı gösterilir.                                    |
| İstasyon arama        | Kullanıcının konumuna göre uygun istasyonlar sorgulanır.                            |
| İstasyon seçimi       | Kullanıcı uygun bir istasyon seçer.                                                 |
| Rota                  | Navigasyon seçilen istasyona yönlendirilir.                                         |
| Ön koşullandırma      | Desteklenen araçlarda batarya sıcaklığı şarja uygun seviyeye getirilmeye çalışılır. |
