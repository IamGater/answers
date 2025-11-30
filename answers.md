# Junior JavaScript Interview Questions — Answers

## Загальні

1. **Які методи HTTP-запитів ви знаєте?**  
   GET, POST, PUT, PATCH, DELETE, OPTIONS, HEAD.

2. **Які версії HTTP-протоколу вам відомі?**  
   HTTP/1.0, HTTP/1.1, HTTP/2, HTTP/3.

3. **Які знаєте коди відповіді HTTP?**  
   1xx — інформаційні,  
   2xx — успішні (200, 201),  
   3xx — редиректи (301, 302),  
   4xx — помилки клієнта (400, 401, 404),  
   5xx — помилки сервера (500, 503).

4. **Що таке CORS? Як усунути проблеми з CORS?**  
   Механізм безпеки, що блокує запити з інших доменів.  
   Вирішення: налаштувати `Access-Control-Allow-Origin`, `Access-Control-Allow-Methods`, `Access-Control-Allow-Headers` на сервері.

5. **Що таке cookie?**  
   Невеликі дані, що зберігаються у браузері (сесія, авторизація, налаштування).

6. **Максимальний розмір cookie?**  
   Близько **4 KB** на один cookie.

7. **Що означає директива `use strict`?**  
   Вмикає строгий режим — забороняє небезпечні конструкції.

8. **Чим JS відрізняється на front-end і back-end?**  
   Front-end — працює у браузері, має DOM.  
   Back-end — Node.js, має доступ до файлової системи, процесів, мережі.

9. **Статична і динамічна типізації**  
   Статична — типи визначаються компілятором.  
   Динамічна — тип визначається під час виконання (JS).

10. **Як клієнт взаємодіє із сервером?**  
    Через HTTP-запити: запит → відповідь.

11. **Що таке REST?**  
    Архітектурний стиль побудови API: ресурси, методи HTTP, стани відповіді.

12. **Що таке мутабельність / іммутабельність?**  
    Мут. — можна змінювати (objects, arrays).  
    Імут. — не змінюються (number, boolean, string).

13. **Як шукати помилки в коді?**  
    `console.log`, debugger, breakpoints в DevTools.

14. **Відомі люди зі світу JS**  
    Brendan Eich, Douglas Crockford, Ryan Dahl.

---

## JS Core

15. **Типи даних у JS**  
    string, number, bigint, boolean, null, undefined, symbol, object.

16. **Як перевірити, чи об’єкт є масивом?**  
    `Array.isArray(value)`.

17. **Як перевірити, чи число є скінченним?**  
    `Number.isFinite(num)`.

18. **Як перевірити, що змінна рівна NaN?**  
    `Number.isNaN(value)`.

19. **Чим відрізняється поведінка isNaN() та Number.isNaN()?**  
    `isNaN()` — робить приведення типів.  
    `Number.isNaN()` — строгий, без приведення.

20. **Порівняйте var, let, const.**  
    var — функціональна область видимості, hoisting.  
    let — блочна область.  
    const — блочна область, не можна перевизначити.

21. **Що таке область видимості?**  
    Частина коду, де змінна доступна: глобальна, функціональна, блочна.

22. **Що таке деструктуризація?**  
    Витягування значень з масивів/об'єктів у змінні.

23. **Для чого setTimeout і setInterval?**  
    `setTimeout` — виконати після затримки.  
    `setInterval` — виконувати регулярно.

24. **Callbacks vs Promises vs async/await**  
    Callbacks — callback hell.  
    Promises — ланцюжки then.  
    async/await — синхронний вигляд для async.

25. **Чи можна записувати нові властивості в прототипи стандартних класів?**  
    Не рекомендується — може зламати сторонній код.  
    Дозволено лише у контрольованому середовищі.  
    Безпечно: перевіряти `Object.hasOwn()`.

26. **Методи масивів**  
    push, pop, shift, unshift, map, filter, reduce, find, some, every, forEach, includes та ін.

27. **Перебираючі методи масиву**  
    map — створює новий масив;  
    filter — фільтрує;  
    reduce — агрегує;  
    forEach — просто перебір;  
    find — знаходить елемент.

