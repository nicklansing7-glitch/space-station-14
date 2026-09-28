# Expedition Laser Carbine v0.1

Prepared 2026-09-29 for the approved light-grey weapon concept, with no permanent laser beam. Includes native 32px inventory/ground, both hands, wielded and back/suit-storage sprites; custom green bolt and impact sprites.

## Behavior
`WeaponLaserCarbineExpeditionMk1` uses BasicEntityAmmoProvider with BOTH capacity and count null: genuinely non-depleting shots, not a large battery. No battery, reload, recharge timer or magazine components. Lower housing is fixed cosmetic geometry. SemiAuto and FullAuto; FullAuto initially selected. Starting test tuning: 4 shots/second, 13 Heat per green bolt, projectile speed 25 and 2-second maximum lifetime. Inherits normal gun wielding/spread behavior. The optic is cosmetic. References the existing laser.ogg firing sound.

## Status
STATIC CHECKS PASSED: YAML parsing, ID uniqueness within the pack, expected parent/component names checked against fork commit 2eaa9d313f6d75970c0f46907283027fed6f5247, RSI state/frame layout, PNG integrity/CRCs/transparency and infinite-provider settings. Uploaded PNG Git blob hashes match the checked package.

NOT YET INSTALLED ON THE USER'S PC OR TESTED IN THE ENGINE: Desktop Commander reports the device offline during authoring. Live startup, sustained firing, projectile color/collision/damage and held/worn sprite registration still require playtesting. A concept picture or an offline preview is not an engine test.

## Install and test
Apply only this commit's added Resources paths to the existing working branch after inspecting its status; do not replace maps or armor or switch away from unsaved mapping. Alternatively use the standalone ZIP from the conversation; that ZIP also includes the editable sprite generator, validator, manifest, and a standard-library Python installer. Its installer was tested for fresh install, idempotent reinstallation, backup of affected files, and preservation of a map sentinel. Do not copy only the YAML: both new RSI folders are required.

Restart server/client after saving active mapping work. In initialized Dev/Sandbox, open the GAME console:

```
spawn WeaponLaserCarbineExpeditionMk1
```

Search `expedition laser carbine` in the entity panel as an alternative. Pick it up with a living character; fire at least 100 shots in an in-game test area away from the unfinished shuttle. Check green bolts/impacts, all modes, both hands, all directions and worn slots. No finite-ammo HUD is added.

## Provenance
Custom native-pixel art based on the approved light-grey concept. No upstream gun sprite pixels copied. LicenseRef-SS14-Project leaves the release-license decision to the project owner and is not a rights-clearance determination. Inherited code and referenced upstream sounds retain their terms. No vanilla assets, map files, armor or C# files are modified.

Sources inspected: BasicEntityAmmoProviderComponent.cs, SharedGunSystem.BasicEntity.cs, GunComponent.cs, base_wieldable.yml, battery_guns.yml, Projectiles/Energy/lasers.yml, Projectiles/Effects/impacts.yml, Projectiles/Bullets/base.yml, and laser_gun.rsi/meta.json at the fork's pinned commit. RSI format: https://docs.spacestation14.com/en/specifications/robust-station-image.html
