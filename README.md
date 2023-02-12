# Arch Linux-ni o'rnatish bo'yicha bosqichma-bosqich qo'llanma

## I. Kirish

Arch Linux nima ekanligini qisqacha tushuntirish: Arch Linux Linux yadrosiga asoslangan bepul va Open Source operatsion tizimdir. Bu doimiy ravishda yangilanadigan distributivdir, ya'ni u doimiy ravishda yangilanadi va foydalanuvchilar eng so'nggi dasturiy ta'minot yangilanishlari va xavfsizlik tuzatishlarini oladi. Arch Linux o'zining soddaligi, moslashuvchanligi va minimalizmi bilan mashhur va o'z tizimini to'liq nazorat qilishni xohlaydigan tajribali Linux foydalanuvchilariga mo'ljallangan.

Qo'llanmaning maqsadi: Ushbu qo'llanmaning maqsadi Arch Linuxni o'rnatish bo'yicha to'liq va bosqichma-bosqich qo'llanmani taqdim etishdir. Ushbu qo'llanma Arch Linux-ga yangi kelgan va uni sinab ko'rmoqchi bo'lgan yangi boshlanuvchilarga, shuningdek Arch Linux-ni o'z tizimlariga o'rnatmoqchi bo'lgan tajribali Linux foydalanuvchilariga yordam berish uchun mo'ljallangan.

Qo'llanma uchun maqsadli auditoriya: Ushbu qo'llanmaning maqsadli auditoriyasi tajriba darajasidan qatiy nazar, Arch Linuxni qanday o'rnatishni o'rganishga qiziqqan har bir kishidir. Qo'llanma Arch Linuxni o'z tizimlariga o'rnatishning oddiy va tushunarli usulini izlayotgan yangi boshlanuvchilar va tajribali Linux foydalanuvchilari uchun javob beradi.

## II. Tizim talablari

Minimal qurilma talablari: Arch Linux-ni muvaffaqiyatli o'rnatish uchun tizimingiz quyidagi minimal qurilma talablariga javob berishi kerak:

* 64 bitli protsessor
* Kamida 512 MB operativ xotira
* Kamida 200 MB bo'sh joyga ega yuklanadigan xotira qurilmasi

Tavsiya etilgan apparat spetsifikatsiyalari: Arch Linux bilan eng yaxshi tajribaga ega boʻlish uchun quyidagi texnik xususiyatlarga ega boʻlish tavsiya etiladi:

* Kamida 2 yadroli zamonaviy 64 bitli protsessor
* Kamida 2 GB operativ xotira
* Kamida 20 Gb bo'sh joyga ega hard disk yoki ssd disk.

Mavjud xotira maydoni: Arch Linux uchun zarur bo'lgan xotira maydoni tizimdan maqsadli foydalanishga va o'rnatiladigan dasturiy ta'minotga bog'liq. Umumiy qoida sifatida, asosiy o'rnatish uchun kamida 20 GB bo'sh joy bo'lishi tavsiya etiladi. Agar siz qo'shimcha dasturlarni o'rnatishni yoki katta hajmdagi fayllarni saqlashni rejalashtirmoqchi bo'lsangiz, sizga ko'proq xotira kerak bo'lishi mumkin.

## III. O'rnatishga tayyorlanish

Arch Linux ISO-ni USB diskiga yozish: Arch Linux-ni o'rnatishdan oldin, Arch Linux ISO bilan yuklanadigan USB diskini yaratishingiz kerak. Buning uchun siz Rufus yoki Etcher kabi vositalardan foydalanishingiz mumkin va yoki linux terminali orqali xam yozishingiz mumkin. Arch Linux ISO-ning so'nggi versiyasini rasmiy Arch Linux veb-saytidan yuklab oling va keyin ISO-ni USB diskiga yozish uchun ushbu vositadan foydalaning.

#### [Arch Linuxni yuklab olish](http://mirror.yandex.ru/archlinux/iso/2023.02.01/)

Havola orqali `.iso` foramatini yuklab oling (tepadan 3 chi)

Arch linuxni linux terminali orqali USB ga yozish

```bash
dd bs=4M if=/home/ismoilovdev/Documents/archlinux-x86_64.iso of=/dev/sdb conv=fsync oflag=direct status=progress
```
bu yerda siz ISO faylga yo'l berasiz masalan `/home/ismoilovdev/Document/archlinux-x86_64.iso`

`of=/dev/sdb` bu yerda mening USB draverim formati sizda boshqacha bo'lishi mumkin buni bilish uchun terminalga root bilan kirib quyidagi buyruqni kiriting> USB drayver kompyuterga ulangan bo'lishi kerak.
```bash
sudo su 
fdisk -l
```
Chiqqan ma'lumotlardan eng pastida USB drayver haqida yozilgan bo'ladi turlari `/dev/sda, /dev/sdb, /dev/sdx` 

