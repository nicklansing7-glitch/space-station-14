# Expedition Drop Armor Mk.I

First implementation: helmet, outer armor, uniform, gloves, and boots. Charcoal
and gunmetal with an amber visor; no identification stripe. All five pieces are
separate wearables, not one flattened character sprite.

## Files and validation

Five RSI directories contain 20 transparent PNGs: one icon, one four-direction
worn sheet, and left/right four-direction held sheets per item. Frame size is
32 x 32. Four-direction sheets are 64 x 64, ordered South, North, East, West.

YAML adds five clothing prototypes and `CrateExpeditionDropMk1`. No vanilla
prototype, map, server setting, or C# file is modified. Parent prototypes were
checked against the connected fork at commit
`2eaa9d313f6d75970c0f46907283027fed6f5247`.

Static checks passed: YAML parsing, unique IDs in this pack, parent names checked
against source, RSI paths and state names, PNG CRC/decompression, RGBA/frame
sizes, transparency, and package hashes. These are NOT engine tests.

**Not yet playtested in the SS14 engine.** The authoring environment has no
working .NET installation or access to the user's running game. First test on
a human character and inspect both body presentations and all four directions.
Species-specific fits, snouts, antennae, and displacement maps need a later pass.
The preview is an offline composite of the actual PNG layers, not a game screenshot.

## Install

Save and commit current ship mapping work before closing the game. Install the
asset commit into your existing feature branch, or use the separate downloadable
asset package. Do not switch away from unsaved mapping work.

For the ZIP: extract it fully, close the client and server, then double-click
`INSTALL.cmd`. Confirm the displayed project folder and type INSTALL. It copies
only manifest-listed files; no maps are included. Existing affected files are
backed up before replacement. It never changes branches, remotes, or Git commits.
The generator is optional; Pillow is not required to install the supplied PNGs.

Restart the server and client normally after installing. In the initialized
Dev/Sandbox map, open the console and run:

```
spawn CrateExpeditionDropMk1
```

Open the crate and equip uniform, boots, gloves, armor, and helmet. F5 search
`expedition` also finds the individual items. Wear testing needs a living player
body, not an admin observer. A kit crate is populated at MapInit and may remain
empty in an uninitialized mapping map; use Sandbox for the first test.

IDs:

```
ClothingHeadHelmetExpeditionDropMk1
ClothingOuterArmorExpeditionDropMk1
ClothingUniformExpeditionCombat
ClothingHandsGlovesExpeditionDropMk1
ClothingShoesBootsExpeditionDropMk1
CrateExpeditionDropMk1
```

## Behavior

Helmet inherits `ClothingHeadHelmetArmoredBase`; outer armor inherits
`ClothingOuterArmorBase`. This keeps ordinary upstream armor protection as a
starting balance. Uniform, gloves, and boots add no extra Armor coefficients.
The helmet hides the Hair, FacialHair, HeadTop, and HeadSide layers.

**This is combat armor, NOT an EVA suit.** No vacuum seal, pressure immunity,
insulation, helmet lamp, visor toggle, or magnetic boots are implemented.

## Playtest checklist

- No new prototype or missing-resource errors at startup.
- Spawn kit in initialized Sandbox; check all five contents.
- Equip all five pieces and inspect S/N/E/W on a human body.
- Check hair hiding, body clipping, and interaction with other clothing.
- Drop each piece, then hold it in both hands to inspect icons.
- Verify the intended protection with the project's normal testing tools.

## Editable sources

PNG layers can be edited directly in a pixel editor. The ZIP additionally includes
`Tools/Exploration/build_expedition_sprites.py`, the explicit pixel-geometry
source (requires Pillow), and a static validator. Regenerating overwrites the
five custom RSI folders, so do not regenerate after hand-editing PNGs unless
you also update the generator. The package manifest must be refreshed after edits
before reusing its installer.

## References

- https://docs.spacestation14.com/en/specifications/robust-station-image.html
- `Resources/Prototypes/Entities/Clothing/Head/helmets.yml`
- `Resources/Prototypes/Entities/Clothing/OuterClothing/armor.yml`
- `Resources/Prototypes/Entities/Clothing/Uniforms/base_clothinguniforms.yml`
- `Resources/Prototypes/Entities/Clothing/Hands/base_clothinghands.yml`
- `Resources/Prototypes/Entities/Clothing/Shoes/base_clothingshoes.yml`
- `Resources/Prototypes/Entities/Structures/Storage/Crates/crates.yml`
