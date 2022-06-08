# Arch Linux o'rnatish bo'yicha mukammal qo'llanma

Bu qo'llanma O'zbekistonda Arch Linuxni Rivojlantirish maqsadida yozilgan

## O'rnatish bosqichlari
## Arch Linuxni o'rnatish uchun talablar:
X86_64 (ya'ni 64 bit) mos keladigan mashina
Minimal 512 MB RAM (tavsiya qilingan 2 Gb)
Kamida 1 Gb bo'sh disk maydoni (asosiy foydalanish uchun tavsiya etilgan 20 Gb)
Faol internet aloqasi
Kamida 2 GB xotira hajmi bo'lgan USB drayver
## 1 bosqichi: ISO-ni yuklab oling
http://mirror.yandex.ru/archlinux/iso/2022.06.01/
quyidali link orqali .ISO faylini yuklab oling tepadan uchinchi
## 2 bosqichi: Arch Linux fleshkaga yozish
Bunda sizga rufus va BalanaTech kabi dasturlar yordam beradi MBR/GPT
Bu qo'llanmada GPT yozilgan Arch o'rnatamiz MBR boshqacha 
MBR uchun https://www.youtube.com/watch?v=FudOL0-B9Hs
## 3 bosqichi: USB dan yuklash
Kompyuteringizni o'chiring va Arch linux yozilgan fleshkani kompyuterga qo'ying va BOOT 
menuga kirib fleshkani tanlab o'ting  keyin birinchi turganiga qo'yib enter bosasiz
## 4 Disklarni ajratish
Talab qilinadi kompyuter kabel bilan interntega ulanishi yoki bo'lmasa telefon orqali USB kabel
ulab telefondan modem bering
```bash
$ lsbk
```
$ lsblk yordamida disklarni ko'ramiz
```bash
$ cfdisk /dev/sda
```
Bu yerdan GPT ni bosib o'tamiz yangi bo'lim ochamiz bunga 512M berib type ga EFI system beramiz 512M bu standart o'zgartirilmasin Swap bo'lim ochamiz Kompyuter RAM ga teng yoki yarmiga teng holda sawp ochamiz
masalan 4GB RAM 4GB swap yoki 2GB swap disklar bo'linayotganda GB o'rnga G yoziladi typega Linux Swap beramiz qolganini esa ext4 formatda xotira beramiz type linux file system O'zgarishlarni saqlash uchun Write bosib yes yozib enter bosamiz keyin Quit bosib chiqib ketamiz
```bash
$ clear
```
Disklarni Ko'ramiz
```bash
$ lsblk
```
$ lsblk bilan dislarni ko'razmiz bizda /dev/sda ichida /dev/sda1,/dev/sda2,/dev/sda3 bo'ladi
/dev/sda1 BOOT uchun /dev/sda2 Swap uchun /dev/sda3 xotira roor partition uchun
## Disklarni Formatlash
```bash
$ mkfs.fat -F32 /dev/sda1
```
//BOOT uchun formatlandi
```bash
$ mkswap /dev/sda2
```
//Swap uchun formatlandi
```bash
$ mkfs.ext4 /dev/sda3
```
//ROOT uchun formatlandi Y/n chiqsa y bosamiz
```bash
$ clear
```
Eslatma Kompyuterdagi barcha Operatsion tizimlar o'chib ketti hozir 
## 6 Jildlarni mountlash
/dev/sda3 ni /mnt jildiga ulaymiz
```bash
$ mount /dev/sda3 /mnt
```
/mnt jildidan boot va EFI jildlar ochib olamiz
```bash
$ mkdir -p /mnt/boot/EFI
```
/dev/sda2 ni Swapga ulaymiz
```bash
$ swapon /dev/sda2
```
/dev/sda1 ni /mnt/boot/EFI jildiga ulaymiz
```bash
$ mount /dev/sda1 /mnt/boot/EFI
```
```bash
$ clear
$ lsblk 
```
disklar shunday ko'rinishi kerak
sda1 512M /mnt/boot/EFI
sda2 RAMga teng [SWAP]
sda3 /mnt
## 7 Arch linuxni asosiy faylarini yuklaymiz
/mnt jildiga archni o'rtamaiz aytagimdek kabelli internet ulangan bo'lishi kerak
internte ishlayotganini tekshirish 
```bash
$ ping -c 3 google.com
```
Internet ishlayotgan bo'lsa paketlarni yangilaymiz
```bash
$ sudo pacman -Sy
```
Arch linuxni o'rnatamiz /mnt jildiga 
```bash
$ pacstrap /mnt base base-devel linux linux-firmware nano openssh networkmanager netctl
```
```bash
$ clear
```
## 8 Arch linuxni sozlash
fstab faylini generatsiya qilib olamiz
```bash
$ genfstab -U -p /mnt >> /mnt/etc/fstab
```
chroot  huquq kerak bo'ladi /mnt ga arch chrootni ulaymiz
```bash
$ arch-chroot /mnt
```
Hostname yozamiz yani Komyuterga Nom ismoilovdev@MacbookPro terminalga kirganimid shu chiqadi 
shu yerdan Macbookpro degan nomni host name dan olyapti
```bash
$ echo "kompyuternomi" > /etc/hostname
```
hostname yozish o'zingizga bog'liq hohlagan nomigzini bering
Root uchun parol yozamiz
```bash
$ passwd
```
New password deb chiqadi siz parol yozasiz yozgan parolingiz ko'rinmaydi
Return New password deb chiqadi bunga hozir yozgan parolingizni yozasiz
Tizimga kirish uchun user ochib olishimiz kerak
```bash
$ useradd -mG whell user_ism
```
user_ism degan joyiga userni kiritasiz asosan ism yoki nik
User uchun parol qo'yamiz
```bash
$ passwd user_ism
```
Bu yerga hozirgi qo'shgan useringizni yozasiz
Parol yozamiz parol ko'rinmaydi enter bosamiz keyin yozgan parolimizni yana bir marta
qayta yozamiz
## 9 Asosiy Sozlamalar
visudo fileni  tahrirlaymiz
```bash
$ EDITOR=nano visudo
```
### visudo filenidan shunaqa kodni topamiz
- root ALL=(ALL) ALL
- ##Uncomment to allow members of group wheel to execute any command 
- #%whell ALL=(ALL) ALL
## visudo filenidan shunaqa kodni topamiz

-  `root ALL=(ALL) ALL`
- `##Uncomment to allow members of group wheel to execute any command`
- `#%whell ALL=(ALL) ALL`
kodning shu yerini topib olamiz bu yerda va manabu ko'rinishga o'zgartiramiz
root ALL=(ALL) ALL
-  `root ALL=(ALL) ALL`
- `##Uncomment to allow members of group wheel to execute any command`
Kodning shu yerini topib olamiz bu yerda va manabu ko'rinishga o'zgartiramiz
-  `root ALL=(ALL) ALL`
- `##Uncomment to allow members of group wheel to execute any command`
- `%whell ALL=(ALL) ALL`
shu kod `#%whell ALL=(ALL)` `ALL` `#` coometda bo'ladi biz shuni commentdan ochib qo'yamiz 
# ni olib tashlab
`ctrl+o` bosib saqlaymiz va enterni bosamiz keyin `ctrl+x` qilib chiqib ketamiz
```bash
$ clear
```
## 10 Kerakli dasturlarni ishga tushiramiz




















