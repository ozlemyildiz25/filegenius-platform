# 🎯 FileGenius™ Professional Platform

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Node.js Version](https://img.shields.io/badge/node-%3E%3D20.0.0-brightgreen)](https://nodejs.org/)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-15+-blue)](https://www.postgresql.org/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.0+-blue)](https://www.typescriptlang.org/)

> **Dünya’nın En Kapsamlı AI Destekli Dosya Uzantısı Analiz ve Yönetim Platformu**

Topluluk destekli, gamifikasyon ile motive edici, 500+ dosya formatını destekleyen profesyonel platform.

-----

## 📌 İçindekiler

- [Hızlı Başlangıç](#-hızlı-başlangıç)
- [Özellikler](#-temel-özellikler)
- [Kurulum](#-kurulum)
- [Yapılandırma](#-yapılandırma)
- [Kullanım](#-kullanım)
- [Katkıda Bulunma](#-katkıda-bulunma)
- [Bağış ve Destek](#-bağış-ve-destek)
- [Lisans](#-lisans)

-----

## 🚀 Hızlı Başlangıç

### Gereksinimler

```bash
# Node.js 20+ ve npm
node --version  # v20.0.0 veya üzeri

# PostgreSQL 15+
psql --version

# Redis 7+
redis-server --version

# Git
git --version
```

### Kurulum (Alpine Linux)

```bash
# 1. Repository'yi klonlayın
git clone https://github.com/ozlemyildiz/filegenius-platform.git
cd filegenius-platform

# 2. Bağımlılıkları yükleyin
npm run setup

# 3. Veritabanını başlatın
npm run db:setup

# 4. Geliştirme sunucusunu başlatın
npm run dev
```

Tarayıcınızda `http://localhost:3000` adresini açın.

-----

## ✨ Temel Özellikler

### 🔍 Akıllı Dosya Analizi

- **AI Destekli Analiz**: Claude API ile kapsamlı format analizi
- **500+ Format Desteği**: Yaygın ve nadir dosya uzantıları
- **Tarihsel Veri**: Doğuş yılından günümüze format geçmişi
- **Risk Değerlendirmesi**: Bozulma ve güvenlik senaryoları

### 🤖 Yapay Zeka Özellikleri

- **Intelligent Q&A**: Format-specific soru-cevap sistemi
- **Auto-Categorization**: Otomatik kategorizasyon
- **Problem Solving**: Açılmama ve bozulma çözümleri
- **Best Practices**: Optimal kullanım önerileri

### 🎮 Gamifikasyon Sistemi

- **Puan Sistemi**: Katkı bazlı ödüllendirme
- **Rozetler**: 50+ farklı başarı rozeti
- **Liderlik Tablosu**: Haftalık/aylık liderler
- **Challenge Sistemi**: Topluluk görevleri

### 👥 Topluluk Özellikleri

- **Community-Driven**: Kullanıcı katkıları ile büyüyen platform
- **Verification System**: Topluluk doğrulama mekanizması
- **Contribution Tracking**: Katkı takip sistemi
- **Real-time Updates**: Canlı topluluk güncellemeleri

### 📊 Analytics & Insights

- **Usage Statistics**: Format kullanım istatistikleri
- **Trend Analysis**: Popülerlik trendleri
- **Comparison Tools**: Format karşılaştırma araçları
- **Performance Metrics**: Platform performans metrikleri

-----

## 📦 Kurulum

### Backend Kurulumu

```bash
cd backend

# Bağımlılıkları yükle
npm install

# Environment dosyasını oluştur
cp .env.example .env

# Veritabanını oluştur ve migrate et
npm run db:create
npm run db:migrate
npm run db:seed

# Geliştirme sunucusunu başlat
npm run dev
```

### Frontend Kurulumu

```bash
cd frontend

# Bağımlılıkları yükle
npm install

# Environment dosyasını oluştur
cp .env.local.example .env.local

# Geliştirme sunucusunu başlat
npm run dev
```

### Docker ile Kurulum

```bash
# Tüm servisleri başlat
docker-compose up -d

# Logları görüntüle
docker-compose logs -f

# Servisleri durdur
docker-compose down
```

-----

## ⚙️ Yapılandırma

### Backend (.env)

```env
# Database
DATABASE_URL=postgresql://ozlemyildiz:password@localhost:5432/filegenius
REDIS_URL=redis://localhost:6379

# AI Services
CLAUDE_API_KEY=your_claude_api_key_here

# Security
JWT_SECRET=your_super_secret_jwt_key_here
BCRYPT_ROUNDS=12

# File Processing
UPLOAD_MAX_SIZE=100MB
TEMP_DIR=/tmp/filegenius

# Email (for notifications)
SMTP_HOST=smtp.gmail.com
SMTP_PORT=587
SMTP_USER=your_email@gmail.com
SMTP_PASS=your_app_password

# Analytics
GOOGLE_ANALYTICS_ID=G-XXXXXXXXXX
```

### Frontend (.env.local)

```env
# API
NEXT_PUBLIC_API_URL=http://localhost:3001
NEXT_PUBLIC_WS_URL=ws://localhost:3001

# Google AdSense (Reklam Sistemi)
NEXT_PUBLIC_ADSENSE_CLIENT_ID=ca-pub-XXXXXXXXXXXXXXXX
NEXT_PUBLIC_ADSENSE_SLOT_HEADER=1234567890
NEXT_PUBLIC_ADSENSE_SLOT_SIDEBAR=0987654321
NEXT_PUBLIC_ADSENSE_SLOT_FOOTER=1122334455

# Analytics
NEXT_PUBLIC_GA_ID=G-XXXXXXXXXX

# Donation/Payment Systems
NEXT_PUBLIC_PAYPAL_CLIENT_ID=your_paypal_client_id
NEXT_PUBLIC_STRIPE_PUBLISHABLE_KEY=pk_test_xxxxxxxxxxxxx
```

-----

## 💻 Kullanım

### API Endpoints

#### Extensions

```bash
# Tüm uzantıları listele
GET /api/extensions?page=1&limit=20

# Uzantı detayı
GET /api/extensions/:name

# Yeni uzantı ekle (auth gerekli)
POST /api/extensions
{
  "name": ".xyz",
  "fullName": "Example Format",
  "description": "Detailed description",
  "category": "document"
}

# Uzantı güncelle
PUT /api/extensions/:id

# Uzantı ara
GET /api/search?q=pdf&category=document
```

#### AI Analysis

```bash
# AI destekli analiz
POST /api/ai/analyze
{
  "extension": ".pdf",
  "query": "What are the best practices for PDF files?"
}

# Format karşılaştırma
POST /api/ai/compare
{
  "extensions": [".pdf", ".docx"],
  "criteria": ["compatibility", "size", "security"]
}
```

#### Gamification

```bash
# Kullanıcı profili
GET /api/users/:id/profile

# Liderlik tablosu
GET /api/leaderboard?period=weekly

# Rozetler
GET /api/badges

# Kullanıcı istatistikleri
GET /api/users/:id/stats
```

### React Hooks Kullanımı

```typescript
// Extension arama
import { useSearch } from '@/hooks/useSearch';

function SearchComponent() {
  const { results, loading, search } = useSearch();
  
  return (
    <SearchBar 
      onSearch={search}
      results={results}
      loading={loading}
    />
  );
}

// AI analiz
import { useAI } from '@/hooks/useAI';

function AnalysisComponent() {
  const { analyze, loading, result } = useAI();
  
  const handleAnalyze = async () => {
    const analysis = await analyze('.pdf', 'security concerns');
    console.log(analysis);
  };
  
  return <button onClick={handleAnalyze}>Analyze</button>;
}
```

-----

## 🤝 Katkıda Bulunma

FileGenius™ topluluk destekli bir projedir. Katkılarınızı bekliyoruz!

### Katkı Süreci

1. **Repository’yi Fork Edin**

```bash
git clone https://github.com/ozlemyildiz/filegenius-platform.git
cd filegenius-platform
git checkout -b feature/yeni-ozellik
```

1. **Değişikliklerinizi Yapın**

```bash
# Git kullanıcı bilgilerinizi ayarlayın
git config user.name "Özlem Yıldız"
git config user.email "ozlem@filegenius.com"

# Değişiklikleri commit edin
git add .
git commit -m "feat: yeni özellik eklendi"
```

1. **Pull Request Gönderin**

```bash
git push origin feature/yeni-ozellik
```

### Commit Kuralları

```bash
# Feature
git commit -m "feat: yeni AI analiz özelliği"

# Bug fix
git commit -m "fix: arama sonuçları düzeltildi"

# Documentation
git commit -m "docs: API dokümantasyonu güncellendi"

# Style
git commit -m "style: kod formatlaması"

# Refactor
git commit -m "refactor: veritabanı sorguları optimize edildi"
```

### Code Review Süreci

✅ Automated tests geçmeli
✅ 2 onay gerekli
✅ Security scan temiz olmalı
✅ Dokümantasyon güncellenmiş olmalı

-----

## 💰 Bağış ve Destek

FileGenius™ açık kaynak ve kar amacı gütmeyen bir projedir. Platformun gelişimi topluluk desteği ile sürdürülmektedir.

### Neden Bağış Yapmalısınız?

🚀 **Server Maliyetleri**: Yüksek performanslı sunucular
🤖 **AI API Kullanımı**: Claude API ücretleri
📊 **Veritabanı Hosting**: PostgreSQL & Redis
🔍 **Elasticsearch**: Güçlü arama altyapısı
👨‍💻 **Geliştirme**: Full-time development

### Bağış Yöntemleri

#### 💳 Kredi/Banka Kartı (Stripe)

[![Stripe Donation](https://img.shields.io/badge/Donate-Stripe-blue?style=for-the-badge&logo=stripe)](https://donate.stripe.com/filegenius)

```
Tek Seferlik: $5, $10, $25, $50, $100
Aylık Destek: $5/ay, $10/ay, $25/ay
```

#### 💵 PayPal

[![PayPal](https://img.shields.io/badge/Donate-PayPal-00457C?style=for-the-badge&logo=paypal)](https://www.paypal.com/donate/?hosted_button_id=FILEGENIUS)

```
PayPal: donate@filegenius.com
```

#### ₿ Kripto Para

```
Bitcoin (BTC):
bc1qxy2kgdygjrsqtzq2n0yrf2493p83kkfjhx0wlh

Ethereum (ETH):
0x1234567890123456789012345678901234567890

USDT (TRC20):
TXyz123456789012345678901234567890
```

#### 🏦 Banka Havalesi (Türkiye)

```
Hesap Sahibi: Özlem Yıldız
Banka: [Banka Adı]
IBAN: TR00 0000 0000 0000 0000 0000 00
Açıklama: FileGenius Donation
```

### Sponsor Seviyeleri

#### 🥉 Bronze Supporter ($5/ay)

- Platform üzerinde “Supporter” rozeti
- Özel Discord kanalına erişim
- Erken özellik erişimi

#### 🥈 Silver Supporter ($10/ay)

- Bronze avantajları +
- Profilinde “Silver Sponsor” badge
- Aylık gelişim raporları
- Özellik önerilerinde öncelik

#### 🥇 Gold Supporter ($25/ay)

- Silver avantajları +
- README’de isim ve link
- Yıllık video call ile proje brifingi
- API rate limit artışı

#### 💎 Diamond Sponsor ($50+/ay)

- Gold avantajları +
- Ana sayfada logo
- Özel özellik geliştirme
- Teknik destek önceliği

### Kurumsal Sponsorluk

Kurumsal sponsor olmak için: **sponsor@filegenius.com**

**Avantajlar:**

- Ana sayfada prominent logo yerleşimi
- Blog yazısı ve sosyal medya duyurusu
- Özel API entegrasyonu
- Whitelabel çözümler
- Dedicated support

-----

## 📊 Reklam Sistemi

Platform, sürdürülebilirliği sağlamak için etik reklam politikası ile Google AdSense kullanmaktadır.

### Reklam Yerleşimi

```typescript
// components/ads/AdUnit.tsx
import { useEffect } from 'react';

export function AdUnit({ slot }: { slot: string }) {
  useEffect(() => {
    try {
      (window.adsbygoogle = window.adsbygoogle || []).push({});
    } catch (err) {
      console.error('AdSense error:', err);
    }
  }, []);

  return (
    <ins
      className="adsbygoogle"
      style={{ display: 'block' }}
      data-ad-client={process.env.NEXT_PUBLIC_ADSENSE_CLIENT_ID}
      data-ad-slot={slot}
      data-ad-format="auto"
      data-full-width-responsive="true"
    />
  );
}
```

### Reklam Politikası

✅ **İzin Verilen:**

- Teknoloji ürün ve servisleri
- Eğitim platformları
- Developer tools
- Cloud services

❌ **İzin Verilmeyen:**

- Kumar ve bahis
- Yetişkin içerik
- Şiddet içerikli oyunlar
- Kripto dolandırıcılığı

### Reklamsız Deneyim

**Premium üyelik** ile reklamsız deneyim:

- $3/ay veya $30/yıl
- Tüm özellikler aktif
- API rate limit 2x
- Öncelikli destek

-----

## 🧪 Testing

```bash
# Unit tests
npm run test

# Integration tests
npm run test:integration

# E2E tests
npm run test:e2e

# Coverage raporu
npm run test:coverage
```

-----

## 📈 Performans

### Benchmarks

```
API Response Time: < 100ms (p95)
Database Query: < 50ms (p95)
AI Analysis: < 3s (avg)
Search Results: < 200ms (p95)
Page Load: < 2s (FCP)
```

### Optimization

- Redis caching (1-hour TTL)
- PostgreSQL indexing
- CDN for static assets
- Image optimization (WebP)
- Code splitting
- Lazy loading

-----

## 🔒 Güvenlik

### Reporting Security Issues

Güvenlik açığı bulursanız: **security@filegenius.com**

**Lütfen public issue açmayın!**

### Security Features

✅ SQL Injection koruması
✅ XSS prevention
✅ CSRF tokens
✅ Rate limiting
✅ File upload scanning
✅ JWT security
✅ HTTPS only
✅ CSP headers

-----

## 📜 Lisans

MIT License - Kar amacı gütmeyen kullanım için ücretsiz

```
Copyright (c) 2025 Özlem Yıldız - FileGenius™

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction for non-commercial purposes.
```

**Ticari kullanım için lisans**: **commercial@filegenius.com**

-----

## 📞 İletişim ve Destek

### Topluluk

- 💬 **Discord**: https://discord.gg/filegenius
- 🐦 **Twitter**: [@FileGeniusPro](https://twitter.com/FileGeniusPro)
- 📧 **Email**: hello@filegenius.com
- 🌐 **Website**: https://filegenius.com

### Destek

- 📖 **Documentation**: https://docs.filegenius.com
- 🎓 **Tutorials**: https://learn.filegenius.com
- 💡 **Feature Requests**: GitHub Issues
- 🐛 **Bug Reports**: GitHub Issues

-----

## 🙏 Teşekkürler

Aşağıdaki projelere teşekkür ederiz:

- [Anthropic Claude](https://anthropic.com) - AI Analysis
- [Next.js](https://nextjs.org) - React Framework
- [PostgreSQL](https://postgresql.org) - Database
- [Redis](https://redis.io) - Caching
- [Elasticsearch](https://elastic.co) - Search Engine

-----

## 📊 İstatistikler

![GitHub stars](https://img.shields.io/github/stars/ozlemyildiz/filegenius-platform?style=social)
![GitHub forks](https://img.shields.io/github/forks/ozlemyildiz/filegenius-platform?style=social)
![GitHub issues](https://img.shields.io/github/issues/ozlemyildiz/filegenius-platform)
![GitHub pull requests](https://img.shields.io/github/issues-pr/ozlemyildiz/filegenius-platform)

-----

<div align="center">

**[Website](https://filegenius.com)** •
**[Documentation](https://docs.filegenius.com)** •
**[Discord](https://discord.gg/filegenius)** •
**[Donate](https://donate.filegenius.com)**

Made with ❤️ by [Özlem Yıldız](https://github.com/ozlemyildiz) and the FileGenius™ Community

</div> filegenius-platform