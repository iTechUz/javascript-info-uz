
# Taqqoslashlar

Biz matematikada ko'plab taqqoslashlarni bilamiz.

Javascriptda ular quyidagicha yoziladi:

- Katta/kichik : <code>a &gt; b</code>, <code>a &lt; b</code>.
- Katta/kichik yoki teng: <code>a &gt;= b</code>, <code>a &lt;= b</code>.
- Teng: `a == b`, iltimos ikki tomonlama tenglik belgisiga e'tibor bering `==` tenglik testini bildiradi, bitta bo'lsa `a = b` topshiriqni bildiradi.
- Teng emas: matematika yozuvida bunday <code>&ne;</code>, lekin Javascriptda bunday yoziladi<code>a != b</code>.

Ushbu maqaloda turli xil taqqoslash turlari haqida bilib olamiz, Javascripy ularni qanday qiladi,shu jumladan ularni o'ziga xosliklarini.
Oxirida siz "JavaScript noaniqliklari" bilan bog'liq muammolarni oldini olish uchun yaxshi retsept topasiz.

## Boolean is the result


Barcha taqqoslash operatorlari mantiqiy qiymatni qaytaradi:

- `true` --  "ha", "to'gri" yoki "haqiqat" degan manoni anglatadi.
- `false` --  "yo'q", "noto'g'ri" or "haqiqat emas".

Masalan:

```js run
alert( 2 > 1 );  // true (correct)
alert( 2 == 1 ); // false (wrong)
alert( 2 != 1 ); // true (correct)
```

Taqqoslash natijasi har qanday qiymat kabi o'zgaruvchiga tayinlanishi mumkin:

```js run
let result = 5 > 4; // assign the result of the comparison
alert( result ); // true
```

## String taqqoslash

Satr boshqasidan kattaroq yoki undaymasligini bilish uchun JavaScript "lug'at" yoki "leksikografik" deb ataladigan tartibdan foydalanadi.

Boshqacha qilib aytganda, satrlar harfma-harf taqqoslanadi.

Masalan:

```js run
alert( 'Z' > 'A' ); // true
alert( 'Glow' > 'Glee' ); // true
alert( 'Bee' > 'Be' ); // true
```

Ikki qatorni solishtirish algoritmi oddiy:

1. Ikkala satrning birinchi belgisini solishtiring.
2. Agar birinchi satrning birinchi belgisi boshqa satrdan kattaroq (yoki kichik) bo'lsa, birinchi qator ikkinchisidan kattaroq (yoki kamroq) bo'ladi. Biz tugatdik.
3. Aks holda, agar ikkala satrning birinchi belgilari bir xil bo'lsa, ikkinchi belgilarni bir xil tarzda solishtiring.
4. Ikkala satrning oxirigacha takrorlang.
5. Agar ikkala satr bir xil uzunlikda tugasa, ular tengdir. Aks holda, uzunroq satr kattaroq bo'ladi.

Yuqoridagi birinchi misolda taqqoslash  `'Z' > 'A'` birinchi bosqichda natijaga erishadi.

Ikkinchi taqqoslash  `'Glow'` va `'Glee'` ko'proq qadamlarni talab qiladi, chunki satrlar har bir belgi bilan taqqoslanadi:

1. `G` bilan bir xil bo'ladi `G`.
2. `l` bilan bir xil bo'ladi `l`.
3. `o` kattaroqdir `e`. Bu yerda to'xtang. Birinchi qator kattaroq.

```smart header="Haqiqiy lug'at emas, balki,Unicode tartibi"
Yuqorida keltirilgan taqqoslash algoritmi taxminan lug'atlar yoki telefon kitoblarida qo'llaniladigan algoritmga teng, ammo u mutlaqo bir xil emas.

Misol uchun, masala muhim. Boshharf `"A"` kichik harfga teng emas `"a"`. Qaysi biri kattaroq? Kichik harf `"a"`. Nega? Chunki kichik harf JavaScript ishlatadigan ichki kodlash jadvalida kattaroq indeksga ega (Unicode). 
Buning aniq tafsilotlari va oqibatlariga string bobida qaytamiz<info:string>.
```

## Har xil turlarni taqqoslash

Har xil turdagi qiymatlarni solishtirganda, JavaScript qiymatlarni raqamlarga aylantiradi.

Masalan:

```js run
alert( '2' > 1 ); // true, string '2' becomes a number 2
alert( '01' == 1 ); // true, string '01' becomes a number 1
```

Mantiqiy qiymatlar uchun, `true` bo'ladi `1` va `0`da  `false`ga aylanadi  .

Masalan:

```js run
alert( true == 1 ); // true
alert( false == 0 ); // true
```

````smart header="Qiziqarli natija"
Ehtimol, bir vaqtning o'zida:

- Ikki qiymat teng.
- Ulardan biri `true` mantiqiy va ikinchisi esa `false` mantiqiy.

