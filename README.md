# Курс: Написание макросов на Python для FreeCAD

## Оглавление
1. [Установка FreeCAD](#установка-freecad)
2. [Настройка консоли и запуск кода](#настройка-консоли-и-запуск-кода)
3. [Построение линии](#построение-линии)
4. [Построение квадрата](#построение-квадрата)
5. [Построение окружности](#построение-окружности)

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
import Part

doc = App.newDocument()

# Создаем две точки
point1 = App.Vector(0, 0, 0)
point2 = App.Vector(10, 0, 0)

# Создаем линию между этими точками
line = Part.LineSegment(point1, point2)

# Добавляем линию в документ
Part.show(line.toShape())

doc.recompute()
```
## Построение квадрата
Для создания квадрата выполните следующий код:

```python
import FreeCAD as App
import Part

doc = App.newDocument()

# Создаем четыре точки
points = [App.Vector(0, 0, 0), App.Vector(10, 0, 0), App.Vector(10, 10, 0), App.Vector(0, 10, 0)]

# Создаем линии между этими точками
lines = [Part.LineSegment(points[i], points[(i + 1) % 4]) for i in range(4)]

# Добавляем линии в документ
for line in lines:
    Part.show(line.toShape())

doc.recompute()
```
## Построение окружности
Для создания окружности в FreeCAD используйте следующий код:

```python
import FreeCAD as App
import Part

doc = App.newDocument()

# Создаем центр и радиус окружности
center = App.Vector(5, 5, 0)
radius = 5

# Создаем окружность
circle = Part.Circle(center, App.Vector(0, 0, 1), radius)

# Добавляем окружность в документ
Part.show(circle.toShape())

doc.recompute()

```



