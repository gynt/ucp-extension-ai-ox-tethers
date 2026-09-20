# AI: Ox Tethers

The AI normally builds up to 3 ox tethers per quarry. It also automatically places a tether whenever it builds or rebuilds a quarry.

These automatic tethers can fill the AI’s housing and stop new peasants from spawning. This extension lets you disable them and customize when more tethers are built.

A **linked ox tether** belongs to the quarry its worker last collected stone from. These links are updated dynamically instead of using a fixed assignment.

## Features
- Allow more than 3 ox tethers per quarry
- Customize the decision rules for placing more ox tethers
- Customize the rules per AI via the AIC

## AIC parameters

### `AIOxTethers_Logic`
0: Original game logic.
1: Dynamic logic using the caps and stone-load rules below.

### `AIOxTethers_MaxOxTethers`
Total ox tether cap per player.

### `AIOxTethers_DynamicMaxOxTethers`
Total ox tether cap = this value × number of quarries.
The lower of the 2 total caps applies at any point.

### `AIOxTethers_ThresholdStoneLoad`
If `stones/linked ox tethers` goes above this value for a quarry, another ox tether is built, subject to the caps. With no linked tethers, the stone amount is used directly.

### `AIOxTethers_DisableInitialOxTether`
0: Automatically place a tether whenever a quarry is built or rebuilt.
1: Disable this automatic placement.

This setting is independent of dynamic logic and its caps.

### `AIOxTethers_MinimumOxTethersPerQuarry`
If a quarry has fewer linked ox tethers than this value, another is built regardless of stone load, subject to the total cap.

### `AIOxTethers_MaximumOxTethersPerQuarry`
Cap on linked ox tethers built for a quarry based on stone load. Keep the minimum at or below this cap.
