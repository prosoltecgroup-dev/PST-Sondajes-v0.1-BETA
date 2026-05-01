# PST-Sondajes-v0.1-BETA
 ## 🗺️ PST Sondajes — Visualización de Sondajes en AutoCAD / Civil 3D

  **PROSOLTEC** presenta la primera versión pública de evaluación (BETA) de **PST Sondajes**,
  un complemento .NET para AutoCAD® y Civil 3D® que automatiza la importación y visualización
  tridimensional de datos de sondajes de exploración minera directamente en el entorno de CAD.

  > ⚠️ **Versión BETA** — Distribuida exclusivamente para evaluación. No se recomienda su uso en
  > entornos de producción sin validación previa de los resultados. Ver Términos y Condiciones
  > incluidos en el complemento.

  ---

  ## ✨ Funcionalidades incluidas

  ### Importación de datos
  - **Collar** — Coordenadas de boca de sondaje (X, Y, Z) y profundidad total
  - **Survey** — Datos de orientación; soporta formato profundidad única y formato FROM–TO
  - **Assays** — Química por intervalo (Au, Cu, Ag, Pb, Zn u otros); valores `<0.05` convertidos automáticamente al 50%
  del límite
  - **Geo / Litología** — Atributos geológicos por intervalo (tipo de roca, mineralización, etc.)
  - Detección automática de nombres de columna: `HOLE-ID`, `HoleID`, `Sample`, `SampleID`, `BHId` y variantes

  ### Cálculo geométrico
  - **Algoritmo de Mínima Curvatura** — Desurveying estándar de la industria minera
  - Soporte para sondajes sin datos de survey (dibujados como verticales)
  - Interpolación lineal de coordenadas para centroides de intervalos
  - Extrapolación tangencial al final del sondaje (EOH)

  ### Visualización en AutoCAD
  - **Traza 3D** — `Polyline3d` en capa `PST_Trace` (color gris)
  - **Etiqueta HoleID** — `DBText` en collar en capa `PST_Collar` (color verde)
  - **Traza coloreada Assay** — Segmentos `Line` por intervalo en capa `&&PST_<atributo>` con esquemas de color:
    - Azul → Rojo
    - Verde → Rojo
    - Arco iris
    - Rangos personalizados (definibles por el usuario)
  - **Traza coloreada Geo** — Segmentos `Line` por intervalo coloreados por categoría de valor
  - **Etiquetas Assay** — `DBText` en centroide de intervalo con valor numérico
  - **Etiquetas Geo** — `DBText` en centroide con valor de atributo
  - Datos extendidos (Xdata) adjuntos a cada entidad: `<campo>: <valor>` (visible con `XDLIST`)
  - Creación automática de capas si no existen

  ### Interfaz de usuario
  - Panel flotante (PaletteSet) activado con el comando `PST_SONDAJES`
  - Ventana de progreso modal con barra de avance, botón Cancelar y resumen de resultados
  - Vista previa de datos cargados con filas MIN / MAX para columnas numéricas
  - Validación de datos con mensajes de advertencia y error por sondaje
  - Drag & drop de archivos CSV sobre los campos de ruta
  - Mapeo visual de colores por valor geológico (auto-poblado desde los datos)
  - Rangos de color personalizados para assays

  ---

  ## 📋 Requisitos del sistema

  | Requisito | Detalle |
  |-----------|---------|
  | **Software** | AutoCAD 2024 o Civil 3D 2024 |
  | **Sistema operativo** | Windows 10 / 11 (64 bits) |
  | **.NET Framework** | 4.8 (incluido en Windows 10/11) |
  | **Arquitectura** | x64 |

  > Compatible probado en **AutoCAD 2024** y **Civil 3D 2024**.
  > Versiones anteriores (2022, 2023) pueden funcionar pero no están garantizadas.

  ---

  ## 📦 Instalación (método NETLOAD — Beta)

  1. Descargar y descomprimir `PST_Sondajes_v0.1-beta.zip` en una carpeta local
     (ejemplo: `C:\PST_Sondajes\`)

  2. Abrir AutoCAD / Civil 3D 2024

  3. En la línea de comandos de AutoCAD escribir:
     NETLOAD

  4. En el cuadro de diálogo, navegar hasta la carpeta descomprimida y seleccionar
  **`PST_Sondajes.dll`**

  5. Escribir el comando para abrir el panel:
     PST_SONDAJES

  > 💡 Para cargar automáticamente al iniciar AutoCAD, agregar la ruta de la carpeta en:
  > *Opciones → Archivos → Rutas de soporte de aplicaciones de confianza*

  ---

  ## 📁 Formatos de CSV soportados

  ### Collar
  HOLE-ID, ESTE, NORTE, LOCATION Z, Length
  DH001, 309015.82, 8332438.83, 4576.85, 150.0

  ### Survey (formato FROM–TO)
  HOLE-ID, FROM, TO, DIP, AZIMUTH
  DH001, 0, 50, -60, 135

  ### Survey (formato profundidad única)
  HoleID, Depth, Azimuth, Dip
  DH001, 0, 135, -60

  ### Assays
  Sample, FROM, TO, Au, Cu, Ag
  DH001, 0, 2.5, 0.32, 1.2, 5.1
  > La columna identificadora puede llamarse: `HOLE-ID`, `HoleID`, `Sample`, `SampleID`, `BHId`, `Id`

  ### Geo / Litología
  HOLE-ID, FROM, TO, ROCK_TYPE, MINER_TYPE
  DH001, 0, 10, SULF, OXID

  ---

  ## ⚠️ Limitaciones conocidas (Beta)

  - La instalación es manual vía `NETLOAD` (no hay instalador automático en esta versión)
  - No se ha probado en versiones de AutoCAD anteriores a 2022
  - El rendimiento con más de 500 sondajes simultáneos no ha sido optimizado
  - Los Property Sets completos de Civil 3D no están implementados (se usa Xdata ligero)

  ---

  ## 🔧 Soporte y tutoriales

  📺 Canal YouTube PROSOLTEC: https://www.youtube.com/channel/UCUiKJa97rZ0x4LYD4Jxiuvw

  Para reportar errores o solicitar nuevas funcionalidades, usar la sección **Issues** de este repositorio.

  ---

  ## 📜 Licencia

  © 2024 PROSOLTEC. Todos los derechos reservados.
  Distribuido bajo Términos y Condiciones de uso BETA — ver detalles dentro del complemento.
