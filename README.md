# 🚀 SmartTax TR - Shopify Vergi ve Fatura Uyumluluk Çözümü

![Status](https://img.shields.io/badge/Status-Production--Ready-success)
![Tech](https://img.shields.io/badge/Tech-Azure%20%7C%20.NET%20Core%20%7C%20React-blueviolet)
![Architecture](https://img.shields.io/badge/Architecture-SaaS%20%2F%20Serverless-blue)

**SmartTax TR**, Shopify Türkiye pazarındaki mağazaların Vergi Usul Kanunu (VUK) gerekliliklerine uyum sağlamasını kolaylaştıran bir **Micro-SaaS** projesidir. Özellikle Shopify Basic planı kullanan işletmelerin, fatura süreçlerini sepet aşamasında optimize etmelerini ve yasal veri toplama ihtiyaçlarını (TCKN/VKN) karşılamalarını sağlar.

---

## 📸 Proje Önizleme

### 1. Müşteri Deneyimi (Frontend)
Müşterilerin sepet aşamasında vergi kimlik numaralarını girmelerini sağlayan, Bireysel ve Kurumsal ayrımı sunan kullanıcı arayüzü.

<img width="100%" alt="Sepet Aşaması" src="https://github.com/user-attachments/assets/bd00beaf-d12f-492e-a904-51877690cf48" />

### 2. Sipariş Yönetimi ve Etiketleme
Doğrulanan verilerin Shopify Admin panelinde otomatik etiketlenmesi (`TCKN_ONAYLI`, `VKN_ONAYLI`) ve sipariş detayına işlenmesi.

<img width="100%" alt="Sipariş Etiketleme" src="https://github.com/user-attachments/assets/5ec27d51-6f0d-4bbc-9aac-96abe6f43727" />

### 3. Yönetim Paneli
Mağaza sahipleri için uygulama ayarlarının (limitler, renk, KVKK metni) yönetildiği entegre dashboard.

<img width="100%" alt="Yönetim Paneli" src="https://github.com/user-attachments/assets/ac7a5038-ff5b-4ccd-93aa-1e664e77dd04" />

---

## 🎯 Temel Özellikler

* **✅ Veri Doğrulama (Validation):** TCKN (Mod10) ve VKN (10 haneli) algoritmaları ile kullanıcı girişlerini kontrol ederek hatalı veri girişini minimize eder.
* **🛡️ Akıllı Limit Yönetimi:** Mağaza sahibi tarafından belirlenen tutar (Örn: 12.000 TL) altındaki siparişlerde veri talebini kapatarak kullanıcı deneyimini korur.
* **🏢 B2B & Kurumsal Ayrımı:** Müşterilere fatura tipi seçeneği sunarak doğru vergi verisinin toplanmasını sağlar.
* **🔐 KVKK & Veri Güvenliği:** Veriler yalnızca sipariş bağlamında işlenir, sunucu tarafında maskelenir (Örn: `11*******11`) ve kalıcı olarak saklanmaz. SmartTax TR, *Data Processor* (Veri İşleyen) rolünde konumlanır.
* **🏷️ Otomatik Etiketleme:** Siparişleri veri tipine göre etiketleyerek muhasebe entegrasyon süreçlerini hızlandırır.

---

## 🛠️ Teknik Mimari

Proje, sürdürülebilirlik ve ölçeklenebilirlik gözetilerek **Clean Architecture** prensipleriyle geliştirilmiştir.

| Katman | Teknoloji | Açıklama |
| :--- | :--- | :--- |
| **Frontend** | React, Shopify Polaris | Modern React Router mimarisi ve UI kütüphanesi. |
| **Backend** | Azure Functions (C#) | .NET Core üzerinde çalışan Serverless mimari. |
| **Güvenlik** | HMAC SHA-256 | Shopify Signature Verification ile istek bütünlüğü doğrulanır. |
| **CI/CD** | GitHub Actions | Azure ortamına otomatik dağıtım süreçleri. |

---

## ⚖️ Teknik Kararlar ve Trade-offs

* **Frontend Dili:** Shopify ekosistem uyumluluğu ve hızlı prototipleme (MVP) gereksinimleri nedeniyle frontend tarafında **JavaScript** tercih edilmiştir.
* **Teknik Borç Yönetimi:** Uzun vadede bakım kolaylığı ve tip güvenliği için **TypeScript** geçişi teknik roadmap'e eklenmiştir.
* **Maliyet/Ölçeklendirme:** Düşük maliyet (Cost-Efficiency) ve yüksek trafik esnekliği için **Serverless** mimari tercih edilmiştir.

---

## 🤖 AI Destekli Geliştirme

Geliştirme sürecinde verimliliği artırmak amacıyla AI destekli geliştirme araçlarından faydalanılmıştır.

1.  Uygulama mimarisi, bileşen hiyerarşisi ve iş kuralları tamamen **geliştirici tarafından tasarlanmıştır.**
2.  AI; tekrar eden UI bileşenleri, refactoring ve boilerplate kod üretiminde verimlilik artırıcı bir araç olarak kullanılmıştır.
3.  Üretilen tüm çıktılar manuel olarak gözden geçirilmiş, test edilmiş ve proje standartlarına uygun hale getirilmiştir.

---

## 🧪 Kalite Güvencesi ve Test Süreçleri

Finansal verilerin doğruluğu için kritik doğrulama mantıkları **TDD (Test Driven Development)** yaklaşımıyla **xUnit** kullanılarak test edilmiştir.

<details>
<summary><b>🛠️ Örnek TCKN/VKN Doğrulama Testlerini Görüntüle</b></summary>

```csharp
  [Theory]
  [InlineData("1234567890")]   // Hatalı uzunluk
  [InlineData("02345678901")]  // 0 ile başlama hatası
  public void Validate_InvalidTckn_ShouldReturnFalse(string tckn)
  {
      // Arrange & Act
      var result = TcknValidator.Validate(tckn);
  
      // Assert
      Assert.False(result);
  }
```
</details>
👨‍💻 Geliştirici Rolü ve Erişim
Bu proje; ürün tasarımı, backend mimarisi ve frontend entegrasyonu dahil olmak üzere tek geliştirici (solo developer) tarafından hayata geçirilmiştir.

🔒 Gizlilik Notu: Kaynak kodları ticari bir ürün olması sebebiyle gizli (Private) tutulmaktadır. Teknik değerlendirme süreçleri kapsamında, mimari ve kod yapısı incelemeye açılabilir.

Mehmet Yeşil - Bilgisayar Mühendisi

Uzmanlık: Backend Development (.NET Core), Cloud Architecture (Azure), Robotics (ROS)
