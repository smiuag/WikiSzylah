# TorchZhyla — ficheros de import

Recursos descargables que el usuario importa desde **Settings → Avanzado → Importar / exportar configuración** (o que asigna a un personaje en el caso del mapa). Cada ZIP es autocontenido: incluye los sonidos referenciados por sus triggers o categorías de ambiente, sin dependencias entre ZIPs.

Formato común: `torchzhyla-config-backup` v4 (ver `triggerPackExport.ts`). Los ZIPs son compatibles con cualquier instalación de TorchZhyla v4+.

---

## Bundle todo-en-uno

### `Config.zip` (~176 MB)
Pack completo con todo lo que sigue debajo. Pensado para alguien que quiere "darme la app entera lista". Contiene:

- 4 plantillas de triggers (262 triggers en total)
- 18 categorías de ambiente con sonidos asignados
- 27 gestos (16 activos por defecto)
- 177 sonidos personalizados

Si solo quieres una parte, usa los ZIPs específicos de abajo — pesan mucho menos.

---

## Plantillas de triggers (una por ZIP)

Cada ZIP contiene **una sola plantilla** + los sonidos que esa plantilla referencia. Al importar, el usuario decide a qué personajes la asigna desde la pantalla de Triggers.

### `pack-sonidos-del-mud.zip` (~4 MB)
30 triggers para sonidos generales de la partida (tells, canales, sucesos, alertas básicas). El más ligero — buen punto de entrada para alguien que quiere "ambientación mínima".

### `pack-combate-completo.zip` (~2 MB)
89 triggers de combate: golpes (recibidos/asestados), kills, hemorragias, alertas de vida (50/30/10%), bloqueos, hechizos preparándose y lanzándose, etc. Sonidos en estéreo paneado donde aplica.

### `pack-comunicaciones.zip` (~6 MB)
39 triggers de telepatía y canales: avisos de tells entrantes, canales abiertos/cerrados, menciones del nick propio, etc.

### `pack-movimiento.zip` (~6 MB)
104 triggers de movimiento: pasos propios, llegada de aliados/enemigos, sigilo, salidas direccionales, sigues a alguien, alguien te sigue, etc. El más completo en cantidad de variantes.

---

## Música ambiente

### `ambient.zip` (~159 MB)
18 categorías con sus mappings (bosque, ciudad, subterráneo, mar, taberna, etc.) y los wavs de bucle de fondo. **Pesa porque los wavs ambient son largos** — cada uno minutos de loop gapless. Si la conexión es lenta, mejor distribuirlo a parte de los packs de triggers.

Importar este ZIP NO toca tus categorías existentes que no vengan en él (merge por categoría). Si una categoría llega en el ZIP, sustituye la tuya.

---

## Gestos

### `gestures.zip` (~5 KB)
27 gestos del terminal con la configuración curada por defecto. 16 activos:

- 8 swipes 1 dedo → norte/sur/este/oeste y diagonales.
- 4 swipes 2 dedos cardinales → arriba/abajo/dentro/fuera.
- 2 pinches → `cerrar` y `abrir` con selector de salidas (autoSend).
- 2 dedos doble tap → prepara `responder` en el input.
- Doble tap + arrastrar arriba → prepara `t` con selector de jugadores (últimos tells recibidos).

Los 11 restantes vienen sin configurar (disabled, vacíos) listos para que el usuario los asigne.

Importar este ZIP **sustituye** todos tus gestos actuales. No se mergea.

---

## Mapa

### `map-reinos-mudlet.json` (~28 MB)
JSON **crudo de Mudlet** del mapa de Reinos de Leyenda — el resultado directo de `lua saveJsonMap(...)` en Mudlet. Se importa desde **Settings → Avanzado → Mis mapas** pulsando "Importar de Mudlet". La app **optimiza al guardarlo** (aplana áreas, traduce direcciones a códigos cortos, resuelve colores via `customEnvColors`, descarta `userData`, etc.) — ese paso tarda 1-3 segundos en el móvil porque el JSON pesa.

Tras la importación se asigna a un personaje desde la pantalla de edición del personaje. Cada personaje puede usar un mapa distinto.

NO importar este JSON con el flujo de configuración (Importar / exportar): va por el flujo separado de "Mis mapas".

---

## Notas de uso

- **Personaje + plantilla**: tras importar una plantilla, asígnala manualmente a tus personajes desde la pantalla de Triggers (la app pregunta tras la importación si ya tienes personajes).
- **Sonidos duplicados**: cada import añade los sonidos con UUIDs frescos. Si importas el mismo ZIP dos veces, tendrás los wavs duplicados en "Mis sonidos" (los puedes borrar a mano).
- **Importar Settings**: la opción "Settings de la app" del modal de importación NO viene rellena en estos ZIPs — son contenido, no configuración personal del usuario.
