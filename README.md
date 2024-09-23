# ML_RecursosHumanos

Ficha Técnica: Proyecto de Análisis de Datos Predictivo

Título del Proyecto: Prueba de Hipótesis en Google Colab

Objetivo:
Realizar una prueba de hipótesis, utilizando una técnica de analisis de datos de segmentación y validación de Hipótesis.

Equipo:
Trabajo Individual.

Herramientas y Tecnologías:
- Python
- Google Slides.
- Google Colab

Procesamiento y análisis:
- limpieza de datos
- exploración de datos
- Técnica de Análisis de datos predictivo
  
Resultados y Conclusiones:
Se probo la hipótesis mediante insights concluidos mediante metricas de score.

Identificación de outliers:

```python
def outliers(df,cols):
  total = {}
  indices_iqr = {}
  for col in cols:
    #IQR
    Q1=df[col].quantile(0.25)
    Q3=df[col].quantile(0.75)
    IQR=Q3-Q1
    INF=Q1-1.5*(IQR)
    SUP=Q3+1.5*(IQR)
    n_outliers=df[(df[col] < INF) | (df[col] > SUP)].shape[0]
    total[col] = n_outliers
    indices_iqr[col] = list(df[(df[col] < INF) | (df[col] > SUP)].index)
  print(total)
  return indices_iqr
```

Manejo de outliers:

```python
# Reemplazar outliers con la media
def modificar_outliers(df,cols,indices):
  for col in cols:
    median_value = df[col].mean()
    outlier_indices = indices[col]
    df.loc[outlier_indices, col] = median_value
  return df
```



Limitaciones/Próximos Pasos:
Identifica y describe cualquier limitación o desafío encontrado durante el proyecto.
Sugiere posibles próximos pasos para extender o mejorar el proyecto de análisis de datos.

Enlaces de interés:
[google slides](https://docs.google.com/presentation/d/18w-sUDPOgsIeiKR9T8BsRMs_BPv5BhhacqgVicb1O3I/edit?usp=sharing)
[google colab](https://colab.research.google.com/drive/1_LCcQKfHfcgpuOnr9-IEP2Z0VaE0DsKA?usp=sharing)
