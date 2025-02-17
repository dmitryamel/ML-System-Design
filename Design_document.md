# ML System Design Doc - [RU]
## Дизайн ML системы - Solar Activity Analysis\<MVP or Production System\> \<1\>

## Вводная часть
**Список возможных задач:**
1. Прогнозирование солнечных бурь
2. Идентификация пятен на снимке, включая их количество, общую площадь, сегментацию по размеру (маленькие, средние и большие)
3. Анализ динамики пятен - сравнение 2 снимков с разницей ровно в 1 солнечные сутки и демонстрация разницы (по количеству пятен, какие пятна увеличились, какие пропали и какие появились).
4. Кластеризация изображений в зависимости от размера/количества солнечных пятен и прочих аномалий
5. Предсказание по фото, есть солнечная вспышка или нет.

**Датасеты / источники данных**:

1. [SDO | Solar Dynamics Observatory](https://sdo.gsfc.nasa.gov/) Данные спутника NASA, наблюдающего за солнечной активностью.

2. [GOES-2-go](https://github.com/blaylockbk/goes2go)   Фреймворк для загрузки спутниковых данных NOAA - The National Oceanic and Atmospheric Administration USA

3. [Данные о солнечной активности в режиме реального времени](https://earthquaketrack.ru/sun/)


4. [Sunspots Monthly Mean Total Sunspot Number - form 1749 to july 2018](https://www.kaggle.com/datasets/robervalt/sunspots)

5. [SpaceWeatherLive.com | Real-time data and plots auroral activity](https://www.spaceweatherlive.com/en.html) Солнечная активность в режиме реального времени

6. [Размеченный датасет для предсказания солнечных вспышек](https://i4ds.github.io/SDOBenchmark/)

7. [Данные о солнечных вспышках](http://www.wdcb.ru/stp/solar/solar_flare_events.ru.html)  Мировой Центр Данных по Солнечно-Земной Физике


**Исследования / Модели / Статьи:**

1. [Global Geomagnetic Perturbation Forecasting Using Deep Learning](https://agupubs.onlinelibrary.wiley.com/doi/10.1029/2022SW003045) Модель предсказания (на основе солнечного ветра) солнечных бурь с открытым кодом.

2. [Описание нейросети по предсказанию солнечных вспышек](https://earth-planets-space.springeropen.com/articles/10.1186/s40623-021-01381-9#:~:text=We%20found%20that%20operational%20DeFN%20achieved%20an%20accuracy%20of%200.99,a%20probability%20threshold%20of%2050%25)


3. [Flare Prediction Using Photospheric and Coronal Image Data](https://arxiv.org/abs/1708.01323)

4. [Comparative Study of Machine Learning Models on Solar Flare Prediction Problem ](https://digitalcommons.usu.edu/cgi/viewcontent.cgi?article=9282&context=etd)

5. [МЕТОДИКА ПРОГНОЗИРОВАНИЯ СОЛНЕЧНОЙ АКТИВНОСТИ НА ОСНОВЕ РАДИОАСТРОНОМИЧЕСКИХ НАБЛЮДЕНИЙ](http://www.sao.ru/Doc-k8/Science/Public/Bulletin/Vol73/N4/ASPB505.pdf)

6. [Astronet](https://www.astronet.ru/) Актуальная научная информация, в том числе по физике Солнца

> ## Термины и пояснения
> - Итерация - это все работы, которые совершаются до старта очередного пилота
> - БТ - бизнес-требования
> - EDA - Exploratory Data Analysis - исследовательский анализ данных
> - `Product Owner`,  `Data Scientist` - роли, которые заполняют соответствующие разделы
> - В этом шаблоне роль `Data Scientist` совмещает в себе компетенции классического `Data Scientist` с упором на исследования и `ML Engineer` & `ML Ops` роли с акцентом на продуктивизацию моделей
> - Для вашей организации распределение ролей может быть уточнено в зависимости от операционной модели


### 1. Цели и предпосылки
#### 1.1. Зачем идем в разработку продукта?
**Цель**:
- создать сервис для анализа и/или предсказания солнечной активности по фото.

**Ожидаемые выгоды** *(в процессе уточнения)*:
- *либо возможность получить прогноз по фото для широкой аудитории интересующихся астрономией;*
- *либо автоматизация генерации важных признаков из фото для последующего использования в задачах мониторинга за солнечной активностью.*

**Критерии успеха** *(в процессе уточнения)*:
- модель разработана
- модель позволяет получить прогноз с заданной точностью
- результаты прогноза можно интерпретировать с научной точки зрения
- реализован интерфейс доступа к модели через web-сайт

#### 1.2. Требования и ограничения

**Требования**:


**Ограничения**:



**Описание процесса работы модели**:



**Критерии успеха пилотного проекта**:



**Возможные пути развития проекта**:


#### 1.3. Что входит в скоуп проекта/итерации, что не входит

- На закрытие каких БТ подписываемся в данной итерации `Data Scientist`
- Что не будет закрыто `Data Scientist`
- Описание результата с точки зрения качества кода и воспроизводимости решения `Data Scientist`
- Описание планируемого технического долга (что оставляем для дальнейшей продуктивизации) `Data Scientist`

#### 1.4. Предпосылки решения

- Описание всех общих предпосылок решения, используемых в системе – с обоснованием от запроса бизнеса: какие блоки данных используем, горизонт прогноза, гранулярность модели, и др. `Data Scientist`

#### 2.1. Постановка задачи

- Что делаем с технической точки зрения: рекомендательная система, поиск аномалий, прогноз, оптимизация, и др. `Data Scientist`

#### 2.2. Блок-схема решения

- Блок-схема для бейзлайна и основного MVP с ключевыми этапами решения задачи: подготовка данных, построение прогнозных моделей, оптимизация, тестирование, закрытие технического долга, подготовка пилота, другое. `Data Scientist`
- [Пример возможной блок схемы](https://github.com/IrinaGoloshchapova/ml_system_design_doc_ru/blob/main/product_schema.png?raw=true)
> Схема обязательно включает в себя архитектуру бейзлайна. Если бейзлайн и основной MVP отличаются несущественно, то это может быть одна блок-схема. Если значительно, то рисуем две: отдельно для бейзлайна, отдельно для основного MVP.
> Если блок-схема **шаблонна** - т.е. её можно скопировать и применить к разным продуктам, то она **некорректна**. Блок-схема должна показывать схему решения для конкретной задачи, поставленной в части 1.

#### 2.3. Этапы решения задачи `Data Scientist`

- Для каждого этапа **по результатам EDA** описываем - **отдельно для бейзлайна** и **отдельно для основного MVP** - все про данные и технику решения максимально конкретно. Обозначаем необходимые вводные, технику предполагаемого решения и что ожидаем получить на выходе, чтобы перейти к следующему этапу.
- Как правило, детальное и структурированное заполнение раздела `2.3` возможно только **по результатам EDA**.
- Если описание в дизайн доке **шаблонно** - т.е. его можно скопировать и применить к разным продуктам, то оно **некорректно**. Дизайн док должен показывать схему решения для конкретной задачи, поставленной в части 1.

> Примеры этапов:
> - Этап 2 - Подготовка прогнозных моделей
> - Этап 3 - Интерпретация моделей (согл. с заказчиком)
> - Этап 4 - Интеграция бизнес правил для расчета бизнес-метрик качества мрдели
> - Этап 5 - Подготовка инференса модели по итерациям
> - Этап 6 - Интеграция бизнес правил
> - Этап 7 - Разработка оптимизатора (выбор оптимальной итерации)
> - Этап 8 - Подготовка финального отчета для бизнеса

*Этап 1 - это обычно, подготовка данных.*

В этом этапе должно быть следующее:

- Данные и сущности, на которых будет обучаться ваша модель машинного обучения. Отдельная таблица для целевой переменной (либо целевых переменных разных этапов), отдельная таблица – для признаков.

| Название данных  | Есть ли данные в компании (если да, название источника/витрин) | Требуемый ресурс для получения данных (какие роли нужны) | Проверено ли качество данных (да, нет) |
| ------------- | ------------- | ------------- | ------------- |
| Продажи | DATAMARTS_SALES_PER_DAY  | DE/DS | + |
| ...  | ...  | ... | ... |

- Краткое описание результата этапа - что должно быть на выходе: витрины данных, потоки данных, др.

> Чаще всего заполнение раздела невозможно без EDA.

 *Этапы 2 и далее, помимо подготовки данных.*

Описание техники **для каждого этапа** должно включать описание **отдельно для MVP** и **отдельно для бейзлайна**:

- Описание формирования выборки для обучения, тестирования и валидации. Выбор репрезентативных данных для экспериментов, обучения и подготовки пилота (от бизнес-цели и репрезентативности данных с технической точки зрения) `Data Scientist`
- Горизонт, гранулярность, частоту необходимого пересчета прогнозных моделей `Data Scientist`
- Определение целевой переменной, согласованное с бизнесом `Data Scientist`
- Какие метрики качества используем и почему они связаны с бизнес-результатом, обозначенным `Product Owner` в разделах `1` и `3`. Пример - WAPE <= 50% для > 80% категорий, bias ~ 0. Возможна формулировка в терминах относительно бейзлайна, количественно. Для бейзлайна могут быть свои целевые метрики, а может их вообще не быть (если это обосновано) `Data Scientist`
- Необходимый результат этапа. Например, необходимым результатом может быть не просто достижение каких-либо метрик качества, а включение в модели определенных факторов (флаг промо для прогноза выручки, др.) `Data Scientist`
- Какие могут быть риски и что планируем с этим делать. Например, необходимый для модели фактор (флаг промо) окажется незначимым для большинства моделей. Или для 50% моделей будет недостаточно данных для оценки `Data Scientist`
- Верхнеуровневые принципы и обоснования для: feature engineering, подбора алгоритма решения, техники кросс-валидации, интерпретации результата (если применимо).
- Предусмотрена ли бизнес-проверка результата этапа и как будет проводиться `Data Scientist` & `Product Owner`

### 3. Подготовка пилота

#### 3.1. Способ оценки пилота

- Краткое описание предполагаемого дизайна и способа оценки пилота `Product Owner`, `Data Scientist` with `AB Group`

#### 3.2. Что считаем успешным пилотом

Формализованные в пилоте метрики оценки успешности `Product Owner`

#### 3.3. Подготовка пилота

- Что можем позволить себе, исходя из ожидаемых затрат на вычисления. Если исходно просчитать сложно, то описываем этап расчетов ожидаемой вычислительной сложности на эксперименте с бейзлайном. И предусматриваем уточнение параметров пилота и установку ограничений по вычислительной сложности моделей. `Data Scientist`

  ### 4. Внедрение `для production систем, если требуется`

> Заполнение раздела 4 требуется не для всех дизайн документов. В некоторых случаях результатом итерации может быть расчет каких-то значений, далее используемых в бизнес-процессе для пилота.

#### 4.1. Архитектура решения

- Блок схема и пояснения: сервисы, назначения, методы API `Data Scientist`

#### 4.2. Описание инфраструктуры и масштабируемости

- Какая инфраструктура выбрана и почему `Data Scientist`
- Плюсы и минусы выбора `Data Scientist`
- Почему финальный выбор лучше других альтернатив `Data Scientist`

#### 4.3. Требования к работе системы

- SLA, пропускная способность и задержка `Data Scientist`

#### 4.4. Безопасность системы

- Потенциальная уязвимость системы `Data Scientist`

#### 4.5. Безопасность данных

- Нет ли нарушений GDPR и других законов `Data Scientist`

#### 4.6. Издержки

- Расчетные издержки на работу системы в месяц `Data Scientist`

#### 4.5. Integration points

- Описание взаимодействия между сервисами (методы API и др.) `Data Scientist`

#### 4.6. Риски

- Описание рисков и неопределенностей, которые стоит предусмотреть `Data Scientist`
