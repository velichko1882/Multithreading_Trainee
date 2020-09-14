# Multithreading


### Задание 1

Задание реализовать с помощью классической многопоточности Java!

Описать с помощью ООП (классы, интерфейсы и наследование) следующую предметную область.

В курортном городке есть два места для обмена валют: обменный пункт и валютчик (оба реализуют логику обмена валют, а также содержат одинаковое поле курса валют, сами подумайте, что я хотел этим сказать 😉). Курс в официальном пункте обмена колеблется вверх-вниз в некотором интервале времени, например, каждые 5 секунд, а лучше сделать рандомайзером от 5 до 10 секунд. Курс у валютчика всегда ниже официального на 5%. Иными словами, изменение официального курса должно приводить к изменению курса у валютчика. Каждый из вариантов обмена содержит очередь, причем очередь обменного пункта не может превышать некое количество n, а валютчик готов обслужить всех без ограничений. Время на обслуживание одного туриста: 3 секунды у обменного пункта, 2 секунды у валютчика.

Город посещают туристы. Их появление в городе непериодично и находится в интервале от 1 до 10 секунд. Из вежливости обменный пункт и валютчик договорились обслуживать туристов по очереди. Вариант реализации права обслуживания можно придумать на Ваше усмотрение. Самое очевидное -предусмотреть boolean-поле у обоих объектов. True будет означать, что данный объект захватил текущего туриста, false – если туриста захватил конкурент. Каждый турист сначала узнает курс, а затем решает совершить сделку. Менять может сумму от 100 до 1000$. Таким образом, значение курса для обеих операций должно совпадать. Для упрощения задачи турист всегда меняет деньги у того объекта, в чью очередь он попал, сделку совершает один раз. Предусмотреть посещение городка 20-30 туристами.

Все временные и числовые интервалы Вы можете изменить, если это требуется для более качественной демонстрации.

Демонстрацию проводить в Runner-классе.


### Задание 2

Решить задание 1 с помощью пакета java.util.concurrent. Классическая многопоточность должна быть заменена.


### Задание 3

Для решения данной задачи использовать только java.util.concurrent.

Описать работу туристического менеждера.

Представим на минутку, что Вы менеджер туристической фирмы. В Ваши обязанности входит разработка и реализация туристического маршрута. 

У Вас есть туристический автобус на 40 мест.  Предположим, что все билеты на тур уже проданы и автобус готов отправляться. Отправляется он только, когда в точку сбора прибудут все 40 туристов. У каждого туриста предусмотреть поле isInTravel, которое при посадке будет установлено в true. На каждой остановке турист сделает одно фото. Для этого предусмотрите счетчик фотографий (одно фото – просто инкремент на один).

Первой остановкой будет Прага. Туристы спешат в Старый город, чтобы выпить по пинте темного чешского пива. Но купить его можно только у одного пивовара, поэтому все вынуждены выстроиться в очередь. Да и пъют пиво все по-разному, кто-то за секунду, а кто-то и за 5. Пусть это время будет стандартным временем употребления пищи для каждого туриста, определить его как внутренний рандом в конструкторе туриста.

Автобус подождет всех.

Дальше туристы отправляются в Париж, Лувр. Они спешат посмотреть на улыбку Джоконды, но подходить к ней могут только по 5 человек одновременно (имею в виду, одновременно стоят 5, один отходит, другой подходит) и стоять 1 секунду.

Автобус будет ждать, пока все туристы посмотрят на произведение искусства.

Следующей остановкой будет вечный Рим, где туристы отведают пиццу или пасту. Все разделятся на две равные группы и посетят два тематических ресторана (подсказка, две очереди, четные и нечетные туристы). Обслуживать их будут по 5 человек, то есть забирать из очереди по очереди 😊 5 человек и одновременно начинать обслуживать, но есть они будут с разной скоростью, а значит, и возвращиться в автобус они будут по одному.

Автобус ждет, пока соберется вся группа.

Последней остановкой будет побережье Испании, где все могут одновременно отдохнуть на пляже. Началом отдыха будем считать приезд автобуса на остановку (начало новой фазы 😉). Время отдыха для каждого туриста будет свое случайное, но не более максимально отведенного (например, пять секунд).

Перед посадкой в автобус каждому туристу будет дана возможность подключиться к общему облаку и скинуть туда все свои фотографии. Алгоритм сброса фото: облаку передать состояние внутреннего счетчика фотографий туриста, а от облака получить нуль. После обработки фотографий последнего туриста вывести количество фотографий в облаке, это должна быть сумма фотографий туристов.

По окончанию отдыха все туристы собираются в автобусе и он отправляется в конечный пункт, где высажывает текущую группу и набирает следующую. Высадку туристов можно осуществить с помощью перевода состояния поля isInTravel в false.

Всего осуществить тур для двух групп (циклически)

Работу менеджера произвести с помощью внятного вывода в логгер.



### Задание 4

Реализовать решение элементарной математической задачи на основе Fork / Join Framework.

Вычислить сумму чисел от 0 до 1_000_000_000. 

Собрать статистику времени в таблицу (можно руками внести в Excel) для следущих случаев:

1. Однопоточное приложение (без Fork / Join Framework)

2. Fork / Join Framework с одним потоком.

3. Fork / Join Framework с двумя потоками вычисления.

4. Fork / Join Framework с четырьмя потоками вычисления.

5. Если есть энтузиазм, то можете посчитать и с разбиением на 8 и 16 потоков вычисления.

На основе статистики сделать обоснованные выводы о целесообразности использования Fork / Join Framework для данной задачи. Также указать конфигурацию Вашего компьютера (объем памяти, количество и частоту ядер процессора). Таблицу залить в репозиторий в корне модуля.