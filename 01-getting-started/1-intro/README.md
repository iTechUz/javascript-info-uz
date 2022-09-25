# Javascript bilan tanishish

Javascript haqida maxsus narsalarni ko'rib chiqamiz,bu bilan nimaga erishamiz,va bu bilan boshqa qanday texnologiyalar yaxshi ishlaydi.

# Javascript nima?
JavaScript dastlab sahifani jonlantirish ucun yasalgan.

Bu dastur tili scripts deb atalgan. Ular veb-sahifaning HTML-da to'g'ri yozilishi va sahifa yuklanishi bilan avtomatik ravishda ishga tushishi mumkun bo'lgan bo'lgan.

Skriptlar oddiy matn sifatida taqdim etiladi va bajariladi. Sizga maxsus ishga tushurish uchun komplikatsiya kerak emas.

Bu yo'nalishda,JavaScript boshqa tillardan farq qilaadi.Java.

# Nega bunday ataldi
Javascript yaratilinganda, dastlab boshqa ismga ega bo'lgan: "LiveScript",lekin o'sha vaqtlarda Java juda mashhur edi, shuning uchun ular uni 'javaning ukasi' deb aytishgan.

Lekin u rivojlangani sari, JavaScript to'liq mustaqil til bo'ldi shahsi spestifikatsiyasi bilan ECMAScript, va hozir Java bilan bog'liqlik holati yo'q.


