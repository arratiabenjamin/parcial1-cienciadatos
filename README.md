# Parcial 1 — Programación para la Ciencia de Datos (SCY1101)

Proyecto de procesamiento y análisis de datos de urgencias médicas, desarrollado en Python/Jupyter, alineado a la rúbrica del **Parcial 1**.

## Objetivo
Construir un flujo completo y reproducible de ciencia de datos que cubra:

- manipulación en **Pandas** (filtros, agrupaciones, joins),
- limpieza y estandarización,
- transformaciones avanzadas (vectorización, broadcasting, pivot/reshape, chunking),
- verificación de integridad/procedencia,
- reporte de resultados con visualizaciones.

## Estructura del proyecto

```text
.
├── notebooks/
│   └── parcial1_rubrica_desarrollo.ipynb
├── data/
│   ├── raw/
│   │   └── urgencias_noprocesados_grupo06.csv
│   └── urgencias_procesados_grupo06.csv
├── outputs/
│   ├── top10_causas.png
│   ├── evolucion_mensual_atenciones.png
│   ├── costo_promedio_triage.png
│   ├── kpis_principales.csv
│   └── reporte_validacion.csv
├── docs/
│   └── rubrica_parcial1.pdf
└── requirements.txt
```

## Dataset
- **Entrada principal:** `urgencias_noprocesados_grupo06.csv`
- **Registros originales:** 4.742
- **Variables originales:** 29

## Qué hace el notebook

`notebooks/parcial1_rubrica_desarrollo.ipynb` implementa:

1. **Carga + procedencia:** hash SHA256 de archivo fuente.
2. **EDA inicial:** tipos, nulos, duplicados, consistencia de métricas.
3. **Limpieza:**
   - eliminación de duplicados exactos,
   - normalización de `SexoPaciente` y `PrioridadTriage`,
   - parseo robusto de fechas con formatos mixtos,
   - imputaciones por establecimiento (numéricas/categóricas),
   - corrección de `NumTotal` como suma de tramos etarios,
   - winsorización de costo (p1–p99).
4. **Manipulación avanzada con Pandas:** filtros, agrupaciones múltiples, joins con dimensiones auxiliares.
5. **Transformaciones avanzadas:** vectorización, broadcasting (z-score), pivot, reshape (`melt`) y chunking por lotes.
6. **Validación de calidad:** reglas de esquema y consistencia.
7. **Exportables:** dataset limpio, KPIs, reporte de validación y gráficos.

## Resultados principales

### KPIs finales
- **Registros finales:** 4.705
- **Atenciones totales:** 726.405
- **Costo total estimado:** CLP **463.485.953,92**
- **Registros corregidos (`NumTotal`):** 97 (2,06%)
- **Causa más frecuente:** *Influenza y neumonia*

### Hallazgos destacados
- Top causas por volumen:
  1. Influenza y neumonia (133.044)
  2. Bronquitis/Bronquiolitis aguda (131.050)
  3. COVID-19 sospecha/confirmada (130.635)
  4. Crisis asmática (112.651)
  5. Insuficiencia respiratoria aguda (109.922)
- Distribución de atención por triage (NumTotal): predomina **C3**, luego **C4** y **C2**.
- Fechas no parseables tras limpieza: 18 registros (quedaron como nulos controlados).

### Validaciones de integridad
Todas las reglas del reporte quedaron en **OK**:
- Semana estadística en rango [1,53]
- Prioridad de triage válida
- Sexo válido
- `NumTotal = suma de tramos`
- Coordenadas dentro de rango esperado para Chile


## Visualizaciones generadas

### 1) Top 10 causas de urgencia por atenciones
![Top 10 causas](outputs/top10_causas.png)

### 2) Evolución mensual de atenciones
![Evolución mensual](outputs/evolucion_mensual_atenciones.png)

### 3) Costo promedio por prioridad de triage
![Costo promedio por triage](outputs/costo_promedio_triage.png)

## Cómo ejecutar

1. Crear entorno e instalar dependencias:

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

2. Abrir Jupyter y ejecutar:

- `notebooks/parcial1_rubrica_desarrollo.ipynb`

> El notebook detecta automáticamente la raíz del proyecto, así que funciona aunque lo ejecutes desde `notebooks/`.

## Correspondencia con la rúbrica (Encargo)
- ✅ Manipulación eficiente en Pandas
- ✅ Reportes y visualizaciones claras
- ✅ Transformaciones avanzadas y optimización
- ✅ Flujo de limpieza justificado técnicamente
- ✅ Entorno reproducible (`requirements.txt`)
- ✅ Verificación de integridad y procedencia

## Autores
Equipo Grupo 06.
