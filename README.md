# 📄 Horst Documentation

หากอธิยายไม่ดีก็ขออภัย เพราะฉันไม่ค่อยได้ทำอะไรแนวนี้ อันนี้ให้ gpt เรียบเรียง

---

## 1. ฟังก์ชั่น _G.Horst_SetDescription

**คำอธิบาย:**  
ฟังก์ชั่นนี้จะรับ 2 ค่าคือ 
```
1 description คือข้อความที่แสดงในรีจอย
2 encode_json (optional) จะใส่หรือไม่ใส่ก็ได้หลักๆเอาไว้ส่ง sheet ในรีจอย
```

### คำอธบิายแบบละเอียด มือใหม่ข้ามไปดู Example เลย

| ชื่อพารามิเตอร์ | ประเภท | คำอธิบาย | ค่าเริ่มต้น |
|-----------------|--------|-----------|-------------|
| `description`   | string | ข้อความที่แสดงในรีจอย | - |
| `encode_json`   | json | Json ที่ผ่าน HttpServiceEncode  | - |

### Example : ตัวอย่างการใช้งาน
---
#### แบบปกติ ไม่ได้ส่ง encode_json
```lua
local messages = "🌲 : 💎 Diamond 500 , ⚔️ Class : Cyborg, Level 3"
_G.Horst_SetDescription(messages)
```
#### แบบส่ง encode_json เพิ่มเติมเอาไว้สำหรับ sheets
```lua
local json_strings = { -- เป็น data ที่ได้จากการเช็ค  เช่น เลเวล, เพชร, ตัวละคร
     Level = 10, 
     Money = 500
}

local HttpService = game:GetService("HttpService") --  Get serivce ของเกม
local EncodeJson = HttpService:JSONEncode(json_strings) -- Encode เป็น json ก่อนเสมอ
    
local messages = "🌲 : 💎 Diamond 1000 , ⚔️ Class : Warrior, Level 5"
_G.Horst_SetDescription(messages, EncodeJson) -- เพิ่ม Parameter
```
### อักษรที่ห้ามใช้ในการส่ง Description
```lua
| ;  -- 2ตัวอักษรนี้ห้ามใช้เด็ดขาด
```

---

## 2. ฟังก์ชั่น _G.Horst_AccountChangeDone

ก็ไม่มีอะไรมากจัฟ เอาไว้ใช้งานเมื่อได้ของที่ต้องการ เช่นเพชรครบ ก็ใช้ _G.Horst_AccountChangeDone() ได้เลย

---

### Example : แบบไม่อ่าน err

```lua
local gems = 900
if gems >= 100 then -- สมมุติว่าเกินเพชร 100 แล้ว ส่ง status Done
    _G.Horst_AccountChangeDone()
end
```

### Example : ตัวอย่างการใช้งานแบบอ่าน err

```lua
local gems = 900
if gems >= 500 then --  สมมุติว่าเกินเพชร 500 แล้ว ส่ง status Done
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
| `true`    | เปลี่ยนสถานะเป็น DONE สำเร็จ |
| `false, err` | เปลี่ยนสถานะเป็น DONE ไม่สำเร็จ พร้อมข้อความ error |

