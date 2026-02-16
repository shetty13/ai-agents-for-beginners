# Memori untuk Agen AI  
[![Agent Memory](../../../translated_images/id/lesson-13-thumbnail.959e3bc52d210c64.webp)](https://youtu.be/QrYbHesIxpw?si=qNYW6PL3fb3lTPMk)

Saat membahas manfaat unik dari pembuatan Agen AI, dua hal yang terutama dibahas: kemampuan untuk memanggil alat untuk menyelesaikan tugas dan kemampuan untuk meningkatkan diri seiring waktu. Memori berada di dasar pembuatan agen yang dapat meningkatkan dirinya sendiri yang dapat menciptakan pengalaman yang lebih baik bagi pengguna kami.

Dalam pelajaran ini, kita akan melihat apa itu memori untuk Agen AI dan bagaimana kita dapat mengelolanya serta menggunakannya untuk keuntungan aplikasi kita.

## Pendahuluan

Pelajaran ini akan membahas:

• **Memahami Memori Agen AI**: Apa itu memori dan mengapa itu penting bagi agen.

• **Mengimplementasikan dan Menyimpan Memori**: Metode praktis untuk menambahkan kemampuan memori ke agen AI Anda, dengan fokus pada memori jangka pendek dan panjang.

• **Membuat Agen AI yang Meningkatkan Diri Sendiri**: Bagaimana memori memungkinkan agen belajar dari interaksi masa lalu dan meningkat seiring waktu.

## Implementasi yang Tersedia

Pelajaran ini mencakup dua tutorial notebook yang komprehensif:

• **[13-agent-memory.ipynb](./13-agent-memory.ipynb)**: Mengimplementasikan memori menggunakan Mem0 dan Azure AI Search dengan kerangka kerja Semantic Kernel

• **[13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)**: Mengimplementasikan memori terstruktur menggunakan Cognee, secara otomatis membangun grafik pengetahuan yang didukung oleh embeddings, memvisualisasikan grafik, dan pengambilan cerdas

## Tujuan Pembelajaran

Setelah menyelesaikan pelajaran ini, Anda akan tahu cara:

• **Membedakan berbagai jenis memori agen AI**, termasuk memori kerja, jangka pendek, dan jangka panjang, serta bentuk khusus seperti memori persona dan episodik.

• **Mengimplementasikan dan mengelola memori jangka pendek dan jangka panjang untuk agen AI** menggunakan kerangka kerja Semantic Kernel, memanfaatkan alat seperti Mem0, Cognee, memori Whiteboard, dan integrasi dengan Azure AI Search.

• **Memahami prinsip-prinsip di balik agen AI yang meningkatkan diri sendiri** dan bagaimana sistem pengelolaan memori yang kuat berkontribusi pada pembelajaran dan adaptasi berkelanjutan.

## Memahami Memori Agen AI

Pada intinya, **memori untuk agen AI mengacu pada mekanisme yang memungkinkan mereka menyimpan dan mengingat informasi**. Informasi ini bisa berupa detail spesifik tentang sebuah percakapan, preferensi pengguna, tindakan masa lalu, atau bahkan pola yang dipelajari.

Tanpa memori, aplikasi AI seringkali tanpa status, artinya setiap interaksi dimulai dari awal. Ini menyebabkan pengalaman pengguna yang berulang dan membuat frustrasi di mana agen "melupakan" konteks atau preferensi sebelumnya.

### Mengapa Memori Penting?

Kecerdasan agen sangat terkait dengan kemampuannya untuk mengingat dan memanfaatkan informasi masa lalu. Memori memungkinkan agen untuk:

• **Reflektif**: Belajar dari tindakan dan hasil masa lalu.

• **Interaktif**: Menjaga konteks selama percakapan yang sedang berlangsung.

• **Proaktif dan Reaktif**: Mengantisipasi kebutuhan atau merespons secara tepat berdasarkan data historis.

• **Otonom**: Beroperasi lebih mandiri dengan menarik pengetahuan yang tersimpan.

Tujuan mengimplementasikan memori adalah membuat agen lebih **andal dan mampu**.

### Jenis-jenis Memori

#### Memori Kerja

Anggap ini seperti selembar kertas coretan yang digunakan agen selama satu tugas atau proses berpikir yang sedang berlangsung. Ini menyimpan informasi langsung yang diperlukan untuk menghitung langkah berikutnya.

Untuk agen AI, memori kerja sering menangkap informasi paling relevan dari sebuah percakapan, bahkan jika riwayat chat lengkap panjang atau terpotong. Fokusnya adalah mengekstrak elemen kunci seperti kebutuhan, proposal, keputusan, dan tindakan.

**Contoh Memori Kerja**

Dalam agen pemesanan perjalanan, memori kerja mungkin menangkap permintaan saat ini dari pengguna, seperti "Saya ingin memesan perjalanan ke Paris". Kebutuhan spesifik ini disimpan dalam konteks langsung agen untuk mengarahkan interaksi saat ini.

#### Memori Jangka Pendek

Jenis memori ini menyimpan informasi selama satu percakapan atau sesi. Ini adalah konteks chat saat ini, memungkinkan agen merujuk kembali ke giliran dialog sebelumnya.

**Contoh Memori Jangka Pendek**

Jika pengguna bertanya, "Berapa biaya penerbangan ke Paris?" dan kemudian melanjutkan dengan "Bagaimana dengan akomodasi di sana?", memori jangka pendek memastikan agen tahu bahwa "di sana" merujuk ke "Paris" dalam percakapan yang sama.

#### Memori Jangka Panjang

Ini adalah informasi yang bertahan di berbagai percakapan atau sesi. Memungkinkan agen mengingat preferensi pengguna, interaksi historis, atau pengetahuan umum selama periode yang lebih lama. Ini penting untuk personalisasi.

**Contoh Memori Jangka Panjang**

Memori jangka panjang mungkin menyimpan bahwa "Ben menyukai ski dan aktivitas luar ruangan, suka kopi dengan pemandangan gunung, dan ingin menghindari lintasan ski tingkat lanjut karena cedera masa lalu". Informasi ini, yang dipelajari dari interaksi sebelumnya, memengaruhi rekomendasi dalam sesi perencanaan perjalanan berikutnya, membuatnya sangat personal.

#### Memori Persona

Jenis memori khusus ini membantu agen mengembangkan "kepribadian" atau "persona" yang konsisten. Memungkinkan agen mengingat detail tentang dirinya sendiri atau peran yang dimaksudkan, membuat interaksi menjadi lebih lancar dan fokus.

**Contoh Memori Persona**

Jika agen perjalanan dirancang sebagai "perencana ski ahli," memori persona mungkin memperkuat peran ini, mempengaruhi responsnya agar sesuai dengan nada dan pengetahuan seorang ahli.

#### Memori Workflow/Episodik

Memori ini menyimpan urutan langkah yang diambil agen selama tugas kompleks, termasuk keberhasilan dan kegagalan. Ini seperti mengingat "episode" atau pengalaman masa lalu untuk belajar darinya.

**Contoh Memori Episodik**

Jika agen mencoba memesan penerbangan tertentu tetapi gagal karena tidak tersedia, memori episodik dapat merekam kegagalan ini, memungkinkan agen mencoba penerbangan alternatif atau menginformasikan pengguna tentang masalah secara lebih terinformasi dalam upaya berikutnya.

#### Memori Entitas

Ini melibatkan ekstraksi dan pengingatan entitas spesifik (seperti orang, tempat, atau benda) dan peristiwa dari percakapan. Memungkinkan agen membangun pemahaman terstruktur dari elemen kunci yang dibahas.

**Contoh Memori Entitas**

Dari percakapan tentang perjalanan sebelumnya, agen mungkin mengekstrak "Paris," "Menara Eiffel," dan "makan malam di restoran Le Chat Noir" sebagai entitas. Dalam interaksi mendatang, agen dapat mengingat "Le Chat Noir" dan menawarkan untuk membuat reservasi baru di sana.

#### Structured RAG (Retrieval Augmented Generation)

Walaupun RAG adalah teknik yang lebih luas, "Structured RAG" disorot sebagai teknologi memori yang kuat. Ia mengekstrak informasi padat dan terstruktur dari berbagai sumber (percakapan, email, gambar) dan menggunakannya untuk meningkatkan presisi, recall, dan kecepatan dalam respons. Berbeda dengan RAG klasik yang hanya mengandalkan kesamaan semantik, Structured RAG bekerja dengan struktur inheren dari informasi.

**Contoh Structured RAG**

Alih-alih hanya mencocokkan kata kunci, Structured RAG dapat mengurai detail penerbangan (tujuan, tanggal, waktu, maskapai) dari email dan menyimpannya secara terstruktur. Ini memungkinkan kueri tepat seperti "Penerbangan apa yang saya pesan ke Paris pada hari Selasa?"

## Mengimplementasikan dan Menyimpan Memori

Mengimplementasikan memori untuk agen AI melibatkan proses sistematis dari **manajemen memori**, yang mencakup pembuatan, penyimpanan, pengambilan, integrasi, pembaruan, dan bahkan "melupakan" (atau menghapus) informasi. Pengambilan adalah aspek yang sangat penting.

### Alat Memori Khusus

#### Mem0

Salah satu cara menyimpan dan mengelola memori agen adalah dengan menggunakan alat khusus seperti Mem0. Mem0 berfungsi sebagai lapisan memori persisten, memungkinkan agen mengingat interaksi relevan, menyimpan preferensi pengguna dan konteks faktual, serta belajar dari keberhasilan dan kegagalan seiring waktu. Ide di sini adalah agen tanpa status berubah menjadi agen dengan status.

Ia bekerja melalui **pipeline memori dua fase: ekstraksi dan pembaruan**. Pertama, pesan yang ditambahkan ke thread agen dikirim ke layanan Mem0, yang menggunakan Large Language Model (LLM) untuk meringkas riwayat percakapan dan mengekstrak memori baru. Selanjutnya, fase pembaruan yang didorong LLM menentukan apakah akan menambah, memodifikasi, atau menghapus memori ini, menyimpannya dalam penyimpanan data hibrida yang dapat mencakup basis data vektor, grafik, dan key-value. Sistem ini juga mendukung berbagai jenis memori dan dapat menggabungkan memori grafik untuk mengelola hubungan antar entitas.

#### Cognee

Pendekatan kuat lainnya adalah menggunakan **Cognee**, memori semantik open-source untuk agen AI yang mengubah data terstruktur dan tidak terstruktur menjadi grafik pengetahuan yang dapat di-query yang didukung oleh embeddings. Cognee menyediakan **arsitektur dual-store** yang menggabungkan pencarian kesamaan vektor dengan hubungan grafik, memungkinkan agen memahami tidak hanya informasi yang mirip, tetapi juga bagaimana konsep saling berhubungan.

Ini unggul dalam **retrieval hibrid** yang menggabungkan kesamaan vektor, struktur grafik, dan penalaran LLM - dari pencarian chunk mentah hingga tanya jawab yang sadar grafik. Sistem ini mempertahankan **memori hidup** yang berkembang dan tumbuh sekaligus tetap dapat di-query sebagai satu grafik terhubung, mendukung konteks sesi jangka pendek dan memori persisten jangka panjang.

Tutorial notebook Cognee ([13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)) menunjukkan pembangunan lapisan memori terpadu ini, dengan contoh praktis mengimpor sumber data beragam, memvisualisasikan grafik pengetahuan, dan melakukan query dengan berbagai strategi pencarian yang disesuaikan dengan kebutuhan spesifik agen.

### Menyimpan Memori dengan RAG

Selain alat memori khusus seperti mem0, Anda dapat memanfaatkan layanan pencarian kuat seperti **Azure AI Search sebagai backend untuk menyimpan dan mengambil memori**, terutama untuk Structured RAG.

Ini memungkinkan Anda mendasari respons agen dengan data Anda sendiri, memastikan jawaban yang lebih relevan dan akurat. Azure AI Search dapat digunakan untuk menyimpan memori perjalanan spesifik pengguna, katalog produk, atau pengetahuan domain lain.

Azure AI Search mendukung kemampuan seperti **Structured RAG**, yang unggul dalam mengekstraksi dan mengambil informasi padat dan terstruktur dari dataset besar seperti riwayat percakapan, email, atau bahkan gambar. Ini memberikan "presisi dan recall superhuman" dibandingkan dengan pendekatan chunking teks dan embedding tradisional.

## Membuat Agen AI Meningkatkan Diri Sendiri

Polanya umum bagi agen yang meningkatkan diri sendiri melibatkan memperkenalkan **"agen pengetahuan"**. Agen terpisah ini mengamati percakapan utama antara pengguna dan agen utama. Perannya adalah untuk:

1. **Mengidentifikasi informasi berharga**: Menentukan apakah ada bagian dari percakapan yang layak disimpan sebagai pengetahuan umum atau preferensi pengguna tertentu.

2. **Ekstrak dan ringkas**: Menyaring pembelajaran atau preferensi penting dari percakapan.

3. **Simpan ke basis pengetahuan**: Menyimpan informasi terestrak ini, seringkali dalam basis data vektor, sehingga dapat diambil kemudian.

4. **Menambah kueri masa depan**: Ketika pengguna memulai kueri baru, agen pengetahuan mengambil informasi relevan yang tersimpan dan menambahkannya ke prompt pengguna, memberikan konteks penting bagi agen utama (mirip RAG).

### Optimasi untuk Memori

• **Manajemen Latensi**: Untuk menghindari memperlambat interaksi pengguna, model yang lebih murah dan cepat dapat digunakan terlebih dahulu untuk dengan cepat memeriksa apakah informasi perlu disimpan atau diambil, hanya memanggil proses ekstraksi/pengambilan yang lebih kompleks saat diperlukan.

• **Pemeliharaan Basis Pengetahuan**: Untuk basis pengetahuan yang terus berkembang, informasi yang jarang digunakan dapat dipindahkan ke "penyimpanan dingin" untuk mengelola biaya.

## Punya Pertanyaan Lebih Lanjut Tentang Memori Agen?

Bergabunglah dengan [Azure AI Foundry Discord](https://aka.ms/ai-agents/discord) untuk bertemu dengan pelajar lain, menghadiri jam kantor, dan mendapatkan jawaban atas pertanyaan Anda tentang Agen AI.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Penafian**:  
Dokumen ini telah diterjemahkan menggunakan layanan terjemahan AI [Co-op Translator](https://github.com/Azure/co-op-translator). Meskipun kami berupaya untuk mencapai ketepatan, harap diperhatikan bahwa terjemahan otomatis dapat mengandung kesalahan atau ketidakakuratan. Dokumen asli dalam bahasa aslinya harus dianggap sebagai sumber otoritatif. Untuk informasi penting, disarankan menggunakan terjemahan profesional oleh manusia. Kami tidak bertanggung jawab atas kesalahpahaman atau interpretasi yang keliru yang timbul dari penggunaan terjemahan ini.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->