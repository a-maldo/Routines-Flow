# 🎮 Routine Flow (TGC Games)

**Estado:** Pre-lanzamiento interno  
**Versión:** v0.23.0 • _2025-10-07_  
**Stack:** HTML + CSS + JavaScript (vanilla) • Sin build • Listo para GitHub Pages

> Juego educativo que transforma las **rutinas reales** del Turabo Gymnastics Center (TGC) en una experiencia **interactiva** para aprender los **nombres**, **orden** y **puntos técnicos** de las destrezas en **Baby Gym, Básico e Intermedio**. Mezcla **ritmo**, **precisión** y **evaluación tipo competencia**.

---

## 📑 Tabla de contenido

- [Características](#-características)
- [Objetivos pedagógicos](#-objetivos-pedagógicos)
- [Demo / Publicación](#-demo--publicación)
- [Inicio rápido](#-inicio-rápido)
- [Controles](#-controles)
- [Estructura del proyecto](#-estructura-del-proyecto)
- [Datos de rutinas (JSON)](#-datos-de-rutinas-json)
- [Persistencia (localStorage)](#-persistencia-localstorage)
- [Puntuación y evaluación](#-puntuación-y-evaluación)
- [Accesibilidad](#-accesibilidad)
- [Desarrollo y convenciones](#-desarrollo-y-convenciones)
- [Roadmap y organización](#-roadmap-y-organización)
- [Monetización educativa y patrocinios](#-monetización-educativa-y-patrocinios)
- [Privacidad](#-privacidad)
- [Soporte y preguntas frecuentes](#-soporte-y-preguntas-frecuentes)
- [Créditos y licencias](#-créditos-y-licencias)
- [Changelog](#-changelog)

---

## ✨ Características

- **Contenido oficial del TGC**: destrezas y secuencias reales por **nivel** y **evento** (piso, viga, salto, barras; según aplique).
- **Modo rítmico**: aparece cada destreza con una ventana de tiempo para acertar al ritmo.
- **Ayudas técnicas**: pistas de **posiciones/movimientos** por destreza (p. ej., _Estrella → brazos extendidos_).
- **Evaluación tipo competencia**: precisión, combo, penalizaciones y resumen de intento.
- **UI/UX lista para clase**: pausa/reanudar, botón **Sonido ON/OFF**, alto contraste.
- **Sin dependencias**: corre localmente con doble clic a `index.html`.
- **GitHub Pages**: docs y manuales en `/docs`.

---

## 🎯 Objetivos pedagógicos

- Reforzar **nombres** y **orden** de las destrezas por nivel/evento.  
- Conectar **técnica** con **ejecución** mediante pistas visuales y sonoras.  
- Facilitar la **retroalimentación** docente con un resumen post-intento.

---

## 🌐 Demo / Publicación

- Público sugerido: `https://turabogymnastics.com/Games/routineflow` (password: Beta) 
- GitHub Pages: configura **Settings → Pages → Branch `main` / Folder `/docs`**.

> El juego es 100% estático: no requiere servidor ni build.

---

## 🚀 Inicio rápido

1. **Clonar/descargar** el repositorio.  
2. **Abrir** `index.html` en el navegador.  
3. (Opcional) Editar los JSON en `./data/routines/` para ajustar secuencias.  
4. (Opcional) Servir con un live server local para auto-reload (p. ej., VSCode _Live Server_).

**Requisitos:** Navegador moderno (Chrome, Edge, Firefox, Safari). Funciona en desktop y móvil (recomendado vertical).

---

## 🕹️ Controles

- **Click/Tap** sobre las notas/targets cuando la destreza llegue a la zona.  
- **Teclas** (si el layout lo define) para aciertos por teclado.  
- **Botón** de **Sonido ON/OFF** en el HUD.  
- **Pausa/Reanudar** desde el HUD o tecla indicada en pantalla.

---

## 🗂️ Estructura del proyecto

root ├─ index.html ├─ /assets               # imágenes, íconos, audio (sfx) ├─ /css                  # estilos ├─ /js                   # lógica │  ├─ core/              # loop, spawner, colliders, scoring │  ├─ ui/                # HUD, menús, modales, toggles │  └─ storage/           # utilidades de localStorage ├─ /data │  └─ routines/          # JSON por nivel/evento └─ /docs                 # Documentación (GitHub Pages) ├─ index.md ├─ manual-usuario.md ├─ guia-docente.md ├─ api.md ├─ monetizacion.md └─ privacidad.md

---

## 🔢 Datos de rutinas (JSON)

Cada archivo representa una secuencia **válida** para un **nivel** y **evento** específicos.

**Ejemplo mínimo:**
```json
{
  "nivel": "Basico",
  "evento": "Piso",
  "secuencia": [
    { "id": "estrella", "alias": "Estrella", "pistas": ["brazos extendidos"], "tiempo": 1200 },
    { "id": "rodada",  "alias": "Rodada adelante", "pistas": ["barbilla al pecho"], "tiempo": 2400 }
  ]
}


## Reglas:

nivel: Baby|Basico|Intermedio (valores oficiales TGC).

evento: Piso|Viga|Salto|Barras (según aplique).

secuencia[]: cada destreza tiene:

id (slug interno), alias (texto visible),

pistas[] (ayudas técnicas breves),

tiempo (ms desde el inicio para la aparición/beat).



> Consulta /docs/api.md para detalles y validación.




---

💾 Persistencia (localStorage)

Claves sugeridas:

rf:settings → volumen, ayudas visuales, modo alto contraste, preferencias.

rf:progress → mejores puntajes por nivel/evento.

rf:version → versión de datos/app para posibles migraciones.


Ejemplo rf:settings:

{
  "audio": { "enabled": true, "volume": 0.8 },
  "accessibility": { "highContrast": false, "fontScale": 1.0 }
}


---

🧮 Puntuación y evaluación

Precisión (timing window): Perfecto / Bien / Temprano / Tarde.

Combo: multiplicador por aciertos consecutivos; se reinicia al fallar.

Penalizaciones: fuera de tiempo, destreza omitida o fuera de orden.

Resumen de intento: precisión media, combo máximo, errores por tipo.


> Las ventanas de tiempo y pesos son configurables en /js/core/scoring.js.




---

♿ Accesibilidad

Modo alto contraste y tamaños legibles.

Focus visible para elementos interactivos.

Sonido opcional (activable en HUD).

Recomendación: usar en pantalla grande al trabajar con grupos.



---

🔧 Desarrollo y convenciones

JS Vanilla (ES Modules), sin frameworks.

Comentarios breves y nombres en español consistentes con la terminología TGC.

Estilos móviles-primero, comprobando accesibilidad (contraste y tamaños).

(Opcional) ESLint/Prettier para estilo de código.


Estructura recomendada de commits: Conventional Commits (feat:, fix:, docs:, refactor:, chore: …).

Contribuciones: ver CONTRIBUTING.md.


---

🗺️ Roadmap y organización

Tablero: GitHub Projects con columnas Backlog → Ready → In progress → Review → Testing → Done.

Épicas clave: Contenido TGC, Ritmo & Spawner, UI/UX, Audio, Evaluación, Docs/Pages, Monetización, Online/Ranking.

Hitos próximos:

v0.24.x → Datos TGC completos por nivel/evento.

v0.30.x → Evaluación expandida + reportes básicos.



Detalles en PROJECTS.md.


---

💸 Monetización educativa y patrocinios

Licencias educativas por sede/escuela (incluye guía docente).

Patrocinios locales con presencia cuidada (logos discretos in-game y en docs).

Edición Pro (futuro): reportes/estadísticas, exportables, ranking global.


Lineamientos y opciones en /docs/monetizacion.md.


---

🔐 Privacidad

No se recolectan datos personales por defecto.

localStorage solo guarda ajustes y puntajes en el navegador del usuario.

Sin cookies de terceros.


Más info en /docs/privacidad.md.


---

🛟 Soporte y preguntas frecuentes

¿Necesito internet?
Solo para la primera carga si se usa GitHub Pages. Luego funciona offline mientras la pestaña siga abierta.

¿Funciona en móvil?
Sí. Recomendado en horizontal y con sonido opcional.

¿Cómo actualizo las rutinas?
Edita/añade archivos en ./data/routines/ siguiendo el esquema JSON. Versiona cambios en CHANGELOG.md.

¿Cómo publico en GitHub Pages?
Activa Settings → Pages y selecciona branch main y carpeta /docs.

¿Otra duda? Abre un issue en el repositorio con capturas y pasos de reproducción.


---

🙌 Créditos y licencias

Diseño y dirección: TGC Games — inspirado en el trabajo educativo del Turabo Gymnastics Center (TGC).

Contenido técnico de rutinas: derivado de la práctica real del TGC (niveles Baby, Básico, Intermedio).

Código: MIT (sugerida). Revisa LICENSE.

Marcas y logotipos: propiedad de sus titulares, uso con fines educativos.


> Si usas este proyecto en otra institución, respeta la autoría del TGC y las licencias.




---

🗓️ Changelog

v0.23.0 — Documentación inicial para Pages, botón Sonido en HUD, esquema de datos con pistas técnicas.

v0.22.2.4 — Spawner: múltiples notas en pantalla pero nunca creadas a la misma vez; 1 nota por intervalo con compensación de frames; fixes menores.


Consulta el historial completo en CHANGELOG.md.


---

Hecho con ❤️ para la comunidad del TGC.