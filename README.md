# Predicción de Deserción de Estudiantes Universitarios

Proyecto del curso **Métodos Numéricos y Optimización para Machine Learning** — Universidad Peruana Cayetano Heredia (2026-I).

El objetivo es construir desde cero un modelo de clasificación binaria capaz de predecir si un estudiante universitario desertará o se graduará, sin el uso de frameworks de modelamiento como scikit-learn. El modelo se optimiza mediante el algoritmo de **Gradiente Descendente** implementado manualmente en Python.

---

## Integrantes

| Nombre | GitHub |
|---|---|
| Matias Alfredo Vidal Elliot | [@matvilliot](https://github.com/matvilliot) |
| Victor Daniel Rivera Torres | [@VictorRiveraT](https://github.com/VictorRiveraT) |
| Jesús Anselmo Morales Alvarado | [@jessusmorales](https://github.com/jessusmorales) |

**Docentes:** Mg. Josue Angel Mauricio Salazar · Lic. Jeremy Karsen Holguin Mori

---

## Estructura del repositorio

```
Prediccion-de-Desercion-de-Estudiantes-Universitarios/
│
├── data/
│   └── data.csv                  # Dataset original (UCI Repository)
│
├── notebooks/
│   └── Avance_Parcial.ipynb      # Notebook principal con EDA, modelo y evaluación
│
├── informe/
│   └── Informe_Parcial.pdf       # Informe parcial (Introducción, Estado del Arte, Metodología)
│
└── README.md
```

---

## Dataset

- **Fuente:** [UCI Machine Learning Repository](https://archive.ics.uci.edu/dataset/697/predict+students+dropout+and+academic+success)
- **Registros:** 4,424 estudiantes de educación superior (institución portuguesa)
- **Features:** 36 variables — demográficas, socioeconómicas y de desempeño académico
- **Variable objetivo:** `Target` con tres clases originales:
  - `Dropout` → desertó (clase 0)
  - `Graduate` → se graduó (clase 1)
  - `Enrolled` → aún cursando (excluida del análisis)
- **Dataset final (binario):** 3,630 registros — 39% Dropout / 61% Graduate

---

## Metodología

Se implementó un modelo de **Regresión Logística** optimizado con **Gradiente Descendente batch**, completamente desde cero usando solo `numpy`, `pandas` y `matplotlib`.

El pipeline es el siguiente:

1. **EDA** — análisis de distribución de clases, variables académicas clave (notas y unidades aprobadas por semestre) y variables socioeconómicas (deuda, beca, edad).
2. **Preprocesamiento** — one-hot encoding aplicado solo sobre train, escalado Z-score sin data leakage (parámetros calculados en train y aplicados a test), adición de columna de bias.
3. **Optimización** — selección de learning rate mediante experimento numérico comparando α ∈ {0.001, 0.01, 0.05, 0.1}. Se eligió **α = 0.01** por convergencia estable.
4. **Criterio de parada** — el algoritmo se detiene anticipadamente si el cambio en la función de costo entre iteraciones es menor a 1×10⁻⁶.
5. **Evaluación** — Accuracy, Precision, Recall, F1-Score y Especificidad calculadas manualmente desde la matriz de confusión.

>  **Sin frameworks de modelamiento.** No se usa scikit-learn ni ninguna librería equivalente. Solo `numpy`, `pandas`, `matplotlib` y `seaborn`.

---

## 📈 Resultados preliminares

> *Se actualizará con los resultados finales del modelo.*

| Métrica | Valor |
|---|---|
| Accuracy | — |
| Precision | — |
| Recall | — |
| F1-Score | — |
| Especificidad | — |

---

## Cómo ejecutar

**1. Clonar el repositorio**
```bash
git clone https://github.com/VictorRiveraT/Prediccion-de-Desercion-de-Estudiantes-Universitarios.git
cd Prediccion-de-Desercion-de-Estudiantes-Universitarios
```

**2. Instalar dependencias**
```bash
pip install pandas numpy matplotlib seaborn
```

**3. Ejecutar el notebook**

Abre `notebooks/Avance_Metodos_v2.ipynb` en Jupyter Notebook o JupyterLab. Asegúrate de que `data/data.csv` esté en la misma ubicación que indica la celda de carga de datos.

---

## Referencias principales

1. Realinho, V. et al. (2022). *Predict Students' Dropout and Academic Success*. UCI ML Repository.
2. Alfaro, C. et al. (2023). *Machine Learning Application in University Management: Classification Model for Dropping Out of Engineering Students in Peru*. LACCEI.
3. Flores, R. et al. (2023). *Model for the Prediction of Dropout in Higher Education in Peru Applying Machine Learning Algorithms*. ResearchGate.
4. Ortiz-Lozano, J. M. et al. (2018). *Perspectives to Predict Dropout in University Students with Machine Learning*. IWOBI.