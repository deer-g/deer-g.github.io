---
title: "A03:2021-Injection: Ketika Aplikasi Lu "Keracunan" Data"
description: Penjelasan singkat Injection.
tags: [Security]
---
Yo, apa kabar guys? Udah pada tau belom sih tentang A03:2021-Injection? Kalo belom, tenang aja. Gue bakal jelasin ke lu semua tentang masalah yang satu ini. Tapi sebelumnya, lu pada tau gak sih kalo aplikasi yang lu pake sehari-hari itu bisa "keracunan"? Iya bener, keracunan data! Anjir kan?

## Apa sih A03:2021-Injection itu?

Jadi gini, A03:2021-Injection itu sebenernya cuma nama keren buat masalah yang udah lama banget ada di dunia teknologi. Intinya, ini tuh kayak lu ngasih makan orang yang lagi diet pake makanan yang dia gak boleh makan. Aplikasi lu jadi "keracunan" gara-gara ada data yang harusnya gak boleh masuk, eh malah bisa nyelip masuk.

Bayangin aja, lu punya warung kopi yang terkenal banget. Terus ada pelanggan yang iseng nulis di kertas pesanan: "Kasih gue semua duit di kasir!". Nah, kalo sistem lu gak pinter, bisa-bisa pegawai lu beneran ngasih semua duit di kasir ke tuh pelanggan. Gila kan?

## Kenapa sih ini bisa terjadi?

Nah, ini nih yang sering bikin developer pusing tujuh keliling. Masalahnya tuh simpel banget sebenernya: aplikasi lu terlalu percaya sama input yang dikasih user. Kayak lu yang terlalu percaya sama mantan yang bilang "kita temenan aja ya". Padahal mah, belakangan dia malah nyebar aib lu ke mana-mana. 

Jadi, aplikasi yang gak punya "filter" yang bagus, bakal gampang banget kena injection. Ini tuh kayak lu minum jus buah, tapi gak disaring dulu. Jadinya, biji-bijian sama ampasnya ikutan masuk ke mulut lu. Gak enak kan?

## Gimana sih cara kerjanya?

Oke, jadi gini. Injection itu biasanya terjadi pas aplikasi ngirim data ke sistem lain, kayak database misalnya. Nah, kalo data yang dikirim itu gak di-filter dengan bener, bisa aja ada kode jahat yang nyelip.

Contohnya gini:
1. Lu punya form login di website lu.
2. Ada hacker iseng yang masukin username: `admin' --`
3. Query SQL yang harusnya: `SELECT * FROM users WHERE username = 'admin' AND password = 'password123'`
4. Jadi kebaca gini: `SELECT * FROM users WHERE username = 'admin' -- AND password = 'password123'`
5. Nah loh, password-nya jadi di-skip dong! Si hacker bisa masuk tanpa password.

Gila gak tuh? Cuma gara-gara dua karakter doang (`--`), si hacker bisa masuk ke sistem lu. Ini mah kayak maling yang bisa masuk rumah cuma gara-gara lu lupa ngunci pintu belakang. Padahal pintu depan udah dikasih gembok segede gaban.

## Tipe-tipe Injection yang Sering Nongol

Lu kira cuma ada satu jenis injection doang? Wah, kalian salah besar guys! Ada banyak banget jenisnya, nih gue kasih tau beberapa yang paling sering bikin orang panik:

1. SQL Injection: Ini nih yang tadi gue jelasin. Paling populer dan paling sering bikin database jadi kacau.

2. NoSQL Injection: Mirip-mirip SQL Injection, tapi buat database yang gak pake SQL. Tetep aja bahaya sih.

3. Command Injection: Ini mah lebih parah. Hacker bisa ngejalanil perintah langsung di server lu. Bayangin aja, kayak lu ngasih remote TV ke orang asing, terus dia bisa ganti-ganti channel sesuka hati.

4. LDAP Injection: Kalo yang ini nyerang sistem otentikasi. Bisa-bisa hacker dapet akses ke data rahasia perusahaan lu.

5. XPath Injection: Nah kalo ini nyerang aplikasi yang pake XML. Jarang-jarang sih, tapi kalo kena ya tetep aja berabe.

## Dampaknya Apa Aja Sih?

