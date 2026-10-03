# Datos, trazabilidad y revisión

## Archivos recibidos

- `ladb_mobility_economy_2024_clean.csv`: dataset consolidado de 15 filas y 12 columnas. Incluido sin modificar.
- `S5 ladb_mobility_economy_project_student.ipynb`: desarrollo original con consignas y revisión académica. Su preparación se reorganizó en `preparacion_historica.ipynb` sin las consignas ni comentarios del revisor.
- `Resumen ejecutivo.ipynb`: narrativa original utilizada como base del resumen revisado en Markdown.

El original leía `/datasets/tomtom_traffic.csv` y `/datasets/oecd_city_economy.csv`. Estos dos archivos no fueron adjuntados. Los nombres no prueban una procedencia oficial ni proporcionan una licencia de redistribución.

## Variables

| Campo | Interpretación disponible |
|---|---|
| City, country, Year | Ciudad, código de país y año |
| JamsDelay | Indicador de demora del dataset; unidad y alcance pendientes de confirmar |
| TrafficIndexLive | Índice de tráfico; escala exacta pendiente de diccionario |
| JamsLengthInKms | Longitud de congestión, según nombre del campo |
| JamsCount | Conteo de congestiones, promediado en la preparación original |
| MinsDelay | Indicador de demora; definición completa no disponible |
| city_gdp_capita | PIB per cápita; moneda y metodología pendientes de confirmar |
| unemployment_pct | Porcentaje de desempleo |
| PM2.5 (μg/m³) | Concentración PM2.5, con coma decimal en el CSV |
| population | Población convertida de millones a personas en el original |

## Transformaciones históricas

El notebook original renombra campos, convierte fechas y formatos numéricos, filtra 2024 y promedia cinco métricas de tráfico por ciudad-país-año. Luego une movilidad y economía por ciudad y año mediante `inner join`. La revisión histórica conserva esas operaciones, modifica rutas y evita sobrescribir el CSV original.

Antes de reproducir la preparación hay que validar las claves y el país en la unión, examinar duplicados, cuantificar ciudades excluidas y comprobar las fechas descartadas por `errors='coerce'`. Un promedio de observaciones disponibles no garantiza un promedio anual representativo. El borrado de puntos en el PIB presupone separadores de miles y debe verificarse contra el formato real.

## Cambios en la interpretación

Se retiró la recomendación original de priorizar inversión en Bogotá: no estaba respaldada por un análisis causal ni de costos y beneficios. No se calcula una «correlación de Bogotá» a partir de una sola fila de esa ciudad.

El notebook principal añade correlaciones y dos exclusiones de sensibilidad: sin Ciudad de México, r = −0.025; sin Santiago, r = 0.335. La muestra completa mantiene todos los registros y da r = 0.283. No se imputa ni elimina el valor 2277 de Santiago: se señala para revisión.

Los gráficos nuevos mantienen PIB y congestión en ejes distintos. PM2.5 se convierte a numérico únicamente en memoria; el archivo de entrada se conserva byte por byte. No se infiere que un dato sea correcto solo porque no tenga nulos.

## Verificación

El notebook de análisis se ejecutó secuencialmente sobre el CSV incluido y se conservaron sus salidas. Las correlaciones usan el método Pearson de pandas y el mismo peso por ciudad. No se calculan valores p ni se afirma significancia estadística. La preparación histórica no fue ejecutada sin sus fuentes.
