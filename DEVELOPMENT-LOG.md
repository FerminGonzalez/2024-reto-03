# Reto 03 — Development Log (Desafío de Inteligencia Artificial)

Historial de trabajo y notas del reto 03 (3 asignaciones con Azure AI).

---

## 2026-10-12 — Auditoría y completado del repositorio

### Naturaleza del reto
A diferencia de los retos 01 y 02, el reto 03 **no tiene backend desplegable**.
Las 3 asignaciones se **demuestran en vivo en los portales de Azure AI**
(Speech Studio, Language Studio, Video Indexer, AI Search). El repositorio
contiene los enunciados, los archivos multimedia/datos de entrada y la guía
de demostración (`SOLUTION.md`).

### Estado inicial
- `README.md`: índice de las 3 asignaciones.
- `SOLUTION.md`: tabla de criterios → servicio Azure y orden de demostración.
- `asignación1/`: `cm_faq.docx`, `booking_request.wav`, `individual_audios/`
  (6 audios), `pronunciation_assessment.mp3`.
- `asignación2/`: `responsible_ai.mp4`, `index.html` (demo), `insight_timeline_interactions.js`.
- `asignación3/`: `complains.csv` (19 quejas multilingües).
- `CLAUDE.md`: brief del reto.

### Verificaciones realizadas
| Verificación | Resultado |
|--------------|-----------|
| Rutas de directorios | ✅ Confirmado: usan **ñ/acento** (`asignación1/`, no `asignacion1/`) |
| `asignación2/insight_timeline_interactions.js` sintaxis (`node --check`) | ✅ Válida |
| `asignación2/index.html` estructura | ✅ 4 `<script>`, referencia al JS en línea 53; marcadores de iframe en líneas ~41 y ~45 |
| `asignación3/complains.csv` | ✅ 8 columnas, 19 filas, 0 inconsistencias; reviews multilingües (es/fr/de/it) |

### Hallazgo / corrección importante
El `CLAUDE.md` original referenciaba `asignacion1/`, `asignacion2/`,
`asignacion3/` **sin ñ ni acentos**, pero los directorios reales del repo son
`asignación1/`, `asignación2/`, `asignación3/`. Corregido para evitar confusiones
al navegar (en terminal usar comillas o tab-completado por los caracteres no ASCII).

### Mejoras aplicadas
1. **`CLAUDE.md`** — corregidas las rutas (`asignaciónN/`), añadidos los servicios
   Azure AI y las entradas de cada asignación; sección de estado actualizada.
2. **`DEVELOPMENT-LOG.md`** — este archivo.

### Resumen de las 3 asignaciones
| # | Objetivo | Servicios Azure AI | Entradas |
|---|----------|--------------------|----------|
| 1 | Servicio al cliente (voz+idioma+FAQ+pronunciación) | Speech, Language (Custom question answering) | `booking_request.wav`, `individual_audios/`, `cm_faq.docx`, `pronunciation_assessment.mp3` |
| 2 | Indexador de video (capacitación) | Video Indexer | `responsible_ai.mp4`, `index.html`, `insight_timeline_interactions.js` |
| 3 | Análisis de quejas (retención/ingresos) | Language, Storage (tablas), AI Search | `complains.csv` |

### Pistas clave (asignación 2)
El `index.html` contiene dos marcadores donde se insertan los **iframes** de
Video Indexer (las "pistas en líneas 41 y 45" del enunciado):
```html
<!-- ADD IFRAME Player HERE -->     <!-- ~línea 41: reproductor -->
<!-- ADD IFRAME Insights HERE -->   <!-- ~línea 45: insights/línea de tiempo -->
```
El `insight_timeline_interactions.js` **no requiere modificarse**; debe guardarse
en la misma carpeta que el `index.html`.

### Pendiente / futuro
- ⬜ Completar la demo en los portales de Azure (requiere suscripción Azure activa).
- ⬜ Los recursos de Azure pueden reutilizarse entre las 3 asignaciones.
