# 🎬 yt-dlp Video Download Guide (YouTube, Facebook, Bilibili, Streamable)

คู่มือ คำสั่งใช้งาน และขั้นตอนการติดตั้ง **yt-dlp** ร่วมกับ **FFmpeg** สำหรับดาวน์โหลดวิดีโอความเร็วสูงจากแพลตฟอร์มชั้นนำ ได้แก่ **YouTube**, **Facebook**, **Bilibili จีน** และ **Streamable**

---

## 📥 ขั้นตอนการติดตั้ง (Installation)

เพื่อให้สามารถดาวน์โหลดและรวมไฟล์วิดีโอความละเอียดสูง (1080p, 4K) หรือแปลงเป็น MP3 ได้อย่างสมบูรณ์ ควรติดตั้งทั้ง **yt-dlp** และ **FFmpeg** ครับ

### 1. ติดตั้ง yt-dlp
เปิด **PowerShell** หรือ **Command Prompt** แล้วเลือกใช้คำสั่งตามวิธีที่คุณสะดวก:

* **ผ่าน Winget (แนะนำสำหรับ Windows):**
  ```powershell
  winget install yt-dlp

```

* **ผ่าน Python (pip):**
```powershell
pip install -U yt-dlp

```



### 2. ติดตั้ง FFmpeg (จำเป็นสำหรับการผสานไฟล์วิดีโอ+เสียงความชัดสูง)

* **ผ่าน Winget (แนะนำสำหรับ Windows):**
```powershell
winget install Gyan.FFmpeg

```



> 💡 **ตรวจสอบการติดตั้ง:** พิมพ์ `yt-dlp --version` และ `ffmpeg -version` หากขึ้นเลขเวอร์ชันแสดงว่าพร้อมใช้งานแล้ว

---

## 🌐 แพลตฟอร์มที่รองรับและคำสั่งแนะนำ

| แพลตฟอร์ม | ตัวอย่างคำสั่ง / เทคนิคที่แนะนำ |
| --- | --- |
| **YouTube** | ใช้ `--concurrent-fragments` เร่งสปีด และ `--cookies-from-browser` สำหรับวิดีโอความชัดสูง |
| **Facebook** | ใช้ `--cookies-from-browser` สำหรับวิดีโอในกลุ่มปิดหรือ Private |
| **Bilibili (จีน)** | ใช้ `--concurrent-fragments 100` เร่งสปีดไฟล์ขนาดใหญ่ |
| **Streamable** | ดึงไฟล์ MP3/MP4 ความเร็วสูงโดยตรง |

---

## 🚀 ตัวอย่างคำสั่งใช้งานจริง (PowerShell / CMD)

### 1. YouTube

ดาวน์โหลดคลิป YouTube ความละเอียดสูงสุด พร้อมเร่งสปีดดาวน์โหลด:

```cmd
yt-dlp --concurrent-fragments 16 "[https://www.youtube.com/watch?v=VIDEO_ID](https://www.youtube.com/watch?v=VIDEO_ID)"

```

### 2. Facebook

ดาวน์โหลดวิดีโอ Facebook (หากเป็นวิดีโอ Private หรืออยู่ในกลุ่ม แนะนำให้ดึง Cookies จากเบราว์เซอร์):

```cmd
yt-dlp --cookies-from-browser chrome "[https://www.facebook.com/watch/?v=VIDEO_ID](https://www.facebook.com/watch/?v=VIDEO_ID)"

```

### 3. Bilibili (จีน)

ดาวน์โหลดวิดีโอ Bilibili เร่งความเร็วแบบ 100 Threads:

```cmd
yt-dlp --concurrent-fragments 100 "[https://www.bilibili.com/video/BV1Wotf6jE8g/](https://www.bilibili.com/video/BV1Wotf6jE8g/)"

```

### 4. Streamable

ดาวน์โหลดวิดีโอจาก Streamable ลงโฟลเดอร์ที่กำหนด:

```cmd
yt-dlp -P "C:\Users\Desktop\dl" "[https://streamable.com/VIDEO_ID](https://streamable.com/VIDEO_ID)"

```

---

## 🔑 เทคนิคแก้ไขปัญหาและตัวเลือกเพิ่มเติม

### 🔓 ดึง Cookies จากเบราว์เซอร์ (แก้ติด Premium / ล็อกอิน / วิดีโอจำกัดอายุ)

หากวิดีโอต้องการการล็อกอิน สามารถดึงสิทธิ์จากเบราว์เซอร์ที่คุณใช้งานอยู่ได้ทันที:

```cmd
yt-dlp --cookies-from-browser chrome "URL_VIDEO"

```

*(เปลี่ยน `chrome` เป็น `edge`, `firefox` หรือ `brave` ตามเบราว์เซอร์ที่ใช้อยู่)*

### 🎵 ดึงเฉพาะเสียง (Extract Audio / MP3)

```cmd
yt-dlp -x --audio-format mp3 "URL_VIDEO"

```

---

## 🖼️ ตัวอย่างการใช้งานจริง (Example)

---

## ⚙️ สรุปตัวเลือกพารามิเตอร์สำคัญ

* `--concurrent-fragments N` : กำหนดจำนวน Connection/Fragment สำหรับดาวน์โหลดพร้อมกัน (เช่น 16, 100)
* `--cookies-from-browser` : ดึงข้อมูลสิทธิ์ล็อกอินจากเบราว์เซอร์เพื่อดาวน์โหลดความละเอียดสูงหรือวิดีโอ Private
* `-P` / `--paths` : กำหนดโฟลเดอร์ปลายทางสำหรับบันทึกไฟล์
* `-x` / `--extract-audio` : ดึงเฉพาะไฟล์เสียงออกจากวิดีโอ
* `-U` / `--update` : อัปเดตตัวโปรแกรม yt-dlp เป็นเวอร์ชันล่าสุด
