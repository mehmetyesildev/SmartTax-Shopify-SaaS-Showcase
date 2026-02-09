# SmartTax TR - Shopify Vergi ve Fatura Uyumluluk Çözümü

SmartTax TR, Shopify Türkiye pazarındaki mağazaların Vergi Usul Kanunu (VUK) gerekliliklerine uyum sağlamasını kolaylaştıran bir Micro-SaaS projesidir. Özellikle Shopify Basic planı kullanan işletmelerin, fatura süreçlerini sepet aşamasında optimize etmelerini ve yasal veri toplama ihtiyaçlarını (TCKN/VKN) karşılamalarını sağlar.

## 📸 Proje Önizleme

### Müşteri Deneyimi (Frontend)
Müşterilerin sepet aşamasında vergi kimlik numaralarını girmelerini sağlayan, Bireysel ve Kurumsal ayrımı sunan kullanıcı arayüzü.
<img width="1507" height="726" alt="Ekran görüntüsü 2026-02-07 191619" src="https://github.com/user-attachments/assets/bd00beaf-d12f-492e-a904-51877690cf48" />

### Sipariş Yönetimi ve Etiketleme
Doğrulanan verilerin Shopify Admin panelinde otomatik etiketlenmesi (TCKN_ONAYLI, VKN_ONAYLI) ve sipariş detayına işlenmesi.
<img width="1647" height="706" alt="Sipariş etiketleme" src="https://github.com/user-attachments/assets/5ec27d51-6f0d-4bbc-9aac-96abe6f43727" />

### Yönetim Paneli
Mağaza sahipleri için uygulama ayarlarının (limitler, renk, KVKK metni) yönetildiği entegre dashboard.
<img width="1622" height="824" alt="Yönetim paneli" src="https://github.com/user-attachments/assets/ac7a5038-ff5b-4ccd-93aa-1e664e77dd04" />

## 🎯 Temel Özellikler

- **Veri Doğrulama (Validation)**: TCKN (Mod10) ve VKN (10 haneli) algoritmaları ile kullanıcı girişlerini kontrol eder, hatalı veri girişini minimize eder.

- **Akıllı Limit Yönetimi**: Mağaza sahibi tarafından belirlenen tutar (Örn: 12.000 TL) altındaki siparişlerde veri talebini kapatarak kullanıcı deneyimini korur.

- **B2B & Kurumsal Ayrımı**: Müşterilere fatura tipi seçeneği sunarak doğru vergi verisinin toplanmasını sağlar.

- **KVKK Uyumluluğu**: Kişisel verileri sunucu tarafında maskeleyerek (Örn: 11*******11) işler ve güvenliği ön planda tutar.

- **Otomatik Etiketleme**: Siparişleri veri tipine göre etiketleyerek muhasebe entegrasyon süreçlerini hızlandırır.

## 🛠️ Teknik Mimari

Proje, sürdürülebilirlik, test edilebilirlik ve ölçeklenebilirlik gözetilerek Clean Architecture prensipleriyle geliştirilmiştir.

- **Frontend**: React, Modern React Router mimarisi ve Shopify Polaris UI kütüphanesi.

- **Backend**: C# .NET Core üzerinde çalışan Azure Functions (Serverless) mimarisi.

- **Güvenlik**: Shopify HMAC Signature Verification ile isteklerin bütünlüğü ve kaynağı kriptografik olarak doğrulanır.

- **Ödeme Entegrasyonu**: Shopify V3 Billing API ile entegre abonelik ve faturalama yönetimi.

- **CI/CD**: GitHub Actions üzerinden Azure ortamına otomatik dağıtım süreçleri.

## 📁 Proje Yapısı

```
├── smart-tax-app (Frontend - React & Shopify CLI)
│   ├── app (Remix/React Router Pages)
│   └── extensions (Theme App Extension - Liquid/JS)
├── SmartTax.Backend (Azure Functions - C#)
│   ├── SmartTax.API (Endpoints & Webhooks)
│   ├── SmartTax.Core (Domain Models & Validators)
│   └── SmartTax.Infrastructure (Security & Data Access)
└── README.md
```

## 🔒 Gizlilik ve Kaynak Kodları

Bu proje ticari bir üründür. Kaynak kodları gizli (Private) bir depoda tutulmaktadır. Teknik mimari, kullanılan teknolojiler ve geliştirme metodolojileri hakkındaki detaylar, teknik incelemeler için talep üzerine paylaşılabilir.

## 👤 Geliştirici

**Mehmet Yeşil** - Bilgisayar Mühendisi

- **Konum**: Konya, Türkiye
- **Uzmanlık**: Backend Development (.NET Core), Cloud Architecture (Azure), Robotics (ROS)