Bugun Javascript faqat brovzerda emas,balki serverlarda ham  yoki [the JavaScript engine] qurilmada ishlidi(https://en.wikipedia.org/wiki/JavaScript_engine).

Brovzerda  "JavaScript virtual machine" nomli dvigiteli bor.

Turli xil dvigitillar tutli xil codenamelariga ega.Misol uchun:
- [V8](https://en.wikipedia.org/wiki/V8_(JavaScript_engine)) -- Chrome, Opera va Edgeda.
- [SpiderMonkey](https://en.wikipedia.org/wiki/SpiderMonkey) -- Firefoxda.
- 
Yuqoridagi shartlarni eslab qolish yaxshidir, chunki ular internetdagi ishlab chiquvchilar maqolalarida qo'llaniladi. Biz ham ulardan foydalanamiz. Misol uchun, agar "X xususiyati V8 tomonidan qo'llab-quvvatlansa", u ehtimol Chrome, Opera va Edge'da ishlaydi.

Dvigatellar murakkab.Lekin asoslari oson.

1. Dvigatel (agar u brauzer bo'lsa, o'rnatilgan) skriptni o'qiydi ("tahlil qiladi").
2. Keyin u skriptni mashina kodiga aylantiradi ("kompilyatsiya qiladi").
3. Va keyin mashina kodi tez ishlaydi.

Dvigatel jarayonning har bir bosqichida optimallashtirishni qo'llaydi. U hatto tuzilgan skriptni ishlayotganini kuzatib boradi, u orqali o'tadigan ma'lumotlarni tahlil qiladi va shu bilimlar asosida mashina kodini yanada optimallashtiradi.

# Brovzerda JavaScript nima qila oladi ?
Zamonaviy JavaScript - bu "xavfsiz" dasturlash tili. U xotira yoki protsessorga past darajadagi kirishni ta'minlamaydi, chunki u dastlab buni talab qilmaydigan brauzerlar uchun yaratilgan.

JavaScript imkoniyatlari jihatdan u ishlayotgan muhitga bogʻliq. Masalan, Node.js JavaScript-ga o'zboshimchalik bilan fayllarni oʻqish/yozish, tarmoq so'rovlarini bajarish va h.k. imkonini beruvchi funksiyalarni qo'llab-quvvatlaydi.

Brovzerda JavaScript veb-sahifani manipulyatsiya qilish, foydalanuvchi va veb-server bilan o'zaro aloqa qilish bilan bog'liq hamma narsani qila oladi.

Misol uchun, brauzerda JavaScript quyidagilarni qila oladi:

Sahifaga yangi HTML qo'shish, mavjud tarkibni o'zgartirish, uslublarni o'zgartirsh.
Foydalanuvchi harakatlariga munosabat bildirish, sichqonchani bosish orqali kursor harakati, tugmachalarni bosish orqali ishga tushirish.

Tarmoq orqali masofaviy serverlarga so'rovlar yuboradi, fayllarni yuklab oladi va yuklanganlar (AJAX va COMET texnologiyalari deb ataladi).
Cookie-fayllarni oladi va o'rnatadi, tashrif buyuruvchiga savollar beradi, xabarlarni ko'rsatadi.
Mijoz tomonidagi ma'lumotlarni eslab qoladi ("mahalliy saqlash").
# Brovzerda JavaScript nima qila olmaydi ?
JavaScript-ning brauzerdagi imkoniyatlari foydalanuvchi xavfsizligini himoya qilish uchun cheklangan. Maqsadi, yomon veb-sahifaning shaxsiy ma'lumotlarga kirishini yoki foydalanuvchi ma'lumotlariga zarar etkazishining oldini olishdir.

Bunday cheklovlarga misollar quyidagilar:

Veb-sahifadagi JavaScript qattiq diskdagi ixtiyoriy fayllarni o'qimasligi/yozmasligi, ularni nusxalashi yoki dasturlarni bajara olmasligi mumkin. UOS funktsiyalariga to'g'ridan-to'g'ri kirish imkoniga ega emas.

Zamonaviy brauzerlar unga fayllar bilan ishlash imkonini beradi, biroq kirish cheklangan va faqat foydalanuvchi muayyan amallarni bajarsa, masalan, faylni brauzer oynasiga “tashlash” yoki uni <input> tegi orqali tanlashda taqdim etiladi.

Kamera/mikrofon va boshqa qurilmalar bilan o'zaro aloqa qilish usullari mavjud, ammo ular foydalanuvchining aniq ruxsatini talab qiladi. Shunday qilib, JavaScript-ni yoqadigan sahifa veb-kamerani yashirincha yoqmasligi, atrofni kuzatmasligi va ma'lumotni NSAga yubormasligi mumkin.

Turli yorliqlar/oynalar odatda bir-biri haqida bilishmaydi. Ba'zan ular, masalan, bir oyna ikkinchisini ochish uchun JavaScript-dan foydalansa. Ammo bu holatda ham, bir sahifadagi JavaScript boshqa saytlardan (boshqa domen, protokol yoki portdan) kelgan bo'lsa, boshqa sahifaga kira olmasligi mumkin.

Bu "Bir xil kelib chiqish siyosati" deb ataladi. Buni hal qilish uchun ikkala sahifa ham ma'lumotlar almashinuviga rozi bo'lishi va uni boshqaradigan maxsus JavaScript kodini o'z ichiga olishi kerak. Biz buni o'quv qo'llanmasida ko'rib chiqamiz.

TBu cheklov, yana, foydalanuvchi xavfsizligi uchun. Foydalanuvchi ochgan http://anysite.com sahifasi, masalan, http://gmail.com URL manzili bilan boshqa brauzer yorlig‘iga kira olmasligi va u yerdan ma’lumotlarni o‘g‘irlamasligi kerak.

JavaScript tarmoq orqali joriy sahifa kelgan server bilan osongina bog'lanishi mumkin. Ammo uning boshqa saytlardan/domenlardan ma'lumotlarni olish qobiliyati zaif. Mumkin bo'lsa-da, bu uzoq tomondan aniq kelishuvni (HTTP sarlavhalarida ifodalangan) talab qiladi. Yana bir bor, bu xavfsizlik chegarasi.

JavaScript brauzerdan tashqarida, masalan, serverda ishlatilsa, bunday cheklovlar mavjud emas. Zamonaviy brauzerlar kengaytirilgan ruxsatnomalarni so'rashi mumkin bo'lgan plaginlar/kengaytmalarga ham ruxsat beradi.

# JavaScript noyob nimq qila oladi ?
JavaScript haqida kamida uchta ajoyib narsa bor:

+ HTML/CSS bilan to'liq integratsiya.
+ Oddiy ishlar oddiygina bajariladi.
+ Barcha asosiy brauzerlar tomonidan qo'llab-quvvatlanadi va sukut bo'yicha yoqilgan.
JavaScript bu uch narsani birlashtirgan yagona brauzer texnologiyasidir.

Bu JavaScript-ni noyob qiladi. Shuning uchun u brauzer interfeyslarini yaratish uchun eng keng tarqalgan vositadir.

Ya'ni, JavaScript serverlar, mobil ilovalar va boshqalarni yaratish uchun ishlatilishi mumkin.

# Tillar JavaScript-ni "ustidan"
JavaScript sintaksisi hammaning ehtiyojlariga mos kelmaydi. Turli odamlar turli xil xususiyatlarni xohlashadi.

Buni kutish mumkin, chunki loyihalar va talablar hamma uchun har xil.

Shunday qilib, yaqinda ko'plab yangi tillar paydo bo'ldi, ular brauzerda ishga tushirilgunga qadar JavaScript-ga ko'chiriladi (o'zgartiriladi).

Zamonaviy vositalar transpilyatsiyani juda tez va shaffof qiladi, aslida ishlab chiquvchilarga boshqa tilda kodlash va uni avtomatik ravishda "qopqoq ostida" aylantirish imkonini beradi.

Bunday tillarga misollar:

CoffeeScript - JavaScript uchun "sintaktik shakar". U qisqaroq sintaksisni taqdim etadi, bu bizga aniqroq va aniqroq kod yozish imkonini beradi. Odatda, Ruby ishlab chiqaruvchilariga yoqadi.
TypeScript murakkab tizimlarni ishlab chiqish va qo'llab-quvvatlashni soddalashtirish uchun "qat'iy ma'lumotlarni yozish" ni qo'shishga qaratilgan. U Microsoft tomonidan ishlab chiqilgan. SHuningdek,Flow ma'lumotlarni yozishni qo'shadi, ammo boshqacha tarzda. Facebook tomonidan ishlab chiqilgan.
Dart mustaqil til bo'lib, u o'z dvigateliga ega bo'lib, u brauzerdan tashqari muhitda (masalan, mobil ilovalar) ishlaydi, lekin JavaScript-ga ham ko'chirilishi mumkin. Google tomonidan ishlab chiqilgan.
Brython JavaScript-ga Python-transpiler bo'lib, JavaScript-ni ishlatmasdan sof Python-da ilovalar yozish imkonini beradi.
Kotlin zamonaviy, ixcham va xavfsiz dasturlash tili bo'lib, u brauzer yoki tugunni nishonga olishi mumkin.
 Albatta, biz ushbu transpilyatsiya qilingan tillardan birini ishlatsak ham, nima qilayotganimizni tushunish uchun JavaScript-ni ham bilishimiz kerak.
# Hisobotlar
JavaScript dastlab faqat brauzer tili sifatida yaratilgan, ammo hozir u ko'plab boshqa muhitlarda ham qo'llaniladi.
Bugungi kunda JavaScript HTML/CSS bilan to'liq integratsiyalashgan eng keng tarqalgan brauzer tili sifatida o'ziga xos mavqega ega.
JavaScript-ga "ko'chiriladigan" va ma'lum xususiyatlarni ta'minlaydigan ko'plab tillar mavjud. JavaScript-ni o'zlashtirgandan so'ng, ularni hech bo'lmaganda qisqacha ko'rib chiqishingiz tavsiya etiladi.