---
title: "`scrollsnapchange`"
description: "Событие остановки прокрутки и выбора новой точки привязки."
baseline:
  - group: scroll-snap-events
    features:
      - api.Document.scrollsnapchange_event
      - api.Element.scrollsnapchange_event
      - api.Window.scrollsnapchange_event
authors:
  - akhmadullin
related:
  - css/scroll-snap-type
  - js/element-scrollsnapchanging
  - js/element-scroll
tags:
  - doka
---

## Кратко

Событие `scrollsnapchange` срабатывает в момент остановки прокрутки и выбора новой точки привязки.

## Как пишется

```js
scrollContainer.addEventListener('scrollsnapchange', function(event) {
  console.log(event)
})
```

## Как понять

Событие `scrollsnapchange` возможно только на контейнерах с [привязкой прокрутки](/css/scroll-snap-type/). Сработает в момент, когда скролл остановился на новой точке привязки, причём до появления события `scrollend`.

Событие содержит ссылки на элементы, к которым привязалась прокрутка:

- `snapTargetBlock` — в блочном направлении;
- `snapTargetInline` — в строчном направлении.

```js
scrollContainer.addEventListener('scrollsnapchange', function(event) {
  // Получаем элемент, к которому привязалась прокрутка в блочном направлении
  console.log(event.snapTargetBlock)

  // Получаем элемент, к которому привязалась прокрутка в строчном направлении
  console.log(event.snapTargetInline)
})
```

Событие полезно, когда нужно получить информацию об элементе, на котором остановилась прокрутка. Попробуйте скроллить в демо ниже:

<iframe title="Получение номера слайда при остановке" src="demos/carousel/" height="550"></iframe>

## Подсказки

💡 Событие не сработает, пока пользователь не отпустит палец или курсор. Если пользователь продолжает зажимать элемент, значит прокрутка не завершилась. Поэтому событие и не сработает.

💡 Событие не сработает, пока точка привязки не изменилась. Если пользователь скроллил, но остановил прокрутку там же, где начал, то и `scrollsnapchange` не появится.
