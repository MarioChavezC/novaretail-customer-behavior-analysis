# NovaRetail+ | Análisis exploratorio del comportamiento de clientes

Análisis exploratorio y correlacional de datos de clientes de una plataforma de comercio electrónico ficticia, con el objetivo de identificar qué variables del comportamiento del cliente presentan mayor asociación con el ingreso anual generado.

> **Importante:** este proyecto identifica asociaciones estadísticas. Correlación no implica causalidad.

## Objetivo del proyecto

Responder la pregunta:

**¿Qué factores del comportamiento del cliente están más fuertemente asociados con el ingreso anual generado?**

El análisis utiliza información de 15,000 clientes y 12 variables correspondientes a 2024.

## Hallazgos principales

- **Compras mensuales e ingreso anual:** asociación positiva extremadamente fuerte (Pearson = 0.967; Spearman = 0.967). Es necesario validar cómo se construyó `ingreso_anual` para descartar una dependencia matemática entre ambas variables.
- **Visitas mensuales e ingreso anual:** asociación positiva débil a moderada (Pearson = 0.337; Spearman = 0.321).
- **Gasto en publicidad dirigida e ingreso anual:** asociación positiva débil (Pearson = 0.197; Spearman = 0.185).
- **Membresía Premium e ingreso anual:** asociación positiva pequeña (correlación punto-biserial = 0.0931).
- **Abandono e ingreso anual:** no se detectó evidencia de asociación en esta muestra (correlación punto-biserial = -0.0028; p = 0.7295).
- **Tipo de dispositivo y región:** asociación prácticamente nula y no significativa (V de Cramér = 0.0124; p = 0.5965).

## Contenido del repositorio

| Archivo | Descripción |
|---|---|
| `Proyecto_NovaRetail_analisis_completo.ipynb` | Notebook con exploración, limpieza, visualizaciones, pruebas estadísticas e interpretación de resultados. |
| `novaretail_comportamiento_clientes_2024.csv` | Dataset utilizado en el análisis. |

## Variables del dataset

El conjunto contiene 12 columnas:

| Variable | Descripción |
|---|---|
| `id_cliente` | Identificador del cliente. |
| `edad` | Edad del cliente. |
| `nivel_ingreso` | Ingreso anual estimado del cliente. |
| `visitas_mes` | Número de visitas a la plataforma durante el mes. |
| `compras_mes` | Número de compras realizadas durante el mes. |
| `gasto_publicidad_dirigida` | Gasto en anuncios asignado al usuario. |
| `satisfaccion` | Calificación de satisfacción en escala de 1 a 5. |
| `miembro_premium` | Membresía Premium: 1 = sí, 0 = no. |
| `abandono` | Abandono de la plataforma: 1 = sí, 0 = no. |
| `tipo_dispositivo` | Dispositivo utilizado: móvil, escritorio o tablet. |
| `region` | Región geográfica: norte, sur, oeste o este. |
| `ingreso_anual` | Ingreso anual generado por el cliente para la empresa. |

## Metodología

El notebook desarrolla las siguientes etapas:

1. **Carga y exploración:** revisión de dimensiones, tipos de datos, valores faltantes, duplicados y distribución de variables.
2. **Preparación:** clasificación de variables numéricas, binarias y categóricas; documentación de supuestos.
3. **Visualización:** histogramas, diagramas de dispersión y mapa de calor de correlaciones.
4. **Análisis estadístico:**
   - Correlación de **Pearson** para medir asociación lineal.
   - Correlación de **Spearman** para medir asociación monotónica.
   - Correlación **punto-biserial** para variables binarias frente a una variable numérica.
   - **V de Cramér** y prueba chi-cuadrada para asociación entre variables categóricas.
5. **Interpretación de negocio:** evidencia visual y numérica, interpretación no causal, limitaciones e implicaciones.
6. **Conclusiones y próximos pasos:** validación de la métrica de ingreso, análisis del embudo de conversión y evaluación de campañas.

Se utiliza un nivel de significancia de 0.05. Debido al tamaño de muestra (15,000 registros), la interpretación considera tanto los valores p como la magnitud de los coeficientes.

## Requisitos

- Python 3
- Jupyter Notebook o JupyterLab
- pandas
- numpy
- seaborn
- matplotlib
- scipy

Instala las dependencias con:

```bash
pip install pandas numpy seaborn matplotlib scipy jupyter
```

## Cómo ejecutar el proyecto

1. Clona o descarga este repositorio.
2. Abre el proyecto en Jupyter Notebook o JupyterLab.
3. Coloca el archivo CSV en la misma carpeta que el notebook.
4. En la celda de carga de datos, utiliza una ruta relativa:

```python
df = pd.read_csv("novaretail_comportamiento_clientes_2024.csv")
```

5. Ejecuta todas las celdas en orden (*Restart Kernel and Run All Cells*).

> El notebook entregado puede contener una ruta local del entorno original (`/mnt/data/...`). Para ejecutarlo en otra computadora, reemplázala por la ruta relativa indicada arriba.

## Limitaciones

- El análisis es observacional y correlacional; no permite establecer causalidad.
- El 30.45% de los clientes presenta `ingreso_anual` igual a cero, y la distribución de esta variable tiene asimetría positiva.
- La asociación extremadamente alta entre `compras_mes` e `ingreso_anual` requiere validar la fórmula y el origen de la variable objetivo.
- No se controlan simultáneamente todos los factores que podrían relacionarse con el ingreso.
- Los datos corresponden a 2024 y no bastan por sí solos para inferir tendencias futuras.
- La correlación entre una variable explicativa y la variable objetivo no determina multicolinealidad. Para evaluarla entre variables explicativas se recomienda revisar la matriz de correlaciones y calcular el VIF.

## Próximos pasos sugeridos

- Documentar y validar la construcción de `ingreso_anual`.
- Analizar la conversión de visitas en compras.
- Segmentar clientes por frecuencia de compra, membresía y comportamiento.
- Evaluar campañas con métricas de conversión, costo de adquisición y retorno de inversión.
- Explorar modelos predictivos después de revisar posibles fugas de información y validar sus supuestos.

## Herramientas

`Python` · `Pandas` · `NumPy` · `Matplotlib` · `Seaborn` · `SciPy` · `Jupyter Notebook`

## Autoría

Proyecto de análisis de datos desarrollado con fines educativos y de portafolio.

---

**Nota:** NovaRetail+ y el contexto del negocio se utilizan como caso de análisis. Las conclusiones deben interpretarse dentro del alcance y las características del dataset disponible.
