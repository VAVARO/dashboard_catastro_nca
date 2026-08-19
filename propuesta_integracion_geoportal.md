# Propuesta de Integración del Catastro de Equipamiento Científico en el Geoportal Ciencia Austral

## 1. Contexto y Objetivos

El **Nodo Ciencia Austral**, en articulación con el Nodo Laboratorio Natural Subantártico y el Nodo Antártico, ha desarrollado la plataforma **Geoportal Ciencia Austral** basada en tecnología ArcGIS Online (AGOL). El objetivo central del Geoportal es democratizar el acceso a los datos e información de Ciencia, Tecnología, Conocimiento e Innovación (CTCI) en la Macrozona Austral, promoviendo la interoperabilidad y el uso colaborativo.

Por otro lado, el **Catastro de Equipamiento Científico de la Macrozona Austral** consolida actualmente **29 equipos e infraestructuras de alta tecnología** distribuidos en **9 instituciones** de las regiones de Aysén y Magallanes (incluido el territorio antártico).

La integración de este catastro en el Geoportal resuelve directamente el problema de invisibilidad y dificultad de acceso a la infraestructura científica regional, transformando una planilla estática en un **recurso geoespacial interactivo y abierto**.

---

## 2. Opciones de Integración según los Mecanismos del Geoportal

De acuerdo con el *Manual de Colaboración del Geoportal Ciencia Austral*, se evalúan tres opciones de integración correspondientes a los tres niveles y secciones de la plataforma:

```
                  ┌─────────────────────────────────────────────────────────┐
                  │   CATASTRO DE EQUIPAMIENTO CIENTÍFICO (29 EQUIPOS)      │
                  └───────────────────────────┬─────────────────────────────┘
                                              │
        ┌─────────────────────────────────────┼─────────────────────────────────────┐
        ▼                                     ▼                                     ▼
┌───────────────┐                     ┌───────────────┐                     ┌───────────────┐
│   OPCIÓN 1    │                     │   OPCIÓN 2    │                     │   OPCIÓN 3    │
│  BIBLIOTECA   │                     │   MAPOTECA    │                     │ VISUALIZADORES│
│  (Documento)  │                     │ (Capa ArcGIS) │                     │  (Dashboard)  │
└───────────────┘                     └───────────────┘                     └───────────────┘
```

---

### OPCIÓN 1: Integración Documental en la "Biblioteca"
*   **Mecanismo del Manual:** *Aporta Documentos* (Sección Biblioteca).
*   **Formato de Entrada:** Archivo PDF / PNG exportado a partir de los documentos `catastro_equipos_cientificos.md` y `acceso_informacion_equipos.md`.
*   **Procedimiento:** 
    1. Cargar los documentos mediante el formulario web de colaboración del Geoportal.
    2. Asignar metadatos (palabras clave: *Equipamiento CTCI*, *Infraestructura Científica*, *Macrozona Austral*, *ANID*, *FONDEQUIP*).
    3. Asignar georreferenciación global a la Macrozona Austral (o vincular a las sedes institucionales).
*   **Ventajas:** 
    *   Implementación inmediata (sin requerimientos de desarrollo técnico).
    *   Disponible de forma rápida para descarga en el catálogo documental.
*   **Desventajas:** 
    *   Información estática (PDF).
    *   No permite filtrado dinámico espacial, búsqueda por radio geográfico ni consulta interactiva por atributos.

---

### OPCIÓN 2: Capa Geoespacial Interactiva en la "Mapoteca" (Feature Layer)
*   **Mecanismo del Manual:** *Aporta Capas Geoespaciales* (Sección Mapoteca).
*   **Formato de Entrada:** Capa de Puntos (`Shapefile`, `GeoJSON`, `GeoPackage` o `Feature Layer` directa en AGOL).
*   **Procedimiento:**
    1.  **Georreferenciación:** Asignar coordenadas geográficas exactas (Latitud/Longitud) a cada uno de los 29 equipos según su ubicación física real (ej. Laboratorio CIEP en Alto Baguales, Campus Lillo U. Aysén, CADI-UMAG en Punta Arenas, Estación Patagonia UC en Bahía Exploradores, Base Escudero en Antártica, etc.).
    2.  **Estandarización de Atributos:** Crear la tabla de atributos de la capa con los siguientes campos estandarizados:

