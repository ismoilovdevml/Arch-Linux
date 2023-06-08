<h1 align="center">Arch Linux-ni o'rnatish bo'yicha bosqichma-bosqich qo'llanma</h1>

<p align="center"><a href="https://xinux.uz" target="_blank"><img src="https://github.com/ismoilovdevml/Arch-Linux/blob/master/assets/banner.png"/></a></p>

## I. Kirish

Arch Linux Linux kerneliga asoslangan bepul va Open Source operatsion tizimdir. Bu doimiy ravishda yangilanadigan distributivdir, ya'ni u doimiy ravishda yangilanadi va foydalanuvchilar eng so'nggi dasturiy ta'minot yangilanishlari va xavfsizlik tuzatishlarini oladi. Arch Linux o'zining soddaligi, moslashuvchanligi va minimalizmi bilan mashhur va o'z tizimini to'liq nazorat qilishni xohlaydigan tajribali Linux foydalanuvchilariga mo'ljallangan.

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

`of=/dev/sdb` bu yerda mening USB draverim formati sizda boshqacha bo'lishi mumkin buni bilish uchun terminalga root bilan kirib quyidagi buyruqni kiriting. USB drayver kompyuterga ulangan bo'lishi kerak.
```bash
sudo su 
fdisk -l
```
Chiqqan ma'lumotlardan eng pastida USB drayver haqida yozilgan bo'ladi turlari `/dev/sda, /dev/sdb, /dev/sdx` 

#### USB orqali yuklash
Yuklanadigan USB drayverini yaratganingizdan so'ng, kompyuteringizni USB bilan yuklashingiz kerak. Buni amalga oshirish uchun USB drayverini kompyuteringizga joylashtiring va uni qayta ishga tushiring. Kompyuteringizning BIOS yoki UEFI konfiguratsiyasiga qarab, BOOT menyusiga kirish va yuklash qurilmasi sifatida USB drayverini tanlash uchun tugmani (masalan, F12 yoki Esc) bosishingiz kerak bo'ladi.

