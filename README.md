# 📚 .NET Web API Project

Bu proje, **ASP.NET Core 6+** kullanılarak geliştirilmiş, çok katmanlı mimariye sahip, güvenli ve ölçeklenebilir bir **RESTful Web API** uygulamasıdır.  
Proje, JWT tabanlı kimlik doğrulama, rate limiting, versiyonlama, response caching ve Swagger dokümantasyonu gibi modern API geliştirme özelliklerini barındırır.

## 🚀 Özellikler

- **Çok katmanlı mimari** (Presentation, Services, Repositories)
- **Entity Framework Core** ile SQL Server bağlantısı
- **JWT Authentication** ile güvenli kimlik doğrulama
- **ASP.NET Core Identity** entegrasyonu
- **Versiyonlama** (API v1, v2)
- **Response Caching & HTTP Cache Headers**
- **IP Rate Limiting** (AspNetCoreRateLimit)
- **CORS** yapılandırması
- **Swagger UI** ile API dokümantasyonu
- **NLog** ile loglama
- **Action Filters** ile özel doğrulama ve hata yönetimi
- **AutoMapper** ile DTO-Entity dönüşümleri

---

## 🛠 Teknoloji Stack

- **ASP.NET Core 6+**
- **Entity Framework Core**
- **SQL Server**
- **JWT & ASP.NET Identity**
- **Swagger / OpenAPI**
- **NLog**
- **AspNetCoreRateLimit**
- **AutoMapper**

---


## 📁 Katmanlı Mimari

📦 .NET-Web-Api-Project
┣ 📂Presentation # Controller katmanı
┣ 📂Services # İş mantığı
┣ 📂Repositories # EF Core repository implementasyonları
┣ 📂WebApi # API giriş noktası (Program.cs, Extensions)
┣ 📂Entities # Modeller ve DTO'lar
┣ nlog.config # NLog yapılandırması
┗ appsettings.json # Konfigürasyon dosyalar

🔌 API Endpoint Örnekleri

Method	  Endpoint	          Açıklama
GET	    /api/v1/books	      Kitap listesini getir
GET	    /api/v1/books/{id}	ID’ye göre kitap getir
POST	  /api/v1/books	Yeni kitap ekle (JWT gerekli)
PUT	    /api/v1/books/{id}	Kitap güncelle (JWT gerekli)
DELETE	/api/v1/books/{id}	Kitap sil (JWT gerekli)
POST	  /api/auth/login	Giriş yap ve JWT token al
POST	  /api/auth/register	Yeni kullanıcı kaydı oluştur

🔐 Ortam Değişkenleri (appsettings.json)

{
  "ConnectionStrings": {
    "sqlConnection": "Server=.;Database=BlogDb;Trusted_Connection=True;TrustServerCertificate=True;"
  },
  "JwtSettings": {
    "validIssuer": "YourIssuer",
    "validAudience": "YourAudience",
    "secretKey": "YourSecretKey"
  }
}

🔍 Query Parametreleri ile Veri Getirme
API; pagination (sayfalandırma), filtreleme, sıralama ve data shaping desteği sağlar.

GET {{baseUrl}}/api/books?pageSize=5&pageNumber=1

🎯 Filtreleme
Belirli fiyat aralıklarındaki kitapları listeleyebilirsiniz.

GET {{baseUrl}}/api/books?pageSize=5&pageNumber=1&maxPrice=500&minPrice=300

📊 Sıralama
Birden fazla alana göre sıralama yapılabilir.

GET {{baseUrl}}/api/books?pageSize=10&pageNumber=1&maxPrice=500&minPrice=10&orderBy=price desc,title

✂ Data Shaping
Sadece istediğiniz alanları döndürmek için fields parametresini kullanabilirsiniz.
Yalnızca belirtilen alanlar yanıt olarak döner.
Büyük veri setlerinde performansı artırır.

{
  {
    "title": "Book A",
    "price": 250
  },
  {
    "title": "Book B",
    "price": 320
  }
}

📜 Swagger Dokümantasyonu
Proje çalıştığında Swagger UI’a şu adreslerden ulaşabilirsiniz:

v1: https://localhost:5001/swagger/v1/swagger.json

v2: https://localhost:5001/swagger/v2/swagger.json

