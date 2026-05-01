# SQL Data Analysis Project - Aggregation & Grouping

This project focuses on advanced data summarizing techniques and is based on a SQL training project provided by Code2Work.

## 📌 What I Did

* Solved complex SQL query tasks focusing on data aggregation (`GROUP BY`, `HAVING`) and aggregate functions (`SUM`, `AVG`, `COUNT`, `MIN`, `MAX`).
* Implemented queries using Python to interact with the PostgreSQL database.
* Passed all test cases successfully.

## 🛠️ Technologies

* Python
* PostgreSQL
* SQL
* pytest

## ✅ Results

* All tests passed successfully

## 📎 Reference

Original project: https://github.com/Code2Work/data-science-project-3

---



# Data Science SQL Project 3 - GROUP BY ve Aggregate Fonksiyonlar

## Proje Kurulumu

1. Projeyi **fork** edin ve kendi hesabınıza **clone** edin.
2. Terminal'de proje klasörüne girin.

### Mac / Linux
```bash
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

### Windows
```bash
python -m venv venv
venv\Scripts\activate
pip install -r requirements.txt
```

## Veritabanı Kurulumu

1. PostgreSQL'in bilgisayarınızda kurulu ve çalışır durumda olduğundan emin olun.
2. `scripts/init_db.py` dosyasındaki SQL komutlarını sırasıyla kendi local veritabanınızda çalıştırın.
3. Tabloların doğru oluştuğundan emin olmak için her tabloya birer `SELECT *` sorgusu atın.

> **Not:** `data/question.py` içindeki `connect_db()` fonksiyonunda veritabanı bağlantı bilgileri var.
> Localinizde test ederken kendi bilgilerinizle değiştirin.
> **Pushlarken bu bilgileri varsayılan haliyle bırakın.**

## Başlangıç Ayarları

1. **`tests/test_question.py`** — Dosyanın altındaki `run_tests()` fonksiyonunda `user_id` değerini **kendi kullanıcı ID'nizle** değiştirin.
2. **`data/question.py`** — `connect_db()` fonksiyonundaki veritabanı şifresini kendi local PostgreSQL şifrenizle değiştirin. **Pushlarken varsayılan haliyle bırakın.**

## Çalışma Şekli

- Sadece `data/question.py` dosyasında çalışın.
- Her fonksiyon içindeki boş `cursor.execute('')` satırına SQL sorgunuzu yazın.
- Diğer dosyaları değiştirmeyin.

## Testleri Çalıştırma

```bash
python watch.py
```

Tek seferlik:
```bash
pytest tests/test_question.py -s -v
```

## Tablolar

### students
| Sütun | Tip |
|-------|-----|
| student_id | SERIAL (PK) |
| first_name | VARCHAR(50) |
| last_name | VARCHAR(50) |
| age | INT |
| city | VARCHAR(50) |

### courses
| Sütun | Tip |
|-------|-----|
| course_id | SERIAL (PK) |
| course_name | VARCHAR(100) |
| category | VARCHAR(50) |

### enrollments
| Sütun | Tip |
|-------|-----|
| enrollment_id | SERIAL (PK) |
| student_id | INT (FK -> students) |
| course_id | INT (FK -> courses) |
| enrollment_date | DATE |

## Sorular

### Bölüm 1: Tarih Fonksiyonları

1. `DATE_TRUNC` ile ay bazlı kayıt sayılarını listele. (`month`, `count` — aya göre sıralı)

2. `DATE_PART` ile kayıtların sadece **yıl bilgisini** al. (Tek sütun: `year`)

### Bölüm 2: Aggregate Fonksiyonlar

3. Tüm öğrencilerin yaşlarının **toplamını** döndür. (Tek değer: `SUM`)

4. Toplam **kurs sayısını** bul. (`SELECT COUNT(course_id) ...` — tek satır döner)

5. Yaşı **ortalama yaştan büyük** olan öğrencileri getir. (Tüm sütunlar, `student_id`'ye göre sıralı)

6. Her kursun **en eski kayıt tarihini** bul. (`course_id`, `first_enrollment` — `course_id`'ye göre sıralı)

### Bölüm 3: GROUP BY + JOIN

7. Her kurs için öğrencilerin **ortalama yaşlarını** bul. (`course_name`, `avg_age` — `course_id`'ye göre sıralı)

8. **En genç** öğrencinin yaşını getir. (Tek değer: `MIN`)

9. Her derse kayıt olmuş **öğrenci sayısını** bul. (`course_name`, `student_count` — `course_id`'ye göre sıralı)

10. Kayıt olunmuş derslerin sadece **isimlerini** getir. (Tek sütun: `course_name` — `course_name`'e göre sıralı, tekrarsız)

---

## İpucu: Ayrı Schema Kullanmak

Localinizdeki PostgreSQL'de başka tablolarla karışmasın istiyorsanız:

```sql
CREATE SCHEMA data3;
```

Tablo ve sorguların başına schema adını ekleyin (`data3.students`, `data3.courses` vb.). Foreign key tanımlarında da schema adını unutmayın. **Pushlarken schema öneki olmadan bırakın.**
