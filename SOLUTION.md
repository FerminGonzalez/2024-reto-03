# Reto 03 — Solución (Desafío de Inteligencia Artificial)

Tres asignaciones basadas en **Azure AI**. No requieren despliegue web; se demuestran en vivo
(en pestañas separadas del navegador) usando los portales de Azure. Recursos a habilitar en
`portal.azure.com`: **Azure AI Speech**, **Azure AI Language**, **Azure AI Video Indexer**,
**Azure Search / AI Search** y una **Storage Account**.

---

## Asignación 1 — Servicio al Cliente (voz + idioma + FAQ + pronunciación)

Entradas: `asignación1/cm_faq.docx`, `asignación1/booking_request.wav`, carpeta `individual_audios/`,
`asignación1/pronunciation_assessment.mp3`.

| Criterio | Servicio Azure | Cómo demostrarlo |
|---|---|---|
| 1. Detección de idioma en tiempo real | **Azure AI Speech → Speech Studio** | Subir `booking_request.wav` a *Real-time speech to text*; activar *automatic language detection* con la lista de 10 idiomas (ar, zh-CN, en-GB, fr-FR, de-DE, ja-JP, ko-KR, ro-RO, es-ES, uk-UA). Mostrar transcripción por párrafos con su idioma. |
| 2. Transcripción y traducción en tiempo real | Speech Studio (speech-to-text + translate) | Para cada audio de `individual_audios/` obtener transcripción en idioma original y **traducción al español** con *Speech translation*. |
| 3. Bot de FAQ | **Azure AI Language → Custom question answering** | Cargar `cm_faq.docx` como fuente de conocimiento. Respuestas literales (no generativas). Reglas: fallback = `No tengo la respuesta a esa pregunta. Por favor, contacta al soporte al cliente para más asistencia.`; saludos `holis` / `que xopa` / `amigo` = `Hola fren 🤙, ¿en qué puedo ayudarte hoy?` |
| 4. Evaluación de pronunciación | **Speech Studio → Pronunciation assessment** | Subir `pronunciation_assessment.mp3`; mostrar *accuracy/fluency/completeness/prosody* y errores (malas pronunciaciones, pausas inesperadas/faltantes). |

Orden de demostración: `1 → 2 → 3.1 → 3.2 → 3.3 → 4`.

---

## Asignación 2 — Indexador de video (capacitación)

Entradas: `asignación2/index.html`, `asignación2/insight_timeline_interactions.js`,
`asignación2/responsible_ai.mp4`.

| Criterio | Servicio Azure | Cómo demostrarlo |
|---|---|---|
| 1. Extraer info de audio/video | **Azure AI Video Indexer** | Crear proyecto, subir `responsible_ai.mp4`, mostrar transcripción con **etiquetas de orador** y navegación clicando el texto. |
| 2. Editar/crear nuevo video | Video Indexer editor | Recortar a **20s < duración < 30s** incluyendo en pantalla los nombres `Eric Horvitz` y `Natasha Crampton` y el texto `Loan Application: DENIED`; previsualizar. |
| 3. Traducción al español | Video Indexer (multi-idioma) | Mostrar transcripción traducida al español junto al texto original. |
| 4. Página de demo | `index.html` local | Editar `index.html` (ver pistas líneas 41 y 45) para embeber reproductor + timeline; `insight_timeline_interactions.js` en la misma carpeta. Mostrar nº de orador y transcripción traducida al español. |

---

## Asignación 3 — Análisis de quejas

Entrada: `asignación3/complains.csv`.

Servicios: **Azure AI Document Intelligence / Azure Storage Tables** (ingesta),
**Azure AI Language** (enriquecimiento por sentencias), **Azure AI Search** (índice + proyecciones).

| Criterio | Cómo demostrarlo |
|---|---|
| 1. Recursos Azure usados | Mostrar Storage Account + Azure AI Search + Azure AI Language en el portal. |
| 2. Cuenta de almacenamiento con tablas | En *Storage Explorer → Tables* mostrar las proyecciones enriquecidas `Documents`, `Sentences`, `KeyPhrases`. |
| 3.1 Campos del índice | En el índice de Azure AI Search mostrar/mapear: `iata_code`, `country`, `city`, `reviews_text`, `hackathon_keyphrases`, `hackathon_language`, `hackathon_translated_text`, `hackathon_sentiment`. |
| 3.2 Búsqueda `*` | Ejecutar consulta `search=*` y mostrar los campos devueltos: `AzureSearch_DocumentKey`, `IATA_code`, `country`, `city`, `hackathon_keyphrases`, `hackathon_language`, `hackathon_translated_text`, `hackathon_sentiment` + `@search.score`. |

Mapeo de habilidades del *skillset* (granularidad de sentencia):
- `hackathon_keyphrases` ← *Key Phrase Extraction* (Key Phrases por oración)
- `hackathon_language` ← *Language Detection*
- `hackathon_translated_text` ← *Text Translation* (a `es`)
- `hackathon_sentiment` ← *Sentiment Analysis*
