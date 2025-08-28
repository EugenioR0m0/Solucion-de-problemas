# Solución de Problemas

## 📌 Descripción de la actividad
Este proyecto corresponde a la materia **SC3314 – Inteligencia Artificial** (Universidad de Monterrey, Dr. Antonio Martínez Torteya).  
El objetivo principal fue **predecir la calificación final (G3) de estudiantes** a partir de información demográfica y de desempeño en los primeros periodos, utilizando técnicas de regresión lineal múltiple.

La base de datos utilizada proviene del [Student Performance Data Set (UCI Machine Learning Repository)](https://archive.ics.uci.edu/dataset/320/student+performance), con 395 observaciones y 10 variables.

---

## 📊 Variables incluidas
- **Escuela**: GP (Gabriel Pereira) o MS (Mousinho da Silveira)  
- **Sexo**: F (femenino) o H (masculino)  
- **Edad**: años cumplidos  
- **HorasDeEstudio**: categorías ordinales (1 = <2h, 2 = 2-5h, 3 = 5-10h, 4 = >10h)  
- **Reprobadas**: número de materias reprobadas previamente  
- **Internet**: acceso a internet en casa (yes/no)  
- **Faltas**: cantidad de inasistencias  
- **G1**: calificación del primer periodo (0–20)  
- **G2**: calificación del segundo periodo (0–20)  
- **G3**: calificación final (0–20, variable objetivo)  

---

## 🚀 Pasos realizados

### **1. Importación de datos**
Se cargó el archivo `Calificaciones.csv` y se inspeccionaron tipos de datos y primeras observaciones.

### **2. Transformación de variables categóricas**
Se aplicó `pd.get_dummies()` para convertir variables categóricas a variables numéricas binarias, eliminando problemas de interpretación en el modelo.

### **3. Identificación de valores atípicos**
Se utilizó el **método de Tukey con k=3** para la variable `Faltas`.  
Se analizaron los casos detectados y se justificó si debían conservarse o eliminarse.

### **4. Matriz de correlación y heatmap**
Se generó una matriz de correlaciones visualizada con seaborn.  
- Se detectó colinealidad entre **G1, G2 y G3**.  
- Se discutió la necesidad de eliminar variables redundantes.

### **5. Inclusión de términos de interacción**
Se añadieron interacciones relevantes como:  
- `G1 * Internet_yes`  
- `HorasDeEstudio * Reprobadas`  
Esto permitió capturar efectos combinados en el desempeño de los estudiantes.

### **6. Entrenamiento y validación del modelo**
- División del dataset en **80% entrenamiento** y **20% prueba**.  
- Entrenamiento con **Regresión Lineal Múltiple**.  
- Métricas de evaluación:  
  - **R² ≈ 0.78**  
  - **MSE ≈ 4.49** (error promedio ≈ 2 puntos sobre la escala 0–20).  
- Se graficaron valores reales vs predichos mostrando buena alineación.
