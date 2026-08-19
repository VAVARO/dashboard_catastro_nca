# Simulación del Dashboard de Equipamiento CTCI para el Geoportal Ciencia Austral

Se ha desarrollado un prototipo interactivo funcional en formato Web (**HTML5 / JavaScript / Leaflet.js**) que simula la experiencia de usuario de un **ArcGIS Dashboard** integrado en el **Geoportal Ciencia Austral**, alimentado con la totalidad de la información de los **29 equipos** e **infraestructuras científicas** catastradas a la fecha.

---

## 📁 Acceso al Prototipo Interactivo

Puedes abrir y presentar este prototipo interactivo directamente en cualquier navegador web abriendo el siguiente archivo:

🌐 **[dashboard_simulacion.html](file:///c:/Users/alvar/OneDrive - Universidad de Chile/Antigravity/Nodo Ciencia Austral/dashboard_simulacion.html)**

---

## 🛠️ Características Principales del Prototipo Desarrollado

```
┌─────────────────────────────────────────────────────────────────────────────────────────────┐
│                          CABECERA: GEOPORTAL CIENCIA AUSTRAL                                │
│                     Visualizador de Equipamiento e Infraestructura CTCI                     │
├─────────────────────────────────────────────────────────────────────────────────────────────┤
│  BARRA DE KPIs:                                                                             │
│  [ Total: 29 ]   [ Instituciones: 9 ]   [ Aysén: 18 ]   [ Magallanes: 11 ]   [ Formular: 1 ] │
├────────────────────────────────────────┬────────────────────────────────────────────────────┤
│ PANEL IZQUIERDO DE BÚSQUEDA Y FILTROS  │ MAPA GEOESPACIAL INTERACTIVO (LEAFLET.JS)          │
│ • Búsqueda en tiempo real por texto    │                                                    │
│ • Filtro dinámico por Institución      │ • Pines de color por Nivel de Acceso (Verde,       │
│ • Filtro dinámico por Categoría        │   Amarillo, Rojo).                                 │
│                                        │ • Pop-ups dinámicos con foto/resumen al hacer clic.│
│ TARJETAS DE EQUIPAMIENTO:              │ • Animación "FlyTo" al seleccionar un equipo desde │
│ • Título, Institución, Tags, Acceso.   │   el panel lateral.                                │
│ • Clic abre Modal con Ficha Técnica.   │                                                    │
└────────────────────────────────────────┴────────────────────────────────────────────────────┘
```

### 1. Panel de Métricas e Indicadores (KPIs)
*   **Total de Equipos Catalogados:** `29`
*   **Instituciones Representadas:** `9`
*   **Equipamiento en Región de Aysén:** `18` (incluye Campus Patagonia UACh en Coyhaique Alto)
*   **Equipamiento en Magallanes y Antártica:** `11`
*   **Equipos con Canal Directo Abierto:** `1` (Museo Regional de Aysén)

### 2. Controles de Filtrado Dinámico y Búsqueda en Tiempo Real
*   **Buscador por Texto Libre:** Permite filtrar instantáneamente por nombre de equipo, marca (ej. *Zeiss*, *Bruker*, *Shimadzu*, *Thies Clima*), laboratorio o palabras clave.
*   **Filtro por Institución:** Selector desplegable con las 9 instituciones del catastro (U. de Aysén, CIEP, INACH, UACh Campus Patagonia, UMAG, COPAS Coastal, Museo Reg. Aysén, INIA, Estación Patagonia UC).
*   **Filtro por Categoría Técnica ANID:** Selección por la taxonomía oficial ANID (*MICROSCOPIOS Y DIFRACTOMETROS*, *CROMATOGRAFOS Y ESPECTROMETROS*, *INSTRUMENTOS BIOANALITICOS*, *AGROPECUARIA*, *OTROS*).
*   **Filtro por Área de Conocimiento OCDE:** Selector por la clasificación estándar OCDE (*Ciencias de la Tierra y Medioambientales*, *Ciencias Biológicas*, *Ciencias Físicas*, *Ciencias Químicas*, *Ciencias Agrícolas*, *Humanidades*).

### 3. Mapa Interactivo Geoespacial (Patagonia y Antártica)
*   Representación de cada laboratorio/equipo mediante **pines de color codificados por su Nivel de Acceso Web**:
    *   🟢 **Verde (Acceso Alto):** Formulario abierto en línea (ej. Google Form del Museo Regional de Aysén).
    *   🟡 **Amarillo (Acceso Medio):** Difusión web institucional con correo directo del encargado.
    *   🔴 **Rojo (Acceso Bajo):** Baja visibilidad online / uso condicionado a proyectos específicos.
*   Georreferenciación exacta mediante las coordenadas `Lat, Lng` incluidas en la Columna J del CSV de la Macrozona Austral.
*   Al hacer clic en un pin del mapa o en una tarjeta del panel lateral, la cámara realiza una transición suave (*flyTo*) hacia la coordenada exacta del laboratorio.

### 4. Ventana Modal de Ficha Técnica Completa
Al presionar **"Ver Ficha Completa"** o seleccionar una tarjeta, se despliega una ventana flotante que incluye:
*   Nombre completo del instrumento y marca/modelo exacto.
*   Categoría técnica ANID y **Área de Conocimiento OCDE**.
*   **Coordenadas exactas (Latitud, Longitud)** y ubicación física detallada.
*   Párrafo de **Descripción y Funcionamiento Técnico** (equilibrio científico-divulgativo).
*   **Botón de Acción Directa:** Enlace a `mailto:` del encargado o enlace al Formulario de Solicitud en línea.

---

## 🐍 Compatibilidad Directa con Streamlit en Python

El archivo CSV actualizado [Catastro Equipamiento Macrozona Austral - Sheet1 (1).csv](file:///c:/Users/alvar/OneDrive - Universidad de Chile/Antigravity/Nodo Ciencia Austral/Catastro Equipamiento Macrozona Austral - Sheet1 (1).csv) incluye la columna `Coordenadas (Latitud, Longitud)`, la cual puede ser procesada y visualizada inmediatamente en un Dashboard de **Streamlit** utilizando el siguiente fragmento de código Python:

```python
import streamlit as st
import pandas as pd

st.set_page_config(page_title="Geoportal NCA - Equipamiento CTCI", layout="wide")
st.title("🔬 Dashboard de Equipamiento CTCI - Macrozona Austral")

# Cargar datos desde el CSV georreferenciado
df = pd.read_csv("Catastro Equipamiento Macrozona Austral - Sheet1 (1).csv")

# Extraer Latitud y Longitud para el mapa
df[["lat", "lon"]] = (
    df["Coordenadas (Latitud, Longitud)"].str.split(",", expand=True).astype(float)
)

# Filtros laterales
st.sidebar.header("Filtros de Búsqueda")
inst = st.sidebar.multiselect("Institución", options=df["Institución Responsable"].unique())
cat_anid = st.sidebar.multiselect("Categoría ANID", options=df["Categoría Técnica: (Por ejemplo: Cromatografía, Microscopía, Espectrometría, Oceanografía, Genética, entre otros)"].unique())
cat_oecd = st.sidebar.multiselect("Área OCDE", options=df["Categoría OCDE de Conocimiento"].unique())

filtered_df = df.copy()
if inst: filtered_df = filtered_df[filtered_df["Institución Responsable"].isin(inst)]
if cat_anid: filtered_df = filtered_df[filtered_df["Categoría Técnica: (Por ejemplo: Cromatografía, Microscopía, Espectrometría, Oceanografía, Genética, entre otros)"].isin(cat_anid)]
if cat_oecd: filtered_df = filtered_df[filtered_df["Categoría OCDE de Conocimiento"].isin(cat_oecd)]

# Mapa georreferenciado
st.subheader("Ubicación Geoespacial de Equipamiento")
st.map(filtered_df[["lat", "lon"]])

# Tabla interactiva
st.subheader("Catastro Detallado")
st.dataframe(filtered_df)
```

---

## 🎯 Puntos a Destacar en la Reunión con el Geoportal

1.  **Demostración de Valor Inmediato:** Presentar este prototipo demuestra al equipo del Geoportal y del NCA que la información de los 29 equipos está **estructurada, georreferenciada y lista** para ser cargada tanto en Streamlit como en ArcGIS Online.
2.  **Facilidad de Migración e Interoperabilidad:** La arquitectura de datos de esta simulación mapea directamente los campos requeridos por Streamlit y por la `Feature Layer` en AGOL:
    *   `Nombre del Equipamiento` → `title`
    *   `Institución Responsable` → `inst`
    *   `Categoría Técnica ANID` → `catAnid`
    *   `Categoría OCDE de Conocimiento` → `catOecd`
    *   `Coordenadas (Latitud, Longitud)` → `lat`, `lng`
3.  **Solución para la Comunidad Científica:** Muestra cómo el Geoportal y el NCA no solo servirán para visualización cartográfica tradicional, sino como un **Catálogo Interactivo de Servicios de Infraestructura CTCI** para la Macrozona Austral.
