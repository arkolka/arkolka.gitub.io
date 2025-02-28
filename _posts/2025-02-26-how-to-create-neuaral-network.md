---
layout: post
title: "Как обучить свою нейросеть: простой путь для новичков"
date: 2025-02-26
categories: Jekyll GitHub AI
comments: true
---

# Как обучить свою нейросеть: простой путь для новичков

## 🔹 Введение

В мире искусственного интеллекта (AI) обучение нейросетей стало доступным даже для новичков. В этой статье мы разберёмся, как можно обучить свою первую нейросеть, какие инструменты понадобятся и как запустить модель на Python.

## 🔹 Что нужно для обучения нейросети?

Перед тем как приступить к обучению, подготовим необходимые инструменты:

### 📌 **Язык программирования**

Мы будем использовать **Python**, так как он наиболее популярен в сфере машинного обучения.

### 📌 **Библиотеки**

Нам понадобятся:

- **TensorFlow** или **PyTorch** — основные библиотеки для построения нейросетей.
- **NumPy** — для работы с массивами данных.
- **Matplotlib** — для визуализации.

Установим их с помощью команды:

```powershell
pip install tensorflow numpy matplotlib
```

(Если используешь PyTorch, вместо `tensorflow` установи `torch` и `torchvision`.)

### 📌 **Данные для обучения**

Для первой нейросети лучше взять готовый датасет. Например, **MNIST** (рукописные цифры) — отличный выбор для новичков.

## 🔹 Создаём свою первую нейросеть

Напишем код для простой нейросети, которая будет распознавать рукописные цифры из MNIST.

```python
import tensorflow as tf
from tensorflow import keras
import numpy as np
import matplotlib.pyplot as plt

# Загружаем датасет MNIST
(x_train, y_train), (x_test, y_test) = keras.datasets.mnist.load_data()

# Нормализация данных (переводим в диапазон от 0 до 1)
x_train, x_test = x_train / 255.0, x_test / 255.0

# Создаём простую модель
model = keras.Sequential([
    keras.layers.Flatten(input_shape=(28, 28)),  # Входной слой (преобразует 28x28 вектор в 1D)
    keras.layers.Dense(128, activation='relu'),  # Скрытый слой с 128 нейронами
    keras.layers.Dense(10, activation='softmax') # Выходной слой (10 классов)
])

# Компилируем модель
model.compile(optimizer='adam',
              loss='sparse_categorical_crossentropy',
              metrics=['accuracy'])

# Обучаем модель
model.fit(x_train, y_train, epochs=5)

# Оцениваем качество на тестовых данных
test_loss, test_acc = model.evaluate(x_test, y_test, verbose=2)
print("Точность на тестовых данных:", test_acc)
```

## 🔹 Как и почему работает эта нейросеть?

### **1. Разбор архитектуры нейросети**

Мы создали **многослойный перцептрон** (MLP), который решает задачу **классификации** рукописных цифр.

#### **Структура модели:**

1. **Входной слой** (`Flatten(input_shape=(28, 28))`)

   - Преобразует **28×28 изображение** в одномерный вектор из 784 чисел.
   - Это необходимо, потому что полносвязные слои требуют **одномерные входные данные**.

2. **Скрытый слой** (`Dense(128, activation='relu')`)

   - 128 нейронов, которые обучаются находить **закономерности в цифрах**.
   - Использует **ReLU (Rectified Linear Unit)**, которая:
     - Если вход < 0 → выдаёт 0.
     - Если вход > 0 → передаёт значение дальше.
   - Помогает избежать **затухания градиентов** и ускоряет обучение.

3. **Выходной слой** (`Dense(10, activation='softmax')`)

   - 10 нейронов, каждый отвечает за одну цифру (0-9).
   - `softmax` превращает выходные значения в **вероятности классов**.
   - Класс с самой высокой вероятностью становится предсказанным ответом.

### **2. Как нейросеть обучается?**

Обучение проходит в несколько этапов:

1️⃣ **Прямой проход (forward pass)**

- Данные проходят через все слои.
- Каждый слой выполняет вычисления (умножение весов, сложение, активация).
- На выходе softmax выдаёт **вероятности классов**.

2️⃣ **Вычисление ошибки (Loss Function)**

- Используется **кросс-энтропийный loss** (`sparse_categorical_crossentropy`).
- Сравнивает предсказанные вероятности softmax с реальными метками (`y_train`).
- Чем больше ошибка, тем сильнее корректируются веса.

3️⃣ **Обратное распространение ошибки (backpropagation)**

- Градиентный спуск корректирует веса нейронов.
- Используется **Adam-оптимизатор**, который эффективно обновляет веса.

4️⃣ **Повторение цикла**

- Мы обучаем сеть **5 эпох**, что означает, что данные проходят через модель 5 раз.
- Каждый раз сеть корректирует свои веса и становится точнее.

### **3. Почему это работает?**

✅ **Скрытый слой помогает находить закономерности** в цифрах.
✅ **ReLU предотвращает затухание градиентов**, что делает обучение стабильным.
✅ **Softmax выдаёт вероятность принадлежности к каждому классу.**
✅ **Градиентный спуск с Adam-оптимизатором** эффективно обучает модель.

## 🔹 Анализируем и улучшаем модель

После обучения нейросети стоит оценить её точность. Если точность низкая, можно попробовать:

- Добавить больше слоёв или нейронов.
- Изменить функцию активации.
- Увеличить количество эпох обучения.

## 🔹 Заключение

Поздравляю! 🎉 Ты только что обучил свою первую нейросеть. Теперь можно попробовать:

- Использовать другой датасет (например, CIFAR-10 для классификации изображений).
- Настроить параметры модели.
- Изучить **PyTorch** как альтернативу TensorFlow.

Машинное обучение — это увлекательный процесс. Пробуй, экспериментируй и создавай свои AI-проекты! 🚀

