# MI: ökörkarámok

Az MI alapesetben legfeljebb 3 ökörkarámot épít kőfejtőnként. Emellett minden kőfejtő építésekor vagy újjáépítésekor automatikusan elhelyez egy karámot.

Ezek az automatikus karámok kimeríthetik az MI lakóhelyeinek kapacitását, így nem jelennek meg új parasztok. A bővítménnyel kikapcsolható ez a viselkedés, és beállítható, mikor épüljenek további karámok.

Egy **hozzárendelt ökörkarám** ahhoz a kőfejtőhöz tartozik, ahonnan a dolgozója legutóbb követ vitt el. Ez a hozzárendelés dinamikusan frissül, nem rögzített.

## Funkciók
- Több mint 3 ökörkarám engedélyezése kőfejtőnként
- A további ökörkarámok építéséről döntő szabályok testreszabása
- A szabályok MI-nkénti testreszabása az AIC-n keresztül

## AIC-paraméterek

### `AIOxTethers_Logic`
0: A játék eredeti logikája.
1: Dinamikus logika az alábbi korlátokkal és kőterhelési szabályokkal.

### `AIOxTethers_MaxOxTethers`
Az ökörkarámok összesített korlátja játékosonként.

### `AIOxTethers_DynamicMaxOxTethers`
Az ökörkarámok összesített korlátja = ez az érték × a kőfejtők száma.
Mindig a 2 összesített korlát közül az alacsonyabb érvényes.

### `AIOxTethers_ThresholdStoneLoad`
Ha a `kő/hozzárendelt ökörkarámok` értéke egy kőfejtőnél meghaladja ezt az értéket, újabb karám épül, a korlátok figyelembevételével. Hozzárendelt karám nélkül közvetlenül a kő mennyisége számít.

### `AIOxTethers_DisableInitialOxTether`
0: Minden kőfejtő építésekor vagy újjáépítésekor automatikusan elhelyez egy karámot.
1: Kikapcsolja ezt az automatikus elhelyezést.

Ez a beállítás független a dinamikus logikától és annak korlátaitól.

### `AIOxTethers_MinimumOxTethersPerQuarry`
Ha egy kőfejtőhöz ennél kevesebb ökörkarám tartozik, a kőterheléstől függetlenül újabb épül, az összesített korlát figyelembevételével.

### `AIOxTethers_MaximumOxTethersPerQuarry`
A kőterhelés alapján egy kőfejtőhöz épített, hozzárendelt ökörkarámok korlátja. A minimum ne legyen nagyobb ennél a korlátnál.
