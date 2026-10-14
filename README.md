# Echoes of Elaria – Lab #4: Gameplay Loops & Progression Systems

DPS937 – Unreal Engine 5 project for Lab #4. Builds on Lab #3
(https://github.com/Jerrizzy001/Lab03_DPS937) and adds persistent progress, treasure rarities,
health pickups, a fire trap, an NPC quest giver with a quest system, a shrine unlock and a player HUD.

**Group:** Arya Manek, Muhammad Hamid Ali Khalid, Jerry Nwachi

## Opening the project

1. Install [Git LFS](https://git-lfs.com) (`brew install git-lfs` / `git lfs install`) **before** cloning.
   All `.uasset`, `.umap`, textures and model files are stored in LFS.
2. `git clone https://github.com/Jerrizzy001/Lab04_DPS937.git`
3. Open `DPS937_ThirdPerson.uproject` in Unreal Engine 5.
4. Open `Content/Levels/Region01_VerdantFlats` and press Play.

## What was added in Lab #4

| Asset | Path | Purpose |
|---|---|---|
| `BP_GameInstance` | `Content/GameAssets/` | Persistent session data: PlayerHealth, PlayerTreasure, CurrentQuest, QuestsCompleted, ShrineUnlocked. Set as the Game Instance Class in Project Settings |
| `BP_PlayerCharacter` (updated) | `Content/Characters/PlayerCharacter/` | Loads health/treasure from the Game Instance on BeginPlay; `AddTreasure` and `ChangeHealth` functions save back to it; creates the HUD; IA_Interact (E) accepts / turns in the quest |
| `BP_Treasure_Bronze` / `_Silver` / `_gold`, `BP_HiddenTreasure` | `Content/GameAssets/` | Treasure rarities worth 10 / 25 / 50 / 50 with unique collection messages |
| `BP_SmallHealthPickup`, `BP_LargeHealthPickup`, `BP_FullRestorePickup` | `Content/GameAssets/` | Health tiers: +25 (green), +50 (blue), full restore (gold, with light) |
| `BP_SpikeTrap` (updated), `BP_FireTrap` | `Content/GameAssets/`, `Content/` | Instant spike damage; fire trap deals 5 damage every second while the player stands in it, with fire particles and a point light as warning |
| `BP_QuestNPC`, `WBP_QuestIndicator` | `Content/` | Quest giver (Paragon Kwang mesh + animation blueprint) with sphere trigger, "!" / "?" / "✓" indicator, "Collect 100 Treasure" quest, 50 treasure reward and shrine unlock |
| `WBP_PlayerHUD` | `Content/` | Health bar + health text, treasure count and active quest, bound to BP_GameInstance |
| `IA_Interact` | `Content/Input/` | E key, added to IMC_Default |
| `BP_LevelPortal`, `LV_TestArea` | `Content/GameAssets/`, `Content/Levels/` | Crystal portal and test level used to verify that values persist across level changes |

Lab #2 and #3 content (world, character, camera, controls, animation) is unchanged.

## Not included
`Binaries/`, `Intermediate/`, `Saved/` and `DerivedDataCache/` are ignored; Unreal regenerates them on first open.