#### USB orqali yuklash
Yuklanadigan USB drayverini yaratganingizdan so'ng, kompyuteringizni USB bilan yuklashingiz kerak. Buni amalga oshirish uchun USB drayverini kompyuteringizga joylashtiring va uni qayta ishga tushiring. Kompyuteringizning BIOS yoki UEFI konfiguratsiyasiga qarab, yuklash menyusiga kirish va yuklash qurilmasi sifatida USB drayverini tanlash uchun tugmani (masalan, F12 yoki Esc) bosishingiz kerak bo'ladi.

![alt text](https://www.wimware.com/design/how-to/boot-from-cd-dvd/Boot-options-entry-key.png)

Rasmda keng tarqalgan kompyuter brednlarining boot menuga kirish usullari

Boot menuga kiring va USB ni tanlab enter bosing

#### Internetga ulanish

Sozlaganingizga qarab, Arch Linux o'rnatilishini yakunlash uchun internetga ulanishingiz kerak bo'ladi. O'rnatish jarayonida yangilanishlar yoki paketlarni yuklab olishingiz kerak bo'lsa, bu ayniqsa muhimdir. Internetga ulanish uchun simli internet yoki simli internet bo'lmasa USB kabel bilan telefondan USB Modemni yoqish va yoki  Wi-Fi tarmog'iga ulashingiz mumkin.

## IV. Diskni qismlarga(partition) ajratish

Bo'limlarga(partition) bo'lish tushuntirish: Bo'limga bo'lish - bu qattiq diskni bir nechta bo'limlarga bo'lish jarayoni bo'lib, ularning har biri har xil turdagi ma'lumotlarni saqlash yoki turli xil operatsion tizimlarni o'rnatish uchun ishlatilishi mumkin. Bo'limlarga ajratish Arch Linux-ni o'rnatish jarayonida muhim qadamdir, chunki u tizimning turli qismlariga ma'lum hajmdagi saqlash joyini ajratish imkonini beradi.

#### Turli qismlarga ajratish sxemalari

Zamonaviy tizimlarda ikkita asosiy bo'lim sxemasi qo'llaniladi: MBR (Master Boot Record) va GPT (GUID Partition Table). MBR ikkitadan kattasi bo'lib, to'rtta asosiy yoki uchta asosiy bo'lim va kengaytirilgan qismni qo'llab-quvvatlaydi. Boshqa tomondan, GPT deyarli cheksiz miqdordagi bo'limlarni qo'llab-quvvatlaydi va UEFI-ga asoslangan tizimlar uchun talab qilinadi.

#### Cfdisk yoki fdisk kabi tool yordamida bo'limlarni yaratish

Qattiq diskingizda bo'limlarni yaratish uchun cfdisk yoki fdisk kabi tooldan foydalanishingiz mumkin. Ushbu tollar diskda bo'limlarni yaratish, o'chirish va o'zgartirish imkonini beradi. Bo'limlarni yaratishda kamida ikkita bo'lim yaratish tavsiya etiladi: biri ildiz(root) `/` fayl tizimi uchun, ikkinchisi esa swap uchun. Ildiz bo'limi kamida 20 GB bo'lishi kerak, swap bo'limi esa tizimingizdagi RAM miqdoriga teng yoki undan biroz kattaroq bo'lishi kerak. Cfdisk yoki fdisk dan foydalanganda ehtiyot bo'lish kerak, chunki noto'g'ri bo'limlar o'chirilsa yoki o'zgartirilsa, ma'lumotlaringizga doimiy ravishda zarar etkazishi mumkin.

## V. Bo'limlarni formatlash

#### Formatlash haqida tushuntirish

Formatlash - fayl tizimi tomonidan foydalanish uchun bo'limni tayyorlash jarayoni. Formatlash jarayonida bo'limda ma'lumotlarning qanday saqlanishi va tashkil etilishini aniqlaydigan fayl tizimi yaratiladi.

#### Bo'limlarda fayl tizimini yaratish

Arch Linuxda foydalanish mumkin bo'lgan bir nechta fayl tizimlari mavjud, jumladan ext4, btrfs va xfs. Ildiz bo'limi uchun eng ko'p ishlatiladigan fayl tizimi ext4, btrfs va xfs esa ilg'or foydalanuvchilar uchun mashhur tanlovdir. Bo'limda fayl tizimini yaratish uchun siz quyidagi buyruqdan foydalanishingiz mumkin:

`lsblk` buyru'gi yordamida bo'limlarni ko'ramiz
```bash
$ lsblk
```
Endi esa cfdisk dasturi orqali diskni bo'limlarga bo'lamiz. 

Eslatma: Agar sizda NVME2 SSD bo'lsa sizda `/dev/nvme0n1` bo'ladi HDD yoki SATA bo'lsa sizda `/dev/sda ` bo'ladi
```bash
$ cfdisk --zero /dev/sda
```
Bu yerdan chiqqan bo'limda GPT ni bosib o'tamiz yangi bo'lim ochamiz bunga `512M` berib type ga `EFI sytem` beramiz. EFI tizimi bo'limi `/boot/efi` directorysiga mount qilinishi va hajmi 512 MB bo'lishi kerak.


Linux swap bo'limi tizimni qo'shimcha virtual xotira bilan ta'minlash uchun ishlatiladi, bu sizning operativ xotirangiz cheklangan bo'lsa, ayniqsa muhimdir. Swap bo'limi tizimda jismoniy xotira tugashi bilan foydalaniladi va tizim ishga tushganda u avtomatik ravishda faollashadi.
Swap bo'lim ochamiz Kompyuter RAM ga teng yoki yarmiga teng holda swap ochamiz. Masalan 4GB RAM 4GB swap yoki 2GB swap disklar bo'linayotganda `GB` o'rnga `G` yoziladi typega `Linux Swap` beramiz.

Ext4 Linux fayl tizimining bo'limi operatsion tizimning ishlashi uchun zarur bo'lgan barcha fayllarni o'z ichiga olgan ildiz(root) directoryni saqlash uchun ishlatiladi. Ildiz bo'limi odatda tizimdagi eng katta bo'lim bo'lib, u erda ma'lumotlaringiz va fayllaringizning aksariyati saqlanadi.
Linux fayl tizimi bo'limini bo'lishuchun `ext4` formatda xotira beramiz typega `Linux file system` qo'yamiz. O'zgarishlarni saqlash uchun `Write` bosib `yes` yozib `enter` bosamiz keyin `Quit` bosib chiqib ketamiz.

Bo'limlarni tekshirib Ko'ramiz.

```bash
$ lsblk
```
$ lsblk bilan bo'limlarni ko'razmiz bizda `/dev/sda` ichida `/dev/sda1`,`/dev/sda2`va `/dev/sda3` bo'lishi kerak.

#### /dev/sda1

Bu tizimdagi birinchi xotira qurilmasidagi bo'lim (sda bilan ifodalanadi) va u odatda EFI tizim bo'limi sifatida ishlatiladi. EFI tizim bo'limi - bu tizimni yuklash uchun zarur bo'lgan boot loader va tizim yordam dasturlarini o'z ichiga olgan bo'lim. Ushbu bo'lim odatda `FAT32` fayl tizimi sifatida formatlanadi va odatda xotira qurilmasining boshida joylashgan.

#### /dev/sda2

Bu tizimdagi birinchi xotira qurilmasidagi bo'lim (sda bilan ifodalanadi) va  u Linux swap bo'limi sifatida ishlatiladi. Linux Swap Partition tizimi uchun virtual xotira sifatida ishlatiladi va u tizimda jismoniy xotira (RAM) tugashi bilan foydalaniladi. Ushbu bo'lim odatda xotira qurilmasining oxirida joylashgan bo'lib, u `swap` fayl tizimi sifatida formatlanadi.

#### /dev/sda3

Bu tizimdagi birinchi xotira qurilmasi (sda bilan ifodalangan) bo'limi bo'lib, u ildiz bo'limi sifatida ishlatiladi. Ildiz bo'limi tizimning asosiy bo'limi bo'lib, u operatsion tizimning ishlashi uchun zarur bo'lgan barcha fayllarni o'z ichiga oladi. Ushbu bo'lim odatda `ext4` fayl tizimi sifatida formatlanadi va odatda tizimdagi eng katta bo'lim hisoblanadi. Ildiz bo'limi fayl tizimining ildizi bo'lgan `/` directorysiga o'rnatiladi.

### Bo'limlarni Formatlash

Bo'limlarni formatlash bo'limda fayl tizimini yaratishni o'z ichiga oladi, bu operatsion tizim xotira maydoniga kirishi va undan foydalanishi uchun zarurdir. Fayl tizimi - bu xotira qurilmasidagi ma'lumotlarni tashkil qilish usuli bo'lib, operatsion tizim uchun fayllar va directorylarga kirish va boshqarish uchun tuzilmani ta'minlaydi.

Bo'limlarni formatlashsiz, operatsion tizim xotira maydoniga kira olmaydi va bo'limdagi ma'lumotlar operatsion tizim tushunadigan tarzda tashkil etilmaydi.

Bundan tashqari, bo'limni formatlash siz foydalanmoqchi bo'lgan fayl tizimining turini tanlash imkonini beradi. Turli fayl tizimlari katta fayllarni qo'llab-quvvatlash, oniy tasvirlarni qo'llab-quvvatlash yoki ma'lumotlarni zichlashni qo'llab-quvvatlash kabi turli xil xususiyatlarga ega. Ehtiyojlaringizga mos fayl tizimini tanlab, tizimingizning ishlashi va funksionalligini optimallashtirishingiz mumkin.

#### /dev/sda1 formatlash

/dev/sda1 qismini EFI tizim bo'limi sifatida formatlash uchun siz quyidagi buyruqdan foydalanishingiz mumkin:

```bash
mkfs.fat -F32 /dev/sda1
```
Eslatma: -F32 opsiyasi fayl tizimini FAT32 sifatida belgilash uchun ishlatiladi.

#### /dev/sda2 formatlash

/dev/sda2 qismini Linux swap bo'limi sifatida formatlash uchun siz quyidagi buyruqdan foydalanishingiz mumkin:

```bash
mkswap /dev/sda2
```

#### /dev/sda3 formatlash

/dev/sda3 qismini ext4 Linux fayl tizimi sifatida formatlash uchun quyidagi buyruqdan foydalanishingiz mumkin:

```bash
mkfs.ext4 /dev/sda3
```


### Bo'limlarni ulash mountlash

Bo'limlarni mountlash zarur, chunki qattiq disk diskda ma'lumotlarni o'qish va yozish uchun operatsion tizimga kirish imkoniyatiga ega bo'lishi kerak. Qattiq disk qismlarga bo'linganda, u turli maqsadlarda ishlatilishi mumkin bo'lgan alohida bo'limlarga bo'linadi. Har bir bo'lim alohida disk sifatida ko'rib chiqiladi va unga kirish uchun fayl tizimidagi directoryga mount qilinishi kerak.

Odatda `/` sifatida belgilangan asosiy bo'lim fayl tizimining ildizidir va barcha kerakli tizim fayllari, dasturlari va ma'lumotlarini o'z ichiga oladi. Operatsion tizimni qattiq diskka o'rnatish uchun bo'limlarni formatlash va keyin fayl tizimidagi tegishli directorylarga mountlash kerak.

Masalan, Arch Linuxda /dev/sda3 bo'limi mount qilinayotgan yangi fayl tizimining ildizi bo'lib xizmat qiluvchi /mnt directorysiga mountlanadi. EFI tizim bo'limi bo'lgan /dev/sda1 bo'limi /mnt/boot/EFI directorysiga mountlanadi, bu EFI yuklash fayllari saqlanadigan joydir. Swap bo'limi bo'lgan /dev/sda2 bo'limi yetarli RAM mavjud bo'lmaganda ma'lumotlarni vaqtincha saqlash uchun ishlatiladigan swap fayl tizimiga mountlanadi.

#### /dev/sda1 mountlash
/mnt jildi ichida boot/EFI jildini ochamiz:

```bash
mkdir -p /mnt/boot/EFI
```

Bu buyruq operatsion tizimni yuklash uchun zarur bo'lgan boot loader va boshqa tizim fayllarini saqlash uchun zarur bo'lgan EFI tizimi bo'limi uchun directory yaratadi. `-p` opsiyasi, agar ular allaqachon mavjud bo'lmasa, asosiy directorylarni yaratish uchun ham ishlatiladi.

```bash
mount /dev/sda1 /mnt/boot/EFI
```

Buyrug'i EFI System bo'limini yangi yaratilgan directoryga mountlash uchun ishlatiladi. Bu operatsion tizimga o'rnatish jarayonida va tizim o'rnatilgandan keyin EFI tizimi bo'limidagi saqlash joyiga kirish va undan foydalanish imkonini beradi.

#### /dev/sda2 mountlash

Linux Swap bo'limini mountlash uchun quyidagi buyruqdan foydalaniladi:

```bash
mount /dev/sda2 /mnt
```
Linux Swap bo'limi operatsion tizim tomonidan virtual xotira sifatida ishlatiladi. Tizimda jismoniy xotira (RAM) tugagach, u swap boʻlimidan vaqtincha operativ xotirada saqlanadigan maʼlumotlarni vaqtincha saqlash uchun foydalanishi mumkin.

#### /dev/sda3 mountlash

```bash
mount /dev/sda3 /mnt
```

buyrug'i operatsion tizimning asosiy bo'limi bo'lgan ildiz qismini mountlash uchun ishlatiladi. Ildiz bo'limi butun fayl tizimini, shu jumladan /home, /usr, /var va boshqalar kabi barcha boshqa directorylarni o'z ichiga oladi.