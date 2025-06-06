# 🎯 House Price Prediction (Kaggle)

> Сравнение трёх популярных градиентных бустингов — XGBoost, LightGBM и CatBoost — на задаче регрессии. Основная метрика качества: RMSE, а также R², на тренировочной и тестовой выборках.

---

## 📦 Описание

Цель проекта — построить и сравнить три мощных алгоритма градиентного бустинга на задаче предсказания числового признака (регрессии).  
Для каждой модели выполнен подбор гиперпараметров. Анализируется переобучение и обобщающая способность моделей.

---

## 🛠️ Использованные технологии

- `pandas`, `numpy` — работа с данными
- `scikit-learn` — метрики, сплит данных
- `XGBoost` — градиентный бустинг от DMLC
- `LightGBM` — быстрый бустинг от Microsoft
- `CatBoost` — бустинг от Yandex с поддержкой категориальных признаков
- `matplotlib`, `seaborn` — визуализация

---

## 📊 Результаты

| Модель     | R² (Test) | RMSE Train | RMSE Test | Гиперпараметры |
|------------|-----------|------------|-----------|----------------|
| 🐍 XGBoost | 0.862     | 14554.31   | **26541.51**  | `{'subsample': 0.8, 'reg_lambda': 1, 'reg_alpha': 0, 'n_estimators': 200, 'min_child_weight': 1, 'max_depth': 3, 'learning_rate': 0.05, 'gamma': 0.1, 'colsample_bytree': 0.8}` |
| 💡 LightGBM| 0.864     | 14671.78   | 29622.39  | `{'subsample': 1.0, 'reg_lambda': 1, 'reg_alpha': 0, 'n_estimators': 200, 'min_child_weight': 1, 'max_depth': 3, 'learning_rate': 0.1, 'colsample_bytree': 0.8}` |
| 🐱 CatBoost| **0.881** | **4417.86**| 28284.28  | `{'subsample': 0.8, 'reg_lambda': 1, 'n_estimators': 300, 'max_depth': 7, 'learning_rate': 0.1}` |

> 📌 *CatBoost показал наилучший результат по R², при этом RMSE на обучении заметно ниже — что может указывать на переобучение. LightGBM переобучился сильнее остальных. XGBoost даёт стабильный баланс.*

---

## 📌 Вывод

📈 Несмотря на то, что CatBoost показал наивысшее значение R² (0.881), **лучшая модель по метрике RMSE на тестовой выборке — это XGBoost**.  
Он обеспечивает наименьшую ошибку на тесте (26,541), сохраняя стабильный баланс между качеством на обучении и тестировании.  
LightGBM продемонстрировал немного хуже RMSE и признаки переобучения.  
CatBoost имеет минимальную ошибку на обучении, но на тесте уступает XGBoost.

✅ **Рекомендуется использовать XGBoost для задач, где важна минимизация ошибки прогноза на новых данных.**

---

## 🚀 Как запустить

```bash
pip install -r requirements.txt
python run_experiment.py