28. **Як працюють оператори?**  
    = — присвоєння  
    == / === — порівняння  
    + - * / % — арифметичні  
    && || ! — логічні  
    &, |, ^ — бітові

29. **Map і Set**  
    Map — пари ключ-значення.  
    Set — унікальні значення.

30. **Глибока та поверхнева копія об’єкта**  
    Shallow: `Object.assign`, `{ ...obj }`.  
    Deep: `structuredClone(obj)`, `JSON.parse(JSON.stringify(obj))`.

---

## Функції

31. **Function declaration vs function expression**  
    Declaration — піднімається (hoisting).  
    Expression — присвоюється змінній.

32. **Анонімна функція**  
    Функція без імені: `() => {}`.

33. **Стрілкові функції**  
    Короткий синтаксис.  
    Не мають свого `this`, `arguments` та `prototype`.

34. **IIFE**  
    Функція, що викликається одразу:  
    `(function(){})();`

35. **Що таке hoisting?**  
    Підняття змінних і функцій на початок області видимості.

36. **Що таке замикання?**  
    Функція запамʼятовує змінні зовнішньої області.

37. **Приклад із setTimeout**
    Код:
    ```js
    let i = 0;
    setTimeout(() => console.log(i), 1000);
    i = 2;
    ```
    Виведе **2**, тому що функція в setTimeout читає значення змінної *на момент виконання*, а не створення.

38. **Рекурсія**
    Функція, що викликає саму себе.
    Приклад:
    ```js
    function factorial(n) {
        if (n === 1) return 1;
        return n * factorial(n - 1);
    }
    ```

39. **this**
    Контекст виконання — те, на що вказує `this` у момент виклику.
    ```js
    const user = {
        name: "Danil",
        sayHi() {
            console.log(this.name);
        }
    };
    ```

40. **Втрата контексту**
    Виникає, коли метод передають як callback:
    ```js
    const obj = {
        num: 5,
        print() {
            console.log(this.num);
        }
    };

    setTimeout(obj.print, 1000); // undefined
    ```
    Вирішення:
    ```js
    setTimeout(obj.print.bind(obj), 1000);
    ```

41. **bind / call / apply**
    ```js
    function greet(a, b) {
        console.log(this.name, a, b);
    }

    const user = { name: "Danil" };

    greet.call(user, 1, 2);   // викликає одразу
    greet.apply(user, [1, 2]); // те саме, але масив аргументів
    const fn = greet.bind(user, 1, 2); // повертає нову функцію
    fn();
    ```

## Front-end

42. **DOM**
    Дерево елементів HTML.
    ```js
    const el = document.querySelector("#box");
    ```

43. **async vs defer**
    ```html
    <script src="a.js" async></script>
    <script src="b.js" defer></script>
    ```
    async — виконується як тільки завантажився  
    defer — після повного парсингу HTML

44. **innerHTML vs innerText**
    ```js
    div.innerHTML = "<b>Bold</b>";
    div.innerText = "<b>Not bold</b>";
    ```

45. **Bubbling**
    Подія іде знизу вверх по DOM.

46. **Зупинити bubbling**
    ```js
    event.stopPropagation();
    ```

47. **Зупинити дефолтну дію**
    ```js
    event.preventDefault();
    ```

48. **this у handler'і**
    ```js
    button.onclick = function() {
        console.log(this); // button
    };
    ```

49. **LocalStorage / SessionStorage**
    ```js
    localStorage.setItem("key", "value");
    localStorage.getItem("key");
    ```

50. **Висота блоку / позиція**
    ```js
    element.offsetHeight;
    element.getBoundingClientRect();
    ```

51. **webpack**
    Бандлер — збирає модулі в один файл.
    Приклад config-а:
    ```js
    module.exports = {
        entry: "./src/index.js",
        output: { filename: "bundle.js" }
    };
    ```

52. **dev vs prod**
    dev — з sourcemaps і без оптимізації  
    prod — мінімізація та tree-shaking  
    ```js
    webpack --mode production
    webpack --mode development
    ```
