# PySpark YouTube Trends

Bu proje, **YouTube Trending Videos** veri setini kullanarak farklı ülkelerdeki popüler video kategorilerini **Apache Spark (PySpark)** ile analiz eder.  
Amaç, büyük veri işleme becerilerini göstermek ve farklı ülkelerdeki trendleri karşılaştırmaktır.

---

## 📂 Veri Seti

Kaynak: [Kaggle – YouTube Trending Video Dataset](https://www.kaggle.com/datasets/datasnaek/youtube-new)

Kullanılan ülkeler:

> US, GB, KR -Diğer kalanlar eklenebilir. CA, DE, FR, IN, JP, MX, RU

Her ülke için iki dosya bulunur:

- `XXvideos.csv` → Videoların detaylı verisi (title, views, likes, dislikes, comment_count, vs.)
- `XX_category_id.json` → Kategori ID - isim eşleşmeleri

---

## ⚙️ Kullanılan Teknolojiler

- **Python 3.10**
- **Apache Spark (PySpark 3.5+)**
- **Matplotlib**
- **Pandas**
- **VSCode**

---

## 🧠 Proje Adımları

1. **Veri Yükleme**  
   Her ülke için CSV ve JSON dosyaları PySpark ile okunur, kategori isimleriyle birleştirilir.
2. **Veri Temizleme**  
   `try_cast()` ile sayısal alanlar dönüştürülür, hatalı veya eksik veriler elenir.
3. **Birleştirme**  
   Tüm ülkeler `unionByName()` ile tek DataFrame’e birleştirilir.
4. **Analiz**
   - Ülke & kategori bazında toplam izlenme
   - Ortalama beğeni oranı (like_ratio)
   - En çok izlenen 10 kategori (her ülke)
5. **Görselleştirme**  
   Matplotlib ile ülke bazında en popüler kategoriler grafik olarak gösterilir.

---

## 🚀 Nasıl Çalıştırılır

1. Sanal ortam oluştur:
   ```bash
   python3.10 -m venv venv
   venv\Scripts\activate
   ```
2. Gereksinimleri kur(venv aktifse)
   pip install -r requirements.txt

**NOT:**
Bu projede spark kullanmayıp pandas ile daha hızlı analiz yapabilirsiniz hatta bu dataset(gb boyutunda degil) için pandas daha hızlı bile çalışır sparkın hazırlık süresi dolayısıyla, bizim amacımız sparkın kullanımını göstermekti.
