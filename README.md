# Horst Documentation

ฟังก์ชั่นสำหรับการส่ง logs และ เปลี่ยนไอดี

---

## Table of Contents
- [Installation](#installation)
- [Usage](#usage)
  - [_G.Horst_SetDescription](#_ghorst_setdescription)
  - [_G.Horst_AccountChangeDone](#_ghorst_accountchangedone)
- [Return Values](#return-values)
- [Notes](#notes)

---

## Functions _G.Horst_SetDescription

ก็คือการ  SetDescription ของ Account ในโปรแกรม

```lua
-- Example: 🛠️ ฟังก์ชัน
1️⃣ _G.Horst_SetDescription

คำอธิบาย:
ส่งข้อความพร้อมรายละเอียดไปยัง WebSocket
หากไม่ส่ง encode_json จะส่งค่า JSON เริ่มต้นเป็น {"MackyJ":"nil"}

Parameters:

ชื่อ	ประเภท	คำอธิบาย
description	string	ข้อความที่จะส่ง
encode_json	any (optional)	ข้อมูลเพิ่มเติมที่เข้ารหัสเป็น JSON (ค่าเริ่มต้น {"MackyJ":"nil"})
