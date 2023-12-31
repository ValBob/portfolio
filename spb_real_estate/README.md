# Исследование объявлений о продаже квартир

## Описание проекта

**Исходные данные**
- архив объявлений о продаже квартир в Санкт-Петербурге и соседних населённых пунктов за несколько лет.


**Задача**
- установить параметры, определяющие рыночную стоимость объектов недвижимости.

*Это позволит построить автоматизированную систему: она отследит аномалии и мошенническую деятельность.*

*По каждой квартире на продажу доступны два вида данных*
- *Первые вписаны пользователем,*
- *вторые — получены автоматически на основе картографических данных.*

## Выводы

В ходе проведенного исследования данных, полученных сервисом `Яндекс.Недвижимость` по `Санкт-Петербургу` и окрестностям за несколько лет были **решены следующие задачи:**
- Произведена загрузка и изучение общей информации, характеризующей набор данных.
- Проведена предобработка данных:
 - *поиск и обработка пропущенных значений по столбцам:*
  - `высота потолка` - заполнена медианным значением по столбцу,
  - `местоположение` - на основании удаленности пропусков от центра заполнена значением "Санкт-Петербург",
  - наличие `балконов` и `апартаменты` - заполнены 0 и False соответственно,
  - данные, генерируемые системой, оставлены без изменения.
 - *Преобразование типов данных:*
  - были преобразованы значения `даты публикации` в формат `даты-времени`.
 - *Устранение неявных дубликатов:*
  - устранение разночтений в написании названий населенных пунктов произведено на основе Собственных имен без указания типов, что позволило устранить `59 неявных дубликатов`.
 - *Обработка выбивающихся значенией:*
  - устранение выбросов по `стоимости объектов` (все что находится за пределами 3х-кратного межквартильного размаха) привело также к нормализации значений по площади объектов и количеству комнат,
  - скорректированы значения `площади кухни` там, где сумма жилой и нежилой площади превышала общую площадь,
  - проведена замена аномальных значений `высоты потолка` на медианное значение.
- Добавлены новые столбцы с вычисленными значениями и категориальными данными.
- Проведён исследовательский анализ данных
 - *Изучен характер распределения данных по заданным признакам*.
 - *Изучен характер распределения длительности продажи квартир:*
  - в `среднем` квартира продается за `93 дня`,
  - `быстрыми` считаются продажи быстрее `44 дней`,
  - `медленными` - дольше, чем `226 дня`.
 - *Изучены факторы, влияющие на стоимость объекта:*
  - наиболее высокая `зависимость` `цены объекта` от его `общей площади` (коэффициент корреляции Пирсона - `0.76`),
  - `стоимость объекта` не зависит от `дня недели` размещения объявления,
  - `стоимость объекта` растёт в зависимости от `категории этажа` в порядке: `первый` -> `последний` -> `другой`,
  - `стоимость объекта` в распределении `по месяцам` показывает локальные `максимумы` в `апреле`, `сентябре` и `ноябре` и `минимум` в `июне`,
  - `стоимость объекта` по годам `снижалась` с `2014 по 2016` годы, в `2016 и 2017` вышла на `плато` и с `2017 по 2019` показывал `рост`.
 - *Произведён расчёт `средней цены квадратного метра` в 10 населённых пунктах с наибольшим числом объявлений:*
  - Населённый пункт с `самой высокой` стоимостью квадратного метра - `Санкт_Петербург` (107 845 руб).
  - Населённый пункт с `самой низкой` стоимостью квадратного метра - `Выборг` (57 933 руб).
 - *Изучена зависимость стоимости объекта от расстояния до центра города:*
  - Имеется `слабая обратная корреляция` (-0.38) стоимости между `стоимостью квадратного метра` и `удаленностью объекта от центра` города.
  - `Средняя стоимость` квадратного метра в самом `центре` - `118 752 руб`.
  - `Средняя стоимость` квадратного метра `на окраине` (32 км) - `64 030 руб`.
  - При этом есть районы, где больший вес имеют другие факторы и при удаленности 27 км средняя стоимость квадратного метра составляет 132 116 руб.  
    
**В целом все задачи, поставленные перед данным исследованием, выполнены. Данные готовы для дальнейшего статистического изучения и создания моделей.**

## Статус

- Проект окончен
