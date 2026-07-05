# Star Citizen - Traducción al Español (con Blueprints/Recompensas)

Traducción no oficial al español de Star Citizen que combina lo mejor de varios
proyectos de traducción comunitaria con la información de **planos (blueprints)
y recompensas de contratos** que aporta [MrKraken/StarStrings](https://github.com/MrKraken/StarStrings)
(en inglés), traducida íntegramente al castellano.

## ¿Qué aporta este proyecto?

- **Base estructural**: [MrKraken/StarStrings](https://github.com/MrKraken/StarStrings),
  que añade a las descripciones de contratos y misiones qué planos y recompensas
  de reputación se pueden obtener al completarlos — información que ninguna
  traducción española incluye actualmente.
- **Máxima cobertura**: el resto de claves del juego (~93.000) se completan
  combinando cuatro proyectos de traducción comunitaria, seleccionando para
  cada línea la fuente más completa y de mejor calidad disponible.
- **Huecos rellenados**: las claves que no existían en ninguna fuente española
  (contenido nuevo del parche actual, o texto exclusivo de MrKraken) se han
  traducido desde cero manteniendo la terminología y el tono del resto del
  archivo.
- **Trazabilidad**: se mantiene un log interno (no distribuido en el propio
  `global.ini`) que indica de qué fuente proviene cada línea, para facilitar
  el mantenimiento futuro.

Este proyecto es un **trabajo derivado**. No pretende sustituir ni desmerecer
el trabajo de ninguno de los equipos originales — al contrario, existe gracias
a él. Ver [Agradecimientos](#agradecimientos--créditos).

## Instalación

1. Descarga `global.ini` desde este repositorio (carpeta
   `data/Localization/spanish_(spain)/global.ini`) o desde la última
   [Release](../../releases) si el proyecto publica una.
2. Copia el archivo a la carpeta de instalación de Star Citizen, dentro de
   `LIVE` (créala si no existe la ruta completa):

   ```
   [Ruta de instalación de Star Citizen]\LIVE\data\Localization\spanish_(spain)\global.ini
   ```

   Por ejemplo:

   ```
   C:\Program Files\Roberts Space Industries\StarCitizen\LIVE\data\Localization\spanish_(spain)\global.ini
   ```

3. Edita (o crea) el archivo `user.cfg` en la raíz de `LIVE`
   (`...\StarCitizen\LIVE\user.cfg`) y añade la línea:

   ```
   g_language = spanish_(spain)
   ```

   Si el archivo ya existe y tiene otras líneas, simplemente añade esta al
   final; no borres el resto del contenido.

4. Inicia el juego. El menú y los textos deberían aparecer en español.

### ¿Sirve para PTU?

Sí. Copia el mismo `global.ini` en la carpeta equivalente de la build PTU
(normalmente `...\StarCitizen\PTU\data\Localization\spanish_(spain)\global.ini`)
y añade la misma línea `g_language = spanish_(spain)` a su `user.cfg`. Ten en
cuenta que PTU cambia de contenido con frecuencia y esta traducción puede
quedarse temporalmente desactualizada respecto a esa build.

## Actualizaciones

Este proyecto incluye una skill reutilizable, `/update-translations` (ver
`.claude/skills/update-translations/`), que actualiza el `global.ini` de forma
incremental: descarga solo los archivos `.ini` de origen (sin clonar los
repos enteros), detecta qué claves faltan en el archivo actual y las resuelve
en paralelo con un pequeño equipo de subagentes (`.claude/agents/`) — un
Manager que planifica, un Scout que trae los archivos y fusiona el resultado,
y varios Translators que traducen cada uno su propio lote. Las claves ya
presentes en el archivo nunca se re-evalúan, así que las ejecuciones
rutinarias son rápidas y baratas. Para una reconstrucción completa desde cero
(por ejemplo tras cambiar las reglas de prioridad/glosario), usa
`tools/build.py` directamente.

## Metodología (resumen)

1. Se usa `MrKraken/StarStrings` (inglés) como esqueleto para los contratos:
   aporta la estructura y el contenido extra de planos/recompensas.
2. Para cada clave, se compara su traducción en las cuatro fuentes españolas
   y se elige la de mejor calidad, con este orden de prioridad por defecto:
   Doncasta1996 > Thord82 > SC-en-Espanol > Dymerz — salvo que una fuente
   tenga una traducción claramente mejor o más actual para esa línea concreta
   (p. ej. si la de mayor prioridad es un placeholder sin traducir).
3. El contenido añadido por MrKraken respecto al texto vanilla (recompensas de
   reputación, planos potenciales, puntos de progreso de escenario, etc.) se
   traduce y se añade a la traducción española ya existente de la base.
4. Las claves sin ninguna traducción española se traducen desde cero,
   manteniendo terminología, tono y marcadores (`<EM4>`, `~mission(...)`, etc.)
   consistentes con el resto del archivo.

## Agradecimientos / Créditos

Este proyecto no existiría sin el trabajo de:

- **MrKraken** — [StarStrings](https://github.com/MrKraken/StarStrings)
  (estructura base en inglés y datos de planos/recompensas de contratos)
- **Jose_Pacheco** y colaboradores (Autovot, JimmyVaras, Keiran, Mornack,
  Speler, ZettaZ) — [Doncasta1996/Star-Citizen-Spanish](https://github.com/Doncasta1996/Star-Citizen-Spanish)
- **Thord82** y equipo Osiris-DevWorks/smart-citizen — [Thord82/Star_citizen_ES](https://github.com/Thord82/Star_citizen_ES)
- **Autovot, Keiran, Sπeler, ZettaZ, Doncasta1996, JimmyVaras, Jota_be,
  juancmontes, 0zzyt0, Mornack** — [SC-en-Espanol/StarCitizen-Localization-Spanish](https://github.com/SC-en-Espanol/StarCitizen-Localization-Spanish)
- **Dymerz** — [Dymerz/StarCitizen-Localization](https://github.com/Dymerz/StarCitizen-Localization)
- **JotaBe1 (Jota_be)** — [JotaBe1/StarCitizen_ESP](https://github.com/JotaBe1/StarCitizen_ESP)
  (distribuido en `.rar` vía Releases; no incorporado automáticamente en esta
  versión por falta de herramientas de extracción en el entorno de
  generación — revisa su repositorio directamente si quieres comparar)
- **0zzyt0** — ["STAR CITIZEN SPA TRANSLATION"](https://www.nexusmods.com/starcitizen/mods/43)
  en Nexus Mods (distribuido en `.zip`; mismo motivo de no incorporación
  automática que el punto anterior)

Si alguna atribución no es correcta o falta algún colaborador, abre un issue
o contacta para corregirlo.

## Aviso legal

Este es un proyecto de fans **no oficial**, sin afiliación con Cloud Imperium
Games, Roberts Space Industries ni ninguna de sus filiales. "Star Citizen",
todos los nombres de naves, organizaciones, sistemas y demás contenido
original del juego son marcas y propiedad de sus respectivos dueños. Este
repositorio se distribuye únicamente con fines de traducción/localización
comunitaria, al amparo de la
[política de localización de la comunidad de CIG](https://robertsspaceindustries.com/spectrum/community/SC/forum/1/thread/star-citizen-community-localization-update).
Úsalo bajo tu propio criterio.
