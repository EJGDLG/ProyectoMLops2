#  Proyecto MLOps – Predicción de Riesgo (Default / Churn)
Pipeline completo de Machine Learning con **MLflow**, **ingeniería de features**, **evaluación exhaustiva**, **validación temporal** y **análisis de impacto en negocio**.

---

##  Estructura del Proyecto
- ── data/
- │ ├── raw/ # Datos originales
- │ ├── processed/ # Datos limpios + features
- ├── notebooks/ # EDA y experimentos
- ├── src/
- │ ├── preprocessing/ # Limpieza y tratamiento
- │ ├── modeling/ # Entrenamiento + MLflow
- │ ├── evaluation/ # Métricas + gráficos
- ├── models/ # Modelos entrenados
- ├── mlruns/ # Registro MLflow
- └── README.md


#  1. Estructura del Dataset

El dataset final contiene **33 variables**, incluyendo:

| Tipo | Variables |
|------|-----------|
| Identificación | `customer_id` |
| Demográficas | `age`, `gender`, `country` |
| Fechas | `signup_date`, `last_purchase_date` |
| Comportamiento | `last_login_days`, `total_orders`, `loyalty_points` |
| Financiero | `avg_order_value`, `payment_issues`, `support_tickets` |
| Marketing | `email_open_rate`, `sms_click_rate`, `promotion_usage` |
| Target | `churn` |

**Insight:** El dataset está completo (0 missing después de imputación), balance altamente desigual.

---

#  2. Preparación de los Datos

###  Limpieza
- 50,000 filas iniciales → sin duplicados.
- Imputación aplicada a:
  - `monthly_income`  
  - `credit_score_proxy`

###  Outliers
- Capados para evitar distorsión en el modelo.

###  Ingeniería de Features
Features creadas:
- `income_to_loan_ratio`
- `log_loan_amount`
- `recent_delinquency_flag`
- `age_band`

Total de **36 features finales**.

###  División Temporal (Train/Test)
- Corte temporal: **2023-12-31**
- Train: 42,879 (17% positivos)  
- Test: 7,121 (17.8% positivos)

---

#  3. Comprensión de Datos (EDA)

Gráficos incluidos en notebooks:

###  Churn por país
Guatemala con mayor churn (~17.5%), México el más bajo (~15.5%).

###  Correlación
- Correlaciones bajas → dataset no lineal.
- Señales débiles pero útiles → requiere modelos avanzados.

###  Distribución de edad
Distribución uniforme → no sesgo demográfico.

---

#  4. Modelado + MLflow

###  Modelo entrenado
- Algoritmo base (clasificador simple de referencia)
- Registro completo con MLflow:
  - parámetros  
  - métricas  
  - gráficos  
  - artefactos  

