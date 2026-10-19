🧪 Experimento A/B en Landing Page

Análisis estadístico de un experimento A/B realizado sobre la página de inicio (landing page) de un sitio web, con el objetivo de decidir qué versión (A o B) genera más conversiones y mayor valor económico para el negocio.

📌 Contexto y objetivo

Se expuso a 40,000 usuarios a una de dos versiones de la landing page. El proyecto responde cuatro preguntas de negocio:

¿Qué versión de la página genera mayor tasa de conversión?
¿Qué versión genera mayor gasto promedio por usuario convertido?
¿La conversión depende de la fuente de tráfico?
¿La conversión depende del tipo de usuario (nuevo o recurrente)?
🗂️ Dataset

Archivo landing_experiment.csv (no incluido en este repositorio), con 40,000 usuarios únicos y 28 días consecutivos de datos (del 2026-01-01 al 2026-01-28).

Columna	Descripción
user_id	Identificador único del usuario
date	Fecha de exposición a la página
landing	Versión de la página mostrada (A o B)
region	Región geográfica del usuario
dispositivo	Tipo de dispositivo
traffic_source	Canal de llegada (Ads, Email, Organic, Referral)
user_type	Nuevo o Recurrente
converted	1 si el usuario convirtió, 0 si no
gasto	Monto gastado (0 si no convirtió)
🔬 Metodología
Validación de datos: tipos de dato, duplicados, rango de fechas, valores negativos y balance entre versiones (~50/50).
Pruebas de hipótesis con α = 0.05:
Pregunta	Prueba
Gasto promedio de convertidos, A vs B	t de Student para dos muestras independientes
Tasa de conversión, A vs B	Chi-cuadrado de independencia
Conversión vs. fuente de tráfico	Chi-cuadrado de independencia
Conversión vs. tipo de usuario	Chi-cuadrado de independencia
Visualización de totales y proporciones con gráficas de barras.
Insight ejecutivo con conclusiones y recomendaciones para stakeholders.
📊 Resultados principales
Versión de la página
	Landing A	Landing B
Usuarios	19,982	20,018
Conversiones	2,512	3,194
Tasa de conversión	12.57%	15.96%
Diferencia de +3.38 puntos porcentuales (≈ 27% más conversión relativa): χ² = 93.65, p < 0.001.
Gasto promedio de usuarios convertidos: la diferencia es significativa (t = −9.37, p < 0.001) y favorece a B, con un tamaño de efecto pequeño a moderado (d de Cohen ≈ 0.25).
Fuente de tráfico
Canal	Tasa de conversión
Email	14.99%
Ads	14.74%
Referral	13.88%
Organic	13.79%

Existe una asociación estadísticamente significativa, pero de magnitud pequeña (≈ 1.2 pp entre el mejor y el peor canal). Orgánico aporta ≈ 45% del tráfico.

Tipo de usuario

Nuevos 14.36% contra recurrentes 14.09% (χ² = 0.513, p = 0.474): no hay evidencia de diferencia.

💡 Conclusiones y recomendaciones
✅ Adoptar la versión B: convierte más y sus clientes gastan más, por lo que genera más valor por ambas vías.
📈 Monitorear la conversión tras el lanzamiento para descartar un efecto de novedad y medir el ingreso por usuario expuesto (conversión × gasto).
🌱 Optimizar la experiencia del tráfico orgánico, el canal más grande: una mejora pequeña tiene gran impacto total.
💰 Evaluar los canales por retorno (costo de adquisición y gasto), no solo por conversión.
🚫 No segmentar la estrategia de conversión por tipo de usuario.
🔍 Siguiente paso: identificar qué elemento de B explica la mejora y confirmar que gana por dispositivo y región.
⚠️ Limitaciones
Las conclusiones causales dependen de que la asignación a A y B haya sido aleatoria.
El experimento cubre 28 días; podría haber efectos de novedad o estacionalidad.
Se realizaron varias pruebas sin ajuste por comparaciones múltiples; la asociación con la fuente de tráfico es marginal y debe interpretarse con cautela.
No se incluyen costos de adquisición por canal.
🛠️ Tecnologías

Python · pandas · matplotlib · SciPy (ttest_ind, chi2_contingency) · Jupyter Notebook

▶️ Cómo ejecutar
bash
git clone <url-del-repositorio>
cd <carpeta-del-proyecto>
pip install pandas matplotlib scipy jupyter
jupyter notebook S9_Version_Student_Proyecto_Landing_Experiment.ipynb

Coloca landing_experiment.csv en la ruta que usa el notebook (/datasets/landing_experiment.csv) o ajusta la ruta en la celda de carga de datos.

👤 Autor

Diego Tenorio Martínez LinkedIn · GitHub
