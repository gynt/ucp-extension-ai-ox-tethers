# KI: Ochsenjoche

Die KI baut normalerweise bis zu 3 Ochsenjoche pro Steinbruch. Außerdem setzt sie bei jedem Bau oder Wiederaufbau eines Steinbruchs automatisch ein Joch.

Diese automatischen Joche können die Wohnkapazität der KI ausschöpfen, sodass keine neuen Bauern mehr erscheinen. Mit dieser Erweiterung lassen sie sich abschalten und die Regeln für den Bau weiterer Joche anpassen.

Ein **zugeordnetes Ochsenjoch** gehört zu dem Steinbruch, von dem sein Arbeiter zuletzt Stein abgeholt hat. Diese Zuordnung wird dynamisch aktualisiert, statt fest vorgegeben zu sein.

## Funktionen
- Mehr als 3 Ochsenjoche pro Steinbruch erlauben
- Entscheidungsregeln für den Bau weiterer Ochsenjoche anpassen
- Regeln pro KI über die AIC anpassen

## AIC-Parameter

### `AIOxTethers_Logic`
0: Ursprüngliche Spiellogik.
1: Dynamische Logik mit den folgenden Limits und Regeln zur Steinlast.

### `AIOxTethers_MaxOxTethers`
Gesamtlimit für Ochsenjoche pro Spieler.

### `AIOxTethers_DynamicMaxOxTethers`
Gesamtlimit für Ochsenjoche = dieser Wert × Anzahl der Steinbrüche.
Es gilt jeweils das niedrigere der 2 Gesamtlimits.

### `AIOxTethers_ThresholdStoneLoad`
Übersteigt `Steine/zugeordnete Ochsenjoche` an einem Steinbruch diesen Wert, wird ein weiteres Joch gebaut, sofern die Limits es erlauben. Ohne zugeordnete Joche wird die Steinmenge direkt verwendet.

### `AIOxTethers_DisableInitialOxTether`
0: Bei jedem Bau oder Wiederaufbau eines Steinbruchs automatisch ein Joch setzen.
1: Dieses automatische Setzen abschalten.

Diese Einstellung ist unabhängig von der dynamischen Logik und ihren Limits.

### `AIOxTethers_MinimumOxTethersPerQuarry`
Hat ein Steinbruch weniger zugeordnete Ochsenjoche als dieser Wert, wird unabhängig von der Steinlast ein weiteres gebaut, sofern das Gesamtlimit es erlaubt.

### `AIOxTethers_MaximumOxTethersPerQuarry`
Limit für zugeordnete Ochsenjoche, die aufgrund der Steinlast für einen Steinbruch gebaut werden. Das Minimum darf nicht höher als dieses Limit sein.
