---
title: GlobalEventHandlers.onerror
slug: Web/API/Window/error_event
tags:
  - API
  - HTML DOM
  - Свойство
  - Ссылка
translation_of: Web/API/GlobalEventHandlers/onerror
original_slug: Web/API/GlobalEventHandlers/onerror
---
{{ ApiRef("HTML DOM") }}

Обработчик события для ошибок среды Javascript.

Обратите внимание, что некоторые/многие `error` не вызывают `window.onerror`, вы должны слушать их специально.

## Синтаксис

```
window.onerror = funcRef;
```

### Параметры

- `funcRef` ссылка на функцию. Когда функция возвращает `true`, блокируется вызов обработчика события по умолчанию. Параметры функции:

  - Сообщение ошибки (string)
  - Url, где произошла ошибка (string)
  - Номер строки, где произошла ошибка (number)
  - Номер столбца для строки, в которой произошла ошибка (number) {{gecko_minversion_inline("31.0")}}
  - [Error Object](/ru/docs/Web/JavaScript/Reference/Global_Objects/Error) (object) {{gecko_minversion_inline("31.0")}}

## Примеры

```js
// Пример 1:

// Предотвращает диалоги об ошибках, отображает какая это функция окна, это нормальное
// поведение - путём переопределения обработчика событий по умолчанию для событий об ошибках, которые
// переходят окну.
window.onerror = null;

// Пример 2:

var gOldOnError = window.onerror;
// Переопределить прошлый обработчик события.
window.onerror = function myErrorHandler(errorMsg, url, lineNumber) {
  if (gOldOnError)
    // Вызвать прошлый обработчик события.
    return gOldOnError(errorMsg, url, lineNumber);

  // Просто запустить обработчик события по умолчанию.
  return false;
}
```

## Примечания

Событие возникает, когда происходит ошибка в скрипте.

При использовании строчной HTML-разметки (\<body onerror="alert('an error occurred')>...), аргументы не именуются. Они могут быть доступны через arguments от `{{ mediawiki.external(0) }}` до `{{ mediawiki.external(2) }}`.

Здесь недоступен `Components.stack.caller для использования`. (Смотрите [**bug 355430**](https://bugzilla.mozilla.org/show_bug.cgi?id=355430).)

## Спецификации

[JavaScript 1.1](http://devedge-temp.mozilla.org/library/manuals/2000/javascript/1.3/reference/handlers.html#1120097)
