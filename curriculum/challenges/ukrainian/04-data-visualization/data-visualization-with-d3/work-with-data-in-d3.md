---
id: 587d7fa7367417b2b2512bc4
title: Робота з даними в D3
challengeType: 6
forumTopicId: 301497
dashedName: work-with-data-in-d3
---

# --description--

Бібліотека D3 фокусується на підході керування даними. Коли у вас є набір даних, ви можете застосувати методи D3, щоб відобразити його на сторінці. Дані надходять у багатьох форматах, але це завдання використовує простий масив чисел.

Перший крок - це повідомити дані D3. Метод `data()` використовується для виділення елементів DOM, щоб приєднати дані до цих елементів. Набір даних передається як аргумент методу.

Поширений шаблон робочого процесу - це створити новий елемент у документі для кожної частини даних у наборі. D3 має метод `enter()` для цієї мети.

Коли метод `enter()` об'єднується з методом `data()`, то він розглядає вибрані елементи з сторінки та порівнює їх із кількістю елементів даних у наборі. Якщо є менше елементів, ніж елементів даних, то створюються відсутні елементи.

Ось приклад, який вибирає елемент `ul` та створює новий елемент списку, що базується на кількості записів у масиві:

```html
<body>
  <ul></ul>
  <script>
    const dataset = ["a", "b", "c"];
    d3.select("ul").selectAll("li")
      .data(dataset)
      .enter()
      .append("li")
      .text("New item");
  </script>
</body>
```

Вибір елементів, які ще не існують, може здатися вам складним. Цей код розповідає D3, щоб спочатку на сторінці вибрати `ul`. Далі виберіть усі елементи списку, які повертають порожню вибірку. Метод `data()` оглядає набір даних і тричі запускає наступний код, один раз для кожного елемента в масиві. Метод `enter()` не бачить елементи `li` на сторінці, але йому потрібно 3 (один для кожного шматка даних у `dataset`). Нові елементи `li` додаються до `ul` і мають текст `New item`.

# --instructions--

Оберіть вузол `body`, а потім оберіть всі елементи `h2`. Маючи D3 створюєте і додаєте тег `h2` для кожного елемента в масиві `dataset`. Текст у `h2` повинен бути `New Title`. Ваш код повинен використовувати методи `data()` і `enter()`.

# --hints--

Ваш документ має мати 9 елементів `h2`.

```js
assert($('h2').length == 9);
```

Текст у елементах `h2` повинен бути `New Title`. Великі літери та інтервали мають збігатися точно.

```js
assert(
  $('h2')
    .text()
    .match(/New Title/g).length == 9
);
```

Ваш код має використовувати метод `data()`.

```js
assert(code.match(/\.data/g));
```

Ваш код має використовувати метод `enter()`.

```js
assert(code.match(/\.enter/g));
```

# --seed--

## --seed-contents--

```html
<body>
  <script>
    const dataset = [12, 31, 22, 17, 25, 18, 29, 14, 9];

    // Add your code below this line



    // Add your code above this line
  </script>
</body>
```

# --solutions--

```html
<body>
  <script>
    const dataset = [12, 31, 22, 17, 25, 18, 29, 14, 9];

    d3.select("body")
      .selectAll("h2")
      .data(dataset)
      .enter()
      .append("h2")
      .text("New Title")

  </script>
</body>
```