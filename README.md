# UCP extension: AI Ox Tethers
This is a mod for the game Stronghold Crusader (Firefly Studios).
The mod works with the Unofficial Crusader Patch.

Vanilla AI has an upper bound on three ox tethers per quarry, plus it always builds an ox tether when it places a quarry.

This combination leads to strange behavior as the game progress. This extension addresses this.

The core feature of this extension is that the ox tethers that belong to a quarry are no longer hardcoded but dynamically computed based on the quarry the ox tether worker took stones from last. These ox tethers are termed "linked ox tethers".

## Features
- Allow more than 3 ox tethers per quarry
- Customize the decision rules for placing more ox tethers
- Customize the rules per AI via the AIC

## AIC parameters

**Introduced by:** [`ai-ox-tethers` 1.0.0](https://github.com/gynt/ucp-extension-ai-ox-tethers/tree/26c92fa). These seven fields use numeric values in AIC files.

**Requirements:** `ai-ox-tethers >=1.0.0`, framework >=3.0.4, frontend >=1.0.2 and `aicloader >=1.1.0`. Enable the module's **Ox Tethers** switch under **General → AI → Fixes**, then select its AIC mode (`oxtethers.mode: use_aic`). The other mode (`override_aic`) uses menu settings and does not register these fields. AI Swapper is optional. Version 1.0.4 requires the conflicting `ucp2-legacy.ai_tethers.enabled` option to be off automatically.

These fields change whether an AI builds more tethers and which quarry it builds them for. A *linked tether* is associated with the quarry its worker last collected stone from. The five dynamic limits/thresholds apply when `AIOxTethers_Logic` is 1; the initial-tether switch is independent.

| Field | Values | Meaning |
| --- | --- | --- |
| `AIOxTethers_DisableInitialOxTether` | 0 or 1 | 0 keeps the automatic tether when a quarry is built/rebuilt; 1 disables it. |
| `AIOxTethers_Logic` | 0 or 1 | 0 uses the game's additional-tether decision; 1 uses the module's dynamic rules below. |
| `AIOxTethers_MaxOxTethers` | Non-negative integer | Stop requesting additional tethers when the player's total reaches this limit. |
| `AIOxTethers_DynamicMaxOxTethers` | Non-negative number | Stop requesting additional tethers when the total reaches this multiplier × quarry count. |
| `AIOxTethers_MinimumOxTethersPerQuarry` | Non-negative integer | Request a tether for a quarry below this linked-tether count, subject to the two total limits. |
| `AIOxTethers_MaximumOxTethersPerQuarry` | Non-negative integer | Exclude a quarry from stone-load requests when its linked count is at or above this value. Keep the minimum at or below this maximum. |
| `AIOxTethers_ThresholdStoneLoad` | Non-negative number | Request another tether when stored stone / linked tethers exceeds this value. With no linked tether, use stored stone directly. A full stone pile is 48. |

These limits govern new requests; they do not delete existing tethers or cap the game's separate automatic initial-tether placement. Use the initial-tether switch too if that automatic placement should stop. The current AIC handler checks numeric type only, so use the meaningful ranges shown above; it does not enforce the Customizations slider limits.

On initial enable, the menu seeds each AI's values and supplied AIC fields replace them. An AIC reset (including character replacement) instead restores fixed module defaults: initial tether **0**, logic **0**, total **100**, quarry multiplier **3**, minimum **1**, maximum **3**, threshold **20**. Omitted fields after reset retain those reset defaults, which can differ from your menu choices. Explicitly provide the fields your AI depends on.

Use these fields inside `Personality` in an AIC Loader file, or inside the lowercase `aic` object in AI Swapper's `character.json`. They apply per AI personality, not per player slot. Example personality fragment:

```json
{
  "AIOxTethers_DisableInitialOxTether": 1,
  "AIOxTethers_Logic": 1,
  "AIOxTethers_MaxOxTethers": 100,
  "AIOxTethers_DynamicMaxOxTethers": 4,
  "AIOxTethers_MinimumOxTethersPerQuarry": 1,
  "AIOxTethers_MaximumOxTethersPerQuarry": 6,
  "AIOxTethers_ThresholdStoneLoad": 20
}
```

## Compact Customizations menu

Version 1.0.4 requires GUI 1.0.16. Find the controls under
**General → AI → Fixes**. Collapsing the main switch hides its description
and all settings. Dynamic limits has its own switch: its explanation and number
fields collapse together. Advanced settings start collapsed.

All menu text is translated into the GUI's nine languages. Configuration keys,
defaults and runtime rules are unchanged.

## Legacy compatibility

While this module is active in Content, the UCP2-Legacy option **Set ox tethers
to a maximum of 10 per AI lord** is required to be off. Both patches change the
automatic ox-tether placement check; the legacy option is not an independent
extra limit. Use this module's maximum instead.

Verified against the installed UCP2-Legacy 2.15.1 patch and both game executables:
the legacy patch at `0x4EFF9A` (Crusader) / `0x4F032A` (Extreme) replaces the
conditional jump inside this module's scan pattern, which starts seven bytes
earlier. Applying the legacy patch makes that scan fail. Its unconditional jump
also bypasses automatic placement regardless of this module's per-AI setting.
The required-off setting follows the existing Running Units compatibility rule.
