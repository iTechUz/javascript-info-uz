# O'zaro ta'sir: ogohlantirish, tezkorlik, tasdiqlash

Brauzerdan demo muhit sifatida foydalanar ekanmiz, keling, foydalanuvchi bilan muloqot qilish uchun bir nechta funksiyalarni ko‘rib chiqamiz:  `alert`,
 `prompt` va `confirm`.

## Ogohlantirish

Bu biz allaqachon ko'rganmiz. U xabarni ko'rsatadi va foydalanuvchi "OK" tugmasini bosishini kutadi.

Masalan:

```js ishga tushadi
alert("Hello");
```

Xabarli mini oyna *modal oyna* deb ataladi. "Modal" so'zi tashrif buyuruvchi oyna bilan ishlamaguncha sahifaning qolgan qismi bilan o'zaro aloqa qila olmasligini, boshqa tugmalarni bosishini va hokazolarni bildiradi. Bu holda -- ular "OK" tugmasini bosmaguncha.

## taklif

`Prompt` funksiyasi ikkita argumentni qabul qiladi:

```js go'zallashtirmaydi

result = prompt(title, [default]);
```

U matnli xabarga ega modal oynani, tashrif buyuruvchi uchun kiritish maydonini va OK/Bekor qilish tugmalarini ko'rsatadi.
`title`
: tashrif buyuruvchiga ko'rsatiladigan matn.

`default`
: Ixtiyoriy ikkinchi parametr, kiritish maydoni uchun boshlang'ich qiymat.

```smart header="The square brackets in syntax `[...]`"
Yuqoridagi sintaksisdagi `default` atrofidagi kvadrat qavslar parametrning ixtiyoriy ekanligini, shart emasligini bildiradi.
```

Mehmon so'rov kiritish maydoniga biror narsa yozishi va OK tugmasini bosishi mumkin. Keyin biz ushbu matnni "natija" da olamiz. Yoki ular Bekor qilish yoki `key:Esc` tugmasini bosish orqali kiritishni bekor qilishlari mumkin, keyin biz `natija` sifatida `null` olamiz.

`promit` ga qo'ng'iroq matnni kiritish maydonidan qaytaradi yoki agar kiritish bekor qilingan bo'lsa, `null`.

Masalan:

```js ishga tushadi
let age = prompt('How old are you?', 100);

alert(`You are ${age} years old!`); // You are 100 years old!
```

````warn header="IE-da: har doim `standart`ni taqdim eting"
Ikkinchi parametr ixtiyoriy, lekin agar biz uni taqdim qilmasak, Internet Explorer so'rovga "aniqlanmagan" matnini kiritadi.

Ko'rish uchun ushbu kodni Internet Explorer-da ishga tushiring:

```js ishga tushadi.
let test = prompt("Test");
```

Shunday qilib, so'rovlar IEda yaxshi ko'rinishi uchun har doim ikkinchi argumentni taqdim etishni tavsiya qilamiz:

```js ishga tushadi
let test = prompt("Test", ''); // <-- for IE
```
````

## confirm

Sintaksis:

```js
result = confirm(question);
```

"Tasdiqlash" funksiyasi "savol" va ikkita tugmachali modal oynani ko'rsatadi: OK va Bekor qilish.


Natija OK bosilsa "to'g'ri", aks holda "noto'g'ri" bo'ladi.

misol uchun:

```js run
let isBoss = confirm("Are you the boss?");

alert( isBoss ); // OK bosilsa rost
```

## Xulosa

Biz tashrif buyuruvchilar bilan muloqot qilish uchun 3 ta brauzer funksiyasini ko‘rib chiqdik:

`alert`
: xabarni ko'rsatadi.

`prompt`

: foydalanuvchidan matn kiritishni soʻragan xabarni koʻrsatadi. U matnni qaytaradi yoki Bekor qilish tugmasi yoki `key:Esc` bosilsa,
 `null`.

`confirm`

: xabarni ko'rsatadi va foydalanuvchi "OK" yoki "Bekor qilish" tugmasini bosishini kutadi. OK uchun “true”, “Bekor qilish” uchun “noto‘g‘ri” qiymatini qaytaradi/
`key:Esc`.

Bu usullarning barchasi modaldir: ular skriptning bajarilishini to'xtatib turadi va tashrif buyuruvchiga oyna o'chirilmaguncha sahifaning qolgan qismi bilan o'zaro aloqa qilishiga ruxsat bermaydi.

Yuqoridagi barcha usullar bilan birgalikda ikkita cheklov mavjud:

1. Modal oynaning aniq joylashuvi brauzer tomonidan aniqlanadi. Odatda, u markazda joylashgan.
2. Oynaning aniq ko'rinishi brauzerga ham bog'liq. Biz uni o'zgartira olmaymiz.

Bu oddiylik uchun narx. Chiroyli derazalar va tashrif buyuruvchi bilan yanada boy muloqot qilishning boshqa usullari mavjud, ammo agar "qo'ng'iroq va hushtak" unchalik muhim bo'lmasa, bu usullar juda yaxshi ishlaydi.