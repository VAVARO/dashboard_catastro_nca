# 🌍 Dashboard y Geoportal de Equipamiento CTCI - Nodo Ciencia Austral

[![Nodo Ciencia Austral](https://img.shields.io/badge/Nodo-Ciencia%20Austral-1E327B?style=for-the-badge)](https://nodoaustral.cl/)
[![Licencia](https://img.shields.io/badge/Estado-Producci%C3%B3n%20%2F%20V2-BDF8B8?style=for-the-badge&logoColor=1C1F40)](https://github.com/VAVARO/dashboard_catastro_nca)
[![Macrozona Austral](https://img.shields.io/badge/Territorio-Ays%C3%A9n%20%7C%20Magallanes%20%7C%20Ant%C3%A1rtica-88B991?style=for-the-badge)](https://github.com/VAVARO/dashboard_catastro_nca)

Visualizador interactivo, georreferenciado y catastro técnico de equipamiento e infraestructura científica y tecnológica (**CTCI**) para la **Macrozona Austral** de Chile (Regiones de Aysén del General Carlos Ibáñez del Campo, Magallanes y de la Antártica Chilena, y Territorio Chileno Antártico).

---

## 🚀 Características Principales

*   **🗺️ Mapa Interactivo Cartográfico:**
    *   Desarrollado con **Leaflet.js** y **Leaflet.markercluster**.
    *   Georreferenciación precisa desde Coyhaique hasta Puerto Williams, Cabo de Hornos e Islas Shetland del Sur / Península Antártica.
    *   Marcadores de pulso con identidad corporativa (Azul `#1E327B` y Verde Menta `#BDF8B8`).
    *   Navegación espacial y zoom inteligente por región y por campus/estación.

*   **📊 Sincronización en Vivo (Live Connection):**
    *   Integración directa mediante **PapaParse** con Google Sheets en tiempo real y fallback local al dataset CSV estructurado.
    *   Filtros dinámicos reactivos: Búsqueda textual en tiempo real, Institución, Categoría Técnica ANID, Categoría OCDE de Conocimiento y Nivel de Acceso.

*   **🔬 Ficha Técnica y Modal de Detalle:**
    *   Visualización de metadatos completos: institución, campus/sede, personal técnico responsable, financiamiento ANID FONDEQUIP, costos formateados en moneda chilena (`$XX.XXX.XXX CLP`), limitaciones operativas, esquemas de mantenimiento y modelos de costo/acceso.
    *   Listado de publicaciones científicas y artículos indexados con enlaces directos a sus **DOIs oficiales**.
    *   Botón estandarizado de contacto directo con encargados/as (`mailto:` preconfigurado o enlace a formulario externo).

*   **🎨 Diseño Visual e Identidad Gráfica:**
    *   Diseño fiel al **Manual de Identidad Gráfica Oficial del Nodo Ciencia Austral** en modo claro de alto contraste.
    *   Tipografía oficial **Montserrat** y jerarquía espacial limpia.
    *   Botón *"Ver Ficha"* en cada tarjeta del sidebar para inspección sin pérdida de contexto cartográfico.

---

## 📂 Estructura del Repositorio

```text
├── index.html                                  # Redirección de entrada (GitHub Pages ready)
├── dashboard_geoportal_v2.html                 # Aplicación web interactiva principal del Geoportal
├── dashboard_simulacion.html                   # Simulación standalone ligera de respaldo
├── Catastro Equipamiento Macrozona Austral.csv # Base de datos oficial catastrada (29 equipos)
├── Logo-Nodo-sinfondo-1-scaled.png             # Logo oficial en alta resolución
│
├── 📑 Informes Técnicos y de Auditoría:
├── catastro_equipos_cientificos.md             # Catastro descriptivo de 29 instrumentos CTCI
├── acceso_informacion_equipos.md               # Análisis de accesibilidad y condiciones de uso
├── propuesta_integracion_geoportal.md          # Especificaciones técnicas de integración
├── responsables_equipamiento_inach.md          # Caracterización técnica y responsables INACH
├── fuentes_verificacion_inach.md               # Auditoría exhaustiva de fuentes y DOIs INACH
├── responsables_equipamiento_umag.md           # Caracterización técnica y responsables UMAG
└── auditoria_ubicaciones_umag_inach.md         # Chequeo y coordenadas verificadas UMAG e INACH
```

---

## 🏛️ Instituciones Catastradas en la Macrozona Austral

1.  **Universidad de Aysén (UAysén)** – Campus Lillo / Campus Río Simpson, Coyhaique.
2.  **Universidad de Magallanes (UMAG)** – CADI-UMAG, Instituto de la Patagonia y Parque Omora.
3.  **Instituto Antártico Chileno (INACH)** – Laboratorios Jorge Berguño, Base Prat, Base Yelcho y AP Viel.
4.  **Centro de Investigación en Ecosistemas de la Patagonia (CIEP)** – Coyhaique.
5.  **Instituto de Investigaciones Agropecuarias (INIA)** – CRI Tamel Aike e INIA Kampenaike.
6.  **Instituto de Fomento Pesquero (IFOP)** – Bases Aysén y Punta Arenas.
7.  **Universidad Austral de Chile (UACh)** – Campus Patagonia, Coyhaique.
8.  **Museo Regional de Aysén** – Coyhaique Alto.
9.  **Centro de Estudios del Cuaternario Fuego-Patagonia y Antártica (CEQUA)** – Punta Arenas.

---

## 💻 Visualización Local y Despliegue

### 1. Visualización Rápida
Puedes abrir directamente en cualquier navegador web moderno:
```bash
# Abrir el geoportal directamente
dashboard_geoportal_v2.html
```

### 2. Despliegue en GitHub Pages
1. Ve a los **Settings** de este repositorio en GitHub.
2. En la sección **Pages**, selecciona la rama `main` (o `master`) y la carpeta `/ (root)`.
3. Haz clic en **Save**. En pocos segundos la aplicación estará disponible en línea.

---

## 📜 Licencia y Créditos
Iniciativa desarrollada para el proyecto **Nodo Ciencia Austral**, financiado por la **Agencia Nacional de Investigación y Desarrollo (ANID)** del Ministerio de Ciencia, Tecnología, Conocimiento e Innovación de Chile.
