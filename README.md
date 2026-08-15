# Distribution-Management-System
This project is a comprehensive Fleet &amp; Micro-Distribution Management System designed for logistics companies, food &amp; FMCG distributors, and wholesale suppliers. It models the entire operational lifecycle — from order placement by supermarkets, through warehouse loading and delivery trips, to proof of delivery, invoicing, and payment tracking.


# 🚚 Fleet & Micro-Distribution Management System
### Filo ve Mikro Dağıtım Yönetim Sistemi | سیستم مدیریت ناوگان و پخش مویرگی

*A portfolio project in Software Analysis & Relational Database Design for wholesale distribution logistics.*

🌐 **Languages:** [🇬🇧 English](#-english) • [🇹🇷 Türkçe](#-türkçe) • [🇮 فارسی](#-فارسی)

📌 **Status:** Database design complete — BPMN, state machines & user stories in progress
🎯 **Domain:** Logistics • FMCG Distribution • Van Sales • Fleet Management

---

## 📁 Repository Structure

```
├── documents/
│   └── html                    # a html file to view and analyse the project  
├── database/
│   └── schema.sql              # Full DDL (38 tables, 5 schemas)
├── docs/
│   ├── document.html           #a html file to view and analyse the whole project and Trilingual table documentation (FA / EN / TR)
└── README.md
```

---

## 🇬 English

### 📖 Overview
This project is a comprehensive **Fleet & Micro-Distribution Management System** designed for logistics companies, food & FMCG distributors, and wholesale suppliers. It models the entire operational lifecycle — from **order placement by supermarkets**, through **warehouse loading and delivery trips**, to **proof of delivery, invoicing, and payment tracking**.

The repository currently contains the complete **relational database design (38 tables across 5 business modules)** with architectural documentation. Process models, wireframes, and user stories are being added progressively.

### 🧩 Modules

| Schema | Responsibility |
|---|---|
| `core` | Users, RBAC roles, dynamic status engine, geographical hierarchy, payments, notifications, OTP authentication |
| `hr` | Internal employees & external customers (supermarket owners) |
| `inv` | Product catalog, producers, tags, warehouses, real-time stock with reserved quantities |
| `mrk` | Supermarket branches, sales orders, order line items, order status history |
| `dlv` | Fleet, drivers, delivery trips, loading lists (two-step approval), proof of delivery, invoices |

### ⭐ Key Features
- ✅ **Multi-warehouse & multi-city** support with hierarchical geographical modeling
- ✅ **Smart Loading List** with two-step approval workflow (Prepared By / Approved By)
- ✅ **Dynamic status tracking** for orders, trips & vehicles — new statuses without code changes
- ✅ **Digital Proof of Delivery (POD)** with receiver identity, signature & receipt image
- ✅ **Reserved inventory management** to prevent overselling
- ✅ **Full audit trail** (status logs + audit fields) on all sensitive entities
- ✅ **OTP-based authentication** with multi-role access control

### 🏗️ Architecture & Design Decisions
- **Modular schema design** — each business domain lives in its own schema
- **PublicID (UUID) + BIGINT ID** — UUIDs exposed in APIs/URLs to prevent ID enumeration; BIGINT keys used internally for high-performance joins
- **Soft Delete + Audit Fields** — `IsDelete / DeletedAt / CreatedBy / DeletedBy` across all core tables for integrity and recoverability
- **Status-driven architecture** — statuses are *data, not code* (`StatusType → Status → CatStatus`), so business workflows evolve without redeployment
- **Normalized relational design** with explicit foreign-key constraints

### 🗺️ Roadmap
- [x] Relational database design (ERD + DDL)
- [ ] BPMN 2.0 end-to-end process models
- [ ] State machine diagrams (Order, DeliveryTrip)
- [ ] User stories with acceptance criteria
- [ ] Wireframes (driver app, warehouse panel, manager dashboard)
- [ ] Sequence diagrams & API contracts (OpenAPI)

---

## 🇹🇷 Türkçe

### 📖 Tanıtım
Bu proje, lojistik şirketleri, gıda ve hızlı tüketim (FMCG) dağıtıcıları ve toptan tedarikçiler için tasarlanmış kapsamlı bir **Filo ve Mikro Dağıtım Yönetim Sistemi**'dir. **Süpermarket siparişlerinden** başlayıp **depo yükleme ve dağıtım seyahatleri** üzerinden **teslimat kanıtı, faturalama ve ödeme takibine** kadar tüm operasyonel yaşam döngüsünü modeller.

Depo şu anda **5 iş modülünde 38 tabloluk eksiksiz ilişkisel veritabanı tasarımını** ve mimari dokümantasyonu içermektedir. Süreç modelleri, wireframe'ler ve kullanıcı hikayeleri aşamalı olarak eklenmektedir.

### ⭐ Temel Özellikler
- ✅ Hiyerarşik coğrafi modelleme ile **çoklu depo ve çoklu şehir** desteği
- ✅ İki aşamalı onay iş akışına sahip **Akıllı Yükleme Listesi** (Hazırlayan / Onaylayan)
- ✅ Sipariş, seyahat ve araçlar için **dinamik durum takibi** — kod değişikliği gerektirmez
- ✅ Alıcı kimliği, imza ve fiş görseli içeren **Dijital Teslimat Kanıtı (POD)**
- ✅ Fazla satışı önleyen **rezerve stok yönetimi**
- ✅ Tüm hassas varlıklarda **kapsamlı denetim izi**
- ✅ Çoklu rol destekli **OTP tabanlı güvenli kimlik doğrulama**

### 🏗️ Mimari Kararlar
- **Modüler schema tasarımı** — her iş alanı kendi schema'sında
- **PublicID (UUID) + BIGINT** — API'lerde UUID (güvenlik), dahili JOIN'lerde BIGINT (performans)
- **Soft Delete + Denetim Alanları** — veri bütünlüğü ve kurtarılabilirlik için
- **Durum odaklı mimari** — durumlar *kod değil, veridir*; iş akışları yeniden dağıtım olmadan evrilir

---

## 🇮🇷 فارسی

### 📖 معرفی
این پروژه یک **سیستم جامع مدیریت ناوگان و پخش مویرگی** است که برای شرکت‌های لجستیک، توزیع مواد غذایی و تأمین‌کنندگان عمده‌فروش طراحی شده است. این سیستم کل چرخه عملیات را مدل‌سازی می‌کند — از **ثبت سفارش توسط سوپرمارکت‌ها**، از طریق **بارگیری انبار و سفرهای توزیع**، تا **رسید تحویل، فاکتور و پیگیری پرداخت**.

این ریپوزیتوری در حال حاضر شامل **طراحی کامل دیتابیس رابطه‌ای (۳۸ جدول در ۵ ماژول کاری)** به همراه مستندات معماری است. مدل‌های فرآیند، وایرفریم‌ها و یوزر استوری‌ها به صورت مرحله‌به‌مرحله اضافه می‌شوند.

### ⭐ ویژگی‌های کلیدی
- ✅ پشتیبانی از **چند انبار و چند شهر** با مدل‌سازی سلسله‌مراتبی جغرافیایی
- ✅ **لیست بارگیری هوشمند** با جریان تایید دومرحله‌ای (تهیه‌کننده / تاییدکننده)
- ✅ **ردیابی داینامیک وضعیت** سفارش‌ها، سفرها و خودروها — بدون نیاز به تغییر کد
- ✅ **رسید تحویل دیجیتال (POD)** با مشخصات گیرنده، امضا و تصویر رسید
- ✅ **مدیریت موجودی رزروشده** برای جلوگیری از فروش بیش از حد
- ✅ **ردیابی کامل تغییرات (Audit Trail)** برای تمام موجودیت‌های حساس
- ✅ **احراز هویت مبتنی بر OTP** با کنترل دسترسی چند نقشی

### 🏗️ تصمیم‌های معماری
- **طراحی ماژولار schema** — هر حوزه کاری در schema مستقل خود
- **PublicID (UUID) + BIGINT** — UUID در APIها (امنیت)، BIGINT در JOINهای داخلی (پرفورمنس)
- **Soft Delete + فیلدهای Audit** — برای یکپارچگی و قابلیت بازیابی داده
- **معماری وضعیت‌محور** — وضعیت‌ها *داده‌اند نه کد*؛ فرآیندهای کسب‌وکار بدون استقرار مجدد تغییر می‌کنند

---

## 👨‍💻 Atabak Jamshidi | اتابک جمشیدی

**[Atabak jamshidi ]** — Software Analyst | Yazılım Analisti | تحلیلگر نرم‌افزار
📍 Tabriz, Iran • 🌐 Open to remote opportunities (Turkey / EU / iran)
🗣️ Turkish (fluent) • Persian (native) • English (intermediate)

🔗 [LinkedIn](https://www.linkedin.com/in/atabak-j-0b7185226/) • 📧 [atabak.jamshidi@outlook.com]

---

> ⚠️ This is a portfolio/training project demonstrating system analysis & database design skills — not a production system.
