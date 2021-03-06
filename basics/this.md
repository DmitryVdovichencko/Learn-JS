# This.

Механизм `this` помогает передать ссылку на объект, что ведет к более чистому коду и простому многократному использованию функций.

### Заблуждения

1. `this` ссылается на себя, т.е.на саму функцию, например для рекурсии.
2. `this` ссылается на область видимости. Область видимости, действительно, объект со свойствами для доступных идентификаторов, но этот объект недоступен в коде напрямую - это часть внутренней реализации движка. Также `this` нельзя использовать, чтобы одна функция получила доступ к внутрениим переменным внутри другой функции.

### На что ссылается this?

Привязка `this` происходит когда функция __выполняется__, а не _объявляется_.

__4 правила привязки this__:

1. Стандартная привязка `this`.

_Применение:_ 

В случае отдельного вызова функции. Общий случай когда остальные правила не работают. В режиме `"use strict"` эта привязка не работает.

_Объект на который указывает `this`_: 

`this` будет указывать на то место, где вызвана функция (в  случае глобальной области видимости - объект `global`)

***


2. Неявная привязка `this`.

_Применение:_ 

Когда функция вызывается в контексте объекта созданного или уже существующего.Сначала функция объявляется а затем в свойство объекта добавляется ссылка на эту функцию.

_Объект на который указывает `this`_: 

`this` будет указывать на тот объект, в контексте которого вызвана функция.

_Замечания:_

* Если имеет место цепочка из двух объектов `this` укажет на последний
* Утеря неявной привязки происходит если: 
1. Несмотря на объявление в объекте, функция будет вызвана в глобальной области видимости. А значит, она будет запрашивать переменные из глобальной области.
2. В случае передачи колбэка функции.

***

3. Явная привязка
С неявной привязкой мы должны менять объект в том плане, что необходимо включить ссылку на саму функцию в объект и использовать это свойство-ссылку на функцию, чтобы привязать this к объекту.
Но что 

_Применение:_ 

Если нам нужно сделать привязку без назначения свойства, ссылающегося на функцию. Для этого есть методы call(..) и apply(..). Вот как они работают. Оба метода принимают параметром объект, который будет использоваться как this. И затем, вызывают эту функцию уже с определенным this.


_Объект на который указывает `this`_: 

`this` будет указывать на тот объект, для которого вызваны методы `call` или `apply`.

_Замечания:_

Не решает проблем с потерей привязки.

***


4. Привязка с помощью конструктора `new`

_Применение:_

В JS конструкторы - это функции, которые вызываются с оператором new перед ними.
Что происходит при вызове конструктора:
1. Из воздуха создается новый объект
2. Вновь созданный объект получает ссылку на `[[Prototype]]`
3. Этот объект привязан к `this` для того вызова функции 
4. До тех пор, пока функция не возвращает свой альтернативный объект, вызов функции с `new` автоматически вернет вновь созданный объект.

## Вносим ясность в `this`

Все функции в JS имеют свойства также как объекты.



