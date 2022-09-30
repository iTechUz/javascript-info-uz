# Code structure

The first thing we'll study is the building blocks of code.

## Statements

Statements are syntax constructs and commands that perform actions.

We've already seen a statement, `alert('Hello, world!')`, which shows the message "Hello, world!".

We can have as many statements in our code as we want. Statements can be separated with a semicolon.

For example, here we split "Hello World" into two alerts:

```js run no-beautify
alert('Hello'); alert('World');
```

Usually, statements are written on separate lines to make the code more readable:

```js run no-beautify
alert('Hello');
alert('World');
```

## Semicolons [#semicolon]

A semicolon may be omitted in most cases when a line break exists.

This would also work:

```js run no-beautify
alert('Hello')
alert('World')
```

Here, JavaScript interprets the line break as an "implicit" semicolon. This is called an [automatic semicolon insertion](https://tc39.github.io/ecma262/#sec-automatic-semicolon-insertion).

**In most cases, a newline implies a semicolon. But "in most cases" does not mean "always"!**

There are cases when a newline does not mean a semicolon. For example:

```js run no-beautify
alert(3 +
1
+ 2);
```

The code outputs `6` because JavaScript does not insert semicolons here. It is intuitively obvious that if the line ends with a plus `"+"`, then it is an "incomplete expression", so a semicolon there would be incorrect. And in this case, that works as intended.

**But there are situations where JavaScript "fails" to assume a semicolon where it is really needed.**

Errors which occur in such cases are quite hard to find and fix.

````smart header="An example of an error"
If you're curious to see a concrete example of such an error, check this code out:

```js run
alert("Hello");

[1, 2].forEach(alert);
```

No need to think about the meaning of the brackets `[]` and `forEach` yet. We'll study them later. For now, just remember the result of running the code: it shows `Hello`, then `1`, then `2`.

Now let's remove the semicolon after the `alert`:

```js run no-beautify
alert("Hello")

[1, 2].forEach(alert);
```

The difference compared to the code above is only one character: the semicolon at the end of the first line is gone.

If we run this code, only the first `Hello` shows (and there's an error, you may need to open the console to see it). There are no numbers any more.

That's because JavaScript does not assume a semicolon before square brackets `[...]`. So, the code in the last example is treated as a single statement.

Here's how the engine sees it:

```js run no-beautify
alert("Hello")[1, 2].forEach(alert);
```

Looks weird, right? Such merging in this case is just wrong. We need to put a semicolon after `alert` for the code to work correctly.

This can happen in other situations also.
````

We recommend putting semicolons between statements even if they are separated by newlines. This rule is widely adopted by the community. Let's note once again -- *it is possible* to leave out semicolons most of the time. But it's safer -- especially for a beginner -- to use them.

## Comments [#code-comments]

As time goes on, programs become more and more complex. It becomes necessary to add *comments* which describe what the code does and why.

Comments can be put into any place of a script. They don't affect its execution because the engine simply ignores them.

**One-line comments start with two forward slash characters `//`.**

The rest of the line is a comment. It may occupy a full line of its own or follow a statement.

Like here:
```js run
// This comment occupies a line of its own
alert('Hello');

alert('World'); // This comment follows the statement
```

**Multiline comments start with a forward slash and an asterisk <code>/&#42;</code> and end with an asterisk and a forward slash <code>&#42;/</code>.**

Like this:

```js run
/* An example with two messages.
This is a multiline comment.
*/
alert('Hello');
alert('World');
```

The content of comments is ignored, so if we put code inside <code>/&#42; ... &#42;/</code>, it won't execute.

Sometimes it can be handy to temporarily disable a part of code:

```js run
/* Commenting out the code
alert('Hello');
*/
alert('World');
```

```smart header="Use hotkeys!"
In most editors, a line of code can be commented out by pressing the `key:Ctrl+/` hotkey for a single-line comment and something like `key:Ctrl+Shift+/` -- for multiline comments (select a piece of code and press the hotkey). For Mac, try `key:Cmd` instead of `key:Ctrl` and `key:Option` instead of `key:Shift`.
```

````warn header="Nested comments are not supported!"
There may not be `/*...*/` inside another `/*...*/`.

Such code will die with an error:

```js run no-beautify
/*
  /* nested comment ?!? */
*/
alert( 'World' );
```
````

Please, don't hesitate to comment your code.

Comments increase the overall code footprint, but that's not a problem at all. There are many tools which minify code before publishing to a production server. They remove comments, so they don't appear in the working scripts. Therefore, comments do not have negative effects on production at all.

Later in the tutorial there will be a chapter <info:code-quality> that also explains how to write better comments.


# Tarjima


# Kod tuzilishi

Biz o'rganadigan birinchi narsa - bu kodning tuzilish bloklari.

## Bayonotlar

Bayonotlar sintaksis tuzilmalari va amallarni bajaradigan buyruqlardir.

Biz allaqachon "Hello, world!" xabarini ko‘rsatadigan  `alert('Hello, world!')` bayonotini ko‘rdik.


Kodimizda biz xohlagancha ko'p bayonotlar bo'lishi mumkin. Bayonotlarni nuqtali vergul bilan ajratish mumkin.

Misol uchun, bu erda biz "Salom dunyo" ni ikkita ogohlantirishga ajratamiz:

```js run no-beautify
alert('Hello'); alert('World');
```


Odatda, kodni yanada o'qilishi uchun bayonotlar alohida satrlarda yoziladi:

```js run no-beautify
alert('Hello');
alert('World');
```

## Nuqtali vergul [#semicolon]


Ko'p hollarda satr uzilishi mavjud bo'lsa, nuqta-vergul qoldirilishi mumkin.


Bu ham ishlaydi:

```js run no-beautify
alert('Hello')
alert('World')
```

Bu erda JavaScript satr uzilishini "noto'g'ri" nuqtali vergul sifatida izohlaydi. Bu [automatic semicolon insertion](https://tc39.github.io/ecma262/#sec-automatic-semicolon-insertion) deb ataladi.

**Eng ko'p qutilar ichida,yangi qatorni nuqtali vergul bildiradi. Lekin "eng ko'p qutilarda"  "har doim" unday ifodalanmaydi!**

Yangi qatorda nuqtali vergulni bildirmaydigan holatlar bor. Masalan:

```js run no-beautify
alert(3 +
1
+ 2);
```

Kod chiqadi `6` chunki JavaScript bu yerga nuqta-vergul qo'ymaydi. Agar chiziq plyus bilan tugasa, intuitiv ravishda aniq `"+"`, keyin bu  "incomplete expression", shuning uchun nuqtali vergul noto'g'ri bo'ladi. Va bu holda, bu maqsadga muvofiq ishlaydi.

**Lekin, JavaScript haqiqatan ham zarur bo'lgan joyda nuqta-vergul qo'yishni "muvaffaqiyatsiz" qiladigan holatlar mavjud.**

Bunday hollarda yuzaga keladigan xatolarni topish va tuzatish juda qiyin.

````smart header="Xatoga misol"

Agar siz bunday xatoning aniq misolini ko'rmoqchi bo'lsangiz, ushbu kodni tekshiring:

```js run
alert("Hello");

[1, 2].forEach(alert);
```

 `[]` va `forEach` haqida o'ylashga hali hojati yo'q . Biz ularni keyin o'rganamiz. Hozir, kodning javobi chiqishini o'ylang: U  `Hello`, keyin `1`, keyin `2`ni ko'rsatadi.

Hozir `alert`dan keyin nuqtali vergulni olib tashlaymiz :

```js run no-beautify
alert("Hello")

[1, 2].forEach(alert);
```

Yuqoridagi kod bilan solishtirsak farqi bitta belgidan iborat: birinchi qatorning oxiridagi nuqta-vergul o'chdi.

Agar biz ushbu kodni ishga tushirsak, faqat birinchi  `Hello` ko'rinadi (va xatolik bor, uni ko'rish uchun konsolni ochishingiz kerak bo'lishi mumkin). Boshqa raqamlar yo'q.

Buning sababi, JavaScript kvadrat qavs oldidan nuqta-vergul qo'ymaydi `[...]`. Shunday qilib, oxirgi misoldagi kod bitta bayonot sifatida ko'rib chiqiladi.

Matorda u qanday ko'rinadi:

```js run no-beautify
alert("Hello")[1, 2].forEach(alert);
```

G'alati ko'rinadi, to'g'rimi? Bu holda bunday birlashish noto'g'ri. Kod to'g'ri ishlashi uchun ogohlantirishdan keyin nuqta-vergul qo'yishimiz kerak.

Bu boshqa holatlarda ham sodir bo'lishi mumkin.
````

Agar ular yangi qatorlar bilan ajratilgan bo'lsa ham, gaplar orasiga nuqta-vergul qo'yishni tavsiya qilamiz. Bu qoida jamiyat tomonidan keng qabul qilingan. Yana bir bor ta'kidlaymiz - ko'pincha nuqtali vergul qo'yish mumkin. Lekin ulardan foydalanish xavfsizroq - ayniqsa yangi boshlanuvchilar uchun.

## Izohlar [#code-comments]

Vaqt o'tishi bilan dasturlar yanada murakkablashadi. Kod nima qilishini va nima uchun ekanligini tavsiflovchi sharhlarni qo'shish kerak bo'ladi.

Sharhlar skriptning istalgan joyiga qo'yilishi mumkin. Ular uning bajarilishiga ta'sir qilmaydi, chunki vosita ularni oddiygina e'tiborsiz qoldiradi.

**Bir qatorli sharhlar ikkita qiyshiq chiziq belgisi bilan boshlanadi  `//`.**

Qatorning qolgan qismi sharhdir. U o'zining to'liq qatorini egallashi yoki bayonotga amal qilishi mumkin.

Bu yerdagi kabi:
```js run
// This comment occupies a line of its own
alert('Hello');

alert('World'); // This comment follows the statement
```

**Ko‘p qatorli izohlar qiyshiq chiziq va yulduzcha bilan boshlanadi <code>/&#42;</code> va yulduzcha va qiyshiq chiziq bilan tugating <code>&#42;/</code>.**

Shunga o'xshash:

```js run
/* An example with two messages.
This is a multiline comment.
*/
alert('Hello');
alert('World');
```

Izohlarning mazmuni e'tiborga olinmaydi, shuning uchun biz kodni ichiga qo'ysak <code>/&#42; ... &#42;/</code>, amalga  oshirilmaydi.

Ba'zan kodning bir qismini vaqtincha o'chirib qo'yish qulay bo'lishi mumkin::

```js run
/* Commenting out the code
alert('Hello');
*/
alert('World');
```

```smart header="Issiq tugmalardan foydalaning!"
Ko'pgina muharrirlarda kod satrini bosish orqali sharhlash mumkin `key:Ctrl+/` bitta qatorli sharh va shunga o'xshash narsalar uchun tezkor tugma`key:Ctrl+Shift+/` -- ko'p qatorli sharhlar uchun (kod qismini tanlang va tezkor tugmani bosing). Mac uchun, harakat qilib ko'ring `key:Cmd` o'rniga `key:Ctrl` va `key:Option` o'rniga `key:Shift`.
```

````warn header="Ichki izohlar qo'llab-quvvatlanmaydi!!"
Bo'lmasligi mumkin `/*...*/` boshqa ichida `/*...*/`.

Bunday kod xato bilan o'ladi:

```js run no-beautify
/*
  /* nested comment ?!? */
*/
alert( 'World' );
```
````

Iltimos, kodingizni sharhlashdan tortinmang.

Sharhlar umumiy kod izini oshiradi, ammo bu umuman muammo emas. Ishlab chiqarish serveriga nashr qilishdan oldin kodni kichiklashtiradigan ko'plab vositalar mavjud. Ular sharhlarni olib tashlashadi, shuning uchun ular ishchi skriptlarda ko'rinmaydi. Shuning uchun sharhlar ishlab chiqarishga umuman salbiy ta'sir ko'rsatmaydi.

Keyinchalik o'quv qo'llanmada bob bo'ladi<info:code-quality> bu shuningdek, qanday qilib yaxshiroq sharh yozishni tushuntiradi.




