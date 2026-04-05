#  Análisis de Eficiencia de Agentes – CallMeMaybe Telecom

##  Descripción del Proyecto
Análisis de la eficiencia operativa de agentes en un call center de telecomunicaciones. El objetivo es identificar operadores de bajo rendimiento mediante KPIs de productividad, evaluar la calidad del servicio al cliente y validar hipótesis estadísticas sobre el comportamiento de las llamadas por plan tarifario.

---

##  Objetivos
- Identificar agentes con bajo rendimiento según AHT y volumen de llamadas
- Analizar la calidad del servicio: llamadas atendidas, no atendidas y tiempo de espera
- Evaluar diferencias estadísticas en llamadas perdidas entre planes tarifarios A, B y C
- Comparar tiempos de espera entre llamadas entrantes y salientes

---

##  Herramientas y Librerías

| Librería | Uso |
|---|---|
| `Pandas` | Manipulación y limpieza de datos |
| `NumPy` | Operaciones numéricas |
| `Matplotlib / Seaborn` | Visualización de KPIs y rankings |
| `SciPy` | Pruebas estadísticas T-test y ANOVA |
| `Statsmodels` | Prueba de Tukey para comparación múltiple |

---

##  Metodología

### 1. Limpieza de Datos
- Conversión de columnas de fecha a formato datetime
- Reemplazo de valores nulos en `operator_id` con 0 para identificar llamadas no atendidas
- Eliminación de duplicados considerando `user_id`, `date`, `direction` y `total_call_duration`

### 2. Análisis Exploratorio de Datos (EDA)

####  Distribución por Plan Tarifario
Histogramas de adquisición de clientes para los planes A, B y C por fecha de inicio.

####  Calidad del Servicio
Análisis mensual de tres categorías de atención:

| Categoría | Descripción |
|---|---|
| Sin servicio | Cliente no fue atendido en ninguna llamada |
| Primera llamada | Cliente fue atendido en el primer intento |
| Más de una llamada | Cliente tuvo que llamar varias veces en el mismo día |

####  Tiempo de Espera Promedio por Mes

| Mes | Tiempo de Espera Promedio |
|---|---|
| Agosto | 402 segundos |
| Septiembre | 348 segundos |
| Octubre | 321 segundos |
| Noviembre | 240 segundos |

####  Ranking de Agentes
Clasificación de operadores por:
- **AHT (Average Handle Time):** Tiempo total acumulado de atención
- **Porcentaje de llamadas atendidas** sobre el total del período

### 3. Pruebas Estadísticas

####  ANOVA + Tukey
**Hipótesis:** ¿Existe diferencia significativa en la tasa de llamadas perdidas entre los planes A, B y C?
- Se aplicó ANOVA de una vía y prueba post-hoc de Tukey para comparaciones múltiples entre grupos.

####  T-test Independiente
**Hipótesis:** ¿La duración promedio de llamadas entrantes es igual a las salientes?
- Se compararon distribuciones de duración entre llamadas `in` y `out`.

####  T-test Pareado
**Hipótesis:** ¿El tiempo de espera promedio es igual entre todos los meses?
- Se compararon tiempos de espera de llamadas entrantes vs salientes por mes.

---

## 📊 Hallazgos Principales
- La mayoría de los clientes son atendidos en la **primera llamada**, lo que indica eficiencia general en la recepción
- Los tiempos de espera más altos se concentran en **agosto y septiembre**, mejorando hacia fin de año
- No es común que un cliente llame más de una vez en el mismo día
- Existen diferencias estadísticamente significativas en llamadas perdidas entre planes tarifarios

---

## ✅ Recomendaciones
- Reforzar la asignación de agentes en agosto y septiembre para reducir tiempos de espera
- Diseñar plan de mejora para operadores identificados en el ranking de bajo rendimiento
- Revisar el plan tarifario con mayor tasa de llamadas perdidas e implementar mejoras de atención
- Monitorear mensualmente el AHT por agente como indicador de productividad

---
om
