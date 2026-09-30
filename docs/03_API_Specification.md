# 03_API_Specification: Charging Station REST API Contract

## Overview (Genel Bakış)

Bu doküman, araç içi yazılımın (EV-SmartCharge) canlı şarj istasyonu verilerini çekmek için kullandığı uygulama programlama arayüzünü (API) tanımlar. 

Analist olarak amacımız, araç ekranı ile bulut sunucu (Cloud) arasındaki veri alışverişi kurallarını belirlemektir.

---

## Endpoint: Get Nearby Charging Stations (Yakındaki İstasyonları Getir)

* **HTTP Yöntemi (Method):** `GET`
* **Servis Adresi (URL):** `/v1/charging-stations`
* **Açıklama:** Aracın mevcut konum bilgisine göre 20 km yarıçapındaki aktif şarj istasyonlarını listeler.

---

## 1. Request Structure (Aracın Gönderdiği İstek / Soru)

Araç yazılımı, konumunu ve arama kriterlerini bulut servisine şu parametrelerle iletir:

* **latitude (Enlem):** Aracın bulunduğu enlem bilgisi (Örn: `41.0082`)
* **longitude (Boylam):** Aracın bulunduğu boylam bilgisi (Örn: `28.9784`)
* **radius_km (Yarıçap):** Aranacak maksimum mesafe (Örn: `20`)

### Örnek İstek Formatı (JSON):
```json
{
  "latitude": 41.0082,
  "longitude": 28.9784,
  "radius_km": 20
}

