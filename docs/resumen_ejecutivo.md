# Resumen ejecutivo

Este proyecto académico explora la relación entre congestión y PIB per cápita en 15 ciudades de 7 países durante 2024. El objetivo es identificar patrones que orienten preguntas de análisis posteriores, sin atribuir efectos causales a la movilidad.

El proceso histórico integra promedios de tráfico por ciudad con datos económicos mediante una unión interna. La revisión reproducible parte del CSV consolidado aportado, comprueba su estructura y utiliza distribuciones, gráficos de dispersión y correlaciones descriptivas. No se encontraron nulos ni claves ciudad-país-año duplicadas en ese archivo; la preparación desde las fuentes no se volvió a ejecutar porque faltan los archivos originales.

Ciudad de México presenta el mayor JamsDelay (2833.06), seguida de São Paulo (1729.19) y Bogotá (1141.55). La correlación de Pearson entre PIB per cápita y JamsDelay es 0.283; al excluir Ciudad de México pasa a −0.025. Esto revela sensibilidad a una observación y limita una interpretación general. La asociación población–JamsDelay es 0.879, lo que motiva estudiar tamaño urbano y alcance de la métrica, sin asumir causalidad.

Se recomienda confirmar unidades, cobertura y el PIB registrado para Santiago (2277), además de incorporar infraestructura, transporte público y métricas de viaje comparables. Las ciudades con indicadores elevados pueden ser objeto de diagnóstico, pero la muestra no permite decidir prioridades de inversión ni estimar beneficios de proyectos de transporte. Cualquier recomendación de inversión requiere evidencia adicional y evaluación de costos y beneficios.
