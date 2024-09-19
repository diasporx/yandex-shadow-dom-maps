# yandex-shadow-dom-maps
Этот репозиторий содержит пример интеграции Yandex Maps API в Shadow DOM для веб-компонентов. Включает инструкции по настройке, рендерингу карты, добавлению маркеров и работе с событиями внутри Shadow DOM.

## Проблемы с интеграцией

При использовании Yandex Maps API внутри компонента с **Shadow DOM** возникают проблемы с областью видимости `window`, что приводит к некорректной работе меток на карте и других компонентов Yandex Maps.

### Решение через iframe (Без надписей маркеров)

Для fix этих багов, карта создается и инициализируется внутри **iframe**. Однако, при таком подходе возникают проблемы с отображением текста для маркеров.
[(Как описано в статье)](https://medium.com/@dagot32167/%D1%81%D0%BF%D0%BE%D1%81%D0%BE%D0%B1-%D1%80%D0%B0%D0%B7%D0%BC%D0%B5%D1%81%D1%82%D0%B8%D1%82%D1%8C-%D1%8F%D0%BD%D0%B4%D0%B5%D0%BA%D1%81-%D0%BA%D0%B0%D1%80%D1%82%D1%83-%D0%B2-shadowdom-ba84a84da037)

### Решение через iframe (С надписями на маркерах)

Если вы хотите, чтобы у вас был Shadow DOM, и карта Яндекс работала корректно, существует решение — создать iframe, внутри которого будет код инициализации карты. Это позволяет обойти проблемы с областью видимости window и корректно отображать карту и её элементы, включая метки.

Вы можете ознакомиться с примером на моем jsfiddle, где показано, как это реализовано:

**[Мой пример на jsfiddle](https://jsfiddle.net/diasporx/fLoz8jpx/123/)**

![изображение](https://github.com/user-attachments/assets/e1b79dbe-c169-40d7-b1ab-466be6ed3352)

Такой подход гарантирует, что карта будет корректно отображаться и реагировать на события, сохраняя преимущества Shadow DOM.
