# Data Pipeline & Business Rules Engine: Telecom Operational Analytics (CallMeMaybe) 📞 Data Engineer Portfolio

Este proyecto implementa un flujo de procesamiento, limpieza y estructuración de datos analíticos para la plataforma de telefonía virtual **CallMeMaybe**. El objetivo principal es construir un motor analítico basado en reglas de negocio específicas para identificar operadores ineficaces, permitiendo optimizar la distribución de cargas, reducir llamadas perdidas y mejorar los tiempos de espera de los clientes en entornos de alta concurrencia.

---

## 🛠️ Stack Tecnológico & Arquitectura

* **Lenguaje de Programación:** Python 3.12+
* **Procesamiento, Limpieza e Ingesta:** Pandas (Data Wrangling), NumPy (Cómputo vectorizado)
* **Visualización Técnica y Modelado:** Matplotlib, Seaborn
* **Entorno de Desarrollo:** Jupyter Notebooks (Estructurado como pipeline reproducible)

---

## ⚙️ Arquitectura del Pipeline y Procesamiento (Enfoque de Ingeniería)

El core del proyecto está diseñado bajo principios de consistencia, calidad de datos (Data Quality) y eficiencia en consultas, dividido en las siguientes etapas críticas:

### 1. Ingesta y Robustez del Esquema (Data Schema)
* Carga de fuentes de datos masivas de registros de llamadas (CDRs - Call Detail Records).
* Validación inicial de tipos y mapeo de variables clave para asegurar la coherencia relacional.

### 2. Transformación y Calidad del Dato (Data Quality & Cleaning)
* **Manejo de Valores Nulos Estructurales:** Implementación de lógicas avanzadas de imputación y sanitización para evitar sesgos en el cálculo de métricas operativas de rendimiento (`call_duration`, `total_call_duration`).
* **Casteo y Normalización Temporal:** Transformación de formatos de fecha/hora dispersos a tipos temporales estandarizados para análisis de series de tiempo.
* **Filtrado de Valores Atípicos (Outliers):** Eliminación de ruidos del sistema y llamadas fallidas que distorsionaban el comportamiento real de los operadores.

### 3. Implementación del Motor de Reglas de Negocio (Business Rules Engine)
Desarrollo de scripts optimizados para segmentar y agrupar millones de registros en función de las tres dimensiones críticas definidas por el negocio:
* **Métrica de Pérdida Extrema:** Cálculo dinámico de volumen de llamadas entrantes perdidas (internas y externas) por operador.
* **Latencia de Atención:** Algoritmia para determinar tiempos de espera prolongados utilizando operaciones vectorizadas (`total_call_duration` vs. `call_duration`).
* **Métricas de Saturación:** Identificación de cuellos de botella en la atención de operadores VIP o segmentos de alto tráfico.

### 4. Capa de Salida y Preparación para Data Marts
* Estructuración de agregaciones optimizadas equivalentes a operaciones complejas de `GROUP BY` y funciones de ventana en SQL.
* Consolidación de un listado indexado de operadores ineficaces listo para ser consumido por un Data Mart o un tablero de inteligencia de negocios (Power BI / Tableau).

---

## 📁 Estructura del Proyecto

```text
├── notebooks/
│   └── telecom_operator_analytics_pipeline.ipynb  <-- Pipeline completo, limpieza y lógica analítica
├── .gitignore
├── requirements.txt                                <-- Dependencias y versiones técnicas
└── README.md                                       <-- Documentación de la arquitectura
