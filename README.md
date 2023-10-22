# Хакатон от компании “Лента” (сентябрь 2023 г.)
Проектное участие в кросс-функциональном хакатоне по разработке ML-продукта предсказательной модели для ООО “Лента”.

## **Краткое описание:**
Необходимо создать алгоритм прогноза спроса на 14 дней для товаров собственного производства. Гранулярность ТК-SKU-День. Сгенерировать различные признаки и
придумать интерпретируемую, описывающую правильные зависимости (повышение цены вызывает логичное падение спроса), модель прогноза спроса.  Дальше необходимо сделать подневной прогноз спроса на тестовом периоде для каждого товара и магазина, и команда Ленты оценит его качество в сравнении с свершившимся фактом. Метрикой качества будет выступать WAPE, посчитанный на уровне товар, магазин, день. Если есть пропущенные значения и по каким-то товарам не предоставлен прогноз, прогноз считается равным нулю.

## Совершенные действия:
1. Проанализировал данные.
2. Провел инжиниринг признаков, а именно: кластеризацию временных рядов спроса на товар и кластеризацию цены, что позволило снизить ошибку предсказания модели.
3. Подготовил Pipeline для обучения модели.
4. Обучил модели: Линейную регрессию, Facebook Prophet, Catboost, выбрал оптимальную и произвел подбор гиперпараметров с помощью библиотеки Optuna.роанализировал важность признаков с помощью Shap. [Notebook с кодом и описанием здесь](https://github.com/ThreeHundredsperSecond/Lenta_Hackathon/blob/main/Notebook/lenta_demand_forecast.ipynb)
5. Реализовал сборку и финализировал ML-продукт для запуска в продуктовое использование. [Интркуция для подготовки и запуска проекта задесь](https://github.com/ThreeHundredsperSecond/Lenta_Hackathon/tree/main/Docker)

## Результат : 🥈
С гордостью объявляю, что наша команда заняла 2 место в хакатоне! Это был потрясающий опыт, и я благодарен за возможность продемонстрировать наши навыки и творчество.
- [Сертификат](https://github.com/ThreeHundredsperSecond/images/blob/main/42.png)

