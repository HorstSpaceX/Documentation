# 📄 Horst Documentation

หากอธิยายไม่ดีก็ขออภัย เพราะฉันไม่ค่อยได้ทำอะไรแนวนี้ อันนี้ให้ gpt เรียบเรียง

---

## ฟังก์ชั่น _G.Horst_SetDescription

**คำอธิบาย:**  
ฟังก์ชั่นนี้จะรับ 2 ค่าคือ 
```
1 description คือข้อความที่แสดงในรีจอยจัฟ
2 encode_json (optional) จะใส่หรือไม่ใส่ก็ได้หลักๆเอาไว้ส่ง sheet ในรีจอยจัฟ
```

### คำอธบิายแบบละเอียด มือใหม่ข้ามไปดู Example เลย

| ชื่อพารามิเตอร์ | ประเภท | คำอธิบาย | ค่าเริ่มต้น |
|-----------------|--------|-----------|-------------|
| `description`   | string | ข้อความที่แสดงในรีจอย | - |
| `encode_json`   | any (optional) | เอาไว้ส่ง sheet ในรีจอย | - |

### Example : ตัวอย่างการใช้งาน
---
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

## 2. ฟังก์ชั่น _G.Horst_AccountChangeDone

ก็ไม่มีอะไรมากจัฟ เอาไว้ใช้งานเมื่อได้ของที่ต้องการ เช่นเพชรครบ ก็ใช้ _G.Horst_AccountChangeDone() ได้เลย

---

### Example : ตัวอย่างการใช้งาน

```lua
local gems = 900
if gems >= 100 then -- สมมุติว่าเกิน 100 แล้ว
    local ok, err = _G.Horst_AccountChangeDone()
    if ok then
        print("Account change done sent successfully!")
    else
        print("Failed to send DONE:", err)
    end
end
```

**ผลลัพธ์ Output :**  

| ค่าที่คืน | ความหมาย |
|-----------|-----------|
| `true`    | ส่งข้อความสำเร็จ |
| `false, err` | ส่งข้อความไม่สำเร็จ พร้อมข้อความ error |