![alt text](https://www.wimware.com/design/how-to/boot-from-cd-dvd/Boot-options-entry-key.png)

Rasmda keng tarqalgan kompyuter brednlarining boot menuga kirish usullari

Boot menuga kiring va USB ni tanlab enter bosing

#### Internetga ulanish

Sozlaganingizga qarab, Arch Linux o'rnatilishini yakunlash uchun internetga ulanishingiz kerak bo'ladi. O'rnatish jarayonida yangilanishlar yoki paketlarni yuklab olishingiz kerak bo'lsa, bu ayniqsa muhimdir. Internetga ulanish uchun simli internet yoki simli internet bo'lmasa USB kabel bilan telefondan USB Modemni yoqish va yoki  Wi-Fi tarmog'iga ulashingiz mumkin.

Tarmoqga ulanish

```bash
ip -c a  
iwctl.                     
device list                
station wlan0 get-networks 
station wlan0 connect SSID 
```
* `ip -c a` Bu buyruq barcha tarmoq interfeyslariga tayinlangan IP manzillarni qisqa va o'qish oson formatda ko'rsatadi. `-c` opsiyasi buyruqni ixcham formatda chiqarishni bildiradi.

* `iwctl` Bu Linuxda simsiz tarmoq interfeyslarini sozlash va boshqarish uchun buyruq qatori vositasi. Bu sizga yaqin-atrofdagi simsiz tarmoqlarni skanerlash, tarmoqqa ulanish va simsiz rejimlarni boshqarish kabi turli operatsiyalarni bajarish imkonini beradi.

* `device list` Bu buyruq `iwctl` bilan foydalanilganda tizimdagi barcha mavjud simsiz tarmoq qurilmalari roʻyxatini koʻrsatadi.

* `station wlan0 get-networks ` Ushbu buyruq `iwctl` bilan foydalanilganda, `wlan0` simsiz tarmoq qurilmasi diapazonidagi barcha mavjud simsiz tarmoqlar ro'yxatini ko'rsatadi.

* `station wlan0 connect SSID` Bu buyruq iwctl bilan foydalanilganda, wlan0 simsiz tarmoq qurilmasini SSID nomi bilan simsiz tarmoqqa ulaydi. SSID-ni ulanmoqchi bo'lgan simsiz tarmoqning haqiqiy nomi bilan almashtiring. Ulangandan so'ng, agar u xavfsiz tarmoq bo'lsa, tarmoq uchun xavfsizlik parolini kiritishingiz kerak bo'ladi.

## IV. Diskni qismlarga(partition) ajratish

Bo'limlarga(partition) bo'lish tushuntirish: Bo'limga bo'lish - bu qattiq diskni bir nechta bo'limlarga bo'lish jarayoni bo'lib, ularning har biri har xil turdagi ma'lumotlarni saqlash yoki turli xil operatsion tizimlarni o'rnatish uchun ishlatilishi mumkin. Bo'limlarga ajratish Arch Linux-ni o'rnatish jarayonida muhim qadamdir, chunki u tizimning turli qismlariga ma'lum hajmdagi saqlash joyini ajratish imkonini beradi.

#### Turli qismlarga ajratish sxemalari

Zamonaviy tizimlarda ikkita asosiy bo'lim sxemasi qo'llaniladi: MBR (Master Boot Record) va GPT (GUID Partition Table). MBR ikkitadan kattasi bo'lib, to'rtta asosiy yoki uchta asosiy bo'lim va kengaytirilgan qismni qo'llab-quvvatlaydi. Boshqa tomondan, GPT deyarli cheksiz miqdordagi bo'limlarni qo'llab-quvvatlaydi va UEFI-ga asoslangan tizimlar uchun talab qilinadi.

#### cfdisk yoki fdisk kabi tool yordamida bo'limlarni yaratish

Qattiq diskingizda bo'limlarni yaratish uchun cfdisk yoki fdisk kabi tooldan foydalanishingiz mumkin. Ushbu tollar diskda bo'limlarni yaratish, o'chirish va o'zgartirish imkonini beradi. Bo'limlarni yaratishda kamida ikkita bo'lim yaratish tavsiya etiladi: biri ildiz(root) `/` fayl tizimi uchun, ikkinchisi esa swap uchun. Ildiz bo'limi kamida 20 GB bo'lishi kerak, swap bo'limi esa tizimingizdagi RAM miqdoriga teng yoki undan biroz kattaroq bo'lishi kerak. cfdisk yoki fdisk dan foydalanganda ehtiyot bo'lish kerak, chunki noto'g'ri bo'limlar o'chirilsa yoki o'zgartirilsa, ma'lumotlaringizga doimiy ravishda zarar etkazishi mumkin.

## V. Bo'limlarni formatlash

#### Formatlash haqida tushuntirish

Formatlash - fayl tizimi tomonidan foydalanish uchun bo'limni tayyorlash jarayoni. Formatlash jarayonida bo'limda ma'lumotlarning qanday saqlanishi va tashkil etilishini aniqlaydigan fayl tizimi yaratiladi.

#### Bo'limlarda fayl tizimini yaratish

Arch Linuxda foydalanish mumkin bo'lgan bir nechta fayl tizimlari mavjud, jumladan ext4, btrfs va xfs. Ildiz bo'limi(root partition) uchun eng ko'p ishlatiladigan fayl tizimi ext4, btrfs va xfs esa ilg'or foydalanuvchilar uchun mashhur tanlovdir. Bo'limda fayl tizimini yaratish uchun siz quyidagi buyruqdan foydalanishingiz mumkin:

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

Ext4 Linux fayl tizimining bo'limi operatsion tizimning ishlashi uchun zarur bo'lgan barcha fayllarni o'z ichiga olgan ildiz(root) directoryni saqlash uchun ishlatiladi. Ildiz bo'limi odatda tizimdagi eng katta bo'lim bo'lib, u yerda ma'lumotlaringiz va fayllaringizning aksariyati saqlanadi.
Linux fayl tizimi bo'limini bo'lishuchun `ext4` formatda xotira beramiz typega `Linux file system` qo'yamiz. O'zgarishlarni saqlash uchun `Write` bosib `yes` yozib `enter` bosamiz keyin `Quit` bosib chiqib ketamiz.

Bo'limlarni tekshirib Ko'ramiz.

```bash
$ lsblk
```
$ lsblk bilan bo'limlarni ko'razmiz bizda `/dev/sda` ichida `/dev/sda1`,`/dev/sda2`va `/dev/sda3` bo'lishi kerak.

```bash
NAME    MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINTS
sda       8:0    1 476.9G  0 disk
├─sda1    8:1    1   512M  0 part /mnt/boot/EFI
├─sda2    8:2    1     4G  0 part [SWAP]
└─sda3    8:3    1 459.9G  0 part /mnt
sr0      11:0    1 779.3M  0 rom /run/archiso/bootmnt
```

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
swapon /dev/sda2
```
Linux Swap bo'limi operatsion tizim tomonidan virtual xotira sifatida ishlatiladi. Tizimda jismoniy xotira (RAM) tugagach, u swap boʻlimidan vaqtincha operativ xotirada saqlanadigan maʼlumotlarni vaqtincha saqlash uchun foydalanishi mumkin.

#### /dev/sda3 mountlash

```bash
mount /dev/sda3 /mnt
```

mount /dev/sda3 /mnt buyrug'i operatsion tizimning asosiy bo'limi bo'lgan ildiz qismini mountlash uchun ishlatiladi. Ildiz bo'limi butun fayl tizimini, shu jumladan /home, /usr, /var va boshqalar kabi barcha boshqa directorylarni o'z ichiga oladi.

Mounlash jarayoni tugaganidan keyin l`sblk` buyru'gi bilan teskhirib ko'rsangiz quyidek chiqishi kerak.
```bash
root@archiso ~ # lsblk
NAME    MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINTS
sda       8:0    1 476.9G  0 disk
├─sda1    8:1    1   512M  0 part /mnt/boot/EFI
├─sda2    8:2    1     4G  0 part [SWAP]
└─sda3    8:3    1 459.9G  0 part /mnt
sr0      11:0    1 779.3M  0 rom /run/archiso/bootmnt
```


## VI. Asosiy tizimni o'rnatish

Arch Linux-dagi asosiy tizim funksional operatsion tizimga ega bo'lish uchun zarur bo'lgan minimal komponentlar to'plamini anglatadi. Bunga Linux kerneli, tizim kutubxonalari, asosiy utilitalar va tollari va boot loader kiradi.

Asosiy tizimni o'rnatishda muammolar chiqmasligi uchun archlinux-keyring dasturini o'rnatib olamiz.

```bash
sudo pacman -Sy archlinux-keyring
```
`sudo pacman -Sy archlinux-keyring` - bu tizimingizga Arch Linux kalitlari paketini o'rnatuvchi buyruq.

Arch Linux kalitlari toʻplami Arch Linux repositoriyalaridan oʻrnatilgan paketlarning yaxlitligi va haqiqiyligini tekshirish uchun foydalaniladigan ochiq kalitlar toʻplamidir. Kalitlar paketlar tranzit paytida hech qanday tarzda buzilmagan yoki o'zgartirilmaganligini ta'minlash uchun ishlatiladi.

Asosiy tizimni o'rnatish uchun `pacstrap` buyrug'i ishga tushiriladi. Ushbu buyruq Arch Linux repositoriyalaridan kerakli paketlar va komponentlarni yuklab oladi va o'rnatadi. U quyidagi tarzda amalga oshiriladi:

```bash
 pacstrap /mnt base base-devel linux linux-firmware nano openssh networkmanager netctl
 ```
Yuqoridagi satrdagi `pacstrap` buyrug'i `/mnt` da o'rnatilgan fayl tizimiga asosiy tizim va kerakli paketlarni o'rnatish uchun ishlatiladi. /mnt directorysi asosiy tizimni o'rnatish uchun maqsadli directory sifatida ishlatiladi.

/mnt dan keyin ko'rsatilgan paketlar asosiy tizimning tarkibiy qismlari bo'lib, ular quyidagilarni o'z ichiga oladi:

* `base:` Funksional tizim uchun zarur bo'lgan asosiy paketlar.
* `base-devel:` manbadan boshqa paketlarni yaratish uchun zarur bo'lgan ishlab chiqish paketlari.
* `linux:` Linux kerneli.
* `linux-firmware:` Linux kerneli uchun zarur bo'lgan mikrodastur(firmware) fayllari.
* `nano:` oddiy matn muharriri.
* `openssh:` Tarmoq orqali xavfsiz aloqa uchun foydalaniladigan Secure Shell (SSH) protokolining amalga oshirilishi.
* `networkmanager:` tarmoq ulanishlarini sozlash va boshqarish imkonini beruvchi tarmoq ulanishi menejeri.
* `netctl:` Arch Linux-da tarmoq ulanishlarini sozlash uchun CLI vositasi.
Belgilangan paketlar Arch Linux paketi repositoriyalaridan yuklab olinadi va /mnt fayl tizimiga o'rnatiladi.


Asosiy tizimni o'rnatish tugallangandan so'ng, `fstab` faylini yaratish kerak. fstab fayli yoki fayl tizimi jadvali operatsion tizim tomonidan yuklash vaqtida qaysi fayl tizimlarini o'rnatish kerakligini va ularni qayerga o'rnatish kerakligini aniqlash uchun ishlatiladi. fstab fayli quyidagi buyruq yordamida yaratililadi:

```bash
genfstab -U /mnt >> /mnt/etc/fstab
```
Ushbu buyruq fayl tizimi jadvalini yaratadi va uni yangi o'rnatilgan operatsion tizim uchun fayl tizimi jadvali bo'lgan `/mnt/etc/fstab  `fayliga qo'shadi. fstab faylining to'g'ri ekanligiga ishonch hosil qilish muhim, chunki noto'g'ri fstab fayli operatsion tizimning to'g'ri yuklanishiga xalaqit berishi mumkin.

Nihoyat, arch-chroot buyrug'ini ishga tushirish orqali root directorisini yangi o'rnatilgan tizimingizga o'zgartiring:

```bash
arch-chroot /mnt
```
`arch-chroot /mnt` - bu joriy tizimingizning root directorini /mnt da o'rnatilgan yangi o'rnatilgan Arch Linux tizimingizning root directoriga o'zgartirish imkonini beruvchi buyruq.

Qisqa qilib aytganda, arch-chroot /mnt Arch Linux-ni o'rnatishda muhim buyruqdir, chunki u tizimingizni yangi o'rnatilgan muhitdan sozlashni davom ettirish imkonini beradi.

## VII. Tizimni sozlash

Asosiy tizim o'rnatilgandan so'ng, tizimni sozlash vaqti keldi. Ushbu bo'limda siz vaqt mintaqasini, klaviatura tartibini, root parolini o'rnatish va yangi foydalanuvchi hisobini yaratishni o'rganasiz.

#### Vaqt mintaqasini sozlash

Vaqt mintaqasini o'rnatish vaqt va sana to'g'ri o'rnatilganligini ta'minlash uchun muhimdir. Vaqt mintaqasini belgilash uchun `timedatectl` buyrug'idan foydalanishingiz mumkin.

```bash
hwclock --systohc --utc
```
`hwclock` buyrug'i tizimingizda qurilma soatini o'rnatish uchun ishlatiladi. `--systohc` opsiyasi qurilma soatini joriy tizim vaqtiga o'rnatish uchun ishlatiladi. `--utc` opsiyasi buyruqqa mahalliy vaqt o'rniga Muvofiqlashtirilgan universal vaqtdan (UTC) foydalanishni aytadi.

```bash
ln -sf /usr/share/zoneinfo/Asia/Tashkent /etc/localtime
```

`ln -sf` buyrug'i vaqt mintaqasi fayli `/usr/share/zoneinfo/Asia/Tashkent` va tizim tomonidan mahalliy vaqtni aniqlash uchun foydalaniladigan `/etc/localtime` fayli o'rtasida ramziy bog'lanishni yaratish uchun ishlatiladi. Buni qilish orqali siz tizimingiz uchun vaqt mintaqasini Asia/Tashkentga o'rnatasiz.


Ushbu buyruqlarni birgalikda ishlatish orqali siz qurilma soatini joriy tizim vaqtiga UTCda o'rnatasiz va tizimingiz uchun Asia/Tashkent uchun vaqt mintaqasini belgilaysiz.

#### Klaviatura tilini sozlash

Arch Linux-da klaviatura tartibini o'rnatish uchun `/etc/vconsole.conf` faylini tahrirlashingiz kerak. Masalan, klaviatura tartibini `en_US.UTF-8` ga o'rnatish uchun siz quyidagilarni bajarasiz:

```bash
echo "KEYMAP=en_US.UTF-8" > /etc/vconsole.conf
````
#### OS tilini tanlash va o'rnatish

Operatsion tizim tilini o'rnatish - bu tizimni kerakli tilda matn va xabarlarni ko'rsatish uchun mahalliylashtirish jarayoni.

Yangi tilni o'rnatish uchun paket menejeri yordamida tilni qo'llab-quvvatlash paketlarini o'rnatishingiz kerak. Masalan, Arch Linux-da siz kerakli tilni qo'llab-quvvatlash paketlarini o'rnatish uchun pacman paket menejeridan foydalanishingiz mumkin. Masalan, ingliz tilini qo'llab-quvvatlashni o'rnatish uchun siz quyidagi buyruqni bajarishingiz mumkin:

```bash
sudo pacman -Sy glibc-locales
```

Mahalliy til sozlamalarini belgilarni kodlashni quuyidagi buyruq bilan sozlaymiz

```bash
nano /ect/locale.conf
```
`nano` matnn muharrir orqali `/ext/locale.conf` faylini ochamiz va quyidagi configratsiyani qo'shib qo'yamiz.

```bash
LANG=en_US.UTF-8
```

locale.conf fayli tizimning mahalliy sozlamalarini, jumladan til va belgilar kodlashni aniqlash uchun ishlatiladi. Bunday holda,` LANG=en_US.UTF-8` qatori tizimning standart tilini `UTF-8`(character encoding) belgilar kodlash bilan Amerika ingliz tiliga (en_US) o'rnatadi.

Va nihoyat, `/etc/locale.conf` faylida LANG muhit o'zgaruvchisini o'rnatish orqali tizim tilini o'rnatishingiz mumkin. Buning uchun `nano` matn muraharriri orqali `/etc/locale.conf` faylidan kerakli tilini tanlab izohdan(`#`) chiqarishingiz kerak.

```bash
nano /etc/locale.conf
```

Tanlangan tilni `#` izohdan chiqarganizdan keyin nano matn muhariridan tharirlangan kodni saqlash uchun `ctrl+o` bosiladi va `enter` bosiladi keyin chiqish uchun esa `ctrl+x` bosib chiqib ketamiz. Keyin mahalliy tilni yaratish uchun quyidagi buyruqni bajarishingiz mumkin:

```bash
sudo locale-gen
```
#### Root parolini yaratish

Root parolini va yangi foydalanuvchini yaratish Linux tizimini o'rnatish jarayonida muhim qadamdir. Root hisobi Linux tizimidagi eng yuqori darajadagi imtiyozlarga ega superuser hisobidir. Ushbu hisob tizimda har qanday amalni bajarishi mumkin, jumladan, dasturiy ta'minotni o'rnatish, fayllarni yaratish va o'zgartirish, tizim sozlamalarini sozlash.

Biroq, xavfsizlik nuqtai nazaridan, kundalik vazifalar uchun root hisobidan foydalanish odatda tavsiya etilmaydi. Shuning uchun cheklangan imtiyozlarga ega yangi foydalanuvchi yaratish yaxshi fikrdir. Shunday qilib, siz root hisobiga o'tmasdan kundalik vazifalarni bajarishingiz mumkin, bu tizimda tasodifan biror narsani buzish xavfini kamaytiradi.

Arch linux uchun hostnomini kiritamiz

```bash
echo "kompyuternomi" > /etc/hostname
```

`echo "kompyuternomi" > /etc/hostname` - Arch Linux operatsion tizimida kompyuteringizning xost nomini o'rnatuvchi buyruq. kompyuternomi degani bu shunchaki misol siz xoxlagan nom berishingiz mumkin masalan linux dasturchi yoki komyuter brendlari nomi.

/etc/hostname fayli tizimingizning xost nomini saqlaydigan konfiguratsiya faylidir. Echo buyrug'ini ishga tushirish va chiqishni ushbu faylga yo'naltirish orqali siz tizimingizning xost nomini "kompyuternomi" ga o'rnatasiz.

Arch Linux-da root parolini yaratish uchun passwd buyrug'idan foydalanishingiz kerak. Bu root foydalanuvchi uchun yangi parolni kiritishingizni so'raydi.

```bash
passwd
```

#### Yangi foydalanuvchi yaratish:

Arch Linux-da yangi foydalanuvchi yaratish uchun siz `useradd` va `passwd` buyruqlaridan foydalanishingiz mumkin. useradd uchun sintaksisi: 

Misol uchun, asilbek ismli foydalanuvchi yaratish uchun siz quyidagilarni bajarasiz:

```bash
useradd -m -G wheel asilbek
```

Keyin passwd buyrug'i yordamida yangi foydalanuvchi uchun parol o'rnating:

```bash
passwd asilbek
```
`useradd` buyrug'idagi `-m` opsiyasi yangi foydalanuvchi uchun home directorysini yaratadi va `-G wheel` opsiyasi foydalanuvchini wheel guruhiga qo'shadi, bu esa foydalanuvchiga ma'muriy vazifalarni bajarish imkoniyatini beradi. `passwd` buyrug'i yangi foydalanuvchi uchun parolni o'rnatadi.


#### Sudoers fayli konfiguratsiya faylini sozlash

```bash
EDITOR=nano visudo
```
ushbu buyruqni ishga tushirganizdan keyin sizda nano matn muharririda sudoers konfigratsiya fayli kodlari ochiladi.
Siz ushbu kodlardan quyidagi kod satrlarini topib olasiz.

```shell
root ALL=(ALL) ALL
##Uncomment to allow members of group wheel to execute any command
#%whell ALL=(ALL) ALL
```

shu kod satrni quyidagi kodga o'zgartirasiz ya'ni `#%whell ALL=(ALL) ALL` ni izohdan chiqarasiz

```shell
root ALL=(ALL) ALL
##Uncomment to allow members of group wheel to execute any command
%whell ALL=(ALL) ALL
```

`EDITOR=nano visudo` - bu nano matn muharriri yordamida tahrirlash uchun sudoers faylini ochadigan buyruq.

`%wheel ALL=(ALL) ALL` - bu  wheel groupi a'zolariga sudo imtiyozlarini berish uchun sudoers fayliga qo'shilishi mumkin bo'lgan qator. wheel groupi Linuxda ko'pincha ma'lum foydalanuvchilarga ma'muriy imtiyozlar berish uchun ishlatiladigan maxsus guruhdir.

Sudoers fayli konfiguratsiya fayli bo'lib, u qaysi foydalanuvchilarga sudo bilan imtiyozli buyruqlarni bajarishga ruxsat berilganligini va ularga qanday buyruqlarni bajarishga ruxsat berilganligini aniqlaydi. Odatiy bo'lib, sudoers fayli faqat root foydalanuvchi tomonidan tahrirlanishi mumkin.

`visudo` buyrug'i sudoers faylini tahrirlash uchun ishlatiladi. Bu buyruq bir vaqtning o'zida faqat bitta foydalanuvchi faylni tahrirlashini ta'minlaydi va faylni saqlashdan oldin uning sintaksisini xatolarga tekshiradi. Bu xatolarning oldini olishga yordam beradi va faylning haqiqiy va funktsional bo'lishini ta'minlaydi.

Sudoers fayliga `%wheel ALL=(ALL) ALL` ni qo'shish wheel groupi a'zolariga sudo imtiyozlarini beradi. Bu ikkala harakat ham yuqori imtiyozlarni talab qiluvchi tizim boshqaruvi vazifalari uchun zarur, lekin tizimdagi har bir foydalanuvchi uchun juda xavflidir.

## VIII Bootloader o'rnatish

Bootloader - bu operatsion tizimni xotiraga yuklaydigan va boshqaruvni unga topshiradigan dastur. Bu kompyuter ishga tushganda ishlaydigan birinchi dasturiy ta'minot bo'lib, u operatsion tizimni ishga tushirish va boshqaruvni unga o'tkazish uchun javobgardir.

Arch Linux uchun mashhur bootloader dasturlari orasida GRUB (GRand Unified Bootloader) va Syslinux mavjud. GRUB ko'pgina Linux distributivlari uchun standart bootloader bo'lib, yuklanadigan operatsion tizimni tanlash uchun menyuga asoslangan interfeysni taqdim etadi. Syslinux bu yengil bootloader moslamasi bo'lib, u odatda USB drayvlar kabi olinadigan muhitdan Linux distributivlarini yuklash uchun ishlatiladi.

Arch Linux-da bootloaderni o'rnatish va sozlash uchun quyidagi amallarni bajarish kerak:

Pacman paket menejeri yordamida quyidagi buyruq bilan bootloaderni o'rnating:

```bash
pacman -S grub efibootmgr dosfstools mtools os-prober intel-ucode
```

Ushbu buyruq Arch Linux tizimida bootloader bilan bog'liq bir nechta paketlarni o'rnatish uchun ishlatiladi. O'rnatilgan paketlar quyidagilar:

* `grub` (GRand Unified Bootloader): Bu o'rnatilgan operatsion tizimlar ro'yxatidan yuklash uchun operatsion tizimni tanlash imkonini beruvchi yuklovchi bootloader.

* `efibootmgr` Bu UEFI (Unified Extensible Firmware Interface) asosidagi tizimlarda EFI tizim qismidagi yuklash yozuvlarini boshqarish uchun foydalaniladigan vositadir.

* `dosfstools` Ushbu paket odatda UEFI tizimlarida yuklanadigan bo'limlar uchun ishlatiladigan MS-DOS FAT fayl tizimlarini yaratish va tekshirish uchun yordamchi dasturlarni taqdim etadi.

* `mtools` Ushbu paket MS-DOS formatidagi disklar va disk tasvirlari bilan ishlash uchun yordamchi dasturlar to'plamini taqdim etadi.

* `os-prober` Ushbu vosita boshqa operatsion tizimlar va bir xil mashinada o'rnatilgan bootloaderlarni aniqlash uchun ishlatiladi.

* `intel-ucode` yoki `amd-ucode` Ushbu paket tizim barqarorligi va xavfsizligini yaxshilashga yordam beradigan Intel protsessorlari va AMD protsessorlari uchun mikrokod yangilanishlarini o'z ichiga oladi.

`pacman` buyrug'i paketlarni Arch Linux tizimiga o'rnatish uchun ishlatiladi. `-S` opsiyasi paketlarni o'rnatish kerakligini va undan keyin ko'rsatilgan paket nomlari o'rnatilishi kerak bo'lgan paketlarni belgilaydi.


#### Linux kerneli uchun dastlabki ramdisk tasvirini qayta tiklash.

```bash
mkinitcpio -p linux
```

`mkinitcpio -p linux` - bu Linux kerneli uchun dastlabki ramdisk tasvirini qayta tiklash uchun ishlatiladigan buyruq. Dastlabki ramdisk tasviri vaqtinchalik fayl tizimi bo'lib, u haqiqiy ildiz fayl tizimi o'rnatilishidan oldin yuklash jarayonida xotiraga yuklanadi. Unda tizimni yuklash uchun zarur bo'lgan asosiy drayverlar va boshqa komponentlar mavjud.

`mkinitcpio -p linux` tizimga ma'lum o'zgarishlar kiritilganda Linux kerneli uchun dastlabki ramdisk tasvirini qayta tiklash uchun zarur. Bu tizimni muvaffaqiyatli yuklash uchun kerakli drayverlar va komponentlar mavjudligini ta'minlaydi.

#### Bootloaderni konfigratsiya qilish

```bash
grub-install --target=x86_64-efi --efi-directory=/boot/EFI --bootloader-id=GRUB --recheck
```
`grub-install` buyrug'i GRUB bootloaderni o'rnatish uchun ishlatiladi. `--target=x86_64-efi` opsiyasi maqsadli arxitektura `x86_64` ekanligini va bootloader UEFI rejimida o'rnatilishi kerakligini bildiradi. `--efi-directory=/boot/EFI` opsiyasi EFI yuklash fayllari saqlanishi kerak bo'lgan directoryni belgilaydi, bu holda, `/boot/EFI`. `--bootloader-id=GRUB` opsiyasi UEFI yuklash menejerida bootloader moslamasi uchun ishlatilishi kerak bo'lgan nomni belgilash uchun ishlatiladi.

Ushbu buyruq UEFI firmwaredan foydalanadigan Arch Linux tizimi uchun GRUB-ni bootloader vositasi sifatida o'rnatish uchun ishlatiladi. GRUB - bu bir nechta operatsion tizimlarni yuklashni qo'llab-quvvatlaydigan va Linux tizimlarida keng qo'llaniladigan mashhur bootloader. grub-install buyrug'i bilan ta'minlangan variantlar maqsadli arxitekturani, EFI bootloader fayllarining joylashuvini va UEFI boot menejerida bootloader nomini belgilash uchun ishlatiladi.

#### GRUB konfiguratsiya faylini yaratish

```bash
grub-mkconfig -o /boot/grub/grub.cfg
```
`grub-mkconfig` buyrug'i GRUB bootloader konfiguratsiya faylini yaratadi. Ushbu fayl tizimning yuklash parametrlarini, jumladan, yuklash uchun mavjud bo'lgan operatsion tizimlarni, yuklash uchun standart operatsion tizimni va standart boot timeout kabi boshqa variantlarni belgilaydi.

`-o` opsiyasi chiqish(output) faylini belgilaydi, bu holda u `/boot/grub/grub.cfg`. Bu fayl `/etc/default/grub` va `/etc/grub.d` directorydagi boshqa konfiguratsiya fayllaridagi sozlamalar asosida yaratilgan.

#### Bootloaderni yangilash

```bash
bootctl update
```
Ushbu qadamlar Arch Linux tizimingizda GRUB bootloaderni o'rnatadi va sozlaydi. Bootloaderni /boot/EFI directorysiga o'rnatiladi va /boot/grub/grub.cfg konfiguratsiya faylidan foydalanadi. bootctl update buyrug'i bootloaderning yangilanganligini va to'g'ri ishlashini ta'minlaydi.

### Kerakli dasturlar va Sozlamalar

Arch linux uchun kerakli dastur, driver va utilitalarni o'rnatamiz.

```bash
pacman -S neofetch python firefox unzip xarchiver git htop net-tools e2fsprogs xfsprogs iproute2
```

`pacman -S` buyrug'i va undan keyin paketlar nomlari ro'yxati ushbu paketlarni Arch Linux-ga o'rnatish uchun ishlatiladi. Quyida sanab o'tilgan har bir paketning qisqacha tushuntirishlari keltirilgan:

* `neofetch` Terminalda tizim ma'lumotlari va qurilma tafsilotlarini ko'rsatish uchun ishlatiladigan buyruq qatori yordam dasturi.

* `python` skript yaratish, veb-ishlab chiqish, ma'lumotlarni tahlil qilish va boshqalar kabi turli maqsadlarda ishlatiladigan mashhur dasturlash tili.

* `firefox` Mozilla tomonidan ishlab chiqilgan mashhur open-source veb-brauzer.

* `unzip` ZIP arxividan fayllarni chiqarish uchun ishlatiladigan buyruq qatori yordam dasturi.

* `xarchiver` ZIP, RAR va TAR kabi turli xil arxiv formatlarini qo'llab-quvvatlaydigan grafik arxiv menejeri.

* `git` Manba kodini boshqarish va dasturiy ta'minot loyihalarida hamkorlik qilish uchun ishlatiladigan mashhur versiya boshqaruv tizimi.

* `htop` CPU va xotiradan foydalanish kabi tizim resurslarini kuzatish uchun foydalaniladigan buyruq qatori yordam dasturi.

* `net-tools` Tarmoq interfeyslarini, jumladan ifconfig, arp va netstatni boshqarish uchun ishlatiladigan buyruq qatori yordam dasturlari to'plami.

* `e2fsprogs` ext2, ext3 va ext4 fayl tizimlarini boshqarish uchun foydalaniladigan yordamchi dasturlar to'plami.

* `xfsprogs` XFS fayl tizimini boshqarish uchun foydalaniladigan yordamchi dasturlar to'plami.

* `iproute2` Tarmoq interfeyslarini, marshrutlash jadvallarini va trafikni boshqarishni boshqarish uchun foydalaniladigan yordamchi dasturlar to'plami.

Ushbu buyruq ushbu paketlarni Arch Linux tizimiga o'rnatadi.



### Grafik drayverlar o'rnatish

Grafik drayverlarni o'rnatish juda muhim, chunki ular tizimingizdagi grafik hardwarening operatsion tizim va dasturiy ta'minot bilan samarali aloqa qilishiga imkon beradi. Tegishli grafik drayverlar o'rnatilmagan bo'lsa, tizimingizning grafik ishlashi buzilgan bo'lishi mumkin, natijada kadrlar tezligi past bo'ladi, grafik artefaktlar va boshqa vizual muammolar paydo bo'ladi. Bundan tashqari, ba'zi dasturiy ta'minotlar tegishli grafik drayverlarsiz to'g'ri yoki umuman ishlamasligi mumkin. Shuning uchun kerakli grafik drayverlarni o'rnatish tizimingizning optimal ishlashi va funksionalligiga erishish uchun juda muhimdir.

Sizda qaysi grafik drayver bo'lsa shuni tanlab o'rnatib olishingiz kerak.

#### intel uchun
```bash
pacman -S xf86-video-intel
```
#### AMD uchun
```bash
pacman -S xf86-video-amdgpu 
```
#### Nvidia uchun
```bash
pacman -S nvidia nvidia-utils
```
#### Virtualbox uchun
```bash
pacman -S virtualbox-gues-utils
```

### Asosiy Arch Linux tizimi uchun SSH va NetworkManager xizmatlarini yoqish

```bash
sudo systemctl enable sshd.service && systemctl enable NetworkManager
```

* `sudo systemctl enable sshd.service`

Tizimda sshd xizmatini yoqadi. sshd - Secure Shell (SSH) protokoli uchun dastur bo'lib, u tarmoq orqali tizimga xavfsiz masofadan kirish imkonini beradi. Sshd xizmatini yoqish orqali siz foydalanuvchilarga SSH mijozi yordamida masofadan turib tizimga ulanishga ruxsat berasiz.

* `systemctl enable NetworkManager`

Tizimda NetworkManager xizmatini yoqadi. NetworkManager Linux tizimlarida, jumladan Ethernet, Wi-Fi va uyali tarmoqlarda tarmoq ulanishlarini boshqaradigan xizmatdir. NetworkManager-ni yoqish orqali siz tizimga tarmoq ulanishlarini avtomatik boshqarish va sozlash imkonini berasiz.

Bu ikkita buyruq birgalikda tizimda SSH-ga kirish va tarmoqni boshqarish imkonini beradi, bu esa tizimga masofadan ulanish va boshqarishni osonlashtiradi. Ushbu xizmatlarni yoqish yoki yoqmaslik tizimning o'ziga xos foydalanish holati va ehtiyojlariga bog'liq. Biroq, ko'pchilik foydalanuvchilar uchun ushbu xizmatlarni yoqish odatiy va tavsiya etilgan amaliyotdir.


### chroot muhitidan chiqish

```bash
exit
```

Oddiy Arch Linux o'rnatilishi kontekstida siz asosiy tizimni o'rnatish va sozlashdan so'ng chroot muhitidan chiqish uchun `exit` buyrug'idan foydalanasiz. Bu zarur, chunki chroot muhiti o'rnatish jarayonida foydalaniladigan vaqtinchalik ildiz fayl tizimi bo'lib, u tizimning doimiy qismi bo'lish uchun mo'ljallanmagan.

Chroot muhitidan chiqish va jonli tizimga qaytish o'rnatish jarayonini yakunlashda muhim qadamdir, chunki u har qanday o'rnatilgan bo'limlarni o'chirish va yangi Arch Linux o'rnatilishidan foydalanishni boshlash uchun tizimni qayta ishga tushirish imkonini beradi.

Shuning uchun, `exit` buyrug'i o'rnatish jarayonini yakunlash uchun zarur va o'rnatish jarayonida tegishli vaqtda ishlatilishi kerak.

```bash
umount -a
```
`umount -a` buyrug'i tizimdagi barcha o'rnatilgan fayl tizimlarini o'chirish uchun ishlatiladi. `-a` opsiyasi tizimning ishlashi uchun muhim deb belgilanganlaridan tashqari barcha fayl tizimlarini o'chirib qo'yish kerakligini bildiradi.

Oddiy Arch Linux o'rnatilishi kontekstida siz chroot muhitidan chiqqaningizdan so'ng va tizimni qayta ishga tushirishdan oldin `umount -a` buyrug'idan foydalanasiz. Bu barcha o'rnatilgan fayl tizimlari to'g'ri o'chirilganligini va ma'lumotlarning buzilishi yoki boshqa muammolarga olib kelishi mumkin bo'lgan uzluksiz fayl tizimi operatsiyalari yo'qligini ta'minlash uchun zarur.

Barcha fayl tizimlarini o'chirish orqali umount -a buyrug'i o'rnatish jarayonida kiritilgan har qanday o'zgarishlar diskda to'g'ri saqlanishini va tizimni qayta ishga tushirishdan oldin toza holatda bo'lishini ta'minlaydi.

Shuning uchun umount -a buyrug'i Arch Linuxni o'rnatish jarayonining muhim qismidir va o'rnatish jarayonida tegishli vaqtda ishlatilishi kerak.

### Tizimni qayta ishga tushirish

```bash
sudo reboot
```
Arch Linuxni o'rnatish jarayonida diskni qismlarga ajratish, asosiy tizimni o'rnatish yoki boot loaderni sozlash kabi muayyan vazifalarni bajarganingizdan so'ng tizimni qayta ishga tushirishingiz kerak bo'ladi. O'rnatish muvaffaqiyatli yakunlanishi uchun o'rnatish yo'riqnomasini diqqat bilan kuzatib borish va tizimni tegishli vaqtlarda qayta ishga tushirish muhimdir.

`sudo reboot`-dan foydalanib, tizim barcha ishlaydigan jarayonlar va xizmatlarni ehtiyotkorlik bilan o'chiradi, o'rnatilgan fayl tizimlarini o'chiradi va tizimni qayta ishga tushiradi. Bu tizimning toza holatda bo'lishini va o'rnatish jarayonida kiritilgan har qanday o'zgarishlarning to'g'ri qo'llanilishini ta'minlaydi.

Shunday qilib, ha, tizimni to'g'ri qayta ishga tushirish va o'rnatish jarayonida kiritilgan har qanday o'zgarishlar to'g'ri qo'llanilishini ta'minlash uchun Arch Linuxni o'rnatish jarayonida sudo reboot buyrug'idan foydalanish zarur.



Arch Linux o'rnatilgandan va tizim qayta ishga tushirilgandan so'ng, kompyuter Arch Linux operatsion tizimi bilan ishga tushadi. Foydalanuvchiga tizimga kirish uchun foydalanuvchi nomi va parolni kiritishi mumkin bo'lgan tizimga kirish so'rovi taqdim etiladi.

Tizimga kirgandan so'ng, foydalanuvchi standart bo'yicha buyruq qatori interfeysiga kirish huquqiga ega bo'ladi. Ushbu minimal o'rnatish foydalanuvchi o'z ehtiyojlariga moslashtirilgan to'liq ishlaydigan tizimni yaratish uchun ish desktop environment yoki window managerni va boshqa dasturlarni qo'lda o'rnatishi kerakligini anglatadi.

Grafik ish stoli muhitini o'rnatish uchun foydalanuvchi kerakli paketlarni o'rnatish uchun pacman paket menejeridan foydalanadi.

## Desktop Environment o'rnatish

Arch Linux-ni o'rnatgandan so'ng, tizim ishlaydi, lekin foydalanuvchi grafik interfeysi (GUI) yoki ish stoli muhiti (DE) bilan birga kelmaydi. Tizimdan grafik interfeys bilan foydalanish uchun DE o'rnatilishi kerak.

DE - bu operatsion tizim bilan o'zaro aloqada bo'lish uchun yaxlit va integratsiyalangan foydalanuvchi interfeysini ta'minlovchi dasturiy ta'minot to'plami. Bunga fayl boshqaruvchisi, grafik ilovalarni ishga tushirish moslamasi va tizim sozlamalari kabi xususiyatlar kiradi. Arch Linux uchun bir nechta DE mavjud, jumladan GNOME, KDE, Xfce, Cinnamon, Deepin, LXDE va boshqalar.

DE ni o'rnatish uchun bir nechta paketlarni o'rnatish kerak, jumladan DE ning o'zi, displey drayverlari va displey menejeri. Displey drayverlari grafik uskuna bilan bog'lanish uchun zarurdir va displey menejeri foydalanuvchilarning tizimga kirishi uchun kirish ekranini taqdim etadi.

### Xfce4 DE o'rnatish

Xfce4 - bu Arch Linux-ga o'rnatilishi mumkin bo'lgan yengil va mashhur ish stoli muhiti. Xfce4 ni o'rnatish uchun terminalda quyidagi buyruqdan foydalanishingiz mumkin:

```bash
sudo pacman -Syyu xfce4 xfce4-goodies lightdm lightdm-gtk-greeter xorg mesa xf86-video-intel
```

```bash
sudo systemctl enable lightdm.service

sudo reboot
```

Ushbu kod XFCE4 ish stoli muhitini va XFCE4 uchun qo'shimcha plaginlar va yordamchi dasturlarni taqdim etadigan xfce4-goodies kabi ba'zi qo'shimcha paketlarni o'rnatadi. Shuningdek, u grafik login screenni taqdim qiluvchi displey menejeri `lightdm` va `GTK+` toolkitdan foydalanadigan `LightDM `displey menejeri uchun greeter lightdm-gtk-greeterni o'rnatadi.

Bundan tashqari, u grafik foydalanuvchi interfeyslari uchun asos bo'lgan dasturiy ta'minot frameworki bo'lgan `X Window System `bo'lgan `xorg` ni o'rnatadi. Shuningdek, u Xorg uchun 3D grafiklarni qo'llab-quvvatlaydigan OpenGL specificationning open-source ilovasi bo'lgan `mesa`-ni o'rnatadi.

Kodning ikkinchi qatori LightDM displey menejerini boshqarish uchun masul bo'lgan tizim xizmati bo'lgan `lightdm.service`-ni ishga tushiradi. Bu LightDM displey menejerining yuklash vaqtida avtomatik ravishda ishga tushishini ta'minlaydi va foydalanuvchiga grafik interfeys orqali tizimga kirish imkonini beradi.

Agar sizga xfce4ni o'zini standart dizayni ko'rishini yoqmasa uni didingizga qarab xoxlagancha bezab olishingiz mumkin. Quyida havolada Arch linuxga o'rnatilgan xfce4ni dizayni o'zgartirish qo'llanmasi va konfiguratsiya fayllar, kodlari bor.

![alt text](https://github.com/ismoilovdevml/Arch-Linux/blob/master/assets/xfce4.png)

### [Xfce4 Ko'rinishi o'zgartirish](https://github.com/ismoilovdevml/de-config/tree/master/xfce4-macos-config)

Agar siz boshqa DE larni o'rnatmoqchi bo'lsagiz quyidagi havola orqai o'zongizga yoqqan De larni o'rnatib olishingiz mumkin

### [Boshqa DE larni o'rnatish qo'llanmasi(o'zbek tilida)](https://t.me/Otabek_Ismoilov/424)

## Xulosa

Xulosa qilib aytganda, biz foydalanuvchilarga yengil va soddalashtirilgan hisoblash muhitini taqdim etuvchi kuchli va sozlanishi mumkin bo'lgan Arch Linux operatsion tizimini o'rnatishni yakunladik. O'rnatish jarayonida biz diskni qismlarga ajratdik, asosiy tizimni o'rnatdik, boot loaderni sozladik, qo'shimcha dasturiy ta'minotni o'rnatdik va tarmoq va foydalanuvchi hisoblari kabi asosiy tizim konfiguratsiyalarini o'rnatdik.

Tizimni qayta ishga tushirgandan so'ng, bizga Arch Linux buyruq qatori interfeysi taqdim etildi, u bizning ehtiyojlarimizga moslashtirilgan va moslashtirilgan. Bu yerdan foydalanuvchilar qo‘shimcha dasturlarni o‘rnatishlari, tizim sozlamalarini sozlashlari va Arch Linux muhitini o‘z xohishlariga ko‘ra nozik sozlashlari mumkin. Keyin biz Desktop Environment o'rnatdik.

O'rnatish jarayoni boshqa Linux distributivlariga qaraganda ancha murakkab bo'lishi mumkin bo'lsa-da, Arch Linux-ning afzalliklari uning moslashuvchanligi, minimalizmi va sozlanishidadir. Bu ularning o'ziga xos ehtiyojlariga moslashtirilishi mumkin bo'lgan yengil va samarali operatsion tizimni xohlaydigan foydalanuvchilar uchun ideal tanlovdir. Ushbu repositoryda qo'llanmaning .docx varianti ham mavjud.


#### Muallif: Otabek Ismoilov
* [Veb-sayt](https://ismoilovdev.vercel.app/)
* [Telegram Blog](https://t.me/Otabek_Ismoilov)
* [Github](https://github.com/ismoilovdevml)

#### Hamjamiyat: Xinux
* [Veb-sayt](https://www.xinux.uz/)
* [Telegram](https://t.me/xinuxuz)

#### Hamjamiyat: Uzinfocom Open Source

* [Veb-sayt](https://oss.uzinfocom.uz)
* [Telegram](https://t.me/uzinfocom_oss)
* [Github](https://github.com/uzinfocom-org)