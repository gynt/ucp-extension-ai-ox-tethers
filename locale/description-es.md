# IA: puestos de bueyes

La IA normalmente construye hasta 3 puestos de bueyes por cantera. También coloca un puesto automáticamente cada vez que construye o reconstruye una cantera.

Estos puestos automáticos pueden agotar la capacidad de alojamiento de la IA e impedir que aparezcan nuevos campesinos. Esta extensión permite desactivarlos y personalizar cuándo se construyen más puestos.

Un **puesto vinculado** pertenece a la cantera de la que su trabajador recogió piedra por última vez. Estos vínculos se actualizan dinámicamente en lugar de usar una asignación fija.

## Funciones
- Permitir más de 3 puestos de bueyes por cantera
- Personalizar las reglas de decisión para construir más puestos de bueyes
- Personalizar las reglas por IA mediante el AIC

## Parámetros AIC

### `AIOxTethers_Logic`
0: Lógica original del juego.
1: Lógica dinámica con los límites y las reglas de carga de piedra siguientes.

### `AIOxTethers_MaxOxTethers`
Límite total de puestos de bueyes por jugador.

### `AIOxTethers_DynamicMaxOxTethers`
Límite total de puestos = este valor × número de canteras.
En todo momento se aplica el menor de los 2 límites totales.

### `AIOxTethers_ThresholdStoneLoad`
Si `piedra/puestos vinculados` supera este valor en una cantera, se construye otro puesto, respetando los límites. Si no hay puestos vinculados, se usa directamente la cantidad de piedra.

### `AIOxTethers_DisableInitialOxTether`
0: Colocar un puesto automáticamente cada vez que se construye o reconstruye una cantera.
1: Desactivar esta colocación automática.

Este ajuste es independiente de la lógica dinámica y de sus límites.

### `AIOxTethers_MinimumOxTethersPerQuarry`
Si una cantera tiene menos puestos vinculados que este valor, se construye otro independientemente de la carga de piedra, respetando el límite total.

### `AIOxTethers_MaximumOxTethersPerQuarry`
Límite de puestos vinculados que se construyen para una cantera según su carga de piedra. El mínimo debe ser igual o inferior a este límite.
