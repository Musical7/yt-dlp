# 🎬 yt-dlp Video Download Guide (YouTube, Facebook, Bilibili, Streamable)

คู่มือ คำสั่งใช้งาน วิธีแก้ไขปัญหา และขั้นตอนการติดตั้ง **yt-dlp** ร่วมกับ **FFmpeg** สำหรับดาวน์โหลดวิดีโอความเร็วสูงจากแพลตฟอร์มชั้นนำ ได้อย่างสมบูรณ์แบบ

---

## 📥 ขั้นตอนการติดตั้ง (Installation)

เพื่อให้สามารถดาวน์โหลดและรวมไฟล์วิดีโอความละเอียดสูง (1080p, 4K) หรือแปลงเป็น MP3 ได้อย่างสมบูรณ์ ควรติดตั้งทั้ง **yt-dlp** และ **FFmpeg** ครับ

### 1. ติดตั้ง yt-dlp
เปิด **PowerShell** หรือ **Command Prompt** แล้วรันคำสั่ง:
```powershell
winget install yt-dlp

```

### 2. ติดตั้ง FFmpeg (จำเป็นสำหรับการผสานไฟล์วิดีโอและเสียง)

รันคำสั่งผ่าน PowerShell:

```powershell
winget install Gyan.FFmpeg

```

> 💡 **ตรวจสอบการติดตั้ง:** พิมพ์ `yt-dlp --version` และ `ffmpeg -version` เพื่อเช็กความพร้อม

---

## 🌐 แพลตฟอร์มที่รองรับและคำสั่งแนะนำ

| แพลตฟอร์ม | ตัวอย่างคำสั่ง / เทคนิคที่แนะนำ |
| --- | --- |
| **YouTube** | ใช้ `--concurrent-fragments` เร่งสปีด และระบุโฟลเดอร์ปลายทาง |
| **Facebook** | ใช้ `--cookies-from-browser` สำหรับวิดีโอในกลุ่มปิดหรือ Private |
| **Bilibili (จีน)** | ใช้ `--concurrent-fragments 100` เร่งสปีดไฟล์ขนาดใหญ่ |
| **Streamable** | ดึงไฟล์ MP3/MP4 ความเร็วสูงโดยตรง |

---

## 🚀 ตัวอย่างคำสั่งใช้งานจริงและวิธีระบุโฟลเดอร์ (PowerShell / CMD)

เพื่อป้องกันปัญหา `Permission Denied` (เนื่องจากบันทึกในโฟลเดอร์ระบบ เช่น System32) แนะนำให้ใช้พารามิเตอร์ `-P` เพื่อระบุโฟลเดอร์ปลายทาง เช่น โฟลเดอร์ Downloads:

### 1. YouTube (พร้อมระบุโฟลเดอร์ Downloads)

```cmd
yt-dlp --concurrent-fragments 16 -P "C:\Users\petch\Downloads" "[https://youtu.be/GgBjViWRDLY](https://youtu.be/GgBjViWRDLY)"

```

### 2. Facebook

```cmd
yt-dlp --cookies-from-browser chrome -P "C:\Users\petch\Downloads" "[https://www.facebook.com/watch/?v=VIDEO_ID](https://www.facebook.com/watch/?v=VIDEO_ID)"

```

### 3. Bilibili (จีน) (เร่งสปีดแบบ 100 Threads)

```cmd
yt-dlp --concurrent-fragments 100 -P "C:\Users\petch\Downloads" "[https://www.bilibili.com/video/BV1Wotf6jE8g/](https://www.bilibili.com/video/BV1Wotf6jE8g/)"

```

### 4. Streamable

```cmd
yt-dlp -P "C:\Users\petch\Downloads" "[https://streamable.com/VIDEO_ID](https://streamable.com/VIDEO_ID)"

```

---

## 🔑 เทคนิคแก้ไขปัญหาและตัวเลือกเพิ่มเติม

### 🔓 ดึง Cookies จากเบราว์เซอร์ (แก้ติด Premium / ล็อกอิน / วิดีโอจำกัดอายุ)

```cmd
yt-dlp --cookies-from-browser chrome "URL_VIDEO"

```

*(เปลี่ยน `chrome` เป็น `edge`, `firefox` หรือ `brave` ตามเบราว์เซอร์ที่ใช้งาน)*

### 🎵 ดึงเฉพาะเสียง (Extract Audio / MP3)

```cmd
yt-dlp -x --audio-format mp3 "URL_VIDEO"

```

---

## 🖼️ ตัวอย่างการใช้งานจริง (Example)

---

## ⚙️ สรุปตัวเลือกพารามิเตอร์สำคัญ

* `-P` / `--paths` : กำหนดโฟลเดอร์ปลายทางสำหรับบันทึกไฟล์ (แก้ปัญหา Permission Denied)
* `--concurrent-fragments N` : กำหนดจำนวน Connection/Fragment สำหรับดาวน์โหลดพร้อมกัน (เช่น 16, 100)
* `--cookies-from-browser` : ดึงข้อมูลสิทธิ์ล็อกอินจากเบราว์เซอร์
* `-x` / `--extract-audio` : ดึงเฉพาะไฟล์เสียงออกจากวิดีโอ
* `-U` / `--update` : อัปเดตตัวโปรแกรม yt-dlp เป็นเวอร์ชันล่าสุด
