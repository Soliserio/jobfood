# JobFood
A Windower addon by Soliserio.

JobFood selects food based on each character’s current main job and saved preference. It uses food from Inventory or retrieves one serving from Mog Satchel, Mog Sack, or Mog Case.

## Features

- Saved food preferences per character and main job.
- Ranked food lists with fallback choices.
- Preview choices without moving or consuming food.
- Current-character and all-local-character commands.
- Skips characters with an existing Food effect.
- Reports missing food and suggests supplies to restock.
- No automatic purchases, antacids, or continuous feeding.

## Installation

1. Extract the ZIP.
2. Place the `jobfood` folder inside your Windower `addons` folder.
3. Keep `jobfood.lua` and `profiles.lua` together.
4. Load the addon in game:

    //lua load jobfood

To load it on all local characters with the Send addon:

    //send @all lua load jobfood

Loading the addon does not consume food.

## Quick Start

Stand still and disengaged. Keep one Inventory slot free if food needs to be retrieved from storage.

Preview your current character’s selection:

    //jf preview

Preview every local character with JobFood loaded:

    //jf preview all

Use one serving on your current character:

    //jf use

Use one serving on each local character with JobFood loaded:

    //jf use all

Each character follows its own job preference. Results appear in each character’s own chat.

## Change Your Food Preference

Save a mode for your current character’s current main job:

    //jf set tankacc

Replace `tankacc` with any mode below.

| Mode | Purpose | Leading choice |
|---|---|---|
| balanced | Physical attack and accuracy | Grape Daifuku |
| accuracy | Physical and ranged accuracy | Sublime Sushi |
| attack | Physical and ranged attack | Soy Ramen |
| magic | Magic damage | Cehuetzi Snow Cone |
| macc | Magic accuracy | Crepe des Rois / Tropical Crepe |
| defense | Defensive protection | Miso Ramen |
| tankacc | Tanking with accuracy | Omelet Sandwich |
| hybrid | Physical and magic accuracy | Oden |
| pet | General pet offense | Grape Daifuku |
| petacc | Pet accuracy | Shiromochi |
| petmacc | Pet magic accuracy | Rolanberry Daifuku |

Higher-quality versions are preferred where included in the list. Seafood Gratin is included as a fallback in relevant modes.

These are practical presets, not guaranteed best-in-slot rankings for every fight. The addon does not detect accuracy caps or automatically interpret your combat role.

Changing a preference does not consume food or remove an existing Food effect.

## Default Job Preferences

| Jobs | Default |
|---|---|
| PLD, RUN | tankacc |
| WHM | defense |
| BLM, RDM, BRD, SCH, GEO | macc |
| BST, SMN, PUP | pet |
| WAR, MNK, THF, DRK, RNG, SAM, NIN, DRG, BLU, COR, DNC | balanced |

Restore the default for your current character’s current job:

    //jf reset

## Temporary Overrides

Use a different mode once without changing your saved preference:

    //jf preview magic
    //jf use magic

Apply a temporary mode to all loaded local characters:

    //jf preview all defense
    //jf use all defense

Normally, use `//jf use all` without specifying a mode so each character follows its own preference.

## View Rankings and Status

Show the ranked food list for your current preference:

    //jf list

Show a specific mode’s ranked list:

    //jf list accuracy

Show your preference and current operation status:

    //jf status

## Cancel

Cancel on your current character:

    //jf cancel

Cancel on all loaded local characters:

    //jf cancel all

Cancellation cannot undo a transfer or item use already sent.

## How Food Is Selected

The addon searches for the highest-ranked available food across:

1. Inventory
2. Mog Satchel
3. Mog Sack
4. Mog Case

Food rank takes priority over storage location. A higher-ranked food in Mog Case beats a lower-ranked food in Inventory.

For identical food, Inventory is preferred, followed by Satchel, Sack, and Case. Only accessible bags are searched.

Storage withdrawals move one serving, not a whole stack.

## Safety and Limitations

- An existing Food effect is left untouched, even if you change modes.
- Stand still before using food.
- Do not manually move or use the selected food during a request.
- Storage transfers require confirmation before item use.
- Successful use requires both a consumption count change and the Food buff.
- Unconfirmed actions stop without automatic retries.
- A failed or canceled request may leave one borrowed serving in Inventory.
- Engaging, death, zoning, logout, or a job change stops the operation.
- No party-wide stewpot foods are selected.
- “All” means local clients with JobFood loaded, not remote party members.
- This addon does not assign keyboard shortcuts.

## Settings

Preferences are stored separately for each character:

    data/<character>.xml

Do not include personal settings files when sharing the addon.

## Testing

Thirty-five offline tests passed. Preview operation was confirmed in game.

Food consumption and storage withdrawals still need live verification. Start with a preview and one-character use before using food on all characters.

## Credits

Author: Soliserio
