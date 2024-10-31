# 4-html-css-js-3D
## Управление 3D объектами в html, css, js

<img src="https://github.com/TeachKait20/NoneCode/blob/main/3D+html/cube-rotate.gif?raw=true" width="200">


Для создания и работы с 3D-объектами в HTML, CSS и JavaScript можно использовать несколько методов и свойств, особенно с помощью CSS для базовых 3D-эффектов и JavaScript с WebGL для более сложных 3D-сцен.

## CSS 3D Трансформации
CSS позволяет применять базовые 3D-эффекты к HTML-элементам без использования JavaScript. Некоторые свойства для этого:

* `transform` — поддерживает 3D-трансформации, такие как вращение, масштабирование, перемещение.
* `rotateX(deg)` — вращает элемент вокруг оси X.
* `rotateY(deg)` — вращает элемент вокруг оси Y.
* `rotateZ(deg)` — вращает элемент вокруг оси Z.
* `translate3d(x, y, z)` — перемещает элемент в трёхмерном пространстве.
* `scale3d(x, y, z)` — масштабирует элемент в трехмерном пространстве.
`perspective` — задает перспективу для 3D-преобразований, что делает объекты ближе к камере больше, а дальше — меньше.
index.html:
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <div class="container">
        <div class="box">3D Box</div>
    </div>
</body>
</html>
```
style.css:
```css
.container {
    perspective: 1000px;
    width: 200px;
    height: 200px;
}

.box {
    width: 100px;
    height: 100px;
    background-color: lightblue;
    transform: rotateY(45deg);
    transform-style: preserve-3d;
}
```
На выходе получаем:

![image](https://github.com/user-attachments/assets/e47b8694-a7b7-4447-87ee-45d4a766f265)

## CSS анимации

Анимации с использованием `@keyframes` в CSS также работают с 3D-преобразованиями. Определение `@keyframes` начинается с указания ключевых моментов анимации, например, начального `(0% или from)` и конечного `(100% или to)`.

Пример:
```css
.element {
    animation-name: myAnimation;
    animation-duration: 2s;
    animation-timing-function: ease-in-out;
    animation-delay: 0s;
    animation-iteration-count: infinite; /* Бесконечная анимация */
}
```
1. `animation-name` — указывает название анимации, созданной с помощью `@keyframes`.
2. `animation-duration` — определяет, сколько времени будет длиться один цикл анимации (например, `2s, 500ms`).
3. `animation-timing-function` — устанавливает тайминг-функцию для анимации, которая влияет на скорость в разные моменты:
* `linear` — постоянная скорость;
* `ease` — медленное начало и конец, быстрая середина;
* `ease-in` — медленный старт;
* `ease-out` — медленное окончание;
* `ease-in-out` — медленный старт и конец.
4. `animation-delay` — задержка перед началом анимации.
5. `animation-iteration-count` — количество повторений анимации (можно использовать infinite для бесконечного повторения).
6. `animation-direction` — задаёт направление выполнения:
* `none` — возвращает элемент к исходному состоянию;
* `forwards` — сохраняет конечное состояние;
* `backwards` — сохраняет начальное состояние;
* `both` — сохраняет начальное и конечное состояние в зависимости от направления.
7. `animation-play-state` — управляет проигрыванием анимации (running — запущено, paused — приостановлено).
```css
@keyframes spin {
    from { transform: rotateY(0deg); }
    to { transform: rotateY(360deg); }
}
.box {
    animation: spin 5s infinite linear;
}
```

