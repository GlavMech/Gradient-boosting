📊 Сравнение моделей CatBoost и XGBoost по метрике ROC AUC

📌 Задача

Провести сравнение двух популярных моделей градиентного бустинга — CatBoost и XGBoost — в задаче бинарной классификации на заданном датасете. Метрика качества — ROC AUC.

🔧 Этапы работы
1. Подготовка данных
- Разделены признаки X и целевая переменная y.
- Обнаружены категориальные признаки.
- Обработаны пропуски:
    - В категориальных признаках заменены на 'missing'.
    - В числовых — на -999.
- Категориальные признаки закодированы с помощью OrdinalEncoder.

2. Разделение на выборки
 - Данные разбиты в соотношении 70% — train, 30% — test с помощью train_test_split.
 - Использовано стратифицированное разбиение по целевой переменной (stratify=y).

3. Обучение моделей «из коробки»
 - CatBoostClassifier обучен без настройки параметров (verbose=0, random_state=42).
 - XGBClassifier обучен с параметрами use_label_encoder=False, eval_metric='logloss', random_state=42.

4. Оценка качества
 - Для обеих моделей получены вероятности положительного класса (predict_proba).
 - Рассчитан ROC AUC на тестовой выборке с помощью roc_auc_score.

5. Сравнение
Выведено, какая модель показала лучший результат в «базовой» (default) конфигурации.

✅ Результаты

``` python
CatBoost ROC AUC: 0.9213
XGBoost (default) ROC AUC: 0.8911
XGBoost (tuned) ROC AUC: 0.9102
Даже после настройки XGBoost не обошёл CatBoost.
```

📦 Используемые библиотеки
pandas
- scikit-learn
- catboost
- xgboost

Установка:
``` pyton
pip install pandas scikit-learn catboost xgboost
```
