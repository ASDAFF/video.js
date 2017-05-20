# Event Target

## Содержание

* [Общая информация](#overview)
* [on() and addEventListener()](#on-and-addeventlistener)
* [off() and removeEventListener()](#off-and-removeeventlistener)
* [one()](#one)
* [trigger() and dispatchEvent()](#trigger-and-dispatchevent)

## Общая информация

События в video.js настроены таким образом, что они имитируют DOM API, который используется в объекте, но также имеют полезные сокращенные функции с одинаковой функциональностью.

## `on()` и `addEventListener()`

Эта функция используется для добавления прослушивания событий в EventTarget.

```js
var foo = new EventTarget();
var handleBar = function() {
  console.log('bar was triggered');
};

foo.on('bar', handleBar);

// This causes any `event listeners` for the `bar` event to get called
// see {@link EventTarget#trigger} for more information
foo.trigger('bar');
// logs 'bar was triggered'
```

## `off()` и `removeEventListener()`

Эта функция используется для удаления функции прослушивания из EventTarget.

```js
var foo = new EventTarget();
var handleBar = function() {
  console.log('bar was triggered');
};

// adds an `event listener` for the `bar` event
// see {@link EventTarget#on} for more info
foo.on('bar', handleBar);

// runs all `event listeners` for the `bar` event
// see {@link EventTarget#trigger} for more info
foo.trigger('bar');
// logs 'bar was triggered'

foo.off('bar', handleBar);
foo.trigger('bar');
// does nothing
```

## `one()`

Эта функция используется для того, чтобы один прослушиватель событий вызывался только один раз и никогда больше.

Использование `on()` и `off()` для имитации `one()` (не рекомендуется)

```js
var foo = new EventTarget();
var handleBar = function() {
  console.log('bar was triggered');
  // после первого триггера удалить этот обработчик
  foo.off('bar', handleBar);
};

foo.on('bar', handleBar);
foo.trigger('bar');
// logs 'bar was triggered'

foo.trigger('bar');
// ничего не делает
```

Использование `one()`

```js
var foo = new EventTarget();
var handleBar = function() {
  console.log('bar was triggered');
};

// удалено после первого триггера
foo.one('bar', handleBar);
foo.trigger('bar');
// logs 'bar was triggered'

foo.trigger('bar');
// ничего не делает
```

## `trigger()` и `dispatchEvent()`

Эта функция используется для запуска события в EventTarget, которое вызывает запуск всех прослушивателей.

> Примечание: if 'click' is in `EventTarget.allowedEvents_`, trigger will attempt to call the
>       `onClick` function if it exists.

```js
var foo = new EventTarget();
var handleBar = function() {
  console.log('bar was triggered');
};

foo.on('bar', handleBar);
foo.trigger('bar');
// logs 'bar was triggered'

foo.trigger('bar');
// logs 'bar was triggered'

foo.trigger('foo');
// does nothing
```
