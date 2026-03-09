# Predicción de Churn - Telecom X Parte 2

Proyecto de Machine Learning para predecir la cancelación de clientes en una compañía de telecomunicaciones.

## Objetivo
Identificar clientes con alto riesgo de churn y entender los principales factores que influyen en la cancelación para proponer estrategias de retención.

## Dataset
- Archivo: `datos_tratados.csv`
- Registros: 7,043 clientes
- Tasa de churn: ~26.5%
- Variables clave: tenure, MonthlyCharges, TotalCharges, Contract, InternetService, OnlineSecurity, TechSupport, PaymentMethod, etc.

## Pipeline ejecutado
1. Carga y limpieza
2. Encoding (One-Hot para categóricas)
3. Análisis exploratorio y correlaciones
4. División train/test (70/30, estratificada)
5. Balanceo de clases con SMOTE
6. Escalado con StandardScaler (para modelos sensibles)
7. Entrenamiento y evaluación de modelos
8. Análisis de importancia de variables

## Modelos evaluados
| Modelo                | Accuracy (test) | F1-score Churn | Recall Churn | Notas                              |
|-----------------------|-----------------|----------------|--------------|------------------------------------|
| Random Forest         | 0.77            | 0.59           | 0.61         | Mejor rendimiento general          |
| Regresión Logística   | 0.75            | 0.58           | 0.67         | Mejor recall (detección churn)     |
| XGBoost               | 0.76            | 0.58           | 0.62         | Buen equilibrio                    |
| SVM (lineal)          | ~0.74           | ~0.57          | ~0.66        | Similar a logística                |
| KNN                   | ~0.73           | ~0.55          | ~0.65        | Sensible a escalado                |

**Mejor modelo general**: Random Forest  
**Mejor para detección temprana**: Regresión Logística

## Variables más influyentes en el churn
1. **Contract_Mes a mes** → Mayor riesgo
2. **Tenure** → Fuerte protector (más antigüedad → menos churn)
3. **InternetService_Fiber optic** → Aumenta probabilidad
4. **MonthlyCharges** → Cargos altos impulsan cancelación
5. **OnlineSecurity_No** / **TechSupport_No** → Falta de estos servicios eleva riesgo

## Estrategias de retención recomendadas
- Migrar clientes a contratos anuales/bianuales con descuentos
- Onboarding intensivo primeros 6 meses
- Bundlear seguridad online + soporte técnico gratis en planes fibra
- Incentivar pagos automáticos (reducir electronic check)
- Alertas predictivas para clientes de alto riesgo

## Requisitos
- Python 3.8+
- Librerías: pandas, numpy, scikit-learn, imbalanced-learn, matplotlib, seaborn

## Estructura del proyecto

telecom-churn/
├── datos_tratados.csv
├── TelecomX2_LATAM_SP_ipnb.ipynb      # Pipeline completo
├── README.md
└── requirements.txt




