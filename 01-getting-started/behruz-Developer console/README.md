# Zamonaviy rejim, "qat'iy foydalaning"

Uzoq vaqt davomida JavaScript moslik muammosisiz rivojlandi. Tilga yangi funksiyalar qo‘shildi, eski funksiya esa o‘zgarmadi.

Bu mavjud kodni hech qachon buzmaslikning foydasiga ega edi. Ammo salbiy tomoni shundaki, JavaScript yaratuvchilari tomonidan qilingan har qanday xato yoki nomukammal qaror tilda abadiy qolib ketgan.

Bu 2009 yilgacha ECMAScript 5 (ES5) paydo bo'lgunga qadar shunday edi. U tilga yangi xususiyatlarni qo'shdi va mavjudlarini o'zgartirdi. Eski kodning ishlashini ta'minlash uchun bunday o'zgartirishlarning aksariyati sukut bo'yicha o'chirilgan. Siz ularni maxsus ko'rsatma bilan faollashtirishingiz kerak: `"use strict"`.

## "qat'iy foydalaning"

Direktiv qatorga o'xshaydi: `"use strict"` yoki `'use strict'`. Agar u skriptning yuqori qismida joylashgan bo'lsa, butun skript "zamonaviy" usulda ishlaydi.

Masalan:

``` js
"qat'iy foydalaning";

// bu kod zamonaviy usulda ishlaydi
...
```

Tez orada biz funksiyalarni (buyruqlarni guruhlash usuli) o'rganamiz shuning uchun funksiya boshida `"use strict"` ni qo'yish mumkinligini oldindan aytib o'tamiz. Buni qilish faqat ushbu funktsiyada qat'iy rejimni yoqadi. Lekin odatda odamlar uni butun skript uchun ishlatishadi.

````warn header="Ushbu qismida \"qattiq foydalanish\" ekanligiga ishonch hosil qiling"
Iltimos, skriptlaringizning yuqori qismida `"use strict"` ekanligiga ishonch hosil qiling, aks holda qattiq rejim yoqilmasligi mumkin.

Bu yerda qattiq rejim yoqilmagan:

js qat`iy emas
ogohlantirish ("ba'zi kod");
// pastdagi "use strict" e'tiborga olinmaydi - u yuqorida bo'lishi kerak

"qat'iy foydalaning";

// qat'iy rejim yoqilmagan


"Qat'iy foydalanish" tepasida faqat sharhlar korinishi mumkin.


warn header=""Qatiy foydalanishni" bekor qilishning iloji yoq
Dvigatelni eski holatiga qaytaradigan no use strict kabi hech qanday korsatma yoq.

Qattiq rejimga kirganimizdan keyin ortga qaytish yoq.
```

## Brauzer konsoli

Kodni ishga tushirish uchun [ishlab chiquvchi konsoli](info:devtools) dan foydalansangiz sukut bo'yicha u qatiy ishlatmasligini unutmang.

Bazan `use strict` farq qilganda, siz notog'ri natijalarga erishasiz.

Xosh aslida konsolda qatiy dan qanday foydalanish kerak?

Birinchidan bir nechta satrlarni kiritish uchun `key:Shift+Enter` tugmalarini bosishga urinib korishingiz mumkin va ustiga `use strict` ni qoyishingiz mumkin masalan:

``` js
"qat'iy foydalanish"; <Yangi qator uchun Shift+Enter>
// ...sizning kodingiz
<Ishga tushirish uchun kiring>
```

U kopgina brauzerlarda yani Firefox va Chrome brauzerlarida ishlaydi.

Agar bunday bolmasa masalan. eski brauzerda qatiy foydalanish ni taminlashning yomon ammo ishonchli usuli mavjud. Uni shunday oramga soling:

``` js
(funktsiya () {
  "qat'iy foydalanish";

  // ...kodingiz shu yerda...
})()
```

## Biz "qat'iy" foydalanishimiz kerakmi?

Savol aniq tuyulishi mumkin ammo unday emas.

Skriptlarni `"use strict"` bilan boshlashni tavsiya qilish mumkin... Lekin nima ajoyib ekanini bilasizmi?

Zamonaviy JavaScript sinflar va modullarni qollab-quvvatlaydi - ilgor til tuzilmalari (biz ularga albatta etib boramiz) ular qatiy foydalanishni avtomatik ravishda yoqadi. Shunday qilib agar biz ulardan foydalansak use strict direktivasini qoshishimiz shart emas.

**Demak, hozircha `"use strict";` skriptlaringizning yuqori qismidagi xush kelibsiz mehmondir. Keyinchalik, kodingiz sinflar va modullarda bo'lganda, uni o'tkazib yuborishingiz mumkin.**

Hozircha biz qatiy foydalanish haqida umumiy malumotga egamiz.

Keyingi boblarda biz til xususiyatlarini organar ekanmiz biz qattiq va eski rejimlar ortasidagi farqni koramiz. Yaxshiyamki ular juda kop emas va ular hayotimizni yaxshilaydi.

Ushbu qollanmadagi barcha misollar agar boshqacha korsatilmagan bolsa (juda kamdan-kam hollarda) qatiy rejimni nazarda tutadi.