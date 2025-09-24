# Horst Documentation

ฟังก์ชั่นสำหรับการส่ง logs และ เปลี่ยนไอดี

---

## ฟังก์ชั่น _G.Horst_SetDescription

**คำอธิบาย:**  
ฟังก์ชั่นนี้จะรับ 2 ค่าคือ 
```
1 description คือข้อความที่แสดงในรีจอยจัฟ
2 encode_json (optional) จะใส่หรือไม่ใส่ก็ได้หลักๆเอาไว้ส่ง sheet ในรีจอยจัฟ
```

### 📄 Documentation Table

| ชื่อพารามิเตอร์ | ประเภท | คำอธิบาย | ค่าเริ่มต้น |
|-----------------|--------|-----------|-------------|
| `description`   | string | ข้อความที่แสดงในรีจอย | - |
| `encode_json`   | any (optional) | เอาไว้ส่ง sheet ในรีจอย | - |

### Example 💡 ตัวอย่างการใช้งาน

#### แบบปกติ ไม่ได้ส่ง encode_json
```lua
local messages = "🌲 : 💎 Diamond 500 , ⚔️ Class : Cyborg, Level 3"
_G.Horst_SetDescription(messages)
```
#### แบบส่ง encode_json เพิ่มเติมเอาไว้สำหรับ sheets
```lua
local messages = "🌲 : 💎 Diamond 1000 , ⚔️ Class : Warrior, Level 5"
local extra_data = { event="level_up", points=500 }
_G.Horst_SetDescription(messages, extra_data)
```

---

## 2️⃣ ฟังก์ชั่น _G.Horst_AccountChangeDone

**คำอธิบายฟังก์ชัน:**  
แจ้งว่า **การเปลี่ยนบัญชีเสร็จเรียบร้อยแล้ว** โดยส่งข้อความ `"DONE"` ไปยัง WebSocket (`_G.ws`)  

### 📄 Documentation Table

| ชื่อพารามิเตอร์ | ประเภท | คำอธิบาย | ค่าเริ่มต้น |
|-----------------|--------|-----------|-------------|
| ไม่มี | - | ฟังก์ชันนี้ไม่รับพารามิเตอร์ | - |

**ผลลัพธ์ (return values):**  

| ค่าที่คืน | ความหมาย |
|-----------|-----------|
| `true`    | ส่งข้อความสำเร็จ |
| `false, err` | ส่งข้อความไม่สำเร็จ พร้อมข้อความ error |

### 💡 ตัวอย่างการใช้งาน

```lua
local ok, err = _G.Horst_AccountChangeDone()
if ok then
    print("Account change done sent successfully!")
else
    print("Failed to send DONE:", err)
end
```
