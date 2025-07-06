# *Memoria de errores*

##  📌*Objetivo del Proyecto*

*El objetivo de este proyecto fue construir un modelo de Machine Learning capaz de predecir el precio de una propiedad listada en Airbnb, utilizando un dataset real obtenido mediante web scraping. Esta versión del proyecto fue la primera aproximación al problema, y aunque logró ciertos resultados razonables, contenía varios errores metodológicos graves que afectaron la validez de los resultados.*

💡 ***Este documento actúa como una memoria de errores, documentando los problemas identificados y las lecciones aprendidas, que llevaron a la creación de una segunda versión del proyecto, méticamente corregida.***

---

## ❌*Principales Errores Detectados*:

###  1. ***Data Leakage: Eliminación de columnas antes del split***

  * *Se eliminaron columnas del dataset **antes de dividir entre train y test**.*
  * *Algunas decisiones se basaron en valores calculados con **todo el dataset**, como correlaciones y porcentaje de nulos.Esto generó un problema de *data leakage*, ya que la información del conjunto de test fue utilizada indirectamente durante el entrenamiento, lo cual **sobreestima el rendimiento real del modelo**.*

### 2. ***Imputación incorrecta de valores nulos***

  * *La imputación de valores nulos se realizó usando la media/mediana calculada **sobre el dataset completo**, en lugar de calcularla solo sobre los datos de entrenamiento.Este error también provocó fugas de información, ya que el conjunto de test se vio afectado por información del train., en una versión corregida, se entrenó el `SimpleImputer` solo con los datos de entrenamiento y se aplicó al test sin recalcular.*

### 3. ***Filtrado agresivo de outliers***

  * *Se eliminó aproximadamente un **20% de los datos** al aplicar un umbral de Z-score = 3 de forma global.Esta decisión, si bien reduce ruido, ***eliminó demasiados valores reales***, sesgando el dataset hacia valores promedio, como resultado, el modelo se enfrentó a un problema mucho más fácil del que habría en la realidad.*

### 4. ***Codificación ordinal inapropiada***

  * *Se aplicó `OrdinalEncoder` a todas las variables categóricas sin considerar si tenían un orden real. Por ejemplo: asignar un "2" a un hotel boutique y un "19" a una villa implica un orden que **no tiene sentido semántico**, esto introduce relaciones artificiales entre categorías y puede distorsionar la interpretación y el entrenamiento del modelo, En versiones posteriores, se utilizó `TargetEncoder`, que codifica según la variable objetivo, o `OneHotEncoder` cuando se trataba de categorías sin orden ni relación.*

---

## 🧠 *Lecciones Aprendidas*

1. ✅ ***Separar train/test antes de cualquier transformación***:*Incluso tareas como imputación, eliminación de columnas o escalado deben hacerse *después* del `train_test_split`.*
2. ✅ ***Evitar el uso de información futura (test) durante el entrenamiento***:*Cualquier conocimiento extraído del test, directo o indirectamente, lleva a un sobreajuste ilusorio.*
3. ✅ ***Usar codificadores adecuados para las variables categóricas***:*Elegir `TargetEncoder` o `OneHotEncoder` según el contexto y la relación semántica de las categorías.
4. ✅ ***Tener precaución al eliminar outliers***:*Un recorte agresivo puede eliminar datos válidos. Ajustar umbrales y probar distintas estrategias (como `IQR` o `Winsorization`).*


## 🚀 *Resultado Final de esta Versión*

*Aunque el modelo en esta versión presentó un rendimiento teóricamente "bueno", ese resultado no es válido debido a los errores de metodología. Fue una etapa necesaria para comprender la importancia de un pipeline riguroso y reproducible en proyectos de Machine Learning.*

*Esta experiencia motivó la creación de una versión completamente revisada, sin data leakage.*

---

##  ⭐*Gracias por leer hasta aquí*

*Este documento forma parte de una reflexión metodológica sobre buenas prácticas en proyectos de ciencia de datos. Equivocarse es parte del proceso, pero reconocer y documentar los errores es lo que realmente construye experiencia profesional.*
