# PlayTo_AmaZoo
Lets play to Ama Zoo


[<img width="743" height="403" alt="image" src="https://github.com/user-attachments/assets/939d0334-2be6-4038-9cad-7dce14490efd" />](https://store.steampowered.com/app/3066360/AmaZoo/?l=french)
https://store.steampowered.com/app/3066360/AmaZoo/?l=french  
- E = Utiliser    
- R = Restart  
- Space = Jump  
- Arrows = Move  
- Enter = Valider   
- Q = Kick  
- Escape = Menu  


| Action     | NES Input ID | Keyboard Mapping (Code + Action) | Xbox Mapping (Code + Action) |
| ---------- | ------------ | -------------------------------- | ---------------------------- |
| Up         | 1281         | 1032 – Space (Jump)              | 1300 – A (Jump)              |
| Right      | 1282         | 1068 – D (Move Left)             | 1317 – Right Arrow           |
| Down       | 1283         | 1013 – Enter (Confirm)           | 1303 – Y (Toggle Direction)  |
| Left       | 1284         | 1065 – A (Move Right)            | 1313 – Left Arrow            |
| A Button   | 1285         | 1069 – E (Use)                   | 1301 – X (Carry / Throw)     |
| B Button   | 1286         | 1081 – Q (Kick)                  | 1302 – B (Kick)              |
| Menu Left  | 1287         | 1027 – Escape (Toggle Menu)      | 1308 – MR (Toggle Menu)      |
| Menu Right | 1288         | 1082 – R (Restart)               | 1305 – SBR (Restart)         |




-----------







With Python and S2W Keyboard:  
- https://github.com/EloiStree/S2W
- 
```
# Game: https://store.steampowered.com/app/3066360/AmaZoo/?l=french  
# https://pypi.org/project/iid42/
from iid42 import *
# https://pypi.org/project/wowint/
from wowint import WowIntegerTarget, WowIntegerKeyboard

import socket
import struct
import time

target_udp = "127.0.0.1"
target_port = 7073
player_index =0


key_left = WowIntegerKeyboard.key_a
key_right = WowIntegerKeyboard.key_d
key_up = WowIntegerKeyboard.key_w
key_down = WowIntegerKeyboard.key_s
key_jump = WowIntegerKeyboard.space
key_restart = WowIntegerKeyboard.key_r
key_kick = WowIntegerKeyboard.key_q
key_valider_enter = WowIntegerKeyboard.enter
key_enter = WowIntegerKeyboard.enter
key_escape = WowIntegerKeyboard.escape
sender = SendUdpIID(target_udp, target_port,True)

## When you leave the game it trigger main menu, so you need to press enter to go back to the game.


# Let's restart the level.
time.sleep(1)
while True:
    bool_full_level = True
    if bool_full_level:
        time.sleep(1)
        sender.push_index_integer( player_index,key_restart)
        time.sleep(1)
        sender.push_index_integer(player_index,key_restart+1000)
        time.sleep(1)
        sender.push_index_integer( player_index,key_enter)
        time.sleep(1)
        sender.push_index_integer(player_index,key_enter+1000)

        time.sleep(1)
        sender.push_index_integer( player_index,key_right)
        time.sleep(1)
        sender.push_index_integer(player_index,key_right+1000)


        time.sleep(1)
        sender.push_index_integer( player_index,key_left)
        time.sleep(1)
        sender.push_index_integer(player_index,key_left+1000)
    time.sleep(4)
```        





