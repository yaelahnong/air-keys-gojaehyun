# 🎹 Air Keys Studio

> 📺 **Referensi utama:** konsep "air keys" / dua roda nada ala **SoundGo** ([@gojaehyun](https://www.instagram.com/p/DXhjQksueS2/) · soundgo.vercel.app)

Mainkan chord di udara — lewat **dua roda (wheel)** yang melayang di atas video webcam.
**Tangan kiri** memilih **nada dasar (root)** di roda kiri, **tangan kanan** memilih
**jenis chord** di roda kanan, keduanya dengan gerakan _pinch_ (jempol + telunjuk).
Chord berbunyi memakai **gelombang sine** selama tangan kiri menahan pinch.

Seluruh aplikasi ada dalam **satu file `index.html`** — tanpa build, tanpa backend,
tanpa dependensi yang perlu di-_install_. Cukup buka di browser.

---

## ✨ Fitur

- 🖐️ **Deteksi 2 tangan real-time** dengan [MediaPipe Hands](https://google.github.io/mediapipe/solutions/hands).
- 🎡 **Roda kiri — pemilih nada:** 7 segmen `C D E F G A B` (searah jarum jam dari atas), tengah = `OFF` (diam).
- 🎡 **Roda kanan — pemilih jenis chord:** 8 segmen `maj · maj7 · 7 · sus4 · m · m7 · dim · aug`.
- 👌 **Pilih lewat pinch** — dekatkan jempol & telunjuk di area roda; segmen yang ditunjuk menyala oranye dengan pointer dot (gaya `Major G`).
- 🔊 **Suara gelombang sine** ([Tone.js](https://tonejs.github.io/)) — chord ditahan (_sustain_) selama tangan kiri pinch, dengan _voice-leading_ mulus saat root berganti.
- 🎛️ **Toolbar** ala referensi: Mode (Two-hand Chord / Single Note), Snap, Simple (ABCDEFG), Scale (Major/Minor), Wave (Sine/Triangle/Square/Sawtooth), Range (1–3 oktaf).
- 🎚️ **Slider sensitivitas pinch.**
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
