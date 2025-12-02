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
    присвоєння — =  
    порівняння — == / ===
    арифметичні — + - * / %  
    логічні — && || !  
    бітові — &, |, ^

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

---

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

---

## Верстка

53. **Що таке блокова модель CSS?**  
    Кожен елемент — прямокутник, що складається з content, padding, border, margin.

54. **Способи центрування блокового контенту по горизонталі та вертикалі**  
    Горизонтально: `margin: 0 auto`, flex `justify-content: center`.  
    Вертикально: flex `align-items: center`, grid `place-items: center`.

55. **Підходи у верстці**  
    Float, Flexbox, CSS Grid, inline-block, позиціонування (absolute, relative, fixed).

56. **Як зробити додаток responsive?**  
    Media queries, flex/grid, відсоткові ширини, viewport units, max-width.

57. **Принципи семантичної верстки**  
    Використання тегів за призначенням (`<header>`, `<article>`, `<footer>`), доступність, SEO.

58. **Навіщо потрібні префікси для CSS-властивостей (-webkit-, -moz-)**  
    Для сумісності зі старими браузерами, що підтримують властивості нестандартно.

59. **Як спростити написання кросбраузерних стилів?**  
    Використовувати Autoprefixer, normalize.css, CSS reset.

60. **Практичне завдання: прокоментувати та виправити поганий CSS/HTML**  
    Використовувати семантичні теги, прибрати !important, уникати fixed px, застосувати flex/grid для розташування.

61. **Що таке CSS-препроцесори?**  
    Sass, LESS, Stylus — додають змінні, міксіни, вкладення, функції для спрощення коду.

---

## Angular

62. **Основні компоненти фреймворку**  
    Module, Component, Directive, Service, Pipe, Route.

63. **Компонент vs Директива**  
    Компонент — UI + логіка. Директива — поведінка елемента або DOM.

64. **Життєвий цикл компонента**  
    Створення → Ініціалізація → Оновлення → Знищення.

65. **Часто використовувані хуки життєвого циклу компонента**  
    ngOnInit, ngOnChanges, ngDoCheck, ngAfterViewInit, ngOnDestroy.

66. **Конструктор vs ngOnInit**  
    Конструктор — ініціалізація залежностей. ngOnInit — логіка після створення компоненту.

67. **Як захистити роут від несанкціонованого доступу**  
    Route guards (`CanActivate`, `CanLoad`), AuthService.

68. **Що таке Lazy loading і для чого використовується**  
    Завантаження модулів тільки при необхідності для економії ресурсів.

69. **Призначення RouterOutlet**  
    Місце для рендерингу компонентів маршруту.

70. **Як компоненти можуть взаємодіяти один з одним**  
    Input/Output, EventEmitter, сервіси для спільного стану.

71. **Як створити two-way binding властивість для компонента**  
    Синтаксис `[()]` — `<input [(ngModel)]="property">`.

72. **Типи форм у фреймворку**  
    Template-driven (NgForm), Reactive (FormGroup/FormControl).

73. **Які стани є у форми**  
    valid/invalid, touched/untouched, dirty/pristine, pending.

74. **Навіщо потрібні сервіси і як з ними працювати**  
    Інкапсулюють логіку та стан, використовуються через Dependency Injection.

75. **Що таке singleton-сервіси**  
    Єдиний екземпляр на весь додаток, забезпечують спільний стан.

76. **Способи оголошення сервісів**  
    `providedIn: 'root'`, providers у модулі або компоненті.

77. **Для чого потрібні модулі**  
    Організація коду; кількість залежить від проєкту. Core, Shared, Feature.

78. **Навіщо потрібні shared модулі**  
    Для повторно використовуваних компонентів, директив, пайпів.

79. **Переваги типізації в TypeScript**  
    Безпечний код, автодоповнення, перевірка помилок під час компіляції.

80. **Можливості TypeScript для типізації**  
    Interfaces, Types, Enums, Generics, Tuple.

81. **Інтерфейс vs Клас**  
    Інтерфейс описує форму даних, клас — реалізацію.