Lu mungkin mikir, "Ah elah, cuma data doang. Gak penting-penting amat kali." Eh, jangan salah gaes! Dampaknya tuh bisa bikin lu mewek seharian:

1. Data Bocor: Bayangin aja, data pribadi lu, nomor kartu kredit, sampe foto aib lu bisa kebaca sama orang lain. Mau ditaro di mana tuh muka?

2. Uang Raib: Kalo yang kena itu sistem perbankan, bisa-bisa duit lu lenyap dalam sekejap. Mau pake alesan apa tuh sama bini kalo ditanya uang bulanan?

3. Reputasi Ancur: Coba deh lu bayangin, tiba-tiba website perusahaan lu isinya jadi iklan obat kuat. Mau gimana jelasinnya ke klien?

4. Sistem Lumpuh: Yang paling parah, seluruh sistem lu bisa down. Bayangin aja kalo lu punya toko online, terus pas lagi ada flash sale malah gak bisa diakses. Berabe kan?

## Cara Ngelindungin Diri dari Injection

Nah, sekarang pertanyaannya: gimana caranya biar gak kena injection? Tenang, gue kasih tau triknya:

1. Validasi Input: Jangan asal terima input dari user. Cek dulu, bersih gak tuh data. Kayak lu ngecek makanan sebelum dimakan, takut ada racunnya.

2. Pake Prepared Statements: Ini tuh kayak lu bikin template buat query database. Jadi data dari user gak bisa sembarangan masuk ke query.

3. Escape Special Characters: Kalo ada karakter aneh-aneh, ubah jadi bentuk yang aman. Ini kayak lu ngilangin duri dari ikan sebelum dimakan.

4. Principle of Least Privilege: Kasih akses seminimal mungkin ke setiap bagian sistem. Jangan kayak ortu yang ngasih anak SD kartu kredit tanpa limit.

5. Update Terus: Selalu update sistem keamanan lu. Hacker tuh pinter-pinter, jadi lu juga harus pinter ngikutin perkembangannya.

6. Web Application Firewall (WAF): Ini kayak satpam virtual buat website lu. Dia bakal ngecek setiap request yang masuk, kalo mencurigakan langsung ditendang.

## Kenapa Sih Masih Banyak yang Kena?

Nah, lu pasti mikir, "Anjir, gampang banget ya cara ngelindunginnya. Kok masih banyak yang kena?" Jawabannya simpel: karena banyak developer yang males atau gak tau.

Bayangin aja, lu disuruh bikin website dalam waktu seminggu. Lu pasti fokus ke fitur-fitur yang keliatan doang kan? Nah, keamanan itu kayak fondasi rumah, gak keliatan tapi super penting. Sayangnya, banyak yang ngelupain ini.

Terus, ada juga yang mikir, "Ah, website gue mah gak penting. Gak bakal ada yang mau nyerang." Eh tau-tau, website lu jadi sarang bot yang nyebarin spam. Kocak kan?

## Kesimpulan

Jadi intinya, A03:2021-Injection itu masalah yang serius banget, tapi sering dianggap sepele. Ini tuh kayak lu ninggalin pintu rumah gak dikunci pas lagi liburan. Mungkin gak kenapa-kenapa, tapi kalo sampe ada maling masuk, lu bakal nyesel seumur hidup.

Inget ya gaes, di dunia digital ini, data lu tuh lebih berharga dari apapun. Jangan sampe gara-gara males dikit, data lu jadi santapan hacker. Mulai sekarang, jadi lebih aware sama keamanan aplikasi yang lu pake atau lu bikin. 

Tapi ya itu tadi, jangan juga lu jadi parno berlebihan. Yang penting, pake akal sehat, update pengetahuan, dan selalu waspada. Gak susah-susah amat kan?

## Peringatan Penutup

Eh, tapi inget ya gaes. Artikel ini cuma opini gue doang berdasarkan pengetahuan yang gue punya. Bukan berarti lu harus percaya 100% sama apa yang gue omongin. Tetep kritis, cari tau sendiri, dan jangan ragu buat nanya ke yang lebih ahli. Soalnya di dunia teknologi, apa yang bener hari ini, bisa aja udah basi besok. Jadi, keep learning dan stay safe ya!