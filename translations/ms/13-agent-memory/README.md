# Memori untuk Ejen AI  
[![Memori Ejen](../../../translated_images/ms/lesson-13-thumbnail.959e3bc52d210c64.webp)](https://youtu.be/QrYbHesIxpw?si=qNYW6PL3fb3lTPMk)

Apabila membincangkan faedah unik mencipta Ejen AI, dua perkara utama dibincangkan: kemampuan untuk memanggil alat bagi menyelesaikan tugas dan kemampuan untuk memperbaiki diri dari masa ke masa. Memori adalah asas dalam mencipta ejen yang memperbaiki diri yang boleh menghasilkan pengalaman lebih baik untuk pengguna kita.

Dalam pelajaran ini, kita akan melihat apa itu memori untuk Ejen AI dan bagaimana kita boleh menguruskannya serta menggunakannya untuk manfaat aplikasi kita.

## Pengenalan

Pelajaran ini akan merangkumi:

• **Memahami Memori Ejen AI**: Apa itu memori dan mengapa ia penting untuk ejen.

• **Melaksanakan dan Menyimpan Memori**: Kaedah praktikal untuk menambah keupayaan memori kepada ejen AI anda, dengan fokus pada memori jangka pendek dan jangka panjang.

• **Membuat Ejen AI yang Memperbaiki Diri**: Bagaimana memori membolehkan ejen belajar dari interaksi lampau dan bertambah baik dari masa ke masa.

## Pelaksanaan Tersedia

Pelajaran ini termasuk dua tutorial buku nota komprehensif:

• **[13-agent-memory.ipynb](./13-agent-memory.ipynb)**: Melaksanakan memori menggunakan Mem0 dan Azure AI Search dengan rangka kerja Semantic Kernel

• **[13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)**: Melaksanakan memori berstruktur menggunakan Cognee, secara automatik membina graf pengetahuan yang disokong oleh embeddings, memvisualisasikan graf, dan pengambilan pintar

## Matlamat Pembelajaran

Selepas selesai pelajaran ini, anda akan tahu bagaimana untuk:

• **Membezakan antara pelbagai jenis memori ejen AI**, termasuk memori kerja, jangka pendek, dan jangka panjang, serta bentuk khusus seperti memori persona dan episodik.

• **Melaksanakan dan mengurus memori jangka pendek dan jangka panjang untuk ejen AI** menggunakan rangka kerja Semantic Kernel, memanfaatkan alat seperti Mem0, Cognee, memori Whiteboard, dan integrasi dengan Azure AI Search.

• **Memahami prinsip di sebalik ejen AI yang memperbaiki diri** dan bagaimana sistem pengurusan memori yang mantap menyumbang kepada pembelajaran dan adaptasi berterusan.

## Memahami Memori Ejen AI

Pada intinya, **memori untuk ejen AI merujuk kepada mekanisme yang membolehkan mereka menyimpan dan mengingati maklumat**. Maklumat ini boleh berupa butiran spesifik tentang perbualan, keutamaan pengguna, tindakan lalu, atau pola yang dipelajari.

Tanpa memori, aplikasi AI biasanya adalah tanpa status, bermaksud setiap interaksi bermula dari awal. Ini menyebabkan pengalaman pengguna yang berulang dan mengecewakan di mana ejen "lupa" konteks atau keutamaan sebelumnya.

### Mengapa Memori Penting?

Kecerdasan ejen sangat berkait rapat dengan kebolehan mereka untuk mengingati dan menggunakan maklumat lalu. Memori membolehkan ejen menjadi:

• **Reflektif**: Belajar dari tindakan dan hasil lampau.

• **Interaktif**: Mengekalkan konteks sepanjang perbualan.

• **Proaktif dan Reaktif**: Meramalkan keperluan atau bertindak balas dengan sesuai berdasarkan data sejarah.

• **Autonomi**: Beroperasi lebih bebas dengan menggunakan pengetahuan tersimpan.

Matlamat melaksanakan memori adalah untuk menjadikan ejen lebih **boleh dipercayai dan berkeupayaan**.

### Jenis Memori

#### Memori Kerja

Bayangkan ini seperti sehelai kertas nota yang digunakan ejen semasa menjalankan tugas atau proses pemikiran tunggal yang sedang berlangsung. Ia menyimpan maklumat segera yang diperlukan untuk mengira langkah seterusnya.

Bagi ejen AI, memori kerja sering menangkap maklumat paling relevan dari perbualan, walaupun sejarah sembang penuh panjang atau dipotong. Ia memfokus pada pengambilan elemen utama seperti keperluan, cadangan, keputusan, dan tindakan.

**Contoh Memori Kerja**

Dalam ejen tempahan perjalanan, memori kerja mungkin menangkap permintaan pengguna semasa, seperti "Saya mahu menempah perjalanan ke Paris". Keperluan khusus ini dipegang dalam konteks segera ejen untuk membimbing interaksi semasa.

#### Memori Jangka Pendek

Jenis memori ini menyimpan maklumat selama tempoh satu perbualan atau sesi semata-mata. Ia adalah konteks sembang semasa, membolehkan ejen merujuk kembali giliran terdahulu dalam dialog.

**Contoh Memori Jangka Pendek**

Jika pengguna bertanya, "Berapa kos penerbangan ke Paris?" dan kemudian bertanya, "Bagaimana pula dengan penginapan di sana?", memori jangka pendek memastikan ejen tahu "di sana" merujuk kepada "Paris" dalam perbualan yang sama.

#### Memori Jangka Panjang

Ini adalah maklumat yang berterusan merentas pelbagai perbualan atau sesi. Ia membenarkan ejen mengingati keutamaan pengguna, interaksi sejarah, atau pengetahuan am untuk jangka masa yang panjang. Ini penting untuk personalisasi.

**Contoh Memori Jangka Panjang**

Memori jangka panjang mungkin menyimpan bahawa "Ben suka bermain ski dan aktiviti luar, gemar kopi dengan pemandangan gunung, dan mahu mengelakkan lereng ski maju kerana kecederaan dahulu". Maklumat ini, yang diperoleh dari interaksi sebelumnya, mempengaruhi cadangan dalam sesi perancangan perjalanan akan datang, menjadikannya sangat diperibadikan.

#### Memori Persona

Jenis memori khusus ini membantu ejen membangunkan "personaliti" atau "persona" yang konsisten. Ia membolehkan ejen mengingati butiran tentang dirinya atau peranan yang dimaksudkan, menjadikan interaksi lebih lancar dan berfokus.

**Contoh Memori Persona**

Jika ejen perjalanan direka sebagai "perancang ski pakar," memori persona mungkin menguatkan peranan ini, mempengaruhi responsnya untuk selari dengan nada dan pengetahuan seorang pakar.

#### Memori Aliran Kerja/Episodik

Memori ini menyimpan urutan langkah yang diambil ejen semasa menjalankan tugas kompleks, termasuk kejayaan dan kegagalan. Ia seperti mengingati "episod" tertentu atau pengalaman lampau untuk mengambil pengajaran daripadanya.

**Contoh Memori Episodik**

Jika ejen cuba menempah penerbangan tertentu tetapi gagal kerana ketiadaan tempat, memori episodik boleh merekod kegagalan ini, membolehkan ejen cuba penerbangan alternatif atau memberitahu pengguna mengenai isu tersebut dengan cara yang lebih bermaklumat semasa percubaan berikutnya.

#### Memori Entiti

Ini melibatkan pengekstrakan dan pengingatan entiti spesifik (seperti orang, tempat, atau benda) dan peristiwa dari perbualan. Ia membolehkan ejen membina pemahaman berstruktur tentang elemen utama yang dibincangkan.

**Contoh Memori Entiti**

Daripada perbualan tentang perjalanan lampau, ejen mungkin mengeluarkan "Paris," "Menara Eiffel," dan "makan malam di restoran Le Chat Noir" sebagai entiti. Dalam interaksi masa depan, ejen boleh mengingati "Le Chat Noir" dan menawarkan untuk membuat tempahan baru di sana.

#### RAG Berstruktur (Generasi Diperkuat Pengambilan)

Walaupun RAG adalah teknik yang lebih luas, "RAG Berstruktur" diketengahkan sebagai teknologi memori yang mantap. Ia mengekstrak maklumat padat, berstruktur dari pelbagai sumber (perbualan, emel, imej) dan menggunakannya untuk mempertingkatkan ketepatan, keterbalikan, dan kelajuan respons. Berbeza daripada RAG klasik yang hanya bergantung pada kesamaan semantik, RAG Berstruktur berfungsi dengan struktur maklumat yang ada.

**Contoh RAG Berstruktur**

Daripada hanya memadankan kata kunci, RAG Berstruktur boleh menguraikan butiran penerbangan (destinasi, tarikh, masa, syarikat penerbangan) dari emel dan menyimpannya secara berstruktur. Ini membolehkan pertanyaan tepat seperti "Penerbangan apa yang saya tempah ke Paris pada hari Selasa?"

## Melaksanakan dan Menyimpan Memori

Melaksanakan memori untuk ejen AI melibatkan proses sistematik **pengurusan memori**, yang merangkumi menjana, menyimpan, mengambil, mengintegrasi, mengemaskini, dan bahkan "melupakan" (atau memadam) maklumat. Pengambilan adalah aspek yang amat penting.

### Alat Memori Khusus

#### Mem0

Satu cara untuk menyimpan dan mengurus memori ejen adalah menggunakan alat khusus seperti Mem0. Mem0 berfungsi sebagai lapisan memori berterusan, membolehkan ejen mengingati interaksi relevan, menyimpan keutamaan pengguna dan konteks fakta, serta belajar dari kejayaan dan kegagalan dari masa ke masa. Idea di sini adalah ejen tanpa status bertukar menjadi ejen berstatus.

Ia berfungsi melalui **saluran memori dua fasa: pengekstrakan dan kemas kini**. Pertama, mesej yang ditambah ke benang perbualan ejen dihantar ke perkhidmatan Mem0, yang menggunakan Model Bahasa Besar (LLM) untuk meringkaskan sejarah perbualan dan mengekstrak memori baru. Seterusnya, fasa kemas kini yang dikendalikan oleh LLM menentukan sama ada untuk menambah, mengubah suai, atau memadam memori ini, menyimpannya dalam stor data hibrid yang boleh merangkumi pangkalan data vektor, graf, dan kunci-nilai. Sistem ini juga menyokong pelbagai jenis memori dan boleh menggabungkan memori graf untuk mengurus hubungan antara entiti.

#### Cognee

Pendekatan berkuasa lain adalah menggunakan **Cognee**, memori semantik sumber terbuka untuk ejen AI yang mengubah data berstruktur dan tidak berstruktur menjadi graf pengetahuan yang boleh dicari yang disokong oleh embeddings. Cognee menyediakan **arsitektur dwi-stor** yang menggabungkan carian kesamaan vektor dengan hubungan graf, membolehkan ejen memahami bukan sahaja apa maklumat yang serupa, tetapi bagaimana konsep berkaitan antara satu sama lain.

Ia cemerlang dalam **pengambilan hibrid** yang menggabungkan kesamaan vektor, struktur graf, dan penaakulan LLM - dari carian pecahan mentah hingga menjawab soalan yang sedar graf. Sistem mengekalkan **memori hidup** yang berkembang dan bertambah sambil kekal boleh dicari sebagai satu graf bersambung, menyokong konteks sesi jangka pendek dan memori berterusan jangka panjang.

Tutorial buku nota Cognee ([13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)) menunjukkan pembinaan lapisan memori bersatu ini, dengan contoh praktikal memproses pelbagai sumber data, memvisualisasikan graf pengetahuan, dan membuat pertanyaan dengan strategi carian berbeza yang disesuaikan dengan keperluan ejen tertentu.

### Menyimpan Memori dengan RAG

Selain alat memori khusus seperti mem0, anda boleh memanfaatkan perkhidmatan carian mantap seperti **Azure AI Search sebagai backend untuk menyimpan dan mengambil memori**, terutamanya untuk RAG berstruktur.

Ini membolehkan anda mengasaskan respons ejen anda dengan data sendiri, menjamin jawapan yang lebih relevan dan tepat. Azure AI Search boleh digunakan untuk menyimpan memori perjalanan khusus pengguna, katalog produk, atau sebarang pengetahuan khusus domain lain.

Azure AI Search menyokong keupayaan seperti **RAG Berstruktur**, yang cemerlang dalam mengekstrak dan mengambil maklumat padat, berstruktur daripada set data besar seperti sejarah perbualan, emel, atau bahkan imej. Ini memberikan "ketepatan dan keterbalikan superhuman" berbanding pendekatan pecahan teks dan embeddings tradisional.

## Membuat Ejen AI Memperbaiki Diri

Corak biasa untuk ejen yang memperbaiki diri melibatkan memperkenalkan **“ejen pengetahuan”**. Ejen berasingan ini memerhati perbualan utama antara pengguna dan ejen utama. Peranannya adalah untuk:

1. **Kenal pasti maklumat bernilai**: Tentukan jika mana-mana bahagian perbualan berbaloi disimpan sebagai pengetahuan umum atau keutamaan pengguna khusus.

2. **Ekstrak dan ringkaskan**: Memadatkan pembelajaran penting atau keutamaan dari perbualan.

3. **Simpan dalam pangkalan pengetahuan**: Menyimpan maklumat yang diekstrak ini, selalunya dalam pangkalan data vektor, supaya boleh diambil kemudian.

4. **Menguatkan pertanyaan masa depan**: Apabila pengguna memulakan pertanyaan baru, ejen pengetahuan mengambil semula maklumat tersimpan yang relevan dan menambahkannya ke dalam prompt pengguna, memberikan konteks penting kepada ejen utama (serupa dengan RAG).

### Pengoptimuman untuk Memori

• **Pengurusan Latensi**: Untuk mengelakkan memperlahankan interaksi pengguna, model yang lebih murah dan pantas boleh digunakan pada mulanya untuk cepat memeriksa sama ada maklumat berbaloi untuk disimpan atau diambil, hanya memanggil proses ekstrak/pengambilan yang lebih kompleks bila perlu.

• **Penyenggaraan Pangkalan Pengetahuan**: Untuk pangkalan pengetahuan yang berkembang, maklumat yang kurang kerap digunakan boleh dipindahkan ke "stor sejuk" untuk mengurus kos.

## Ada Soalan Lagi Mengenai Memori Ejen?

Sertai [Discord Azure AI Foundry](https://aka.ms/ai-agents/discord) untuk berjumpa dengan pelajar lain, menghadiri waktu pejabat dan dapatkan jawapan bagi soalan Ejen AI anda.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Penafian**:  
Dokumen ini telah diterjemahkan menggunakan perkhidmatan terjemahan AI [Co-op Translator](https://github.com/Azure/co-op-translator). Walaupun kami berusaha untuk ketepatan, sila ambil perhatian bahawa terjemahan automatik mungkin mengandungi kesilapan atau ketidakakuratan. Dokumen asal dalam bahasa asalnya hendaklah dianggap sebagai sumber yang sahih. Untuk maklumat kritikal, terjemahan profesional oleh manusia adalah disyorkan. Kami tidak bertanggungjawab atas sebarang salah faham atau salah tafsir yang timbul daripada penggunaan terjemahan ini.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->