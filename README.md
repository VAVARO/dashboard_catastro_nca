# 🌍 Geoportal y Dashboard de Equipamiento CTCI - Nodo Ciencia Austral

[![Nodo Ciencia Austral](https://img.shields.io/badge/Nodo-Ciencia%20Austral-1E327B?style=for-the-badge)](https://nodoaustral.cl/)
[![Licencia](https://img.shields.io/badge/Estado-Producci%C3%B3n%20%2F%20V2-BDF8B8?style=for-the-badge&logoColor=1C1F40)](https://github.com/VAVARO/dashboard_catastro_nca)
[![Macrozona Austral](https://img.shields.io/badge/Territorio-Ays%C3%A9n%20%7C%20Magallanes%20%7C%20Ant%C3%A1rtica-88B991?style=for-the-badge)](https://github.com/VAVARO/dashboard_catastro_nca)

Plataforma interactiva, georreferenciada y de acceso abierto para el catastro técnico de equipamiento e infraestructura científica y tecnológica (**CTCI**) de la **Macrozona Austral de Chile** (Región de Aysén del General Carlos Ibáñez del Campo, Región de Magallanes y de la Antártica Chilena, y Territorio Chileno Antártico).

---

## 📌 1. Visión General y Arquitectura

El Geoportal permite a investigadores/as, instituciones y tomadores de decisión explorar, filtrar y solicitar acceso a los **37 equipamientos científicos mayores y medianos** catastrados en la macrozona.

### Flujo de Datos y Resiliencia (Dual-Mode)
1. **Conexión en Vivo (Online):** Al cargar, la aplicación consulta directamente la planilla pública de Google Sheets en formato CSV mediante `PapaParse`. Esto permite que cualquier edición en la planilla se refleje inmediatamente en el dashboard sin tocar código.
2. **Respaldo Local Integrado (Offline / Contingencia):** Si la conexión a internet falla o el archivo se abre localmente (`file:///`), el sistema conmuta automáticamente a una constante embebida (`LOCAL_CSV_BACKUP`) enriquecida con los datos del catálogo curado `Catastro_v4.csv`.
3. **Diccionario Descriptivo Científico:** Incorpora un motor en JavaScript (`SCIENTIFIC_DESCRIPTIONS` y `getScientificDescription()`) que asocia automáticamente el principio físico/técnico y las aplicaciones científicas a cada equipo.

---

## 📂 2. Mapa del Repositorio y Catálogo de Archivos

A continuación se detalla el propósito exacto de cada elemento del repositorio para facilitar su mantenimiento y transferencia a futuros administradores:

```text
├── 🌐 Aplicación Web Principal (Producción):
│   ├── index.html                                  # Entrada web que redirige al Geoportal de Producción (GitHub Pages)
│   ├── dashboard_geoportal_v2.html                 # APLICACIÓN PRINCIPAL (HTML/CSS/JS autónomo de producción)
│   └── Logo-Nodo-sinfondo-1-scaled.png             # Logo oficial en alta resolución del Nodo Ciencia Austral
│
├── 📊 Base de Datos Oficial:
│   └── Catastro_v4.csv                             # Dataset maestro y curado (37 equipamientos, contactos, DOIs, coordenadas)
│
└── 📑 Informes Técnicos, Auditorías y Criterio Científico:
    ├── catastro_equipos_cientificos.md             # Diccionario descriptivo técnico y funcional de los 37 equipos
    ├── acceso_informacion_equipos.md               # Auditoría de presencia web, tarifas, formularios y modelos de acceso
    ├── auditoria_ubicaciones_umag_inach.md         # Verificación y georreferenciación de precisión para UMAG e INACH
    ├── fuentes_verificacion_inach.md               # Respaldo documental, DOIs, papers WoS/Scopus e historial INACH
    ├── responsables_equipamiento_inach.md          # Fichas técnicas de investigadores y técnicos responsables (INACH)
    ├── responsables_equipamiento_umag.md           # Fichas técnicas de investigadores y técnicos responsables (UMAG)
    ├── propuesta_integracion_geoportal.md          # Especificaciones de diseño UI/UX y arquitectura inicial
    └── Manual_de_Colaboración_Geoportal.pdf       # Manual institucional de usuario y colaboración
```

---

## 🔍 3. Catálogo de Archivos y Componentes

El repositorio se encuentra optimizado y libre de duplicados. Todos los archivos cumplen una función específica:

| Archivo | Rol en el Proyecto | Tipo |
| :--- | :--- | :---: |
| **`index.html`** | Entrada del despliegue en GitHub Pages. Redirige a `dashboard_geoportal_v2.html`. | Frontend / Routing |
| **`dashboard_geoportal_v2.html`** | **Aplicación web central en producción.** Contiene diseño, mapa interactivo, filtros, modal y lógica. | Frontend / Producción |
| **`Catastro_v4.csv`** | Base de datos maestra con los 37 equipos normalizados y enriquecidos. | Datos / Fuente de Verdad |
| **`Logo-Nodo-sinfondo-1-scaled.png`** | Asset gráfico institucional mostrado en el header y documentación. | Multimedia |
| **`catastro_equipos_cientificos.md`** | Diccionario fuente de las descripciones científicas integradas en el Geoportal. | Documentación Técnica |
| **`acceso_informacion_equipos.md`** | Auditoría y documentación metodológica de acceso y tarifas. | Documentación Metodológica |
| **`auditoria_ubicaciones_umag_inach.md`** | Documentación de verificación de coordenadas geográficas. | Documentación Geográfica |
| **`fuentes_verificacion_inach.md`** | Respaldo de publicaciones científicas y DOIs para INACH. | Auditoría Científica |
| **`responsables_equipamiento_inach.md`** | Directorio verificado de responsables INACH. | Directorio de Contactos |
| **`responsables_equipamiento_umag.md`** | Directorio verificado de responsables UMAG. | Directorio de Contactos |
| **`Manual_de_Colaboración_Geoportal.pdf`** | Manual de usuario y colaboración institucional. | Documentación de Usuario |
| **`propuesta_integracion_geoportal.md`** | Documento histórico de diseño técnico y arquitectura. | Arquitectura de Software |

---

## 🛠️ 4. Guía de Mantenimiento para Futuros Administradores

### A. ¿Cómo actualizar o agregar datos de equipamiento?
1. **Opción recomendada (en tiempo real):** Editar directamente la planilla compartida de Google Sheets. Al recargar la página web, los cambios aparecerán inmediatamente.
2. **Opción local:** Si se actualiza el archivo `Catastro_v4.csv`, se recomienda copiar las nuevas filas dentro de la constante `LOCAL_CSV_BACKUP` en `dashboard_geoportal_v2.html` (alrededor de la línea 1830) para mantener el soporte offline sincronizado.

### B. ¿Cómo agregar la descripción de un nuevo equipo?
En `dashboard_geoportal_v2.html`:
1. Abrir el objeto `SCIENTIFIC_DESCRIPTIONS` (L1620 aprox.) y añadir la entrada con el título y la descripción científica redactada.
2. En la función `getScientificDescription(title, inst, brand)` (L1710 aprox.), añadir la condición con palabras clave que mapee al nuevo texto.

### C. ¿Cómo funciona la ficha técnica y el contacto?
- Al hacer clic en *"Ver Ficha"* o en un marcador del mapa, se abre el modal con la información del equipo.
- **Correo visible y botón de copiado:** En la sección *Operación, Responsable y Contacto*, se muestra el correo directo (`#modalContactEmail`) y el botón `Copiar Correo` (`copyModalEmail()`) que copia la dirección con 1 clic al portapapeles y despliega una alerta toast.
- **Botón de contacto inferior:** El botón `Contacto con el/la encargado/a` abre el cliente de correo prellenado con asunto institucional o redirige al formulario externo correspondiente.

### D. Tecnologías y Librerías Utilizadas
- **HTML5 / CSS3 nativo:** Sin frameworks pesados; carga ultrarrápida y diseño responsive (modo claro con paleta corporativa `#1E327B`, `#EFF7F0`, `#BDF8B8`, `#88B991`).
- **Leaflet.js (v1.9.4):** Renderizado cartográfico con tiles *CartoDB Positron*.
- **Leaflet.markercluster (v1.5.3):** Agrupamiento dinámico de marcadores geográficos.
- **PapaParse (v5.4.1):** Parser CSV en vivo desde Google Sheets.
- **FontAwesome 6.4.0 & Google Fonts (Montserrat):** Iconografía y tipografía institucional.

---

## 🚀 5. Despliegue en GitHub Pages

1. Ir a los **Settings** del repositorio en GitHub.
2. En la sección **Pages** (menú lateral izquierdo):
   - **Source:** *Deploy from a branch*.
   - **Branch:** `main` (o `master`) / Carpeta: `/ (root)`.
3. Guardar. El archivo `index.html` redirige automáticamente a `dashboard_geoportal_v2.html`.

---

## 📜 6. Créditos y Financiamiento

- **Iniciativa y Financiamiento:** Desarrollado en el marco del proyecto **Nodo Ciencia Austral**, financiado por la **Agencia Nacional de Investigación y Desarrollo (ANID)** del Ministerio de Ciencia, Tecnología, Conocimiento e Innovación de Chile.
- **Elaboración y Desarrollo:** [Álvaro Contreras Barrios](https://www.linkedin.com/in/alvaro-contreras-barrios/)
