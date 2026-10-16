ยินดีครับ! สำหรับ Repository ใหม่ที่ชื่อ **`ytdlp`** (หรือ `yt-dlp`) ที่ใช้เก็บคู่มือและสคริปต์สำหรับการดาวน์โหลดวิดีโอ (เช่น Bilibili, YouTube ฯลฯ)

นี่คือเนื้อหาไฟล์ **`README.md`** แบบสมบูรณ์ที่จัดทำขึ้นมาเป็นพิเศษ รวมทั้งคำสั่งเร่งสปีดด้วย `--concurrent-fragments` ตัวอย่างจากรูปภาพหน้าจอของคุณ และคำสั่งที่ใช้บ่อยครับ สามารถคัดลอกไปวางใช้งานได้เลยครับ:

```markdown
# 🎬 yt-dlp Fast Video Download Guide

คู่มือและรวมคำสั่งใช้งาน **yt-dlp** สำหรับดาวน์โหลดวิดีโอจากเว็บบอร์ดและแพลตฟอร์มต่างๆ (เช่น Bilibili, YouTube, TikTok) ด้วยความเร็วสูง

---

## ⚡ คุณสมบัติเด่น
* **Multi-Fragment Download:** ดึงข้อมูลไฟล์วิดีโอแบบแยกส่วนพร้อมกัน เร่งความเร็วการดาวน์โหลดให้เต็มแบนด์วิดท์
* **Cross-Platform:** รองรับเว็บไซต์วิดีโอชั้นนำมากกว่า 1,000+ เว็บไซต์ทั่วโลก
* **Cookies Integration:** รองรับการดึง Cookies จากเบราว์เซอร์เพื่อโหลดวิดีโอความละเอียดสูง (เช่น 1080p 60fps)

---

## 📥 การติดตั้ง (Installation)

### Windows (PowerShell / Winget)
```powershell
winget install yt-dlp

```

### หรือติดตั้งผ่าน pip (Python)

```powershell
pip install -U yt-dlp

```

---

## 🚀 ตัวอย่างคำสั่งใช้งานเร่งสปีด (Usage Examples)

### 1. ดาวน์โหลดวิดีโอแบบเร่งสปีด (Concurrent Fragments)

แบ่งการดาวน์โหลดออกเป็นหลายส่วนพร้อมกัน ช่วยให้โหลดเร็วขึ้นอย่างมาก:

* **โหมดสปีดปกติ (16 Threads):**
```cmd
yt-dlp --concurrent-fragments 16 "[https://www.bilibili.com/video/BV1Wotf6jE8g/](https://www.bilibili.com/video/BV1Wotf6jE8g/)"

```


* **โหมดสปีดสูงสุด (100 Threads):**
```cmd
yt-dlp --concurrent-fragments 100 "[https://www.bilibili.com/video/BV1Wotf6jE8g/](https://www.bilibili.com/video/BV1Wotf6jE8g/)"

```



### 2. ดาวน์โหลดโดยใช้ Cookies จากเบราว์เซอร์ (แก้ปัญหาติดสมาชิก Premium/1080p 60fps)

```cmd
yt-dlp --cookies-from-browser chrome "URL_VIDEO"

```

*(สามารถเปลี่ยน `chrome` เป็น `edge`, `firefox` หรือ `brave` ตามเบราว์เซอร์ที่คุณใช้)*

### 3. เลือกโหลดเฉพาะไฟล์เสียง (MP3)

```cmd
yt-dlp -x --audio-format mp3 "URL_VIDEO"

```

### 4. กำหนดโฟลเดอร์ปลายทางสำหรับเซฟวิดีโอ

```cmd
yt-dlp -P "C:\Users\Desktop\dl" "URL_VIDEO"

```

---

## 🖼️ ตัวอย่างการใช้งานจริง (Example)

ภาพตัวอย่างการใช้คำสั่ง `--concurrent-fragments` ดาวน์โหลดวิดีโอจาก Bilibili บน Command Prompt:

---

## ⚙️ สรุปตัวเลือกพารามิเตอร์สำคัญ

| Option | คำอธิบาย |
| --- | --- |
| `--concurrent-fragments N` | กำหนดจำนวน Connection/Fragment สำหรับดาวน์โหลดพร้อมกัน (เช่น 16, 100) |
| `--cookies-from-browser` | ดึงข้อมูลสิทธิ์ล็อกอินจากเบราว์เซอร์เพื่อโหลดความละเอียดสูง |
| `-P` / `--paths` | กำหนดโฟลเดอร์ปลายทางสำหรับบันทึกไฟล์ |
| `-x` / `--extract-audio` | แปลงไฟล์และดึงเฉพาะเสียงออกจากวิดีโอ |
| `-U` / `--update` | อัปเดตตัวโปรแกรม `yt-dlp` เป็นเวอร์ชันล่าสุด |

```

---

### 💡 ข้อแนะนำในการตั้งชื่อ Repository บน GitHub[cite: 10]:
จากรูปภาพแรก[cite: 10] หากใส่ชื่อ `ytdlp`[cite: 10] GitHub อาจจะขึ้นเตือนปรับให้เป็น `-ytdlp` หากมีเว้นวรรคติดมานิดหน่อย แนะนำให้พิมพ์ชื่อเน้นๆ ว่า `yt-dlp` หรือ `ytdlp` โดยไม่มีเว้นวรรคหน้าข้อความ เพื่อให้ได้ URL ที่สวยงามครับ[cite: 10]

```
