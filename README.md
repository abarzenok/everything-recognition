# Распознавание чего угодно

Проект на основе [opencv](https://pypi.org/project/opencv-python/), распознающий конфигурируемые типы объектов на видео, получаемом с веб-камеры. 

### Как установить

Python3 должен быть уже установлен. 
Затем используйте `pip` (или `pip3`, есть есть конфликт с Python2) для установки зависимостей:
```
pip install -r requirements.txt
```

### Как запустить и остановить
Для запуска проекта, нужно выполнить `run.py`:

```python
python run.py
```
Запустится нативное окно, в котором транслируется изображение с веб-камеры (оденьтесь). Программа останавливается по нажатию на `q` на клавиатуре. Если не удастся подключиться к веб-камере, в консоль будет выводиться ошибка, вплоть до остановки программы. 

При успешной трансляции с камеры, на ней выделяются прямоугольниками распознанные объекты. Объекты для распознавания можно настроить, см. [Как настроить](#как-настроить).

### Как настроить
Настройка распознаваемых объектов осуществляется в файле `config.py`.

В нем хранится словарь `CASCADES`, в котором перечислены объекты для распознавания:
```python
CASCADES = {
    "Cat face": {
        "path": "haarcascades/faces/haarcascade_frontalcatface_extended.xml",
        "color": (0, 255, 255),
        "draw": True
    },
    "Speed limit": {
        "path": "haarcascades/road-signs/Speed Limit Signs/LBP_Size_24/Speedlimit_24_15Stages.xml",
        "color": (0, 255, 0),
        "draw": False
    }
}
```
В `path` указывается путь до файла в формате `.xml` с предварительно обученной моделью. Путь задается относительно директории, в которой лежит `run.py`. В проекте уже есть несколько предобученных моделей, в директории `haarcascades`.

В `color` задается цвет рамки, которая обрамляет найденный объект. Цвет задается в формате `(Green, Blue, Red)`. Например, для зеленого цвета, необходимо задать `(255, 0, 0)`, а для синего - `(0, 255, 0)`.

В `draw` можно включить или отключить обработку добавленных моделей. `True` - объект обрабатывается и отрисовывается, `False` - объект игнорируется.


### Цель проекта

Код написан в образовательных целях на онлайн-курсе для веб-разработчиков [dvmn.org](https://dvmn.org/).
