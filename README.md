# Horst WebSocket Utilities for Roblox

A small Lua utility for sending messages via a WebSocket (`_G.ws`) in Roblox.  
Includes functions for sending descriptions and notifying when an account change is done.

---

## Table of Contents
- [Installation](#installation)
- [Usage](#usage)
  - [_G.Horst_SetDescription](#_ghorst_setdescription)
  - [_G.Horst_AccountChangeDone](#_ghorst_accountchangedone)
- [Return Values](#return-values)
- [Notes](#notes)

---

## Installation

Simply include these functions in a LocalScript in Roblox and make sure `_G.ws` is a valid WebSocket connection.

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
