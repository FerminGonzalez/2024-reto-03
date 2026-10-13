# 2024-reto-03 - Desafío de Inteligencia Artificial

## Propósito
Desafío de hackathon 2024: Tres asignaciones relacionadas con IA para mejora de operaciones empresariales.

## Asignaciones

> **Nota de rutas:** los directorios reales usan **ñ y acentos**: `asignación1/`,
> `asignación2/`, `asignación3/`. Al navegar en terminal, usa comillas o tab-completado.

### Asignación 1 - Satisfacción y retención del cliente
- **Enfoque**: Servicio al cliente (voz + idioma + FAQ + pronunciación)
- **Ruta**: `asignación1/`
- **Azure AI**: Speech (Speech Studio), Language (Custom question answering)
- **Entradas**: `cm_faq.docx`, `booking_request.wav`, `individual_audios/`, `pronunciation_assessment.mp3`

### Asignación 2 - Capacitación de colaboradores
- **Enfoque**: Indexador de videos
- **Ruta**: `asignación2/`
- **Azure AI**: Video Indexer
- **Entradas**: `responsible_ai.mp4`, `index.html` (demo con iframes), `insight_timeline_interactions.js`

### Asignación 3 - Retención de clientes e ingresos
- **Enfoque**: Análisis de quejas
- **Ruta**: `asignación3/`
- **Azure AI**: Language (análisis de texto), Storage (tablas), AI Search
- **Entradas**: `complains.csv` (19 quejas multilingües, 8 columnas)

## Estructura del repositorio
```
asignación1/  - Código y recursos asignación 1
asignación2/  - Código y recursos asignación 2
asignación3/  - Código y recursos asignación 3
README.md     - Descripción general (índice de asignaciones)
SOLUTION.md   - Solución detallada (tabla de criterios -> servicio Azure)
```

## Comandos habituales
```bash
# Navegar entre asignaciones
cd asignacion1/
cd asignacion2/
cd asignacion3/

# Revisar contenido
ls -la
cat README.md 2>/dev/null || echo "No hay README específico"
```

## Formato de commits (Convencionales)
```
git commit -m "asignacion: descripción breve - número"

tipos sugeridos:
- asignacion1: trabajos en servicio al cliente
- asignacion2: indexación de videos o ML
- asignacion3: análisis de quejas o dashboards
- docs: documentación de hallazgos
- feat: nuevo modelo/característica
```

## Estado actual
- ✅ 3 subcarpetas de asignación (`asignación1/`, `asignación2/`, `asignación3/`)
- ✅ README.md (índice) y SOLUTION.md (tabla criterios → servicio Azure) en root
- ✅ Entradas de cada asignación presentes (audio, video, HTML/JS, CSV)
- ✅ Verificado: JS `insight_timeline_interactions.js` sintaxis válida;
  CSV `complains.csv` con 19 filas / 8 columnas consistentes
- ⬜ Las demos se ejecutan en los portales de Azure AI (no hay backend que correr localmente)
