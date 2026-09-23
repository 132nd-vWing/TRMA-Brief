# ACM Training

The ACM (Air Combat Maneuvering) mode is a self-service BFM. ** Only blue**
player can call up a bandit from their own cockpit, at any time, anywhere on the map.

## Control

The menu is under the F10 entry **ACM Training**. It is per flight,
not per pilot — everyone in the same client group shares one menu and one bandit, so
in a multi-slot flight the last selection made wins.

### Weapons

* **Full A/A** — the BVR load: the full radar-missile fit.
* **WVR / BFM** — the merge load: short-range IR and guns only.

These are the same aggressor templates used by the range drones, so a bandit's fit is
whatever that airframe carries in its `_BFM` or full A/A template.



## Spawn geometry

When you press **SPAWN BANDIT**:

* **Bearing** — random, 000 to 359. You will not know where they are coming from.
* **Range** — 15 to 25 NM.
* **Aspect** — nose-on. They are pointed straight back down the bearing at you.
* **Altitude** — random inside a window from 7000 ft below you to 7000 ft above you.
  The top of that window is capped at 25000 ft, but never below your own altitude — so
  if you are already at or above 25000 ft the bandits come in at your level or below
  rather than every one of them pinned to the cap.
* **Speed** — if they spawn in your front sector they match your speed. If they spawn
  behind you they get 1.25x your speed, so they can actually catch you. Clamped to
  250-1200 kt. If your speed cannot be read, they get 400 kt.



## Enemy ROE

* The bandits are given an INTERCEPT mission against **your flight specifically**, by
  identity. They are not looking for targets of opportunity and will not wander off after
  something else that flies past.
* Bandit skill is set to **Good**, the same as the range drones.
* One bandit group per flight. Pressing **SPAWN BANDIT** again replaces what you have

## Leash and cleanup

A watchdog runs every 30 seconds.

* **Leash** — if the bandit ends up more than **60 NM** from you it is despawned.
* **Bandit destroyed** — you get *"ACM: bandit is down. Knock it off."* and the slot is
  freed for the next spawn.
* **Despawn Bandit** — removes it immediately, any time.
* **You leave or your flight is wiped out** — your bandit is removed with you. Nothing is
  left orphaned in the air.

## Notes and limits

*  The aggressor templates are red, so a red player would get a
  same-coalition bandit that would never fight him.
