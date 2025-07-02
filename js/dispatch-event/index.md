---
title: "Метод `dispatchEvent`"
description: "Инициирует отправку события."
authors:
  - akhmadullin
related:
  - js/events
  - js/event
  - js/custom-event
tags:
  - doka
---

## Кратко

Метод `dispatchEvent` используется для программного запуска события, чтобы другие части приложения могли отреагировать на него через обработчики событий.

## Как пишется

```javascript
const event = new Event('click')

element.dispatchEvent(event)
```

## Как понять

Метод `dispatchEvent` используется для инициирования события вручную, без участия пользователя. Он принимает объект события, созданный заранее, и передаёт его на обработку системе событий. Затем вызываются обработчики, «слущающие» это событие.

`dispatchEvent` принимает в качестве параметра:

- обычное событие, созданное через [`Event`](/js/event/);
- пользовательское событие, созданное через [`CustomEvent`](/js/custom-event/).

Метод возвращает `false`, если событие может быть отменено и один из обработчиков события вызвал [`event.preventDefault()`](/js/event-prevent-default/), и `true` — в остальных случаях.

Метод полезен, когда нужно программно вызвать событие.

Например, он пригодится для создания собственных событий.

```javascript
const toogleMenuEvent = new CustomEvent('tooglemenuevent', {
  detail: {
    isOpen: true,
  }
})

document.dispatchEvent(toogleMenuEvent)
```

Или для имитации пользовательских действий при тестировании.

```javascript
const event = new Event('click')

element.dispatchEvent(event)
```

## Подсказки

💡 Отличить событие, созданное через `dispatchEvent`, от остальных можно с помощью свойства `event.isTrusted`. Оно будет равно `true` для событий, инициированных браузером, действиями пользователя или вызовами программных методов, например `element.focus()`, и `false` для событий, вызванных через `dispatchEvent`.

```javascript
if (event.isTrusted) {
  console.log('Это событие вызвано браузером.')
} else {
  console.log('Это событие вызвано через dispatchEvent.')
}
```
