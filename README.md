# Ujian Praktik Mobile Programming — Aplikasi Catatan (React Native)

Buatlah aplikasi **Catatan** dengan fitur **CRUD** dan **pencarian**, menggunakan React Native (Expo) dan SQLite.

## Materi yang diujikan
Komponen dasar (View, Text, Image, TextInput) · State · Navigasi/Route · Flexbox · FlatList · Reusable Component · SQLite

## Cara memulai
```bash
npm install
npm start          # menjalankan aplikasi (Expo)
npm test           # menjalankan tester
```
Setelah `npm test`, buka **`hasil-tes/laporan.html`** di browser untuk melihat laporan
(jumlah lulus/gagal, persentase, dan pesan error tiap tes).
Gunakan `npm run test:watch` agar tes berjalan otomatis setiap kali file disimpan.

## Aturan
1. Kerjakan semua bagian bertanda **`TODO`** di folder `src/`.
2. **Jangan mengubah** file `App.js`, `jest.config.js`, folder `__tests__/` dan folder `tester/`.
3. Gunakan **testID** dan **nama fungsi/route persis** seperti spesifikasi di bawah (tester mencarinya berdasarkan nama itu).
4. Nilai ditentukan dari persentase tes yang lulus di laporan.

## Daftar TODO
| No | File | Materi |
|----|------|--------|
| 1 | `src/database/db.js` | SQLite — buat tabel |
| 2 | `src/database/noteRepository.js` | SQLite — query CRUD + pencarian |
| 3 | `src/components/AppButton.js` | Reusable component |
| 4 | `src/components/SearchBar.js` | Reusable component, TextInput |
| 5 | `src/components/NoteCard.js` | Reusable component, Flexbox |
| 6 | `src/components/EmptyState.js` | View, Text, Image |
| 7 | `src/screens/HomeScreen.js` | State, FlatList, pencarian, navigasi |
| 8 | `src/screens/FormScreen.js` | Create & Update |
| 9 | `src/screens/DetailScreen.js` | Read & Delete |
| 10 | `src/navigation/AppNavigator.js` | Navigasi / route |

## Spesifikasi

### Database
- Tabel `notes`: `id` (INTEGER PK AUTOINCREMENT), `title` (TEXT NOT NULL), `content` (TEXT), `created_at` (TEXT)
- `initDatabase()`, `getAllNotes()`, `searchNotes(keyword)`, `getNoteById(id)`,
  `addNote({ title, content })` → mengembalikan id baru, `updateNote(id, { title, content })`, `deleteNote(id)`
- Data diurutkan dari yang terbaru (`id DESC`). Pencarian pada judul **atau** isi.

### Route
| Nama route | Layar | Parameter |
|------------|-------|-----------|
| `Home` | HomeScreen (layar pertama) | – |
| `Form` | FormScreen | `{ id }` (opsional; ada = mode edit) |
| `Detail` | DetailScreen | `{ id }` |

### testID
| Layar / Komponen | testID |
|------------------|--------|
| Home | `home-screen`, `note-list` (FlatList), `add-button` |
| SearchBar | `search-input` |
| NoteCard | `note-card-{id}` (contoh `note-card-3`) |
| EmptyState | `empty-state` |
| Form | `form-screen`, `input-title`, `input-content`, `save-button`, `error-title` |
| Detail | `detail-screen`, `detail-title`, `detail-content`, `edit-button`, `delete-button` |

### Perilaku
- Home menampilkan daftar dari SQLite memakai `FlatList`; jika kosong tampil `EmptyState`.
- Mengetik di `SearchBar` memfilter daftar (judul atau isi, tidak peka huruf besar/kecil).
- Menyimpan form dengan judul kosong **tidak** menyimpan data dan menampilkan teks `error-title`.
- Hapus memakai `Alert.alert` dengan tombol berteks **"Hapus"** sebagai konfirmasi.

## Tips
- Baca pesan error di `hasil-tes/laporan.html`; tiap tes diberi nomor dan penjelasan.
- Kerjakan berurutan dari TODO 1 ke 10: database → komponen → layar → navigasi.
- Tampilan (warna, ukuran, dll.) bebas, selama spesifikasi di atas terpenuhi.
