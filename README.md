# Challenge-Telecom-X-an-lisis-de-evasi-n-de-clientes---Parte-2
# 📊 Predicción de Cancelación de Clientes (Customer Churn)

**Autor:** Christian Arturo Rivera Caballero

## 🎯 Descripción del Proyecto
Este proyecto de Data Science tiene como objetivo desarrollar modelos predictivos para identificar qué clientes tienen la mayor probabilidad de cancelar sus servicios de telecomunicaciones (Churn). A través de un análisis exhaustivo y la construcción de un pipeline de Machine Learning, el proyecto busca anticiparse a la fuga de clientes y proporcionar estrategias de retención basadas en datos reales.

## 🧠 Objetivos
- Preparar y limpiar los datos para el modelado (eliminación de ruido, codificación y normalización).
- Manejar el desbalanceo de clases en la variable objetivo.
- Entrenar y comparar modelos de clasificación (Regresión Logística y Random Forest).
- Evaluar el rendimiento utilizando métricas avanzadas (Recall, F1-Score, Curva ROC).
- Interpretar la importancia de las variables y proponer conclusiones estratégicas de negocio.

## 🛠️ Tecnologías y Librerías Utilizadas
- **Lenguaje:** Python
- **Manipulación de Datos:** Pandas, NumPy
- **Machine Learning:** Scikit-Learn (Logistic Regression, Random Forest, StandardScaler)
- **Visualización:** Matplotlib, Seaborn

## ⚙️ Metodología

1. **Preprocesamiento de Datos:**
   - Eliminación de características sin valor predictivo (`ID_Cliente`).
   - Mapeo de la variable objetivo binaria (`Evasion`).
   - Transformación de variables categóricas utilizando **One-Hot Encoding**.
   - Estandarización de escalas numéricas (mediante `StandardScaler`) estrictamente para los modelos basados en optimización matemática.

2. **Manejo del Desbalanceo:**
   - Se identificó un desbalance en los datos (73.5% retención vs 26.5% abandono).
   - Se ajustaron los pesos de las clases dentro de los algoritmos (`class_weight='balanced'`) para penalizar severamente los errores en la predicción de la clase minoritaria.

3. **Modelado y Evaluación:**
   - Se dividió el dataset en un conjunto de entrenamiento (80%) y prueba (20%) de forma estratificada.
   - Se entrenaron dos modelos: **Regresión Logística** (datos normalizados) y **Random Forest** (datos sin normalizar).
   - Se priorizó la métrica de **Recall** (Sensibilidad) dado el alto costo de negocio que representan los falsos negativos en problemas de Churn.

## 📈 Resultados Clave

| Modelo | Exactitud (Accuracy) | F1-Score | Recall (Detección de Churn) | Overfitting |
| :--- | :---: | :---: | :---: | :---: |
| **Regresión Logística** | 74.0% | 61.5% | **78.3%** | No |
| **Random Forest** | 78.6% | 53.9% | 46.8% | **Sí** |

**Conclusión del Modelado:** La **Regresión Logística** demostró ser el modelo superior para este caso de uso. Aunque el Random Forest logró una alta exactitud en entrenamiento, sufrió un severo sobreajuste (Overfitting) perdiendo capacidad de generalización. La Regresión Logística, en cambio, logró detectar exitosamente a casi 8 de cada 10 clientes en riesgo de cancelación.

## 💡 Estrategias de Retención Propuestas

A partir de los coeficientes del modelo, se identificaron los principales impulsores de la cancelación y se desarrollaron las siguientes estrategias:
1. **Migración de Contratos:** El contrato "Mes a Mes" es el mayor factor de abandono. Se recomienda implementar campañas de upselling ofreciendo beneficios por migrar a contratos de 1 o 2 años.
2. **Auditoría de Fibra Óptica:** Los usuarios de fibra óptica mostraron alta tendencia a la fuga. Es vital revisar la competitividad del precio y la estabilidad técnica del servicio.
3. **Automatización de Pagos:** Reducir la fricción incentivando el cambio de "Cheque Electrónico" a cobros automáticos mediante tarjeta de crédito.
4. **Fidelización Temprana:** La antigüedad es el principal escudo contra el Churn; enfocar el esfuerzo de soporte en los primeros 6 meses de ciclo de vida del usuario es crítico.

## 🚀 Cómo ejecutar este proyecto
1. Clona este repositorio.
2. Asegúrate de tener las librerías necesarias instaladas (`pip install pandas numpy scikit-learn matplotlib seaborn`).
3. Ejecuta el archivo Jupyter Notebook o script de Python adjunto, verificando que el dataset `TelecomX_Procesado.csv` se encuentre en la misma ruta.