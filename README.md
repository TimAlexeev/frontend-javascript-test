Тестовое задание на позицию Frontender
======================================

Напутствие к тестовому заданию. При решении задания нельзя использовать готовые фреймворки и компоненты. Нас интересует как вы умеет решать подобные задачи и создавать что-то с нуля.

Fuzbuz задачи
=============

Задача №1
----------
Написать функцию dscount, которая подсчитывает количество идущих подряд символов s1 и s2 в строке, без учёта регистра.
Функция должна пройти следующие тесты, как минимум:

```
    "use strict";
    console.clear();
    
    (w => {
        // Yor code here ...
        Ваш код реализации функции dscount
        // ... //
    
    
        // Для удобства можно использовать эти тесты:
        try {
            test(dscount, ['ab___ab__', 'a', 'b'], 2);
            test(dscount, ['___cd____', 'c', 'd'], 1);
            test(dscount, ['de_______', 'd', 'e'], 1);
            test(dscount, ['12_12__12', '1', '2'], 3);
            test(dscount, ['_ba______', 'a', 'b'], 0);
            test(dscount, ['_a__b____', 'a', 'b'], 0);
            test(dscount, ['-ab-аb-ab', 'a', 'b'], 2);
    
            console.info("Congratulations! All tests success passed.");
        } catch(e) {
            console.error(e);
        }
    
        // Простая функция тестирования
        function test(call, args, count, n) {
            let r = (call.apply(n, args) === count);
            console.assert(r, `Finded items count: ${count}`);
            if (!r) throw "Test failed!";
        }
    
        return '--- End ---';
    })(window);
```

Данный код работает в последних версиях Google Chrome и Chromium.
Если вы будете пользоваться другим браузером (что не запрещено) для прогона или Nodejs, то вы сами решаете как организорвать тесты.
Нас интересует, в первую очередь, сам код функции.



Задача №2
----------


Практические задачи
===================

Задача №1
----------

Необходимо разработать javascript-компонент для сортировки таблиц с данными.

Функционал
----------
- Сортировка по столбцам: при нажатии на название столбца строки таблицы сортируются по возрастанию, при повторном клике - по убыванию. Графическим элементом или текстовым сообщением указывается направление сортировки.
- Клиентская пагинация: данные необходимо отображать постранично, максимум 50 элементов на страницу. Необходимо предоставить пользовательскую навигацию для перехода по страницам.
- Фильтрация: компонент предоставляет текстовое поле, в которое пользователь может ввести текст и строки таблицы, данные которых не содержат подстроку, введённую пользователем, скрываются. Перефильтрация осуществляется по нажатию на кнопку Найти.
- По клике на строку таблицы значения полей выводятся в дополнительном блоке под таблицей.
- Данные в таблицу загружаются с сервера. Способ загрузки с сервера на ваш выбор.

Для демонстрации работы компонента необходимо сделать простую HTML страницу.
Пользователю предлагается выбрать набор данных: маленький или большой.
При выборе набора данных он загружается с сервера и по данным строится таблица.

Формат данных от сервера
------------------------

Сервер возвращает JSON-массив данных.
Пример данных: 
```
[
	{
		id: 101,
		firstName: "Sue",
		lastName: "Corson",
		email: "DWhalley@in.gov",
		phone: "(612)211-6296",
		adress: {
			streetAddress: "9792 Mattis Ct",
			city: "Waukesha",
			state: "WI",
			zip: "22178"
		},
		description: "et lacus magna dolor..."
	}
}
```

Маленький объем данных берется по ссылке
http://www.filltext.com/?rows=32&id={number|1000}&firstName={firstName}&lastName={lastName}&email={email}&phone={phone|(xxx)xxx-xx-xx}&adress={addressObject}&description={lorem|32}

Большой объем данных берется по ссылке
http://www.filltext.com/?rows=1000&id={number|1000}&firstName={firstName}&delay=3&lastName={lastName}&email={email}&phone={phone|(xxx)xxx-xx-xx}&adress={addressObject}&description={lorem|32}

Замечания
---------
- Особое внимание следует уделить скорости работы. Зависание интерфейса при выполнении операций загрузки данных, фильтрации, сортировки недопустимо.
- Во время загрузки данных стоит показать какой-то идикатор
- Разрешённые библиотеки: jQuery, Lodash/Underscore, Backbone, самописный. Но вам придется объяснить выбор и причину использования. Использование сторонних библиотек будет плюсом только в случае если это оправданно и вы сможете объяснить причину выбора. Показав свои знания в грамотном применении сторонних готовых решений, вы имеете шанс повысить свою профессиональную привлекательность для нас.
- Пишите код так, как бы вы его писали в работе - внутренности задания будут оцениваться даже тщательней, чем внешнее соответствие заданию. Код должен быть организован так, чтобы его можно было заново использовать.
- Помните про обработку ошибок!
- Верстка может быть самая простая. Визуализацию и украшение делаете на ваш вкус. Мы не против использования  http://getbootstrap.com/ или похожего UI фреймворк, но только для UI представления (нельзя использовать JS код для решения залачи, но можно использовать доля оформительских эффектов(анимации и тому подобное))!

Дполнительным Плюсом будет:
- Использование TypeScript или ES6+(babel).

### Схема визуального представления данных

```
+------+------------+-----------------+-----------------+---------------+
| id ▲ | firstName ▼| lastName      ▼ | email          ▼| phone        ▼|
+------+------------+-----------------+-----------------+---------------+
| 101  | Sue        | Corson          | DWhalley@in.gov | (612)211-6296 |
+------+------------+-----------------+-----------------+---------------+
| 102  | Lor        | Ipsumd          | dwhalley@in.gov | (612)211-6296 |
+------+------------+-----------------+-----------------+---------------+
| 103  | Ips        | Umdolo          | dwhalley@in.gov | (612)211-6296 |
+------+------------+-----------------+-----------------+---------------+
```

Если выбран пользователем с id = 101 , то под таблицей выводим следующую информацию:

```
Выбран пользователь <b>Sue Corson</b>
Описание:
<textarea>
et lacus magna dolor...
</textarea>
Адрес проживания: <b>9792 Mattis Ct</b>
Город: <b>Waukesha</b>
Провинция/штат: <b>WI</b>
Индекс: <b>22178</b>
```

Дополнительно напишите нам, как вы тестировали результат своей работы. Какие используете инструменты и как вы осуществляете тестирование.

Результат выполнения задания нужно будет оформить здесь же, на гитхабе.
В качестве ответа не нужно присылать никаких(!) ZIP архивов и наборов файлов. Все ваши ответы должны быть оформлены на https://github.com/ .
Вы присылаете только ссылку на ваш репозиторий. У нас в компании применяется GIT, и если вы его не знаете, вам стоит освоить базу самостоятельно.
Если у вас еще нет аккаунта, то это хороший повод его завести.

Если есть вопросы, вы всегда их можете задать, связавшись с человеком, который выдал вам задание.
