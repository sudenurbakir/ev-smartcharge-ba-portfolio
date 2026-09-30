## 2. Response Structure (Sunucunun Verdiği Yanıt / Cevap)

Bulut sunucu, başarılı bir isteğin ardından `200 OK` durum kodu ile bulunan şarj istasyonlarının listesini döndürür.

### Örnek Başarılı Yanıt Formatı

```json
{
  "status": "success",
  "total_found": 2,
  "stations": [
    {
      "station_id": "ST-101",
      "station_name": "Kadıköy Akıllı Şarj Noktası",
      "distance_km": 3.2,
      "available_connectors": 4,
      "connector_type": "CCS Fast Charger"
    },
    {
      "station_id": "ST-204",
      "station_name": "Üsküdar Hızlı Şarj İstasyonu",
      "distance_km": 5.1,
      "available_connectors": 1,
      "connector_type": "Type 2"
    }
  ]
}
```

### Yanıt Alanları

| Alan                   | Açıklama                                                             |
| ---------------------- | -------------------------------------------------------------------- |
| `status`               | İşlemin başarılı veya hatalı olduğunu belirtir.                      |
| `total_found`          | Bulunan toplam istasyon sayısını belirtir.                           |
| `station_id`           | Şarj istasyonunun benzersiz kimliğidir.                              |
| `station_name`         | Şarj istasyonunun adıdır.                                            |
| `distance_km`          | İstasyonun kullanıcıya olan uzaklığını kilometre cinsinden belirtir. |
| `available_connectors` | Kullanılabilir soket sayısını belirtir.                              |
| `connector_type`       | İstasyondaki soket/şarj bağlantı tipini belirtir.                    |

---

## 3. Error Handling (Hata Durumu Yönetimi)

İnternet bağlantısının kesilmesi veya sunucudan veri alınamaması durumunda sistem çökmemelidir.

Sistem, sürücüye anlaşılır bir hata mesajı göstermeli ve hatanın nedenini belirten bir hata kodu döndürmelidir.

### Örnek Hata Yanıtı

```json
{
  "status": "error",
  "error_code": "ERR_NO_CONNECTION",
  "message": "Şarj istasyonu verilerine ulaşılamadı. Lütfen internet bağlantınızı kontrol ediniz."
}
```

### Hata Alanları

| Alan         | Açıklama                                            |
| ------------ | --------------------------------------------------- |
| `status`     | İşlemin hata ile sonuçlandığını belirtir.           |
| `error_code` | Hatanın türünü belirten benzersiz kodudur.          |
| `message`    | Kullanıcıya gösterilecek açıklayıcı hata mesajıdır. |

### Beklenen Sistem Davranışı

* İnternet bağlantısı olmadığında sistem hata mesajı göstermelidir.
* Sunucudan veri alınamadığında uygulama çökmemelidir.
* Kullanıcıya anlaşılır bir hata mesajı gösterilmelidir.
* Hata durumunda uygun `error_code` döndürülmelidir.
* Kullanıcı bağlantıyı tekrar denemek için yönlendirilmelidir.
