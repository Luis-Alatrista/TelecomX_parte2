Informe Final — Modelado Predictivo de Churn en Telecom X

1. Propósito del análisis

El objetivo principal de este proyecto es predecir la cancelación de clientes (churn) en la empresa Telecom X. La anticipación a este fenómeno permite a la compañía implementar estrategias de retención efectivas, optimizar campañas de marketing y reducir la pérdida de ingresos.  

Este trabajo buscó identificar qué variables impactan más en la decisión de un cliente de cancelar su servicio y construir modelos predictivos que puedan clasificar con precisión a los clientes con mayor riesgo de abandono.

2. Estructura del proyecto

El proyecto está organizado en los siguientes archivos y recursos:

- Notebook principal `TelecomX_parte2.ipynb`  
  Contiene todo el flujo de trabajo (preprocesamiento, análisis, modelado y resultados).
  
- Datos tratados:`telecomx_churn_clean.csv`  
  Archivo en formato CSV con los datos limpios y listos para modelado (derivado de la Parte 1).

- Visualizaciones: generadas dentro del notebook (matriz de correlación, boxplots, scatter plots, matriz de confusión, importancia de variables).

3. Preparación de los datos

3.1 Clasificación de variables
- Numéricas: antigüedad del cliente (tenure), cargos mensuales, cargos totales, entre otras.  
- Categóricas: tipo de contrato, método de pago, servicios adicionales, género, etc.

3.2 Normalización y codificación
- Se aplicó One-Hot Encoding (OHE) a todas las variables categóricas para hacerlas compatibles con los algoritmos de Machine Learning.  
- La variable objetivo Churn se transformó a formato binario (1 = Canceló, 0 = Activo).  
- Se eliminó cualquier columna que representara un ID único, ya que no aporta valor al modelo.

3.3 Separación de conjuntos
Los datos fueron divididos en:  
- Entrenamiento (80%) para ajustar los modelos.  
- Prueba (20%) para evaluar el rendimiento en datos no vistos.  

3.4 Justificación de decisiones
- Se construyeron dos modelos complementarios:  
  - Regresión Logística → requiere normalización y es útil para interpretar coeficientes.  
  - Random Forest → robusto, no necesita normalización y permite obtener importancias de variables.  
- En caso de desbalance de clases, se consideró la aplicación de técnicas como **SMOTE** para oversampling de la clase minoritaria.

4. Análisis Exploratorio de Datos (EDA)

Durante el EDA se generaron varias visualizaciones:

- Matriz de correlación: permitió identificar relaciones entre variables numéricas y la cancelación.  
- Tenure × Churn: clientes con menor tiempo de contrato mostraron una mayor tasa de cancelación.  
- TotalCharges × Churn: clientes con cargos totales bajos (por baja antigüedad) presentan más propensión a cancelar.  

Insight clave: 
Los clientes recién incorporados con contratos mes a mes son el segmento más vulnerable a la cancelación.

5. Ejecución del cuaderno

5.1 Requisitos de bibliotecas
El notebook requiere las siguientes bibliotecas en Python 3.x:

5.2 Carga de datos

El notebook asume que el archivo telecomx_churn_clean.csv se encuentra en la misma carpeta de trabajo o en la ruta definida dentro del código.

5.3 Ejecución

1. Abrir el notebook en Google Colab o Jupyter Notebook.
2. Ejecutar todas las celdas secuencialmente.
3. Revisar las secciones de:
Preparación de datos
Balanceo de clases
Modelos entrenados (LR y RF)
Métricas de evaluación
Interpretación de resultados

6. Conclusiones

Factores más relevantes: tipo de contrato, tiempo de antigüedad y cargos totales.
Mejor modelo: Random Forest ofreció un rendimiento más estable, aunque la Regresión Logística permitió mayor interpretabilidad de los coeficientes.

Estrategias recomendadas:
Incentivar contratos de largo plazo para nuevos clientes.
Fomentar el uso de pagos automáticos.
Implementar alertas tempranas para clientes con bajo tenure y cargos bajos.

Con este pipeline, Telecom X puede anticiparse a la cancelación de clientes y tomar acciones preventivas que mejoren la retención.
