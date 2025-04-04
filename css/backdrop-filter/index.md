---
title: "`backdrop-filter`"
description: "Свойство для применения фильтров к фоновой картинке."
baseline:
  - group: backdrop-filter
    features:
      - css.properties.backdrop-filter
authors:
  - goingtogogo
keywords:
  - фильтр фона
  - размытие фона
  - эффект матового стекла
related:
  - css/filter-functions
  - css/filter
  - css/background-blend-mode
tags:
  - doka
---

## Кратко

Свойство `backdrop-filter` позволяет применять визуальные эффекты (размытие, контраст, прозрачность и т. д.) к фону элементов, находящихся за целевым элементом. Оно работает так же, как свойство [`filter`](/css/filter/), но вместо того, чтобы изменять сам элемент, применяется только к его фону. Чтобы эффект заработал, у элемента должен быть прозрачный фон (`rgba`, `opacity`, `transparent` и т.д.), иначе `backdrop-filter` не будет заметен.

## Пример

```css
div {
  backdrop-filter: blur(15px);
}
```

## Как пишется

В качестве значения можно задать один или несколько фильтров, перечисляя их через пробел. Вот какие значения можно использовать:

- `blur(px)` — размытие фона. Например, `blur(15px)` создаст эффект размытого стекла.
- `brightness(%)` — регулирует яркость заднего фона. `brightness(150%)` делает фон ярче, а `brightness(50%)` затемняет его.
- `contrast(%)` — изменяет контрастность. Значение `contrast(200%)` увеличит контраст вдвое, а `contrast(50%)` сделает его ниже.
- `grayscale(%)` — переводит фон в оттенки серого. `grayscale(100%)` полностью уберёт цвета, а `grayscale(50%)` сделает их менее насыщенными.
- `opacity(%)` — управляет прозрачностью фона. Например, `opacity(50%)` сделает фон полупрозрачным.
- `sepia(%)` — придаёт фону тёплый, коричневатый оттенок. `sepia(100%)`, стилизует его под старую фотографию.
- `hue-rotate(deg)` — изменяет оттенок фона. Например, `hue-rotate(90deg)` сдвинет цветовой тон на 90 градусов по кругу HSL.
- `invert(%)` — инвертирует цвета. `invert(100%)` полностью перевернёт цвета, делая их противоположными.
- `none` — сбрасывает все фильтры, фон остаётся без изменений.

Попробуйте разные фильтры в интерактивном примере ниже:

<iframe title="Песочница" src="demos/playground/" height="660"></iframe>

Более подробно о фильтрах можно узнать в статье о [функциях фильтров](/css/filter-functions/).

## Подсказки

💡 Можно указать несколько функций через пробел. Причём при разном порядке функций результат будет отличаться.

💡 Поддержка в браузерах [хорошая](https://caniuse.com/?search=backdrop-filter), но в более старых версиях Safari может потребоваться префикс `-webkit`.