Masalan:

```js run
let a = 0;
alert( Boolean(a) ); // false

let b = "0";
alert( Boolean(b) ); // true

alert(a == b); // true!
```

JavaScript nuqtai nazaridan, bu natija juda normaldir. Tenglik tekshiruvi qiymatlarni raqamli konvertatsiya yordamida o'zgartiradi (shuning uchun `"0"`ga aylanadi `0`), 
aniq "Mantiqiy" konvertatsiya boshqa qoidalar to'plamidan foydalanadi.
````

## Qattiq tenglik

Muntazam tenglikni tekshirishda `==` muammo bor. U quyidagilardan farq  `0` qila olmaydi `false`:

```js run
alert( 0 == false ); // true
```

Xuddi shu narsa bo'sh satr bilan sodir bo'ladi:

```js run
alert( '' == false ); // true
```

Buning sababi, har xil turdagi operandlar tenglik operatori tomonidan raqamlarga aylantiriladi  `==`. Bo'sh satr, xuddi ga o'xshab  `false`, nolga aylanadi.

`0` Agar biz farq qilmoqchi bo'lsak, nima qilishimiz kerak `false`?

**Qattiq tenglik operatori  `===` turdagi konvertatsiya qilmasdan tenglikni tekshiradi.**

Boshqacha qilib aytganda, agar `a` va `b` har xil turdagi bo'lsa, ularni aylantirishga urinmasdan  `a === b`  `false`ga darhol qaytadi .

Keling, sinab ko'raylik:

```js run
alert( 0 === false ); // false, because the types are different
```

 `!==` ga o'xshash "qat'iy teng bo'lmagan" operator ham mavjud   `!=`.

Qattiq tenglik operatori yozish uchun biroz ko'proq vaqt talab etadi, lekin nima bo'layotganini aniq ko'rsatadi va xatolar uchun kamroq joy qoldiradi.
****
## Null va undefined bilan taqqoslash


Boshqa qiymatlar bilan solishtirganda  `null` yoki intuitiv bo'lmagan `undefined`  xatti-harakatlar mavjud.

Qattiq tenglikni tekshirish uchun `===`
: Bu qiymatlar har xil, chunki ularning har biri har xil turdagi.

    ```js run
    alert( null === undefined ); // false
    ```

For a non-strict check `==`
: There's a special rule. These two are a "sweet couple": they equal each other (in the sense of `==`), but not any other value.

    ```js run
    alert( null == undefined ); // true
    ```

For maths and other comparisons `< > <= >=`
: `null/undefined` are converted to numbers: `null` becomes `0`, while `undefined` becomes `NaN`.

Now let's see some funny things that happen when we apply these rules. And, what's more important, how to not fall into a trap with them.

### Strange result: null vs 0

Let's compare `null` with a zero:

```js run
alert( null > 0 );  // (1) false
alert( null == 0 ); // (2) false
alert( null >= 0 ); // (3) *!*true*/!*
```

Mathematically, that's strange. The last result states that "`null` is greater than or equal to zero", so in one of the comparisons above it must be `true`, but they are both false.

The reason is that an equality check `==` and comparisons `> < >= <=` work differently. Comparisons convert `null` to a number, treating it as `0`. That's why (3) `null >= 0` is true and (1) `null > 0` is false.

On the other hand, the equality check `==` for `undefined` and `null` is defined such that, without any conversions, they equal each other and don't equal anything else. That's why (2) `null == 0` is false.

### An incomparable undefined

The value `undefined` shouldn't be compared to other values:

```js run
alert( undefined > 0 ); // false (1)
alert( undefined < 0 ); // false (2)
alert( undefined == 0 ); // false (3)
```

Why does it dislike zero so much? Always false!

We get these results because:

- Comparisons `(1)` and `(2)` return `false` because `undefined` gets converted to `NaN` and `NaN` is a special numeric value which returns `false` for all comparisons.
- The equality check `(3)` returns `false` because `undefined` only equals `null`, `undefined`, and no other value.

### Avoid problems

Why did we go over these examples? Should we remember these peculiarities all the time? Well, not really. Actually, these tricky things will gradually become familiar over time, but there's a solid way to avoid problems with them:

- Treat any comparison with `undefined/null` except the strict equality `===` with exceptional care.
- Don't use comparisons `>= > < <=` with a variable which may be `null/undefined`, unless you're really sure of what you're doing. If a variable can have these values, check for them separately.

## Summary

- Comparison operators return a boolean value.
- Strings are compared letter-by-letter in the "dictionary" order.
- When values of different types are compared, they get converted to numbers (with the exclusion of a strict equality check).
- The values `null` and `undefined` equal `==` each other and do not equal any other value.
- Be careful when using comparisons like `>` or `<` with variables that can occasionally be `null/undefined`. Checking for `null/undefined` separately is a good idea.