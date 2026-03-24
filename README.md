# 🎬 MovieDB: PostgreSQL Relational Database System

Bu proje, sosyal bir sinema platformu (Letterboxd alternatifi) için sıfırdan tasarlanmış kapsamlı bir ilişkisel veritabanı (RDBMS) sistemidir. Projenin ana odağı; veri tutarlılığını sağlamak, kullanıcı etkileşimlerini yönetmek ve veritabanı seviyesinde otomasyon (fonksiyon/trigger) kurgulamaktır.

### 🚀 Öne Çıkan Teknik Geliştirmeler

* **Akıllı Öneri Algoritması (PL/pgSQL):** Kullanıcıların izleme geçmişini ve en çok etkileşime girdiği favori türleri analiz ederek yeni filmler öneren `film_oner_favori_ture_gore` fonksiyonu.
* **Veri Bütünlüğü ve Otomasyon (Triggers):**
  * `spam_engelleme`: Kullanıcıların aynı filme mükerrer inceleme veya puan girmesini veritabanı katmanında engelleyen tetikleyici.
  * `clean_user_data`: Yeni üye kayıtlarında kullanıcı adı ve e-posta formatlarını otomatik olarak standartlaştıran veri temizleme yapısı.
* **Analitik Raporlama (Views):**
  * `yonetmen_karnesi`: Yönetmenlerin filmografisine göre genel başarı ve ortalama puan performanslarını listeleyen dinamik görünüm.
  * `pasif_kullanici_alarmi`: Platformda son 90 gün içinde hiçbir aktif eylem (izleme, puanlama) gerçekleştirmeyen kullanıcıları tespit eden analiz sorgusu.

### 🏗️ Veritabanı Mimarisi

Sistem, normalizasyon kurallarına uygun olarak gereksiz veri tekrarını önleyecek şekilde tasarlanmış olup şu temel yapılardan oluşur:

* **Medya Varlıkları:** `film`, `actor`, `director`, `genre` ve `language` tabloları.
* **Kullanıcı Hiyerarşisi:** Temel `user_account` tablosu, abonelik seviyelerini belirleyen `subscriber` (Standart, Gold, Premium) ve kayıtlı olmayan `guest_user` yapıları.
* **Etkileşim Verileri:** 1 ile 10 arasında kısıtlamalı (constraint) puanlama mimarisine sahip `review` ve kullanıcı geçmişini tutan `watch_history` tabloları.

### ⚙️ Kurulum ve Kullanım

Bu repodaki sistem; tüm tablo şemalarını, örnek verileri, fonksiyonları ve tetikleyicileri (triggers) korumak amacıyla bir **PostgreSQL Backup (.sql)** dosyası olarak yüklenmiştir. 

Projeyi lokalinizde çalıştırmak ve incelemek için `.sql` uzantılı dosyayı indirip, pgAdmin veya tercih ettiğiniz bir PostgreSQL istemcisi üzerinden veritabanınıza *Restore (Geri Yükle)* işlemi yapmanız yeterlidir.
