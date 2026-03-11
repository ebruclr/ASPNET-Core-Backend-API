# CineClub: ASP.NET Core API ve İçerik Yönetim Sistemi

## Genel Bakış
Bu proje, modern web standartları kullanılarak geliştirilmiş, dinamik içerik yönetimi ve RESTful API servislerini kapsayan bir arka uç (back-end) geliştirme çalışmasıdır. Mevcut CineClub platformu üzerine; veri bütünlüğünü sağlayan iş mantığı kuralları, kullanıcı bazlı kısıtlamalar ve asenkron veri akışı sağlayan API uç noktaları entegre edilmiştir.

## Öne Çıkan Özellikler
* **Kullanıcı Bazlı Doğrulama (Business Logic):** Admin yetkisine sahip olmayan kullanıcıların, her film için yalnızca bir adet inceleme (review) bırakabilmesini sağlayan kontrol mekanizması geliştirilmiştir.
* **Gelişmiş İnceleme Takibi:** Güncellenen yorumlar için otomatik olarak "Edited" etiketi ve düzenleme zaman damgası (**timestamp**) gösterimi eklenmiştir.
* **RESTful API Entegrasyonu:**
    * **Top-Rated Servisi:** En yüksek puan alan filmleri JSON formatında döndüren performanslı bir uç nokta kurgulanmıştır.
    * **Yorum Servisi:** Belirli bir filme ait tüm kullanıcı yorumlarını, puanlarını ve yazar bilgilerini asenkron olarak listeleyen servis yapısı oluşturulmuştur.

## Teknoloji Yığını
* **Dil:** C#
* **Framework:** .NET Core MVC / Web API
* **ORM:** Entity Framework Core
* **Veritabanı Yönetimi:** LINQ (Dinamik sorgulama için)
* **Veri Formatı:** JSON (API iletişimi için)

## API Dokümantasyonu

| Uç Nokta (Endpoint) | Metot | Açıklama |
| :--- | :--- | :--- |
| `/api/movies/top-rated` | `GET` | Film adı, çıkış yılı ve ortalama puanı içeren listeyi JSON olarak döndürür. |
| `/api/reviews/{movieId}` | `GET` | Belirli bir filme ait tüm yorum içeriğini, puanları ve yazar bilgilerini asenkron olarak döndürür. |

## Geliştirme ve Uygulama Detayları
* **Veri Güvenliği:** Sunucu taraflı (server-side) kontrollerle mükerrer veri girişi engellenmiş ve veri tutarlılığı (**Data Integrity**) optimize edilmiştir.
* **Asenkron Programlama:** Veritabanı ve API süreçleri, sistem performansını artırmak amacıyla asenkron (`async/await`) yapılarla kurgulanmıştır.
* **Modüler Mimari:** Kod yapısı, Controller ve API katmanları arasında sorumlulukların ayrılması (Separation of Concerns) prensibine uygun olarak geliştirilmiştir.
