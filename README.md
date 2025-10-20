🏅 Routines Flow (nombre del juego)
Versión: v0.24.6.2
Estado: Estable — Pre-lanzamiento interno
Desarrollado para: Turabo Gymnastics Center (TGC)
Autor: Axel Maldonado — Proyecto TGC Games
Fecha: 2025-10-20

Cambios clave (v0.24.6.2):
- Fix MULTI: contador visible muestra restantes (xN → x0=OK) y no “rebota” texto.
- Swipe: ya no penaliza si hubo toque sin completar el gesto; solo será Miss al cruzar línea.
- HOLD: anclaje más preciso a 2px por encima de la línea mientras se mantiene presionado.
- Seguridad post-línea: si el DOM aparece tarde y ya cruzó, se registra Miss inmediatamente (sin parpadeo).
- Aros por carril: alineación precisa con nota y grosor real de la hitline (64×64, 6px).
- Se mantienen: rf-v0.4 (tap/hold/swipe/multi), QA/Tuning, Early/Late, anti-mash, grid.
