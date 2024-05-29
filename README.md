# Знакомство с FreeCAD и с его основами

## Оглавление
1. [Установка FreeCAD](#установка-freecad)
2. [Настройка консоли и запуск кода](#настройка-консоли-и-запуск-кода)
3. [Построение линии](#построение-линии)
4. [Построение квадрата](#построение-квадрата)
5. [Построение окружности](#построение-окружности)
6. [Построение условного знака (стрелки)](#построение-условного-знака-стрелки)
7. [Создание группы](#Создание-группы)
8. [Перемещение группы с помощью функции Move](#Перемещение-группы-с-помощью-функции-Move)
9. [Поворот группы с помощью функции Rotate](#Поворот-группы-с-помощью-функции-Rotate)
10. [Масштабирование группы ](#Масштабирование-группы)
11. [Установка Pandas в образ FreeCAD](#Установка-Pandas-в-образ-FreeCAD)
12. [Соединение линий между точками](#Соединение-линий-между-точками)
## Установка FreeCAD
Чтобы начать работать с FreeCAD, необходимо установить его. Следуйте этим шагам:

1. Перейдите на официальный сайт [FreeCAD](https://www.freecadweb.org/).
2. Выберите версию для вашей операционной системы и скачайте установочный файл.
3. Запустите скачанный файл и следуйте инструкциям по установке.

## Настройка консоли и запуск кода
Для написания и запуска макросов на Python в FreeCAD выполните следующие действия:

1. Откройте FreeCAD.
2. Включите консоль Python:
   - Перейдите в меню `View` -> `Panels` -> `Python console`.
3. Для создания нового макроса:
   - Перейдите в меню `Macro` -> `Macros...`.
   - Нажмите `Create` и введите имя для вашего макроса, затем нажмите `Save`.
4. Напишите ваш код в открывшемся окне макросов.
5. Чтобы запустить макрос:
   - Нажмите `Execute` в окне макроса или нажмите кнопку `Execute` в панели инструментов.

## Построение линии
Для создания линии в FreeCAD используйте следующий код:

```python
import FreeCAD as App
import Draft

# Получаем текущий активный документ
doc = App.activeDocument()

# Создаем две точки
point1 = App.Vector(0, 0, 0)
point2 = App.Vector(10, 0, 0)

# Создаем линию между этими точками
line = Draft.makeLine(point1, point2)

doc.recompute()
```
## Построение квадрата
Для создания квадрата выполните следующий код:

```python
import FreeCAD as App
import Draft

# Получаем текущий активный документ
doc = App.activeDocument()

# Создаем четыре точки
points = [App.Vector(0, 0, 0), App.Vector(10, 0, 0), App.Vector(10, 10, 0), App.Vector(0, 10, 0), App.Vector(0, 0, 0)]

# Создаем линии между этими точками
for i in range(len(points) - 1):
    Draft.makeLine(points[i], points[i + 1])

doc.recompute()
```
## Построение окружности
Для создания окружности в FreeCAD используйте следующий код:

```python
import FreeCAD as App
import Draft

# Получаем текущий активный документ
doc = App.activeDocument()

# Получаем текущий активный документ
doc = App.activeDocument()
# Создаем центр и радиус окружности
center = App.Vector(5, 5, 0)
radius = 5

# Создаем окружность
circle = Draft.makeCircle(radius, center)

doc.recompute()
```
## Построение условного знака (стрелки)
Для создания условного знака стрелки выполните следующий код:
```python
import FreeCAD as App
import Draft

# Получаем текущий активный документ
doc = App.activeDocument()

# Создаем точки для стрелки
point1 = App.Vector(0, 0, 0)     # Начало стрелки
point2 = App.Vector(10, 0, 0)    # Конец стрелки
point3 = App.Vector(7, 3, 0)     # Верхняя точка наконечника
point4 = App.Vector(7, -3, 0)    # Нижняя точка наконечника


line1 = Draft.makeLine(point1, point2)
line2 = Draft.makeLine(point2, point3)
line3 = Draft.makeLine(point2, point4)
doc.recompute()
```
## Создание группы 
Для создании групппы выполните следующий код:
```python
# Создаем группу и добавляем в нее линии
group = doc.addObject("App::DocumentObjectGroup", "Group1")
group.addObject(line1)
group.addObject(line2)
group.addObject(line3)
```
## Перемещение группы с помощью функции Move
Для перемещения групппы выполните следующий код:
```python
# Смещаем объекты в группе на вектор (10, 0, 0)
Draft.move(group.OutList, App.Vector(10, 0, 0), copy=False)
```
## Поворот группы с помощью функции Rotate
```python
# Определяем ось вращения
axis = App.Vector(0, 0, 0) 
# Вращаем объекты в группе на 90 градусов относительно заданной оси
Draft.rotate(group.OutList, 90, axis)
```
## Масштабирование группы
```python
Draft.scale(group.Group, scale=App.Vector(2, 2, 2), center=App.Vector(0, 0, 0), copy=False)
```
## Установка Pandas в образ FreeCAD
Открываете CMD консоль через администратора и вводите следующие команды
Указываете свой путь к папке bin в FreeCAD, после устанавливаете библиотеку Pandas
```bash
cd "C:\Program Files\FreeCAD\bin"
pip install pandas
```
## Соединение линий между точками
```python
lines_list = [
    (1, 2), (2, 3), (3, 4), (4, 5), (5, 6), (6, 7), (7, 1), 
    (7, 8), (8, 9), (9, 7), (11, 13), (11, 10), (10, 12), 
    (12, 13), (8, 5), (1, 11), (10, 3), (10, 4), (12, 5), 
    (9, 2), (11, 9), (9, 3), (8, 6), (13, 6), (8, 4)
]

for line in lines_list:
    i = 1
    for point in line:
        if i == 1:
            indx = df.index[df["Names"] == point]
            point1 = App.Vector(df['x'][indx], df['y'][indx], df['z'][indx])
            i = 0
        else:
            indx = df.index[df["Names"] == point]
            point2 = App.Vector(df['x'][indx], df['y'][indx], df['z'][indx])
            i = 1
    line = Draft.make_line(point1, point2)
```
Добавление подписей к точкам
```python
for i in range(len(x_coords)):
    if Name[i] != "Names":  # Пропуск первой строки с заголовками
        t = [str(Name[i])]  # Список с текстом для подписи
        p = App.Vector(x_coords[i], y_coords[i], z_coords[i])  # Координаты для подписи
        place = App.Placement(p, App.Rotation())
        text = Draft.make_text(t, place)
        text.ViewObject.FontSize = 0.00005  # Установка размера шрифта
        Draft.move(text, App.Vector(0.03, 0, 0.0), copy=False)
```

