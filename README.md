# Evaluación 3 – Optimización y Auditoría de un Pipeline de Deep Learning

**TLY1102 · Grupo 5** · Nicolas Fernandez Vera, Victor Gutierrez, Bastian Gutierrez
Docente: Jazna Meza Hidalgo · Noviembre 2026

Clasificación de 6 letras de la lengua de señas americana (A, C, F, K, O, Y) con el dataset
Sign Language MNIST, comparando una **MLP** y una **CNN** en un pipeline de 9 etapas:
carga → EDA → preprocesamiento → construcción → entrenamiento → regularización → evaluación → auditoría → optimización.

## Contenido
| Archivo | Descripción |
|---|---|
| `Evaluacion3_TLY1102_Grupo5_FINAL.ipynb` | Notebook con el pipeline completo y sus resultados |
| `Evaluacion3_TLY1102_Grupo5_FINAL.pptx` | Presentación de resultados |

## Cómo ejecutar
1. Descargar el dataset desde [Kaggle – Sign Language MNIST](https://www.kaggle.com/datasets/datamunge/sign-language-mnist).
2. Abrir el notebook en Colab: [Abrir en Colab](https://colab.research.google.com/drive/1hkCLVZGTa_SkzHTNRudeU-Ouxl50BzCB)
3. Activar GPU (*Entorno de ejecución → Cambiar tipo de entorno → GPU*) y subir `Sign Language MNIST.zip` al panel de archivos.
4. *Entorno de ejecución → Ejecutar todas* (≈ 10–12 min, por el grid search).

## Metodología
- **Partición 80/20 por familias:** las variaciones de una misma foto original quedan juntas, así la validación mide fotos nuevas (casi-copias en validación: 94,9 % al azar → 0,7 %).
- **Un entrenamiento por modelo**, con la regularización integrada (Batch Normalization, Dropout, L2, Data Augmentation, Early Stopping).
- **Auditoría en validación:** métricas, matrices de confusión, sesgos y Grad-CAM.
- **Optimización con grid search:** 9 configuraciones para la MLP y 27 para la CNN.

## Resultados (validación)
| Modelo optimizado | F1 | Accuracy | Errores (de 1.262) | Parámetros |
|---|---|---|---|---|
| MLP | 0,923 | 0,926 | 93 | 109.702 |
| **CNN** | **0,983** | **0,983** | **21** | **56.790** |

**Modelo recomendado: CNN optimizada** (lr 0,01, Dropout 0,3, L2 0,0001).

## Limitaciones
Sin conjunto de prueba independiente (la misma validación elige y compara los modelos), solo 6 letras.