82. **Інтерфейс vs Абстрактний клас**  
    Інтерфейс — лише сигнатури, абстрактний клас — часткова реалізація.

83. **Інтерфейс vs Тип (type)**  
    type можна комбінувати, об’єднувати; interface — розширювати.

84. **Що таке RxJS і як використовується у Angular**  
    Observables для HTTP, forms, event streams; інтегрується з async pipe та HttpClient.

85. **Observable vs Promise**  
    Observable — багато значень, lazy; Promise — одне значення, eager.

86. **Для чого потрібні Subjects і які їх типи**  
    Subjects — multicasting Observables. Типи: Subject, BehaviorSubject, ReplaySubject, AsyncSubject.

87. **Кілька послідовних запитів до API через RxJS**  
    Використання pipe + switchMap/concatMap/mergeMap.

88. **switchMap, concatMap, mergeMap**  
    switchMap — скасовує попередній, concatMap — послідовно, mergeMap — паралельно.

89. **Як конфігурувати Angular-застосунок**  
    angular.json, environment.ts, імпорт модулів, providers.

90. **Навіщо потрібні environment-файли**  
    Різні середовища (dev, prod); не для секретних ключів.

91. **Smart vs Dumb компоненти**  
    Smart — логіка, state; Dumb — презентація, отримує дані через Input.

92. **NgForm, FormGroup, FormControl**  
    NgForm — template-driven; FormGroup/FormControl — reactive.

93. **Навіщо потрібен async pipe**  
    Автоматично підписується на Observable і відписується.

94. **Як стежити за розвитком Angular**  
    Оф. документація, GitHub, блоги; Misko Hevery.

---

## React

95. **Класові компоненти**  
    Мають state та lifecycle methods. `class MyComp extends React.Component {}`

96. **Що зберігати в state, а що передавати через props**  
    State — локальний стан компонента. Props — дані від батьків.

97. **Хуки**  
    useState, useEffect, useMemo, useCallback; зручні для функціональних компонентів.

98. **Фрагменти та портали**  
    Fragments `<></>` — без дод. DOM елемента. Portals — рендер у інший DOM вузол.

99. **Refs**  
    Доступ до DOM елемента або збереження mutable значень.

100. **Методи життєвого циклу компонента**  
    componentDidMount, componentDidUpdate, componentWillUnmount.

101. **У якому методі робити запити на сервер**  
    componentDidMount — після рендеру.

102. **Підписка та відписка від listener**  
    useEffect або componentWillUnmount; відписка потрібна для уникнення memory leaks.

103. **Досвід роботи з Context**  
    Глобальний стан, коли props drilling незручний.

104. **Особливість PureComponent**  
    Оптимізація рендерингу через shallow comparison props/state.

105. **Мемоізовані селектори**  
    useMemo, reselect; кешують обчислення для оптимізації.

106. **Переваги React**  
    Компонентна архітектура, Virtual DOM, простота інтеграції.

107. **Чому React швидкий**  
    Virtual DOM мінімізує реальні маніпуляції з DOM.

108. **Навіщо ключі у списках**  
    Для відслідковування елементів. Індекси допустимі тільки для статичних списків.

109. **Основна ідея Redux**  
    Центральний store, unidirectional data flow, predictability.

110. **Робота зі стилями в React**  
    CSS Modules, styled-components, inline styles, SASS/LESS.

111. **React: бібліотека чи фреймворк**  
    React — бібліотека UI, не повний фреймворк.

112. **jQuery + React**  
    Можна, але небажано через прямі маніпуляції DOM.

113. **Codemod**  
    Скрипти для автоматичного рефакторингу коду React.

114. **Налаштування проєкту з нуля**  
    Create React App, Vite, Webpack, Babel.

115. **Бібліотеки у зв’язці з React**  
    React Router, Redux, Recoil, Axios, Styled-components, Material-UI.

116. **Найскладніше реалізувати у React**  
    Оптимізація рендерингу, складна логіка форм та state management.

---