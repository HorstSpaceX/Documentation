# Horst Documentation

ฟังก์ชั่นสำหรับการส่ง logs และ เปลี่ยนไอดี

---

## ฟังก์ชั่น _G.Horst_SetDescription

**คำอธิบายฟังก์ชัน:**  
ส่งข้อความพร้อมรายละเอียดไปยัง WebSocket (`_G.ws`) ของโปรแกรม หากไม่ส่ง `encode_json` จะใช้ค่า JSON เริ่มต้น `{"MackyJ":"nil"}`  

### 📄 Documentation Table

| ชื่อพารามิเตอร์ | ประเภท | คำอธิบาย | ค่าเริ่มต้น |
|-----------------|--------|-----------|-------------|
| `description`   | string | ข้อความที่จะส่งไปยัง WebSocket | - |
| `encode_json`   | any (optional) | ข้อมูลเพิ่มเติมที่จะเข้ารหัสเป็น JSON | `{"MackyJ":"nil"}` |

### 💡 ตัวอย่างการใช้งาน

#### 1️⃣ แบบไม่มี JSON เพิ่มเติม
```lua
local messages = "🌲 : 💎 Diamond 500 , ⚔️ Class : Cyborg, Level 3"
_G.Horst_SetDescription(messages)
```
**ผลลัพธ์:**  
ส่งข้อความไปยัง WebSocket พร้อม JSON เริ่มต้น: `{"MackyJ":"nil"}`

#### 2️⃣ แบบส่ง JSON เพิ่มเติม
```lua
local messages = "🌲 : 💎 Diamond 1000 , ⚔️ Class : Warrior, Level 5"
local extra_data = { event="level_up", points=500 }
_G.Horst_SetDescription(messages, extra_data)
```
**ผลลัพธ์:**  
ส่งข้อความพร้อม JSON `{"event":"level_up","points":500}` ไปยัง WebSocket
