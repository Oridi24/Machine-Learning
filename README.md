# ***Machine-Learning***
*El aprendizaje automático (Machine Learning, ML) es un campo de la inteligencia artificial que permite a las máquinas aprender de los datos y tomar decisiones sin ser programadas explícitamente. A través de algoritmos matemáticos y estadísticas computacionales, ML permite construir modelos capaces de hacer predicciones o descubrir patrones ocultos en grandes volúmenes de información.*

----
## *Predicción de Precios de Airbnb con Machine Learning*

### 📌 *Objetivo del Proyecto*

*El objetivo principal de este proyecto ha sido desarrollar un modelo de aprendizaje automático capaz de predecir el precio de una propiedad listada en Airbnb a partir de un conjunto de datos reales obtenidos mediante técnicas de scraping. A diferencia de datasets artificiales o académicos, este conjunto presenta un elevado grado de desorganización y ruido, lo cual supone un reto realista y enriquecedor, obligando a aplicar no solo conocimientos técnicos, sino también juicio crítico y metodológico en cada etapa.*


## *1era Parte: Análisis Exploratorio (EDA)*

* ***División inicial: Train/Test***:
  * *Separamos el dataset desde el principio para evitar fugas de información y simular un entorno de producción real. Esto garantiza que las decisiones de limpieza y selección de variables se basen solo en el conjunto de entrenamiento.*
    
* ***Análisis Estadístico: Medidas de dispersión y localización***:
  * *El EDA nos permitió identificar valores atípicos, columnas con alta proporción de nulos, variables redundantes y comportamientos inesperados. Tomamos decisiones informadas sobre limpieza y transformación.*
     
* ***Filtrado de columnas con +96% de nulos***: *Se eliminaron columnas altamente vacías por su baja utilidad y alto riesgo de ruido o sesgo.*
  
* ***Evaluación de relevancia de columnas restantes***: *Se revisó cada columna para decidir si aportaba valor predictivo.*


## *2da Parte: Preprocesamiento del Dataset*

1. ***Tratamiento de variables***:
   * *Eliminación de columnas irrelevantes: URLs, descripciones textuales sin estructurar, variables redundantes o con alta correlación.*
   * *Imputación de valores nulos:*
     * *Numéricos → Mediana (más robusta ante outliers).*
     * *Categóricos → Moda.*
       
2. ***Codificación de variables categóricas***: *Se usó `TargetEncoder`, ideal para regresión y superior a `OrdinalEncoder` cuando no hay un orden lógico entre categorías.*
   
3. ***Detección y tratamiento de outliers***:*Con Z-Score: se probó con umbrales de 3 (eliminaba 26%) y 4 (15%). Se adoptó 4 como opción intermedia para preservar información sin sacrificar limpieza.*
   
4. ***Transformaciones y escalado***: *Se usó StandardScaler y solo se escaló el conjunto de entrenamiento (⚠️ evitar data leakage).*
   
5. ***Análisis de correlación***:*Solo sobre `train`, para identificar variables redundantes sin comprometer la integridad del modelo.*


##  *3era Parte: Algoritmos de Machine Learning*

1. ***Transformaciones y preparación***: *Se aplicaron transformaciones logarítmicas y polinómicas (`PolynomialFeatures`) para capturar relaciones no lineales.*
   
2. ***Selección y evaluación de modelos***:
   * *Modelos lineales: `Ridge` y `Lasso` → útiles en casos con multicolinealidad.*
   * *Modelos basados en árboles: `DecisionTreeRegressor`, `RandomForestRegressor`, `SVR` con kernel RBF.*
   * *Modelos avanzados: `HistGradientBoostingRegressor`, `LightGBM`, `XGBoost`*.
     
3. ***Entrenamiento y métricas***:
   * *Evaluación con `MSE` (Error Cuadrático Medio) y `R²` (Coeficiente de Determinación).*
   * *Validación cruzada (`Cross-Validation`) para evitar overfitting.*
   * *Ajuste de hiperparámetros con `GridSearchCV`.*


### 🔍 *Recapitulación General*

* ***Transformaciones consistentes***: *todas las transformaciones fueron aplicadas por separado a `train` y `test` para evitar fugas de información.*
* ***Variable objetivo***: *`price` fue separada y tratada como variable dependiente en los modelos de regresión.*
* ***Métricas de evaluación***:
  * 📉 *`MSE`: mide error absoluto medio al cuadrado.*
  * 📈 *`R²`: mide proporción de variabilidad explicada por el modelo.*


### ⚠️*Atención: Diagnóstico del rendimiento*

* *Los primeros modelos (Ridge/Lasso) mostraron un R² bajo (\~0.22) y MSE alto.*
* *Estrategias de mejora:*
  * *Se aplicaron transformaciones polinómicas*.
  * *Se probaron modelos más robustos como `SVR`, `RandomForest`, `Bagging`, `Boosting`, etc.*

### 🤖*Justificación de técnicas avanzadas*:

* ***Kernel methods***: *permiten capturar relaciones no lineales transformando el espacio de características.*
* ***Boosting***: *mejora precisión combinando modelos débiles y corrigiendo errores.*
* ***Bagging***: *mejora estabilidad reduciendo varianza.*
* ***Random Forest***: *diversifica árboles, reduce sobreajuste y mejora generalización*.
* ***Cross-Validation***: *mejora robustez de evaluación y comparabilidad entre modelos.*


### ✅ *Conclusiones Finales*

* ***Mejoras observadas***: *tras aplicar técnicas más avanzadas, el rendimiento mejoró significativamente.*
* ***Aún hay margen***:
  * *Crear nuevas variables derivadas (e.g., `precio por persona extra`)*.
  * *Selección de características.*
  * *Revisión de outliers y tratamientos con NLP para texto.*
   
* ***Coste computacional***:*algunos modelos tardaron hasta 70 minutos*.

> *Para los objetivos de este proyecto: manejo adecuado de técnicas de ML, aplicación de modelos avanzados, tratamiento riguroso de datos y documentación clara; este punto marca un cierre adecuado.*

---

## 📁 *Estructura del Proyecto*

```
├── Airbnb_Price_Prediction
│   ├── README.md
│   ├── proyecto_con_data_leakage
│   │   ├── main_leakage.ipynb
│   │   └── README.md                   💡 # Memoria de errores
│   └── proyecto_sin_data_leakage
│       ├── main_final_model.ipynb
│       └── dataset_final.csv
```

---

### *¡Gracias por visitar el proyecto!*

*Si te ha parecido interesante, no dudes en dejar una estrella ⭐ en el repositorio :)*

---

### 💡 ***Requisitos Previos:***

*Antes de ejecutar el proyecto, asegúrate de cumplir con los siguientes requisitos:*

- *Modificacion de ruta correspondiente para el Dataset*
- *Instalación de librerías necesarias*:

   ```bash
   pip install pandas numpy matplotlib seaborn scikit-learn

---
### ⚠️ ***Disclaimer***

*El dataset utilizado en este proyecto pertenece a **Airbnb** y ha sido extraído mediante tecnicas de scrapping con fines **investigativos**.*  
***Este trabajo no tiene fines comerciales*** *y contiene errores y aproximaciones con fines ilustrativos*.  