| Campo (Atributo) | Tipo de Dato | Ejemplo / Contenido |
| :--- | :--- | :--- |
| `ID_Equipo` | Texto | `EQP-001` |
| `Nombre_Equipo` | Texto | `Microscopio de Fuerzas Atómicas` |
| `Institucion` | Texto | `Universidad de Aysén` |
| `Categoria_Tecnica` | Texto | `Microscopía`, `Oceanografía`, `Cromatografía`, `Meteorología`, etc. |
| `Marca_Modelo` | Texto | `Asylum Research / Infinity BIO` |
| `Ubicacion_Fisica` | Texto | `Laboratorio de Fisiología Celular y Metabolismo, Coyhaique` |
| `Comuna` | Texto | `Coyhaique` |
| `Region` | Texto | `Región de Aysén` |
| `Estado_Actual` | Texto | `Activo`, `Inactivo`, `Activo con restricciones` |
| `Modelo_Acceso` | Texto | `Convenio`, `Tarifario público`, `Sin costo` |
| `Canal_Contacto` | Texto / URL | `mailto:investigacion@uaysen.cl` o enlace a Formulario Google |
| `Nivel_Acceso_Web` | Texto | `Alto`, `Medio`, `Bajo` |
| `Descripcion_Cientifica` | Texto Largo | Párrafo breve sobre funcionamiento, propósito y aplicaciones |

    3.  **Publicación:** Subir la capa vía Survey123 o AGOL y vincularla al grupo institucional **"Mapoteca del Geoportal Ciencia Austral"**.
*   **Ventajas:**
    *   Permite visualizar espacialmente la distribución de la capacidad científica regional.
    *   Los usuarios pueden filtrar capas por institución o categoría técnica dentro del mapa del Geoportal.
    *   Datos abiertos e interoperables descargables en múltiples formatos.
*   **Desventajas:**
    *   Requiere consolidar y validar las coordenadas GPS de cada laboratorio antes de la publicación.

---

### OPCIÓN 3: Aplicación / Dashboard Dedicado en "Visualizadores" (Recomendada)
*   **Mecanismo del Manual:** *Crea y Comparte Aplicaciones* (Sección Visualizadores).
*   **Formato de Entrada:** *ArcGIS Dashboard* o *StoryMap* interactivo.
*   **Descripción del Aplicativo:** **"Dashboard de Infraestructura y Equipamiento Científico de la Macrozona Austral"**.

```
┌──────────────────────────────────────────────────────────────────────────────────────────┐
│                             PANEL SUPERIOR DE FILTROS                                     │
│ [ Selector Institución ▼ ]   [ Selector Categoría Técnica ▼ ]   [ Estado de Acceso ▼ ]   │
├────────────────────────────────────────┬─────────────────────────────────────────────────┤
│           MAPA INTERACTIVO             │              INDICADORES Y DETALLE              │
│                                        │  • Total Equipos: 29                             │
│   (Puntos georreferenciados de         │  • Instituciones: 9                             │
│   equipos con simbología por           │  • Equipos en Aysén: 18 / Magallanes: 11         │
│   Categoría Técnica)                   │                                                 │
│                                        │  FICHA DEL EQUIPO SELECCIONADO:                 │
│   [Pop-up al hacer clic]:              │  - Nombre / Marca y Modelo                      │
│   - Foto del equipo                    │  - Descripción Breve (1-2 párrafos)             │
│   - Contacto directo / Formulario      │  - Requisitos y Nivel de Acceso                 │
│   - Botón: [Solicitar Uso]             │  - [ Botón Directo a Solicitud ]                │
└────────────────────────────────────────┴─────────────────────────────────────────────────┘
```

