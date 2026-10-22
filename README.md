# BOTAŞ Yemekhane Mobil Uygulaması

BOTAŞ bünyesinde gerçekleştirilen yaz stajı kapsamında, kurum personelinin yemekhane menülerini takip edebilmesi ve yemekleri değerlendirebilmesi amacıyla geliştirilmiş mobil uygulama projesidir.

Proje, **React Native mobil istemci**, **Spring Boot REST API** ve **MySQL veritabanından** oluşmaktadır. İki kişilik ekip çalışması olarak geliştirilmiştir.

## Özellikler

- Kullanıcı kayıt ve giriş işlemleri
- Personel ve yönetici rolleri
- Günlük ve haftalık yemek menülerinin görüntülenmesi
- Yemeklere puan verme ve yorum yapma
- Kullanıcı profili ve hesap işlemleri
- Yönetici için menü yönetimi ve değerlendirme sonuçlarının görüntülenmesi
- Açık ve koyu tema desteği
- Mobil uygulama ile REST API entegrasyonu

## Kullanılan Teknolojiler

| Mobil uygulama | Backend | Veritabanı |
| --- | --- | --- |
| React Native | Java, Spring Boot | MySQL |
| TypeScript | Spring Security, JWT | Spring Data JPA, Hibernate |
| React Navigation | Maven, Flyway | SQL |
| Redux Toolkit | REST API | |
| Axios, AsyncStorage | | |

## Proje Yapısı

```text
cafeteria-system/
├── YemekhaneMobile/       # React Native mobil uygulaması
│   ├── src/
│   │   ├── api/           # API istemcisi
│   │   ├── navigation/    # Ekran yönlendirmeleri
│   │   ├── screens/       # Kullanıcı, giriş ve yönetici ekranları
│   │   ├── services/      # Uygulama servisleri
│   │   ├── store/         # Durum yönetimi
│   │   └── theme/         # Tema tanımları
│   └── package.json
└── yemekhane-backend/     # Spring Boot REST API
    ├── src/
    ├── .env.example
    ├── pom.xml
    └── setup-local.sql
```

## Kurulum

### Gereksinimler

- Node.js **22.11.0 veya üzeri**
- Android Studio ve Android SDK (Android için)
- Java ve Spring Boot projesini çalıştırabilecek uygun JDK
- MySQL

### 1. Depoyu klonlayın

```bash
git clone https://github.com/AlimertYasar/cafeteria-system.git
cd cafeteria-system
```

### 2. Backend yapılandırması

MySQL sunucusunda yerel veritabanını ve kullanıcıyı hazırlayın. `yemekhane-backend/setup-local.sql` dosyasını kendi ortamınıza göre inceleyebilirsiniz.

`yemekhane-backend/.env.example` dosyasını `.env` olarak kopyalayın ve veritabanı bağlantısı ile JWT ayarlarını kendi ortamınıza göre düzenleyin. **Gerçek parolaları veya JWT anahtarlarını GitHub'a göndermeyin.**

Backend klasöründe Maven Wrapper ile uygulamayı başlatın:

```bash
cd yemekhane-backend
./mvnw spring-boot:run
```

Windows için `mvnw.cmd spring-boot:run` komutunu kullanabilirsiniz. Ortam değişkenlerinin Spring Boot sürecine aktarıldığından emin olun; `.env` dosyası her ortamda otomatik yüklenmeyebilir.

### 3. Mobil uygulamayı başlatma

Yeni bir terminalde:

```bash
cd YemekhaneMobile
npm install
npm start
```

Ardından başka bir terminalde Android uygulamasını çalıştırın:

```bash
npm run android
```

Mobil uygulamanın API adresini çalıştırdığınız backend sunucusuna göre ayarlayın. Android emülatörü ile fiziksel cihazın yerel sunucuya erişim adresi farklı olabilir.

## Yetkilendirme

Sistemde iki temel rol bulunmaktadır:

- **USER:** Menüleri görüntüleme ve yemekleri değerlendirme gibi personel işlemleri.
- **ADMIN:** Menü oluşturma/güncelleme ve yönetim işlemleri.

Backend tarafında JWT tabanlı kimlik doğrulama ve rol bazlı erişim kontrolü kullanılmaktadır.

## Ekip ve Katkılar

Bu proje, BOTAŞ yaz stajı kapsamında iki kişilik ekip tarafından geliştirilmiştir.

- **Alimert Yaşar — Frontend:** React Native mobil uygulamasının tüm frontend geliştirmesi, ekran tasarımları, navigasyon ve kullanıcı arayüzleri.
- **Ekip arkadaşı — Backend:** Spring Boot servisleri, veritabanı ve backend altyapısı.
- **Ortak çalışma:** Mobil uygulama ile backend API endpointlerinin entegrasyonu ve sistemin birlikte test edilmesi.

## Proje Hakkında

Bu çalışma, staj kapsamında geliştirilmiş bir eğitim/prototip projesidir. Kurumun resmî olarak yayımladığı veya üretim ortamında kullandığı bir uygulama olduğu iddia edilmemektedir.

## Repository

[GitHub – AlimertYasar/cafeteria-system](https://github.com/AlimertYasar/cafeteria-system)
