# Vision-por-Computador
Clasificación multiclase de imágenes: Comparativa de rendimiento entre redes CNN entrenadas desde cero, ffNNs y Transfer Learning con EfficientNetV2S.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1TCuddaLtRi2AFsh637PnfkGGnSD8hKiK?usp=sharing)
> **Nota:** Haz clic en el botón de arriba para abrir el notebook directamente en Google Colab.

---

## Descripción General

Este proyecto de **Visión por Computador** implementa y evalúa de manera empírica la eficacia de tres familias de modelos de Redes Neuronales en la tarea de **Clasificación Multiclase** sobre el complejo dataset **CIFAR-100** (100 categorías).

El objetivo principal es demostrar y cuantificar el valor de las arquitecturas especializadas (CNN) y de la transferencia de conocimiento (Transfer Learning) en comparación con modelos base (ffNN).

## Metodología de Comparativa

El trabajo se basa en la implementación, entrenamiento y validación de tres arquitecturas diferentes sobre el mismo conjunto de datos (CIFAR-100, imágenes de 32x32 píxeles):

1.  **Red Neuronal Feedforward (ffNNs):** Utilizada como **línea base (baseline)** para medir el rendimiento de un modelo que ignora la estructura espacial de la imagen.
2.  **Red Neuronal Convolucional (CNN) desde Cero:** Se entrena una arquitectura profunda nativa para el dataset, demostrando la capacidad de las capas convolucionales para la extracción de características locales.
3.  **Transfer Learning (EfficientNetV2S):** Se utiliza el modelo **EfficientNetV2S** (pre-entrenado en ImageNet) y se aplica la técnica de **Fine-Tuning** (ajuste fino) para transferir su conocimiento al dominio de CIFAR-100, buscando el mayor rendimiento posible.

---

## Pre-procesamiento y Datos

* **Dataset:** **CIFAR-100** (100 clases de imágenes pequeñas).
* **Aumentación de Datos:** Se implementó una robusta estrategia de *Data Augmentation* creando imágenes espejo **horizontal y vertical**, lo que incrementó el set de entrenamiento de 50,000 a **200,000 imágenes** para prevenir el sobreajuste (*overfitting*).
* **Normalización:** Las imágenes se normalizaron entre 0 y 1.
* **Codificación:** Las etiquetas se convirtieron a formato **One-Hot Encoding** (`tf.keras.utils.to_categorical`).

## Resultados Clave

| Modelo Evaluado | Arquitectura Clave | Precisión Media (Mean Accuracy) | Observaciones |
| :--- | :--- | :--- | :--- |
| **1. ffNN (Línea Base)** | Capas Densas / Aplanadas | **~35.45%** | Bajo rendimiento debido a la pérdida de información espacial. |
| **2. CNN (Desde Cero)** | Capas Convolucionales / Max Pooling | **~50.38%** | Mejora significativa; valida la extracción jerárquica de características. |
| **3. Transfer Learning** | **EfficientNetV2S** (Fine-Tuning) | **~53.38%** | El mejor rendimiento, demuestra el valor del conocimiento pre-entrenado. |

### Conclusión Principal
La **arquitectura** de la red es el factor más determinante para la clasificación de imágenes. El paso de ffNN a CNN supuso la mayor ganancia de rendimiento. El **Transfer Learning** con una arquitectura de última generación (EfficientNetV2S) confirmó la ventaja de aprovechar el conocimiento a gran escala para obtener el mejor resultado final.

---

## Estructura del Notebook

El notebook está dividido en las siguientes secciones, con el código de entrenamiento, validación y métricas (Accuracy, Recall, Precision, Matrices de Confusión) para cada modelo:

1.  Carga de los datos y pre-procesamiento con aumentación de datos.
2.  Reconocimiento de imágenes con ffNNs.
3.  Reconocimiento de imágenes con CNNs (entrenada desde cero).
4.  Reconocimiento de imágenes con Transfer Learning (EfficientNetV2S).
5.  Explicación y Conclusiones finales.
