---
title: "`object-view-box`"
description: "Кадрируем изображение с помощью CSS."
baseline:
  - group: object-view-box
    features:
      - css.properties.object-view-box
      - css.properties.object-view-box.none
authors:
  - akhmadullin
related:
  - html/img
  - css/object-fit
  - css/object-position
tags:
  - doka
---

## Кратко

Свойство `object-view-box` задаёт, какая часть изображения должна быть видна.

## Пример

```css
.cropped-element {
  object-view-box: inset(20%);
}
```

## Как понять

По своему поведению свойство `object-view-box` похоже на атрибут `viewBox` в [SVG](/html/svg/).

Оно устанавливает размеры окна отображения в [замещаемых элементах](https://developer.mozilla.org/ru/docs/Web/CSS/CSS_images/Replaced_element_properties), вроде [`<img>`](/html/img/), [`<video>`](/html/video/), [`<canvas>`](/html/canvas/). Контент, попавший в заданную область, будет виден, а остальной скроется.

Область отображения, заданную через `object-view-box`, браузер воспринимает в качестве исходного элемента, и свойства вроде [`object-fit`](/css/object-fit/) и [`object-position`](/css/object-position/) применяются именно к этой области. За счёт этого можно реализовать кадрирование изображения без изменения самого файла.

## Как пишется

Возможные значения `object-view-box`:

- `none` — значение по умолчанию, окно отображения не задаётся;
- `<basic-shape-rect>` – окно отображения задаётся в виде прямоугольника с помощью функций [`inset()`](https://developer.mozilla.org/en-US/docs/Web/CSS/basic-shape/inset), [`xywh()`](https://developer.mozilla.org/en-US/docs/Web/CSS/basic-shape/xywh).

## Использование

```css
.object-view-box-inset {
  object-fit: cover;
  object-view-box: inset(15% 15% 15% 15%);
}
```

<iframe title="Задаём область отображения через inset()" src="demos/inset/" height="770"></iframe>

```css
.object-view-box-xywh {
  object-fit: cover;
  object-view-box: xywh(10% 10% 75% 75%);
}
```

<iframe title="Задаём область отображения через xywh()" src="demos/xywh/" height="770"></iframe>

## Подсказки

💡 _Замещаемый элемент_ — это HTML-элемент, отображающий внешний ресурс, например, картинку или видео. Браузер берёт содержимое не из HTML-разметки, а подставляет готовое «встроенное» представление. В CSS мы можем менять размер и расположение такого элемента, но не управлять его внутренним содержимым.

💡 Помимо `object-view-box` есть и другие способы обрезать изображение, например, [`overflow: hidden`](/css/overflow/) и [`clip-path`](/css/clip-path/). В чём между ними разница?

Свойство `object-view-box` работает с содержимым ресурса. Оно позволяет выбрать прямоугольную область внутри замещаемого элемента и показать только её — как будто кадрируем исходный файл.

`overflow: hidden` и `clip-path` скрывают части уже отрисованного элемента снаружи: первый обрезает рамкой контейнера, второй вырезает фигуру по маске. При этом весь ресурс остаётся внутри элемента, даже если часть его не видна.

Таким образом, `object-view-box` задаёт «кадр» внутри источника, а `overflow` и `clip-path` — форму или рамку снаружи.

<iframe title="Сравниваем разные способы обрезки контента" src="demos/object-view-box-vs-others/" height="770"></iframe>
