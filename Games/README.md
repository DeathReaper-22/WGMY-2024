# Games
- World 1 Resource: [Resources/World I.zip](Resources/World%20I.zip)
- World 2 Resource: [Resources/World_II.apk](Resources/World%20II.apk)
- World 3 Resource: [https://monaruku.itch.io/wgmy2024](https://monaruku.itch.io/wgmy2024) Password: WGMY2024
- World 6 Resource: [https://monaruku.itch.io/wgmy-ver-2](https://monaruku.itch.io/wgmy-ver-2) &lt;Released and solved after CTF&gt;

# Preface
For all the world challenges, the team's approach was to use Inspect Element (Initial thought was to use Cheat Engine but couldn't get it to work). This is because the World I file can be deduced to be a JS compiled app (because of NWJS description) and World II provided hint was `Tbh this is not a natively built app, more like something just wrapped into an app`

For World 1, run the extracted exe as `"World I.exe" --remote-debugging-port=9222` then open `http://localhost:9222/` to access the Inspect Element

For World 2, install the apk into Android phone and plug the phone into PC with USB debugging enabled. Open `chrome://inspect#devices` to view the Inspect Element

For World 3 and 6, just open the iFrame in a new tab to directly access the context.

Once Inspect Element is opened, you can explore the variables available, `$data<Object>` are the data dictionary where as `$game<Object>` are game runtime variables. 

Use the console and run `$dataWeapons[5].params = [99999, 99999, 99999, 99999, 99999, 99999, 99999, 99999]` to give yourself max stat through your weapon to be able to defeat bosses easily.

# Solution
For World 1, 2 and 3, the steps to obtain the flags are similar 
- For flag 1 and 2: Defeat the bosses on the repective floors and obtain the dropped item, then interact with the item.
    - World 1 - Flag 1: `wgmy{5ce` [Evidence/World 1 - Flag 1.png](Evidence/World%201%20-%20Flag%201.png)
    - World 1 - Flag 2: `7d7a7140` [Evidence/World 1 - Flag 2.png](Evidence/World%201%20-%20Flag%202.png)
    - World 2 - Flag 1: `wgmy{406` [Evidence/World 2 - Flag 1.png](Evidence/World%202%20-%20Flag%201.png)
    - World 2 - Flag 2: `8a87d81d` [Evidence/World 2 - Flag 2.png](Evidence/World%202%20-%20Flag%202.png)
    - World 3 - Flag 1: `wgmy{811` [Evidence/World 3 - Flag 1.png](Evidence/World%203%20-%20Flag%201.png)
    - World 3 - Flag 2: `a332e71b` [Evidence/World 3 - Flag 2.png](Evidence/World%203%20-%20Flag%202.png)
- For flag 3: Defeat boss on floor 3; Do not proceed through orb without interacting with chest first. Flag is available through interaction with chest.
    - World 1 - Flag 3: `ebabf5cd` [Evidence/World 1 - Flag 3.png](Evidence/World%201%20-%20Flag%203.png)
    - World 2 - Flag 3: `8c901043` [Evidence/World 2 - Flag 3.png](Evidence/World%202%20-%20Flag%203.png)
    - World 3 - Flag 3: `5d4651ed` [Evidence/World 3 - Flag 3.png](Evidence/World%203%20-%20Flag%203.png)
- For flag 4: Defeat boss of floor 4, the terrain will change. Do not proceed forward. Observe and make rounds on the changed terrain for the flag. 
    - World 1 - Flag 4: `43effd` [Evidence/World 2 - Flag 4.mp4](Evidence/World%202%20-%20Flag%204.mp4)
    - World 2 - Flag 4: `885bac` [Evidence/World 2 - Flag 4.mp4](Evidence/World%202%20-%20Flag%204.mp4)
    - World 3 - Flag 4: `d3ddca` [Evidence/World 3 - Flag 4.mp4](Evidence/World%203%20-%20Flag%204.mp4)
- For flag 5: Defeat boss of floor 5. Interact with the new NPC, and translate digit to alphabet (23 7 13 25 = wgmy). Then insert `wgmy` into the orb to obtain flag item. Interact with flag item to get flag (QR code format).
    - World 1 - Flag 5: `3fcaac2}` [Evidence/World 1 - Flag 5.png](Evidence/World%201%20-%20Flag%205.png)
    - World 2 - Flag 5: `4f51785}` [Evidence/World 2 - Flag 5.png](Evidence/World%202%20-%20Flag%205.png)
    - World 3 - Flag 5: `ce5b748}` [Evidence/World 3 - Flag 5.png](Evidence/World%203%20-%20Flag%205.png)

As for World 6, there is a slight difference (floor 2 has a puzzle to potentially obtain flag 2?). So we approach this challenge differently.
- As a note, flags 1, 2, 3 and 5 are now items, but show QR code (For World 1, 2 and 3, only flags 1, 2 and 5 are items). So just run `$gameParty._items = {33: 1, 34: 1, 35: 1, 36: 1}` (technically you can do this for the previous worlds as well) in console and you can interact with flag items 1, 2, 3 and 5.
    - World 6 - Flag 1: `wgmy{6b2` [Evidence/World 6 - Flag 1.png](Evidence/World%206%20-%20Flag%201.png)
    - World 6 - Flag 2: `217eb493` [Evidence/World 6 - Flag 2.png](Evidence/World%206%20-%20Flag%202.png)
    - World 6 - Flag 3: `3ed3b03a` [Evidence/World 6 - Flag 3.png](Evidence/World%206%20-%20Flag%203.png)
    - World 6 - Flag 5: `06e8865}` [Evidence/World 6 - Flag 5.png](Evidence/World%206%20-%20Flag%205.png)
- For flag 4, it is similar to previous worlds but you need walkthrough walls to reach the terrain. Run `$gamePlayer._through = true` to activate walk through and observe the terrain after defeating the boss.
    - World 6 - Flag 4: `291c3c` [Evidence/World 6 - Flag 4.mp4](Evidence/World%206%20-%20Flag%204.mp4)

# Flags
- World 1: wgmy{5ce7d7a7140ebabf5cd43effd3fcaac2}
- World 2: wgmy{4068a87d81d8c901043885bac4f51785}
- World 3: wgmy{811a332e71b5d4651edd3ddcace5b748}
- World 6: wgmy{6b2217eb4933ed3b03a291c3c06e8865} 