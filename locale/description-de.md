# KI-Logik: Ochsenjoche

Die Standard-KI von Stronghold Crusader ist auf drei Ochsenjoche pro Steinbruch limitiert und platziert bei jedem neuen Steinbruch automatisch ein Joch. Dies führt zu ineffizienter Steinlogistik. Dieses Plugin ersetzt die starre Zuweisung durch eine dynamische Logik.

Die Kernfunktion ist die dynamische Verknüpfung: Ein Ochsenjoch wird nun dem Steinbruch zugeordnet, von dem es zuletzt Steine abgeholt hat. Basierend auf dieser dynamischen Zuteilung entscheidet die KI, ob und wo weitere Ochsenjoche zur Optimierung der Steinabholung erforderlich sind.

---
## Funktionen
- Aufhebung des harten Limits von 3 Ochsenjochen pro Steinbruch.
- Konfigurierbare Entscheidungsregeln für den Bau von Ochsenjochen.
- Individuelle Anpassung der Regeln für jede KI über die AIC-Datei.

---
## AIC-Parameter

### `AIOxTethers_DisableInitialOxTether`
- **0:** Standardverhalten. Die KI baut bei jedem Steinbruch ein initiales Ochsenjoch.
- **1:** Deaktiviert das initiale Ochsenjoch. Der Bau erfolgt ausschließlich über die Logik-Parameter.

### `AIOxTethers_Logic`
- **0:** Vanilla-Logik.
- **1:** Aktiviert die dynamische Zuweisungslogik dieses Plugins.

### `AIOxTethers_MaxOxTethers`
Definiert die absolute Obergrenze an Ochsenjochen für die KI. Dieser Wert wird unter keinen Umständen überschritten.

### `AIOxTethers_DynamicMaxOxTethers`
Definiert eine dynamische Obergrenze. Das Maximum berechnet sich aus: `(Dieser Wert) * (Anzahl der Steinbrüche)`.

### `AIOxTethers_MinimumOxTethersPerQuarry`
Soll eine Unterversorgung verhindern. Fällt die Anzahl der einem Steinbruch zugewiesenen Ochsenjoche unter diesen Wert, wird der Bau eines neuen Jochs für diesen Steinbruch veranlasst.

### `AIOxTethers_MaximumOxTethersPerQuarry`
Verhindert den Bau weiterer Ochsenjoche für einen Steinbruch, sobald die Anzahl der ihm zugewiesenen Joche diesen Wert erreicht hat.

### `AIOxTethers_ThresholdStoneLoad`
Der Schwellenwert, der den Bedarf für ein neues Ochsenjoch signalisiert. Ein neues Joch wird gebaut, wenn das Ergebnis der Formel `Steine im Steinbruch / zugewiesene Joche` diesen Wert übersteigt.
