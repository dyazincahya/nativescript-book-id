| Versi | Ditulis Pada | Penulis |
|-------|----|-----|
| 1.0 | *Juni 2024* sampai *Agustus 2024* | [Kang Cahya](https://github.com/dyazincahya) |

# BAB VIII : MERILIS APLIKASI



**8.1 Konfigurasi**

Sebelum Anda mem-build dan merilis aplikasi yang Anda buat ke publik, ada beberapa hal yang perlu Anda perhatikan, di antaranya adalah:

- Application ID
- Application Name
- Launch Icon
- Launch Screen
- <a name="_hlk175462036"></a>Minimum SDK dan Target SDK

Pastikan poin-poin di atas sudah ter-set dengan baik di aplikasi Anda.

**8.1.1 Application ID**

Application ID akan digunakan sebagai identitas unik saat aplikasi Anda dipublikasikan di Google Play Store. Application ID ini sangat krusial dan tidak boleh berubah-ubah, karena berfungsi seperti Primary Key di database. Setelah aplikasi Anda dipublikasikan di Google Play Store, URL aplikasi Anda akan berbentuk seperti ini:

```
https://play.google.com/store/apps/details?id=com.example.appname
```


Di sini, *com.example.appname* adalah Application ID yang sudah Anda tentukan sebelumnya. Untuk mengubah Application ID pada aplikasi yang Anda buat, Anda dapat mengubahnya pada file *nativescript.config.ts*. Ubah pada bagian variabel “id”.

```javascript
import { NativeScriptConfig } from "@nativescript/core";

export default {
  id: "com.example.appname",
  appPath: "app",
  appResourcesPath: "App_Resources",
  android: {
    v8Flags: "--expose_gc",
    markingMode: "none",
  },
} as NativeScriptConfig;
```

**8.1.2 Application Name**

Untuk mengatur Application Name, Anda dapat menambahkan file baru (jika belum ada) dengan nama *strings.xml* pada *App\_Resources\Android\src\main\res\values*. Lalu salin kode di bawah ini dan sesuaikan nama aplikasinya sesuai yang Anda mau.

```xml
<?xml version="1.0" encoding="utf-8"?>
<resources>
    <string name="app_name">Your App Name</string>
    <string name="title_activity_kimera">Your App Name</string>
</resources>
```

**8.1.3 Launch Icon**

Launch icon (juga dikenal sebagai *App Icon* atau *Launcher Icon*) adalah ikon yang digunakan untuk mewakili aplikasi di layar utama (Home Screen) dan di daftar atau list aplikasi (App Drawer) pada perangkat Android. Ikon ini adalah salah satu elemen yang paling terlihat oleh pengguna, dan berfungsi sebagai titik awal interaksi pengguna untuk meluncurkan aplikasi.

![A screenshot of a phone

Description automatically generated](Aspose.Words.b64db7ef-d822-4bf1-aa55-162161ad2fb9.001.png)

***Gambar 8.1 Daftar Launch Icons di App Drawer Android***

Cara mengatur Launch Icon sudah pernah dibahas pada BAB 4. Anda dapat melihatnya kembali di Sub BAB 4.1, poin 8, mengenai perintah *ns resources generate icons*. 

**8.1.4 Launch Screen**

Launch Screen (juga dikenal sebagai *Splash Screen*) adalah layar sementara yang ditampilkan saat aplikasi pertama kali diluncurkan, sebelum aplikasi sepenuhnya siap untuk digunakan. Layar ini biasanya muncul selama beberapa detik, memberikan pengguna visual yang menarik sementara aplikasi memuat sumber daya yang diperlukan di latar belakang.

Di Nativescript, untuk mengatur Launch Screen di lakukan dengan cara di generate, sehingga Anda tidak perlu mengaturnya secara manual, walau begitu, Anda tetap harus menyediakan aset gambarnya terlebih dahulu, rekomendasi gambar untuk Launch Screen adalah berbentuk kotak dengan ukuran tinggi 1000px dan lebar 1000px.

![A logo for a book demo

Description automatically generated](Aspose.Words.b64db7ef-d822-4bf1-aa55-162161ad2fb9.002.png)

***Gambar 8.2 Contoh gambar Launch Screen***

Cara mengatur Launch Screen sudah pernah dibahas pada BAB 4. Anda dapat melihatnya kembali di Sub BAB 4.1, poin 9, mengenai perintah *ns resources generate splashes*.

**8.1.5 Minimum SDK dan Target SDK**

Minimum SDK dan Target SDK adalah dua pengaturan penting dalam pengembangan aplikasi Android yang menentukan kompatibilitas aplikasi dengan versi Android tertentu. Keduanya berperan dalam memastikan bahwa aplikasi Anda dapat berjalan dengan baik pada berbagai perangkat Android yang memiliki versi sistem operasi yang berbeda.

1. **Minimum SDK** (minSdkVersion) adalah versi minimum dari sistem operasi Android yang diperlukan untuk menjalankan aplikasi Anda. Ini berarti bahwa perangkat yang menjalankan versi Android lebih rendah dari versi ini tidak akan bisa memasang atau menjalankan aplikasi Anda. Tujuannya untuk mengatur Minimum SDK dapat membantu memastikan bahwa fitur-fitur yang Anda gunakan dalam aplikasi tersedia pada perangkat yang memasang aplikasi. Misalnya, jika Anda menggunakan API yang hanya tersedia di Android 6.0 (API level 23), Anda perlu menetapkan minSdkVersion ke 23 atau lebih tinggi. Dengan menetapkan Minimum SDK ke versi yang lebih rendah, aplikasi Anda bisa menjangkau lebih banyak pengguna. Namun, Anda harus berhati-hati untuk memastikan bahwa aplikasi masih berfungsi dengan baik pada semua versi yang didukung. Risiko menetapkan minSdkVersion terlalu rendah bisa membuat aplikasi Anda harus mengatasi tantangan kompatibilitas, seperti fitur yang tidak didukung atau perilaku yang berbeda pada versi Android yang lebih lama. 
1. **Target SDK** (targetSdkVersion) adalah versi sistem operasi Android yang menjadi target aplikasi Anda. Ini menunjukkan bahwa aplikasi Anda telah diuji dan dirancang untuk berjalan dengan baik pada versi Android tersebut. Tujuan dari mengatur Target SDK adalah untuk membantu sistem operasi memahami bagaimana aplikasi Anda harus berperilaku. Dengan mengatur targetSdkVersion ke versi terbaru yang didukung oleh aplikasi, Anda memastikan bahwa aplikasi akan memanfaatkan fitur dan peningkatan terbaru yang tersedia pada versi Android tersebut. Meskipun aplikasi Anda mungkin menargetkan versi terbaru dari Android, sistem operasi akan tetap memungkinkan aplikasi untuk berjalan pada versi yang lebih lama (sesuai dengan *minSdkVersion*). Namun, beberapa fitur atau perubahan perilaku mungkin diaktifkan hanya jika perangkat menjalankan versi Android yang sesuai dengan *targetSdkVersion* atau lebih tinggi.

Anda dapat mengatur Minimum SDK dan Target SDK pada file *app.gradle* yang berada di *App\_Resources\Android*.

```gradle
android {
  compileSdkVersion 34
  buildToolsVersion "34"

  defaultConfig {
    minSdkVersion 24
    targetSdkVersion 34

    // Version Information
    versionCode 1
    versionName "1.0.0"
    
    generatedDensities = []
  }
}
```

Selain itu, ada banyak hal yang dapat Anda atur atau tambahkan pada file app.gradle, seperti mengonfigurasi Proguard, menambahkan dependencies dari bahasa Native, atau lainnya. Anda juga dapat mengatur informasi versi aplikasi di sini, yang mana informasi ini akan digunakan saat Anda mempublikasikan aplikasi ke Google Play Store.

*Saat Anda mempublikasikan aplikasi di Google Play Store, pastikan Anda selalu menaikkan angka dari versionCode setiap kali ingin memperbarui aplikasi Anda.*

**8.2 Keystore**

Keystore adalah file penyimpanan yang berisi sertifikat kriptografi dan kunci pribadi yang digunakan untuk menandatangani aplikasi Android. Penandatanganan aplikasi dengan Keystore memastikan bahwa aplikasi tersebut sah dan diidentifikasi dengan benar oleh sistem operasi Android. 

**8.2.1 Fungsi Keystore**

Berikut adalah beberapa fungsi Keystore dalam Pengembangan Aplikasi Android:

- Setiap aplikasi yang dipasang pada perangkat Android harus ditandatangani dengan kunci digital yaitu Keystore, gunanya untuk memastikan bahwa aplikasi tersebut berasal dari sumber yang terpercaya.
- Keystore berfungsi untuk membantu dalam memastikan bahwa aplikasi yang dipasang atau diperbarui berasal dari pengembang yang sama.
- Ketika Anda merilis pembaruan untuk aplikasi Anda, Anda harus menggunakan Keystore yang sama untuk menandatangani APK atau AAB. Jika tidak, sistem Android akan menganggap pembaruan sebagai aplikasi yang berbeda dan tidak akan mengizinkan pembaruan tersebut dipasang.
- Aplikasi yang akan diunggah ke Google Play Store harus ditandatangani dengan Keystore. Google Play Store tidak akan menerima aplikasi yang tidak ditandatangani atau yang ditandatangani dengan kunci yang tidak terpercaya.

Maka dari itu sangat di haruskan untuk menyimpan Keystore dengan Aman, Keystore adalah file yang sangat penting. Jika hilang atau tidak dapat diakses, Anda tidak akan dapat memperbarui aplikasi Anda karena Anda tidak bisa menandatanganinya dengan kunci yang sama. 

*Keystore itu bisa di ibaratkan sebagai KTP dari pengembang aplikasi, jadi jangan pernah membagikan Keystore atau kata sandinya dengan siapa pun yang tidak dipercaya, karena dapat digunakan untuk menandatangani aplikasi atas nama Anda.*

**8.2.2 Membuat Keystore**

Untuk membuat Keystore, Anda bisa menggunakan Keytool, yang merupakan bagian dari Java Development Kit (JDK). Berikut adalah perintah dasar untuk membuat Keystore:

```bash
# Format perintah untuk membuat Keystore
keytool -genkey -v -keystore <your_keystore_name>.keystore -keyalg RSA -keysize 2048 -validity 10000 -alias <your_alias_name>

# Contoh perintah untuk membuat Keystore
keytool -genkey -v -keystore my-release-key.keystore -keyalg RSA -keysize 2048 -validity 10000 -alias my-alias
```

- **<your\_keystore\_name>.keystore**: Nama file keystore yang akan dibuat.
- **-keyalg RSA**: Algoritma kunci, biasanya RSA.
- **-keysize 2048**: Ukuran kunci dalam satuan bit.
- **-validity 10000**: Validitas atau masa berlaku kunci dalam satuan hari (10.000 hari berarti sekitar 27 tahun).
- **<your\_alias\_name>**: Alias untuk kunci yang digunakan dalam keystore.

Saat perintah di atas di jalankan, ada beberapa hal yang akan di tanyakan dan harus Anda isi, di antaranya adalah:

- Password for Keystore?
- Alias Name for Keystore?
- What is your first and last name?
- What is the name of your organizational unit?
- What is the name of your organization?
- What is the name of your City or Locality?
- What is the name of your State or Province?
- What is the two-letter country code for this unit?

Pastikan Anda mengisi pertanyaan di atas dengan informasi yang benar sesuai dengan identitas Anda sebagai pengembang. Bisa saja Anda mengisi secara asal-asalan, hanya saja ada konsekuensi negatif yang mungkin dapat terjadi di kemudian hari, di antaranya sebagai berikut:

1. Anda dapat kehilangan identitas pengembang jika informasi diisi sembarangan, keystore tidak akan memberikan identitas pengembang yang sah, yang dapat menimbulkan masalah saat mempublikasikan atau memperbarui aplikasi.
1. Akan timbul masalah saat pembaruan aplikasi jika keystore tidak valid atau informasi di dalamnya tidak konsisten, Anda mungkin tidak dapat menandatangani pembaruan aplikasi. Ini berarti pengguna tidak akan bisa memperbarui aplikasi yang sudah terpasang.
1. Ada potensi mengalami penolakan dari Google Play Store, karena Google Play Store memiliki standar ketat untuk penandatanganan aplikasi. Jika keystore tidak diisi dengan benar, aplikasi Anda bisa ditolak saat diunggah ke Play Store.
1. Ada risiko keamanan jika mengisi data secara asal-asalan, ini dapat mengurangi keamanan aplikasi, membuka kemungkinan bagi pihak yang tidak berwenang untuk meniru tanda tangan Anda dan mendistribusikan versi aplikasi yang telah diubah.
1. Berpotensi kehilangan akses ke aplikasi yang Anda buat sendiri jika Anda tidak menyimpan data keystore dengan baik atau lupa detail penting seperti kata sandi, Anda mungkin tidak akan bisa mengakses atau memperbarui aplikasi Anda di masa depan.

Jadi, sangat penting untuk mengisi data keystore dengan benar dan menyimpannya dengan aman.

Pastikan Anda mengingat Alias Name dan Password dari Keystore Anda, karena dua informasi tersebut akan sering Anda gunakan. Setiap kali Anda melakukan build aplikasi untuk produksi, Anda akan memerlukan keystore, dan saat keystore digunakan, Anda akan diminta untuk memasukkan Alias Name dan Password dari keystore tersebut. Alias Name dan Password keystore ini dapat diibaratkan sebagai Username dan Password untuk login ke sebuah aplikasi.

**8.3 Build Aplikasi**

Pada platform Android terdapat dua format output utama saat melakukan build aplikasi, yaitu APK dan AAB. Kedua format tersebut memiliki peran, kelebihan dan kekurangannya masing-masing. APK merupakan format output Tradisional yang sudah lama ada, sedangkan AAB merupakan format output baru dari Android yang baru di perkenalkan sekitar tahun 2018 lalu pada konferensi Google I/O. Sejak Agustus 2021 format AAB di jadikan format standar untuk mempublikasikan aplikasi Android di Google Play Store.

**8.3.1 Format Output**

Untuk pengujian (testing) dan distribusi langsung, Anda dapat menggunakan format output tradisional, yaitu APK. Format APK memudahkan Anda untuk memasang dan membagikan aplikasi tanpa perlu melalui Google Play Store. Namun, untuk distribusi dan publikasi di Google Play Store, disarankan untuk menggunakan format output AAB. Format AAB sangat direkomendasikan oleh Google karena dapat mengurangi ukuran file saat diunduh dan meningkatkan efisiensi pengiriman aplikasi ke berbagai jenis perangkat, sehingga aplikasi Anda lebih optimal dan cepat diakses oleh pengguna.

APK (Android Package Kit)

Kelebihan

- Mendukung pemasangan langsung
- Mudah dibagikan, Anda bisa dengan mudah membagikan file APK untuk pengujian beta atau distribusi di luar Google Play Store.
- Tidak memerlukan proses tambahan, saat membuat APK, Anda mendapatkan satu file yang siap untuk dipasang, tanpa perlu proses tambahan seperti yang dibutuhkan oleh AAB.

Kekurangan

- Ukuran File Lebih Besar.
- Kurang Optimal, Karena semua sumber daya disertakan, pengguna dengan perangkat tertentu mungkin mengunduh data yang sebenarnya tidak diperlukan. Sehingga proses pengunduhan akan menjadi lebih lama.

AAB (Android App Bundle)

Kelebihan

- Ukuran unduhan menjadi lebih kecil.
- Pengelolaan sumber daya yang lebih baik.
- Mendukung fitur modularisasi, ini memungkinkan pengguna mengunduh modul tertentu hanya ketika diperlukan.

Kekurangan

- Tidak bisa langsung dipasang.
- Tidak cocok untuk distribusi langsung.

**8.3.2 Flag dan Perintah Build**

Perintah dasar untuk melakukan build aplikasi di Nativescript hanya cukup dengan mengetikan perintah:

```bash
ns build <platform_name>
```

Proses build aplikasi terbagi menjadi dua, yaitu Build Development dan Build Production. Ketika Anda menjalankan perintah di atas, itu merupakan perintah untuk melakukan Build Development. Jika Anda ingin melakukan Build Production, Anda dapat menambahkan beberapa flag tambahan, salah satunya adalah flag --release. Flag ini digunakan untuk mengoptimalkan aplikasi Anda untuk distribusi akhir, seperti publikasi ke Google Play Store, dengan memastikan bahwa aplikasi Anda dibangun dalam mode rilis yang lebih efisien dan aman.

Berikut adalah perintah lengkap untuk melakukan build aplikasi. Kita asumsikan letak file Keystore berada pada direktori root drive D.

```bash
# Format perintah
ns build android –release \
  --key-store-path <path-to-your-keystore> \
  --key-store-password <your-key-store-password> \
  --key-store-alias <your-alias-name> \
  --key-store-alias-password <your-alias-password>

# Contoh perintah
ns build android  --release \
  --key-store-path D:\my-release-key.keystore \
  --key-store-password 12345678 \
  --key-store-alias my-alias \
  --key-store-alias-password 12345678
```

*Hilangkan karakter Backslash ( \ ) jika perintah di tulis dalam satu baris yang sama.*

Secara default, format output yang digunakan saat melakukan Build adalah APK. Jika Anda ingin melakukan build dengan format yang lebih spesifik sesuai kebutuhan, Anda dapat menambahkan flag --aab untuk menghasilkan format output AAB, atau --apk untuk tetap menggunakan format output APK.

```bash
# Contoh perintah untuk build dengan format APK
ns build android  --release \
  --key-store-path D:\my-release-key.keystore \
  --key-store-password 12345678 \
  --key-store-alias my-alias \
  --key-store-alias-password 12345678 \
  --apk

# Contoh perintah untuk dengan format AAB
ns build android  --release \
  --key-store-path D:\my-release-key.keystore \
  --key-store-password 12345678 \
  --key-store-alias my-alias \
  --key-store-alias-password 12345678 \
  --aab
```

Semua file hasil build, baik itu format APK maupun AAB, secara default akan disimpan di direktori *NS\_PROJECT/platforms/android/app/build/outputs*. Namun, Anda dapat mengkustomisasi lokasi penyimpanan file hasil build dengan menambahkan flag   *--copy-to*. Misal Anda ingin memindahkan lokasinya ke direktori *NS\_PROJECT/dist/build.apk* atau *NS\_PROJECT/dist/build.aab,* perintahnya kurang lebih seperti ini:

```bash
# Contoh perintah untuk build dengan format APK
ns build android  --release \
  --key-store-path D:\my-release-key.keystore \
  --key-store-password 12345678 \
  --key-store-alias my-alias \
  --key-store-alias-password 12345678 \
  --aab
  --copy-to dist/build.apk

# Contoh perintah untuk dengan format AAB
ns build android  --release \
  --key-store-path D:\my-release-key.keystore \
  --key-store-password 12345678 \
  --key-store-alias my-alias \
  --key-store-alias-password 12345678 \
  --aab
  --copy-to dist/build.aab
```

Berikut adalah flag yang Anda dapat gunakan saat melakukan build aplikasi di Nativescript.

|**Flag**|**Butuh Value?**|**Deskripsi**|
| - | - | - |
|**--release**|Tidak, hanya flag|Membangun aplikasi dalam mode rilis (release mode). Flag ini digunakan saat Anda siap untuk mempublikasikan aplikasi.|
|**--key-store-path**|YA|Mengatur path ke file keystore saat membangun aplikasi Android dalam mode rilis.|
|**--key-store-password**|YA|Mengatur kata sandi keystore yang digunakan untuk membangun aplikasi Android dalam mode rilis.|
|**--key-store-alias**|YA|Mengatur alias keystore yang digunakan untuk membangun aplikasi Android dalam mode rilis.|
|**--key-store-alias-password**|YA|Mengatur kata sandi untuk alias keystore|
|**--copy-to**|YA|Menyalin APK atau AAB hasil build ke lokasi tertentu setelah proses build selesai.|
|**--apk**|Tidak, hanya flag|Menentukan format file output untuk APK|
|**--aab**|Tidak, hanya flag|Menentukan format file output untuk AAB|
|**--env.uglify**|Tidak, hanya flag|Mengaktifkan uglification kode, yang memperkecil ukuran aplikasi dengan menghapus kode yang tidak diperlukan.|
|**--bundle**|Tidak, hanya flag|Mengaktifkan bundling aplikasi menggunakan webpack. Flag ini sering digunakan untuk menghasilkan file yang lebih kecil dan lebih cepat.|
|**--env.production**|Tidak, hanya flag|Mengatur Environment menjadi Production. Biasanya digunakan bersamaan dengan --bundle untuk optimasi aplikasi.|
|**--env.aot**|Tidak, hanya flag|Mengaktifkan Ahead-of-Time (AOT) compilation untuk Aplikasi Nativescript yang menggunakan Angular.|
|**--env.snapshot**|Tidak, hanya flag|Mengaktifkan V8 heap snapshots untuk mempercepat startup aplikasi.|
|**--env.sourceMap**|Tidak, hanya flag|Menghasilkan source maps untuk debugging|
|**--clean**|Tidak, hanya flag|Membersihkan build yang ada sebelumnya sebelum memulai build yang baru|
|**--no-hmr**|Tidak, hanya flag|Menonaktifkan Hot Module Replacement (HMR) saat menjalankan build dalam mode development.|
|**--env.ios**|Tidak, hanya flag|Flag ini digunakan untuk memaksa bundling hanya untuk platform iOS.|
|**--env.android**|Tidak, hanya flag|Flag ini digunakan untuk memaksa bundling hanya untuk platform Android.|

Pada tahap ini, proses build telah selesai. Langkah selanjutnya adalah Anda tinggal mempublikasikan file hasil build ke Google Play Store.

4. **Ringkasan**

Pastikan aplikasi Anda sudah terkonfigurasi dengan baik sebelum di Build dan dipublikasikan ke publik, mulai dari Application ID, Application Name, Launch Icon, Launch Screen, Minimum SDK, Target SDK, dan aspek penting lainnya.

Pastikan juga saat membuat Keystore, Anda mengisi data dengan benar (tidak asal-asalan). Simpan dengan aman file Keystore Anda, terutama data seperti Alias Name dan Password Keystore, karena informasi ini sangat penting dan akan sering digunakan dalam proses build aplikasi.

Saat tahap pengujian, Anda bisa menggunakan format output APK, karena format tersebut dapat dengan mudah dipasang pada perangkat pengguna secara langsung tanpa melalui Google Play Store. Jika Anda tidak berencana mempublikasikan aplikasi di Google Play Store, Anda dapat tetap menggunakan format output APK saat melakukan Build Production. Alasannya sederhana: format APK memudahkan pemasangan aplikasi langsung pada perangkat pengguna tanpa perlu melalui proses distribusi di Google Play Store.

Sangat direkomendasikan untuk menggunakan format output AAB saat mempublikasikan aplikasi di Google Play Store. Alasannya, format AAB dapat menghasilkan ukuran file yang lebih kecil dan mendukung fitur modularisasi. Dengan menggunakan AAB, aplikasi Anda akan lebih cepat dan efisien saat diunduh oleh pengguna dari Play Store dibandingkan dengan menggunakan format output APK.

