---
title: "`scrollsnapchanging`"
description: "Срабатывает во время прокрутки в момент определения потенциальной точки привязки."
baseline:
  - group: scroll-snap-events
    features:
      - api.Document.scrollsnapchanging_event
      - api.Element.scrollsnapchanging_event
      - api.Window.scrollsnapchanging_event
authors:
  - akhmadullin
related:
  - css/scroll-snap-type
  - js/element-scrollsnapchange
  - js/element-scroll
tags:
  - doka
---

## Кратко

Событие `scrollsnapchanging` срабатывает во время прокрутки в момент определения браузером потенциальной точки привязки.

## Как пишется

```js
scrollContainer.addEventListener('scrollsnapchanging', function(event) {
  console.log(event)
})
```

## Как понять

На событие `scrollsnapchanging` могут подписаться контейнеры с [привязкой прокрутки](/css/scroll-snap-type/). Событие сработает во время скролла, когда браузер определил точку, к которой будет привязана прокрутка, если она будет остановлена прямо сейчас.

Событие содержит ссылки на элементы, к которым может быть привязана прокрутка:

- `snapTargetBlock` — в блочном направлении;
- `snapTargetInline` — в строчном направлении.

```js
scrollContainer.addEventListener('scrollsnapchanging', function(event) {
  // Получаем элемент, к которому может быть привязана прокрутка в блочном направлении
  console.log(event.snapTargetBlock)

  // Получаем элемент, к которому может быть привязана прокрутка в строчном направлении
  console.log(event.snapTargetInline)
})
```

Событие может быть полезно, если необходимо получить информацию о пролистываемом элементе прямо во время прокрутки. Попробуйте прокрутить контейнер.

<aside>

🚧 На момент написания статьи событие `scrollsnapchanging` доступно только в Chromium браузерах. Проверяйте поддержку на [Can I use](https://caniuse.com/mdn-api_element_scrollsnapchanging_event).

</aside>

<iframe title="Использование события в карусели" src="demos/carousel/" height="500"></iframe>

## Подсказки

💡 В отличие от [scrollsnapchange](/js/element-scrollsnapchange/), которое ждет завершения прокрутки, `scrollsnapchanging` срабатывает в момент пролистывания. Если пользователь медленно скроллит, не отрывая палец или курсор, событие сработает несколько раз, пока он пролистывает возможные точки привязки. Каждый раз, когда браузер определяет, что при остановке прокрутка зафиксируется на новом элементе, событие сообщает, какой это элемент.

💡 При быстром пролистывании, охватывающем несколько точек привязки, событие сработает один раз — для конечной точки.