*   **Procedimiento:**
    1. Construir la capa Geoespacial de la Opción 2 en ArcGIS Online.
    2. Diseñar la interfaz en *ArcGIS Dashboards* o *ArcGIS Web AppBuilder*.
    3. Configurar ventanas emergentes (*Pop-ups*) interactivas que incluyan la descripción breve redactada en el catastro, datos de contacto y enlaces directos a formularios de reserva (ej. el Google Form del Museo Regional de Aysén).
    4. Vincular la aplicación al grupo **"Visualizadores del Geoportal Ciencia Austral"**.
*   **Ventajas:**
    *   **Máximo impacto visual e institucional** para reuniones con la seremi de Ciencia, GORE, ANID y universidades.
    *   Facilita la toma de decisiones estratégicas de inversión (identifica vacíos territoriales de equipamiento).
    *   Permite a cualquier investigador encontrar en segundos qué equipo existe, dónde está y cómo solicitarlo.
*   **Desventajas:**
    *   Requiere configuración de la aplicación en AGOL por parte del equipo del Geoportal.

---

## 3. Cuadro Comparativo de las Opciones

| Criterio | Opción 1: Biblioteca (PDF) | Opción 2: Mapoteca (Capa GIS) | Opción 3: Visualizador (Dashboard) |
| :--- | :--- | :--- | :--- |
| **Tiempo de Implementación** | Inmediato (< 1 hora) | Corto (1 - 2 días) | Medio (3 - 5 días) |
| **Interactividad Espacial** | Nula | Media (Filtros en mapa) | **Alta** (Dashboard integrado) |
| **Búsqueda por Atributos** | Texto en PDF | Filtros de tabla GIS | **Filtros dinámicos visuales** |
| **Facilidad de Uso Público** | Media | Media-Baja (requiere uso de SIG) | **Muy Alta** (Navegación intuitiva) |
| **Cumplimiento Manual Geoportal** | Sección *Biblioteca* | Sección *Mapoteca* | Sección *Visualizadores* |
| **Valor de Gestión CTCI** | Bajo | Medio | **Excelente (Toma de decisiones)** |

---

## 4. Estrategia Gradual Recomendada para la Reunión

Para optimizar la presentación ante el equipo del Geoportal, se sugiere proponer una **implementación por fases acumulativas**:

1.  **Fase 1 (Inmediata - Hoy):** Cargar el informe en formato PDF a la **Biblioteca** utilizando el formulario web del Geoportal (Opción 1), asegurando presencia documental inmediata.
2.  **Fase 2 (Próxima semana):** Entregar al equipo técnico del Geoportal el archivo `GeoJSON` o `Shapefile` con las coordenadas normalizadas de las 9 instituciones y la tabla de atributos completa para su publicación en la **Mapoteca** (Opción 2).
3.  **Fase 3 (Hito de Lanzamiento):** Co-diseñar el **Dashboard de Equipamiento CTCI Austral** para publicarlo en la sección de **Visualizadores** (Opción 3), posicionándolo como una herramienta clave de articulación macrozonal.

---

## 5. Puntos de Acuerdos a Solicitar en la Reunión

Durante la reunión con el equipo del Geoportal, se recomienda definir los siguientes aspectos técnicos:

1.  **Designación de Responsables:** ¿Quién asignará las coordenadas exactas de laboratorio si se requiere mayor precisión geométrica?
2.  **Asignación de Cuentas AGOL:** Determinar si la capa será subida por un *Usuario Externo* (formulario Survey123 + envío de datos) o si un miembro del Nodo con *Cuenta de Organización AGOL* la publicará directamente en el grupo oficial.
3.  **Mantenimiento y Actualización:** Acordar una frecuencia de revisión semestral o anual para actualizar el estado operativo de los equipos y la incorporación de nueva infraestructura en la Macrozona Austral.
