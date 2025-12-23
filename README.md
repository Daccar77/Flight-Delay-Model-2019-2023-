✈️ FlightOnTime – Predicción de Retrasos de Vuelos
📌 Descripción del proyecto

FlightOnTime es un sistema predictivo que estima si un vuelo despegará puntual o con retraso, utilizando datos históricos de vuelos.
El objetivo del proyecto es apoyar a aerolíneas, aeropuertos y pasajeros en la toma de decisiones anticipadas frente a posibles retrasos.

Este repositorio contiene la parte de Data Science del MVP desarrollado para una hackathon académica, enfocado en un modelo de clasificación binaria listo para ser consumido por un backend vía API.

🎯 Problema de negocio

Los retrasos en vuelos generan:

insatisfacción de los pasajeros,

costos operativos para aerolíneas,

problemas logísticos en aeropuertos (conexiones perdidas, reprogramaciones).

La solución busca predecir el riesgo de retraso antes de la salida, usando información disponible previamente al vuelo.

🧠 Enfoque de Data Science

El modelo aprende patrones históricos a partir de variables como:

aerolínea,

aeropuerto de origen,

hora de salida,

día de la semana,

distancia del vuelo.

La predicción se formula como un problema de clasificación binaria:

0 → Puntual

1 → Retrasado (retraso mayor a 15 minutos)

📊 Dataset

Fuente: Dataset público de vuelos (2019–2023).

Tamaño original: millones de registros.

Estrategia:

carga optimizada,

selección de columnas relevantes,

reducción del tamaño para evitar sobrecarga de memoria.

Columnas utilizadas

FL_DATE

AIRLINE

ORIGIN

DISTANCE

DEP_DELAY

DEP_TIME

🧹 Limpieza y preparación de datos

Eliminación de vuelos cancelados.

Eliminación de registros con valores nulos.

Eliminación de duplicados.

Creación de la variable objetivo:

RETRASADO = 1 si DEP_DELAY > 15

RETRASADO = 0 en caso contrario.

🛠️ Feature Engineering

Se crearon variables temporales clave:

DEP_HOUR: hora de salida del vuelo.

DAY_OF_WEEK: día de la semana (0 = lunes, 6 = domingo).

IS_WEEKEND: indicador de fin de semana.

Estas variables permiten capturar patrones operativos y de congestión.

🤖 Modelo predictivo

Algoritmo: Random Forest Classifier

Justificación:

captura relaciones no lineales,

es robusto frente a ruido,

funciona bien con variables mixtas (numéricas y categóricas).

Evaluación

Se utilizaron métricas de clasificación:

Accuracy

Precision

Recall

F1-score

El modelo logra un desempeño consistente y adecuado para un MVP.

📦 Exportación del modelo

El modelo se exporta junto con su contrato de entrada, permitiendo su uso directo en producción:

Archivo generado:

flight_delay_model_backend.pkl


Contiene:

el modelo entrenado,

la lista exacta de columnas esperadas por el backend.

🔌 Integración con Backend

El backend debe enviar la información del vuelo en el siguiente formato:

{
  "aerolinea": "Delta Air Lines Inc.",
  "origen": "ATL",
  "fecha_partida": "2025-11-10T14:30:00",
  "distancia_km": 350
}


Dentro del notebook se incluye una función que:

convierte fecha_partida en variables temporales,

prepara el input exactamente como el modelo lo espera.

Esto evita que el backend tenga que manipular fechas o features.

🚀 Cómo ejecutar el notebook

Abrir el notebook en Google Colab o Jupyter.

Ejecutar las celdas en orden, de arriba hacia abajo.

Al finalizar, se generará el archivo:

flight_delay_model_backend.pkl


Entregar ese archivo al equipo de backend para su integración.

📁 Estructura del repositorio
/
├── Proyecto_Aerolineas.ipynb
├── flight_delay_model_backend.pkl
└── README.md

👥 Equipo

Proyecto desarrollado como parte de una hackathon académica, por un equipo multidisciplinario de:

Data Science

Back-End

Front-End

Este repositorio corresponde exclusivamente a la entrega de Data Science.

🏁 Estado del proyecto

✔ MVP funcional
✔ Modelo entrenado y evaluado
✔ Listo para consumo vía API
✔ Alineado con los requisitos del desafío
