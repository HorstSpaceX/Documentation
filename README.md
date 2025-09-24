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
-- Example: _G.ws = some WebSocket connection
