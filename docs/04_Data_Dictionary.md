# 04_Data_Dictionary: Battery & Charging Data Model

## Overview 

Bu doküman, EV-SmartCharge sisteminin çalışırken arka planda tuttuğu ve kullandığı temel veri başlıklarını (Veri Sözlüğü) tanımlar. 

Analist olarak amacımız, hangi bilginin ne tür bir veri formatında saklanacağını belirlemektir.

---

## 1. Battery Telemetry Data (Batarya Anlık Verileri)

Sistem tarafından sürekli izlenen ve değerlendirilen batarya durum verileridir:

| Veri Adı (Field Name) | Veri Tipi (Type) | Açıklama | Örnek Veri |
| :--- | :--- | :--- | :--- |
| `battery_id` | Metin (String) | Bataryanın benzersiz kimlik numarası | `BAT-88392` |
| `temperature_celsius` | Sayı (Decimal) | Bataryanın anlık sıcaklık değeri (°C) | `58.5` |
| `state_of_charge` | Tam Sayı (Integer) | Bataryanın yüzde olarak şarj seviyesi (%) | `12` |
| `is_overheated` | Mantıksal (Boolean) | Bataryanın tehlikeli sıcaklıkta olup olmadığı durumu | `True` / `False` |

---

## 2. Charging Station Data (Şarj İstasyonu Verileri)

Haritada listelenen şarj noktalarına ait temel bilgilerdir:

| Veri Adı (Field Name) | Veri Tipi (Type) | Açıklama | Örnek Veri |
| :--- | :--- | :--- | :--- |
| `station_id` | Metin (String) | İstasyonun benzersiz kodu | `ST-101` |
| `station_name` | Metin (String) | İstasyonun ekranda görünecek adı | `Kadıköy Akıllı Şarj` |
| `distance_km` | Sayı (Decimal) | Aracın istasyona olan uzaklığı (km) | `3.2` |
| `available_connectors`| Tam Sayı (Integer) | O anda boş olan şarj soketi sayısı | `4` |
| `is_active` | Mantıksal (Boolean) | İstasyonun çalışır durumda olup olmadığı | `True` |
