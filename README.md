# Business-analytics-Gabriel-y-Miguel

# Práctica: red de centros deportivos con Python

Autores: Miguel Colás Ruiz y Gabriel Rueda Benavidez.

## Fuentes de datos
- **Actividad y catálogo de centros:** datos sintéticos docentes de MABA (`actividad.csv` y `centros.xlsx`). No son datos reales.
- **Meteorología:** API histórica de Open-Meteo, del 1 al 14 de septiembre de 2026, para Madrid, Barcelona y Valencia (temperatura máxima y mínima en °C y precipitación en mm).

## Entradas
Están en la carpeta `datos/`:
- `actividad.csv`: 504 sesiones (una fila por sesión).
- `centros.xlsx` (hoja `centros`): 6 centros, dos por ciudad.

## Cómo ejecutarlo en Google Colab
1. Abrir `Practica_centros_alumnado_v02.ipynb` en Google Colab.
2. Conectar el entorno de ejecución.
3. Ejecutar las celdas en orden. Cuando se solicite, seleccionar a la vez `actividad.csv` y `centros.xlsx` de la carpeta `datos`.
4. Repetir la carga si se inicia un entorno nuevo.

## Salidas
Se generan en la carpeta `salidas` y se descargan en `resultados_centros.zip`:
- `actividad_preparada.csv`, `meteo_diaria.csv`
- `resumen_centros.csv`, `ocupacion_por_turno.csv`, `visitas_diarias.csv`
- `visitas_diarias.png` y `ocupacion_actividad.png`
- `fuentes.json`

## Decisiones de revisión con IA

| Decisión | Consulta y sugerencia | Qué aceptaste o cambiaste | Comprobación y resultado |
|---|---|---|---|
| 1 | Pregunté si mi cálculo de ocupación con `apply(..., axis=1)` era correcto Sugirió llamar a `calcular_ocupacion(preparada['visitas'], preparada['plazas'])` directamente con las columnas. | Cambié el `apply` por la llamada directa, porque la función solo hace una operación aritmética. | Ejecuté de nuevo la celda y el `head()` dio los mismos valores (68.75, 62.5, 58.33).  |
| 2 | Pregunté si `preparada.groupby(['actividad', 'turno'])['ocupacion_pct'].mean()` calculaba la ocupación media por actividad y turno. Confirmó que era correcta. |  No cambié nada, porque ya coincidía con lo que pide el enunciado. | Calculé a mano la media de Yoga por la tarde con un filtro y coincidió con la tabla. |

## Diferencia entre la versión inicial y la final
En la versión inicial había huecos sin completar, por ejemplo tabla_ciudad = None en consultar_meteo. En la versión final están resueltos y el notebook contiene las salidas y todas las respuestas.
