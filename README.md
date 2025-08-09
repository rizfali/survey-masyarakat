# Aplikasi Survei Kepuasan Masyarakat

Aplikasi web berbasis Laravel untuk survei kepuasan masyarakat yang memungkinkan pengguna mengisi kuesioner, mencatat jawaban, dan menghasilkan laporan statistik.

## Fitur Utama

### Untuk Pengguna (Public)
- ✅ Melihat daftar survei yang tersedia
- ✅ Mengisi survei dengan berbagai tipe pertanyaan
- ✅ Form yang responsif dan user-friendly
- ✅ Halaman terima kasih setelah submit

### Untuk Admin
- ✅ Dashboard dengan statistik lengkap
- ✅ Manajemen survei (CRUD)
- ✅ Manajemen pertanyaan dengan berbagai tipe
- ✅ Laporan statistik dengan grafik
- ✅ Ekspor data ke PDF/Excel (placeholder)
- ✅ Analisis demografis responden

## Tipe Pertanyaan yang Didukung

1. **Text Input** - Input teks singkat
2. **Text Area** - Input teks panjang
3. **Number Input** - Input angka
4. **Radio Button** - Pilihan tunggal
5. **Checkbox** - Pilihan ganda
6. **Rating (1-5)** - Skala penilaian

## Teknologi yang Digunakan

- **Backend**: Laravel 11.x
- **Frontend**: Bootstrap 5.3
- **Database**: MySQL
- **Charts**: Chart.js
- **Icons**: Font Awesome 6.4

## Instalasi

### Prerequisites
- PHP 8.1+
- Composer
- MySQL/MariaDB
- Node.js & NPM (untuk asset compilation)

### Langkah Instalasi

1. **Clone repository**
   ```bash
   git clone <repository-url>
   cd surveymasyarakat
   ```

2. **Install dependencies**
   ```bash
   composer install
   npm install
   ```

3. **Setup environment**
   ```bash
   cp .env.example .env
   php artisan key:generate
   ```

4. **Konfigurasi database di `.env`**
   ```env
   DB_CONNECTION=mysql
   DB_HOST=127.0.0.1
   DB_PORT=3306
   DB_DATABASE=surveymasyarakat
   DB_USERNAME=root
   DB_PASSWORD=
   ```

5. **Jalankan migration dan seeder**
   ```bash
   php artisan migrate
   php artisan db:seed
   ```

6. **Compile assets (opsional)**
   ```bash
   npm run dev
   ```

7. **Jalankan server**
   ```bash
   php artisan serve
   ```

8. **Akses aplikasi**
   - Public: http://localhost:8000
   - Admin: http://localhost:8000/admin

## Struktur Database

### Tabel Utama

1. **surveys** - Data survei
   - id, title, description, is_active, start_date, end_date, timestamps

2. **questions** - Data pertanyaan
   - id, survey_id, question_text, question_type, options, is_required, order, timestamps

3. **survey_responses** - Data responden
   - id, survey_id, respondent_name, respondent_email, respondent_phone, respondent_address, respondent_age, respondent_gender, session_id, completed_at, timestamps

4. **answers** - Data jawaban
   - id, survey_response_id, question_id, answer_text, timestamps

## Routes

### Public Routes
- `GET /` - Halaman beranda
- `GET /survey/{id}` - Form survei
- `POST /survey/{id}` - Submit survei
- `GET /survey/{id}/thankyou` - Halaman terima kasih

### Admin Routes
- `GET /admin` - Dashboard admin
- `GET /admin/surveys` - Daftar survei
- `GET /admin/surveys/create` - Form buat survei
- `POST /admin/surveys` - Simpan survei
- `GET /admin/surveys/{id}` - Detail survei
- `GET /admin/surveys/{id}/edit` - Form edit survei
- `PUT /admin/surveys/{id}` - Update survei
- `DELETE /admin/surveys/{id}` - Hapus survei
- `GET /admin/questions` - Daftar pertanyaan
- `GET /admin/questions/create` - Form buat pertanyaan
- `POST /admin/questions` - Simpan pertanyaan
- `GET /admin/questions/{id}` - Detail pertanyaan
- `GET /admin/questions/{id}/edit` - Form edit pertanyaan
- `PUT /admin/questions/{id}` - Update pertanyaan
- `DELETE /admin/questions/{id}` - Hapus pertanyaan
- `GET /admin/reports` - Daftar laporan
- `GET /admin/reports/{id}` - Detail laporan
- `GET /admin/reports/{id}/export` - Export laporan

## Fitur Laporan

### Statistik yang Tersedia
- Total responden per survei
- Distribusi demografis (jenis kelamin, usia)
- Analisis jawaban per pertanyaan
- Grafik pie chart untuk pilihan ganda
- Grafik bar chart untuk rating
- Tabel statistik dengan persentase

### Visualisasi Data
- Chart.js untuk grafik interaktif
- Responsive design untuk mobile
- Export ke PDF/Excel (dalam pengembangan)

## Keamanan

- CSRF protection untuk semua form
- Validasi input yang ketat
- Session management untuk tracking responden
- Sanitasi data sebelum disimpan

## Pengembangan Selanjutnya

### Fitur yang Direncanakan
- [ ] Authentication & Authorization
- [ ] Multi-language support
- [ ] Advanced analytics
- [ ] Email notifications
- [ ] API endpoints
- [ ] Mobile app integration
- [ ] Real-time dashboard
- [ ] Advanced export features

### Perbaikan Teknis
- [ ] Implementasi PDF export dengan DomPDF
- [ ] Implementasi Excel export dengan Laravel Excel
- [ ] Unit testing
- [ ] Performance optimization
- [ ] Caching implementation

## Kontribusi

1. Fork repository
2. Buat feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit changes (`git commit -m 'Add some AmazingFeature'`)
4. Push ke branch (`git push origin feature/AmazingFeature`)
5. Buat Pull Request

## Lisensi

Distributed under the MIT License. See `LICENSE` for more information.

## Kontak

- Email: [your-email@example.com]
- Project Link: [https://github.com/yourusername/surveymasyarakat]

## Screenshots

### Halaman Beranda
![Homepage](screenshots/homepage.png)

### Form Survei
![Survey Form](screenshots/survey-form.png)

### Dashboard Admin
![Admin Dashboard](screenshots/admin-dashboard.png)

### Laporan Statistik
![Reports](screenshots/reports.png)
