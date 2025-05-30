---
title: "`column-span`"
description: "Нарушаем правила колоночной вёрстки и растягиваем элемент сразу на несколько колонок."
baseline:
  - group: column-span
    features:
      - css.properties.column-span
      - css.properties.column-span.all
      - css.properties.column-span.none
authors:
  - xpleesid
related:
  - html/flow
  - css/display
  - css/columns
tags:
  - doka
---

## Кратко

Свойство `column-span` позволяет элементу растянуться на несколько колонок при многоколоночной вёрстке.

## Как пишется

Можно указать одно из двух ключевых слов – `none` или `all`.

```css
  .item1 {
    column-span: none;
  }

  .item2 {
    column-span: all;
  }
```

## Как понять

Если указать `none`, то элемент не будет растягиваться на несколько колонок. `none` – значение по умолчанию.

Если указать `all`, то элемент выпадет из [потока](/html/flow/) и растянется на все колонки. До и после него появятся переносы, контент до и после независимо разделится на колонки.

## Пример

Создадим простой блок, в котором будут два параграфа, разделённых заголовком.

```html
  <div class="wrapper">
    <p>Душа моя озарена неземной радостью...</p>
    <h2>Заголовок 2 уровня</h2>
    <p>Душа моя озарена неземной радостью...</p>
  </div>
```

```css
.wrapper {
  column-count: 4;
  column-width: 250px;
}
```

<iframe title="Пример без column-span" src="demos/without-span/" height="270"></iframe>

Как мы видим, получилось не очень красиво. Заголовок может переноситься по колонкам – скорее всего, мы не ожидаем такого поведения от [блочного](/css/display/#kak-ponyat) элемента. Чтобы было красиво, зададим для заголовка `column-span`.

```css
h2 {
  column-span: all;
}
```

<iframe title="Пример с column-span" src="demos/with-span/" height="300"></iframe>

Заголовок «выпал» из общего потока многоколоночного текста. Теперь он растянут на всю ширину, до и после него есть переносы, а параграфы разделились по колонкам так, словно мы задали `column-count` для каждого из них.
