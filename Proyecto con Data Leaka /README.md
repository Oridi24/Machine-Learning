- Has tomado decisiones sobre qué columnas eliminar antes de dividir entre train y test. El error no sería tan grave si no hubieses calculado la correlación. Utilizas la correlación calculada sobre todos los datos para tomar decisiones sobre qué columnas eliminar, etc.

- Esto está mal. El dataset de "test" tiene que funcionar como si fuesen datos completamente nuevos. Si lo has utilizado para calcular correlaciones, ya no son datos nuevos. Esto te va a llevar a sobreestimar el desempeño de tu modelo.

- Igualmente, cuando imputas la media/mediana/etc a los valores nulos, debes conservar el imputador que has entrenado con los datos de train para reutilizarlo en los datos de test. No puedes calcular la media/mediana etc en test, porque así vas a sobreestimar el desempeño en test.
- Outliers: has eliminado el 20% de los datos!
- Creo que es por esto que tu modelo parece tan bueno: al quedarte sólo con valores "medios", el modelo lo tiene muy fácil (y también has filtrado información de test al entrenar
- Has usado un "ordinal encoder" para todo, pero no tiene sentido en muchos casos: estás diciendo que p.ej. un boutique hotel tiene un 2 pero una villa tiene un 19, mientras que una camper tiene un 4. Por qué deberían estar ordenadas así? Es mejor probar p.ej. TargetEncoder.
