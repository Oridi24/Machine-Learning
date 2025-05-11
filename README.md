# Machine-Learning
# 🏡 Predicción de precios de Airbnb - Proyecto de Machine Learning

Este proyecto tiene como objetivo desarrollar un modelo de regresión para predecir el precio de anuncios de propiedades en Airbnb, utilizando técnicas de ciencia de datos y aprendizaje automático. A lo largo del proyecto se realiza una exploración, limpieza, preprocesamiento exhaustivo y modelado avanzado del dataset proporcionado.

---

## ⚠️ Disclaimer

El dataset utilizado en este proyecto pertenece a **Airbnb** y ha sido extraído con fines **netamente pedagógicos** y de **aprendizaje personal**.  
**Este trabajo no tiene fines comerciales** y puede contener errores o aproximaciones con fines ilustrativos.  
Se recomienda no utilizarlo en producción sin revisión profesional.

---

## 📌 Estructura del Proyecto

El desarrollo del proyecto se divide en **tres etapas principales**:

### 1️⃣ Exploración de Datos (EDA) + Técnicas de Análisis
- Análisis exploratorio y visualización con `Seaborn` y `Matplotlib`
- Detección de nulos, duplicados y outliers
- Análisis de distribución y correlación de variables
- Codificación y conteo de variables categóricas
- Filtrado de columnas no relevantes

### 2️⃣ Preprocesamiento + Técnicas Avanzadas
- Imputación de nulos (media, mediana, moda)
- Escalado y transformación (`StandardScaler`, `RobustScaler`, `LogTransform`)
- Reducción de dimensionalidad con `PCA`
- Selección de características con `f_regression`, `mutual_info_regression`
- Codificación de variables categóricas (`OrdinalEncoder`, `OneHotEncoder`)
- Preparación para modelos (train/test split, validación cruzada)

### 3️⃣ Despliegue de Algoritmos / Problema de Regresión
- Modelos implementados:
  - `LinearRegression`
  - `Ridge (L2)`
  - `Lasso (L1)`
  - `DecisionTreeRegressor`
  - `KernelRidge`
  - `HistGradientBoostingRegressor`
  - `LightGBM`
  - `XGBoost + GridSearchCV`
- Evaluación con:
  - `MSE`, `RMSE`, `MAE`, `R²`
- Validación cruzada (`cross_val_score`)
- Ajuste de hiperparámetros (`GridSearchCV`)

---

## 💡 Tecnologías y Librerías Utilizadas

- `Python 3.x`
- `pandas`
- `numpy`
- `matplotlib`
- `seaborn`
- `scikit-learn`
- `xgboost`
- `lightgbm`
- `scipy`
- `joblib`
- `warnings`
- `os` y `sys`
- `utils` (paquete personalizado del entorno)

---

## ✅ Requisitos Previos

Antes de ejecutar el proyecto, asegúrate de cumplir con los siguientes requisitos:

1. **Importación del paquete `utils` en el entorno de trabajo**
   - Asegúrate de que esté disponible en tu carpeta o entorno Jupyter.

2. **Instalación de librerías necesarias**
   Puedes instalar los requisitos con:

   ```bash
   pip install pandas numpy matplotlib seaborn scikit-learn xgboost lightgbm scipy
