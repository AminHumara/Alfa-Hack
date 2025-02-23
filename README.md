# Alfa-Hack
Хакатон от Альфа-Банка ( 01.11.2024 - 12.11.2024)

## Команда JULEBINO TEAM:
**TeamLead**: Белянинов Илья
- Ешеров Амин
- Абдухаликов Глеб
- Тежельникова Анна

## Итоговый ROC-AUC-Score:
- 0.861735

## Результат:
- 8 Место

# Трек: Склонность физических лиц к инвестициям

## Описание задачи
Задача заключается в прогнозировании склонности физических лиц к инвестициям на основе предоставленных данных. Цель — построить модель машинного обучения, которая сможет предсказать вероятность того, что клиент будет склонен к инвестированию. Это позволит финансовым организациям более эффективно предлагать инвестиционные продукты и услуги, минимизируя затраты на привлечение клиентов.

Данные содержат информацию о клиентах, включая различные признаки (фичи), такие как демографические данные, финансовые показатели, поведенческие характеристики и другие. Целевая переменная `target` указывает на склонность клиента к инвестициям (`1` — склонен, `0` — не склонен).

---

## Решение задачи

### 1. Подготовка данных
- **Загрузка данных**: Данные загружаются из нескольких CSV-файлов, содержащих информацию о клиентах. Используется библиотека `dask` для работы с большими объемами данных.
- **Объединение данных**: Данные из разных файлов объединяются в один датасет для дальнейшего анализа и обработки.
- **Обработка категориальных признаков**: Категориальные признаки преобразуются в строковый тип для корректной работы с моделью CatBoost.

---

### 2. Анализ данных
- **Исследование распределения целевой переменной**: Проведен анализ распределения классов целевой переменной `target`. В данных наблюдается баланс между классами (примерно равное количество клиентов, склонных и не склонных к инвестициям).
- **Анализ уникальных значений**: Проведен анализ уникальных значений в категориальных признаках для понимания их разнообразия.
- **Корреляционный анализ**: Построена корреляционная матрица для выявления сильно коррелированных признаков, которые могут быть исключены из модели.

---

### 3. Отбор признаков
- **Важность признаков**: С помощью модели CatBoost проведен анализ важности признаков. Отобраны наиболее значимые признаки для построения модели.
- **Исключение коррелированных признаков**: Удалены сильно коррелированные признаки, чтобы избежать мультиколлинеарности и улучшить качество модели.

---

### 4. Построение модели
- **Разделение данных**: Данные разделены на обучающую, валидационную и тестовую выборки с использованием стратификации для сохранения баланса классов.
- **Обучение модели CatBoost**: Использована библиотека CatBoost для построения модели классификации. Гиперпараметры модели подобраны с помощью библиотеки Optuna.
- **Оценка качества модели**: Качество модели оценивается с помощью метрики ROC-AUC. Проведено несколько экспериментов с разными наборами данных и гиперпараметрами для улучшения качества модели.

---

### 5. Прогнозирование и формирование сабмита
- **Прогнозирование на тестовых данных**: Построенная модель применяется к тестовым данным для получения прогнозов.
- **Усреднение прогнозов**: Для уменьшения дисперсии и улучшения качества прогнозов проведено усреднение результатов нескольких моделей.
- **Формирование итогового сабмита**: Результаты прогнозирования сохранены в файл для отправки на конкурс.

---

## Результаты
- **ROC-AUC Score**: Итоговое значение метрики ROC-AUC на тестовых данных составило **86.1735**.
- **Итоговый сабмит**: Файл с прогнозами (`submission_66.csv`) содержит предсказанные вероятности склонности клиентов к инвестициям.

---

## Используемые технологии и библиотеки
- **Python**: Основной язык программирования для решения задачи.
- **Pandas, Dask**: Для работы с данными.
- **CatBoost**: Для построения модели классификации.
- **Optuna**: Для подбора гиперпараметров модели.
- **Seaborn, Matplotlib**: Для визуализации данных.
- **Scikit-learn**: Для разделения данных и оценки качества модели.
```
