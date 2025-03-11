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

На событие `scrollsnapchange` могут подписаться контейнеры с [привязкой прокрутки](/css/scroll-snap-type/). Событие сработает в момент, когда прокрутка остановилась и была выбрана новая точка привязки, но до появления события `scrollend`.

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

Событие может быть полезно, если необходимо получить информацию об элементе, на котором остановилась прокрутка. Попробуйте прокрутить контейнер.

<iframe title="Использование события в карусели" src="demos/carousel/" height="500"></iframe>

<aside>

🚧 На момент написания статьи событие `scrollsnapchange` доступно только в Chromium браузерах. Проверяйте поддержку на [Can I use](https://caniuse.com/mdn-api_element_scrollsnapchange_event).

</aside>

## Подсказки

💡 Событие не сработает, пока пользователь не отпустит палец или курсор. Если пользователь продолжает зажимать элемент, значит прокрутка не завершилась. Поэтому событие и не сработает.

💡 Событие не сработает, если точка привязки не изменилась. Если пользователь скроллил, но остановил прокрутку на том же элементе, что и был выбран до этого, событие не сработает. Нет смены точки прокрутки, нет и события.
