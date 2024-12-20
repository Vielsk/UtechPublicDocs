# Мир

- [Основное меню](../README.md)

## Общие сведения

Мир является условно бесконечным, процедурно генерируемым, состоит из тайлов и разделен на вертикальные уровни, подобно игре Dwarf Fortress. Между уровнями существует не разрушаемая (но редактируемая) непрозрачная перегородка, поэтому визуально слои полностью разделены и никак не взаимодействуют с друг другом. Переход между уровнями осуществляется при взаимодействии персонажа с особыми тайлами мира (лестницами, пещерами, и т.п.).

Слой, расположенный на нулевом уровне считаются расположенными на поверхности, а слои расположенные на отрицательных уровнях  считаются подземными. Естественное освещение имеется только на поверхности, на подземных уровнях естественного освещения нет, влияние погодных условий (солнца, ветра, дождя, снега и т.д.) распространяется только на поверхностный слой.

Тайлы на уровне расположены слоями:

| Слой  | Описание                                                                                                            |
| ----- | ------------------------------------------------------------------------------------------------------------------- |
| Floor | Перегородка между слоями, не разрушается, но может подвергаться изменению, например рытье каналов, засыпка водоемов |
| Cover | Напольное покрытие, например пол из досок, снег, трава, и т.д.                                                      |
| Main  | Основной тайл, на котором располагаются стены, механизмы, структуры и т.д.                                          |

Тайл на основном слое может быть структурой, которая занимает места больше, чем тайл, и отображается отдельным тайлом. Это позволяет создавать деревья, столбы, вышки связи, опоры линий электропередач и т.д.

На глубоких уровнях персонаж не сможет находиться без специальной экипировки из-за отсутствия воздуха, наличия отравляющих газов, температурных условий.

## Моделирование мира

Модель мира хранит дату (число дней от начала игры), время (в секундах от начала дня), моделирует погоду (осадки, силу и направление ветра, температуру, температуру на поверхности). Температура и ветер на поверхности плавно изменяется в течение дня. Дата и время увеличиваются со временем. Температура на поверхности зависит от погодных условий, температура под землей зависит от глубины, и может изменяться вне зависимости от температуры на поверхности из-за воздействия каких-либо других причин. 

## Генерация мира

Генерация производится точечно по координатам точки (x, y, l), где l - слой. Слои с (l > 0) находятся в воздухе и обычно являются пустыми.

Поверхностный слой (l = 0) содержит большое количество структур (деревьев, распределенных по поверхности) и покрыт снегом.

Подземные слои (l < 0), могут содержать пещеры, а также полезные ископаемые. Подземный мир состоит из горных пород. Какая именно порода будет генерироваться решается с использованием шума. Порода в основном состоит из пустой каменной породы, которая может в себе содержать вкрапления полезных ископаемых, как распределенных по породе, так и расположенных (часто большими) жилами. Порода содержит много материала, поэтому большие объемы руками (без техники) не выкопать и не перенести. 

Игра сохраняет только изменения внесённые в игровой мир. Неизмененная информация не хранится, а процедурно генерируется каждый раз. 

---
© 2024 Вадим Бельский (bielski.vadim@gmail.com)