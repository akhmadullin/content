---
title: "Объект пользовательского события `CustomEvent`"
description: "Информация о пользовательском событии, произошедшем на странице."
authors:
  - akhmadullin
related:
  - js/event
  - js/events
  - js/dom
tags:
  - doka
---

## Кратко

Объект `CustomEvent` описывает пользовательское событие. С помощью него можно оповестить подписчиков о том, что нужное событие произошло и передать связанную с этим информацию.

## Как пишется

```javascript
const myCustomEvent = new CustomEvent('mycustomevent', {
  detail: {
    key: 'value'
  }
})
```

## Как понять

`CustomEvent` позволяет создать пользовательское (кастомное) событие. Такие события позволяют разработчику самостоятельно определить, когда событие происходит, как оно называется, и какие данные с ним передаются. Пригодится, когда стандартных DOM-событий (например, `click`, `input`) недостаточно для описания происходящего на странице.

`CustomEvent` похож на обычный [`Event`](/js/event/). Основное отличие — `CustomEvent` позволяет передать дополнительные данные, а `Event` нет.

Конструктор `CustomEvent` принимает в себя два аргумента:

- `type` — строка с названием события;
- `options` (необязательный) — объект со свойствами события:
  - `detail` (необязательный) — данные любого типа, которые необходимо передать вместе с событием;
  - `bubbles` (необязательный, по умолчанию false) — является ли событие [всплывающим](/js/events/#vsplytie-sobytiy);
  - `cancelable` (необязательный, по умолчанию false) — является ли событие отменяемым;
  - `composed` (необязательный, по умолчанию false) — должно ли событие переходить из теневого DOM в обычный.

Отправить пользовательское событие можно с помощью [dispatchEvent](https://developer.mozilla.org/en-US/docs/Web/API/EventTarget/dispatchEvent).

## Подсказки

💡 Кастомные события пригодятся, когда нужно сообщить другим частям приложения о каком-либо действии или изменении. Использование `CustomEvent` позволяет избавиться от прямых зависимостей между модулями и сделать их менее связными.

```javascript
// Модуль А
const userLoginEvent = new CustomEvent('userlogin', {
  detail: {
    username: authData.username,
  }
})

document.dispatchEvent(userLoginEvent)

// Модуль Б
const username = document.getElementById('username')

document.addEventListener('userlogin', (event) => {
  username.textContent = event.detail.username
})
```

<iframe title="Сообщаем об авторизации пользователя с помощью CustomEvent" src="demos/user-login/" height="480"></iframe>
