# 🎹 Air Keys Studio

> 📺 **Referensi utama:** konsep "air keys" / dua roda nada ala **SoundGo** ([@gojaehyun](https://www.instagram.com/gojaehyun.go/) · soundgo.vercel.app)

Mainkan chord di udara — lewat **dua roda (wheel)** yang melayang di atas video webcam.
**Tangan kiri** memilih **nada dasar (root)** di roda kiri, **tangan kanan** memilih
**jenis chord** di roda kanan, keduanya dengan gerakan _pinch_ (jempol + telunjuk).
Chord berbunyi memakai **gelombang sine** selama tangan kiri menahan pinch.

Seluruh aplikasi ada dalam **satu file `index.html`** — tanpa build, tanpa backend,
tanpa dependensi yang perlu di-_install_. Cukup buka di browser.

---

## ✨ Fitur

- 🖐️ **Deteksi 2 tangan real-time** dengan [MediaPipe Hands](https://google.github.io/mediapipe/solutions/hands).
- 🎡 **Roda kiri — pemilih nada:** searah jarum jam dari atas, tengah = `OFF` (diam). Ikut checkbox **Simple**: dicentang = 7 tuts putih `C D E F G A B`, dilepas = 12 nada kromatik `C C# D D# E F F# G G# A A# B`.
- 🎡 **Roda kanan — pemilih jenis chord:** 8 segmen `maj · maj7 · 7 · sus4 · m · m7 · dim · aug`. Hanya di mode **Two-hand Chord** — pada mode **Single Note** roda ini hilang sepenuhnya dan tangan kanan diabaikan.
- 👌 **Pilih lewat pinch** — dekatkan jempol & telunjuk di area roda; segmen yang ditunjuk menyala oranye dengan pointer dot (gaya `Major G`).
- 🔊 **Suara gelombang sine** ([Tone.js](https://tonejs.github.io/)) — 4 `Tone.Oscillator` yang berbunyi terus-menerus; saat root/quality berganti, frekuensi tiap voice **di-glide** (`frequency.rampTo`) & gain di-fade, **bukan** di-trigger ulang → perpindahan tidak memotong suara (sama seperti sound.gojaehyun.com).
- 🎛️ **Toolbar** ala referensi: Mode (Two-hand Chord / Single Note), Snap, Simple (ABCDEFG), Scale (Major/Minor), Wave (Sine/Triangle/Square/Sawtooth), Range (1–3 oktaf).
- 🎯 **Mode Single Note:** roda kiri tetap di tempatnya, roda kanan hilang, tangan kanan tidak dipakai. Nada berbunyi tunggal (4 voice unison, terdengar satu nada tapi lebih tebal) dan sel *Quality* di status bar jadi `—`. Pilihan quality lama tetap tersimpan saat kembali ke mode Chord.
- 🎚️ **Slider sensitivitas pinch** dan **slider volume** master (−40 dB s/d +6 dB; posisi paling kiri = Mute).
- 🎵 **Transpose −12…+12 semiton.** Menggeser *nada*, bukan tampilan: label roda tetap `C D E F G A B` apa adanya, sementara status bar menampilkan nada yang benar-benar berbunyi (pinch `C` dengan transpose `+2` → roda tetap tulis `C`, status bar tulis `D`).
- 📊 **Status bar:** root terpilih, quality, chord aktif, dan level audio output.
- 🌑 Antarmuka _dark theme_ dengan overlay roda transparan di atas video.

---

## 🎮 Cara Bermain

1. Klik **▶ Mulai** dan izinkan akses webcam.
2. Dua roda muncul di kiri & kanan layar.
3. **Tangan kiri:** arahkan ke segmen nada di roda kiri lalu **pinch** → root terpilih & chord mulai berbunyi.
4. **Tangan kanan:** arahkan ke segmen jenis chord di roda kanan lalu **pinch** → mengubah kualitas chord.
5. Arahkan tangan kiri ke **OFF** (tengah roda) untuk berhenti, atau lepas pinch.

> 💡 Roda kiri ditunjuk oleh **tangan kiri** dan roda kanan oleh **tangan kanan** —
> posisinya sudah cocok dengan tampilan cermin (selfie).

---

## 🚀 Cara Menjalankan

**Cukup buka `index.html` di Google Chrome** (double-click). Untuk hasil terbaik
(beberapa browser membatasi webcam pada `file://`), jalankan server lokal:

```bash
cd air-keys-gojaehyun
python3 -m http.server 8000
# lalu buka http://localhost:8000
```

---

## 🛠️ Teknologi

- **MediaPipe Hands** (via CDN) — deteksi 21 landmark tangan real-time.
- **Tone.js** (via CDN) — `PolySynth(Sine)` untuk sintesis chord.
- **HTML5 Canvas** — render roda + overlay di atas video (mirror selfie).
- **Vanilla JavaScript** — tanpa framework, tanpa backend.
