# Arch Linux o'rnatish bo'yicha mukammal qo'llanma

Bu qo'llanma O'zbekistonda Arch Linuxni Rivojlantirish maqsadida yozilgan <br>
Sizlarga yana bitta qo'llanmani tavsiya qilmoqchiman bu video qo'llanma <br>
Arch linuxni o'rnatishdan oldin shu videoni ko'rishni tavsiya qilardim <br>
Muallif: Anvar Alimov <br>
[You Tube video](https://youtu.be/G8WcurParfA) <br>

## O'rnatish bosqichlari
#Arch Linuxni o'rnatish uchun talablar:
X86_64 (ya'ni 64 bit) mos keladigan mashina
Minimal 512 MB RAM (tavsiya qilingan 2 Gb)
Kamida 1 Gb bo'sh disk maydoni (asosiy foydalanish uchun tavsiya etilgan 20 Gb)
Faol internet aloqasi
Kamida 2 GB xotira hajmi bo'lgan USB drayver
## 1 ISO faylni yuklab oling
http://mirror.yandex.ru/archlinux/iso/2022.06.01/
quyidali link orqali .ISO faylini yuklab oling tepadan uchinchi
## 2 Arch Linux fleshkaga yozish
Bunda sizga rufus va Balena Etcher kabi dasturlar yordam beradi MBR/GPT
Agar siz linuxda bo'sangiz va terminal orqali yozmoqchi bo'lsangiz quyidagi buyruqni yozing
```bash
$ dd bs=4M if=/home/ismoilovdev/Documents/archlinux-x86_64.iso of=/dev/sdb conv=fsync oflag=direct status=progress
```
bu yerda siz ISO ga path berasiz bu yerda `/home/ismoilovdev/Document/archlinux-x86_64.iso` <br>
`of=/dev/sdb` bu yerda mening USB draverim formati sizda boshqacha bo'lishi mumkin buni bilish uchun terminalga root bilan kirib quyidagi buyruqni kiriting, USB drayver kompyuterga ulangan bo'lishi kerak.<br>
```bash
$ sudo su 
$ fdisk -l
```
Chiqqan ma'lumotlardan eng pastida USB drayver haqida yozilgan bo'ladi turlari `/dev/sda, /dev/sdb, /dev/sdx`

Bu qo'llanmada GPT yozilgan Arch o'rnatamiz MBR boshqacha 
[MBR uchun video qo'llanma](https://www.youtube.com/watch?v=FudOL0-B9Hs)
## 3 USB dan yuklash
Kompyuteringizni o'chiring va Arch linux yozilgan fleshkani kompyuterga qo'ying va BOOT 
menyuga kirib fleshkani tanlab o'ting  keyin birinchi turganiga qo'yib enter bosasiz

![alt text](https://937862693-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FSFrNj7gaqbMUSNNqIdQ1%2Fuploads%2FNtWEFRWYvMBvDclF65b4%2Farch1.png?alt=media&token=8ed69d3f-e2e2-42c8-a5aa-7f59877b6031)

## 4 Disklarni ajratish
Talab qilinadi kompyuter kabel bilan internetga ulanishi yoki bo'lmasa telefon orqali USB kabel
ulab telefondan modem berilishi kerak.
```bash
$ lsblk
```
`$ lsblk` yordamida disklarni ko'ramiz
```bash
$ cfdisk /dev/sda
```
Bu yerdan GPT ni bosib o'tamiz yangi bo'lim ochamiz bunga `512M` berib type ga `EFI sytem` beramiz `512M` bu standart o'zgartirilmasin Swap bo'lim ochamiz Kompyuter RAM ga teng yoki yarmiga teng holda sawp ochamiz
masalan 4GB RAM 4GB swap yoki 2GB swap disklar bo'linayotganda `GB` o'rnga `G` yoziladi typega `Linux Swap` beramiz qolganini esa `ext4` formatda xotira beramiz type `Linux file system` O'zgarishlarni saqlash uchun `Write` bosib `yes` yozib `enter` bosamiz keyin `Quit` bosib chiqib ketamiz
```bash
$ clear
```
Disklarni Ko'ramiz
```bash
$ lsblk
```
`$ lsblk` bilan dislarni ko'razmiz bizda `/dev/sda` ichida `/dev/sda1`,`/dev/sda2`,`/dev/sda3` bo'ladi
`/dev/sda1` BOOT uchun `/dev/sda2` Swap uchun `/dev/sda3` xotira roor partition uchun
## 5 Disklarni Formatlash
```bash
$ mkfs.fat -F32 /dev/sda1
```
BOOT uchun formatlandi
```bash
$ mkswap /dev/sda2
```
Swap uchun formatlandi
```bash
$ mkfs.ext4 /dev/sda3
```
ROOT uchun formatlandi`[Y/n]` chiqsa `y` bosamiz
```bash
$ clear
```
Eslatma Kompyuterdagi barcha Operatsion tizimlar o'chib ketti hozir 
## 6 Jildlarni mountlash
`/dev/sda3` ni `/mnt` jildiga ulaymiz
```bash
$ mount /dev/sda3 /mnt
```
`/mnt` jildidan boot va EFI jildlar ochib olamiz
```bash
$ mkdir -p /mnt/boot/EFI
```
`/dev/sda2` ni Swapga ulaymiz
```bash
$ swapon /dev/sda2
```
`/dev/sda1` ni` /mnt/boot/EFI` jildiga ulaymiz
```bash
$ mount /dev/sda1 /mnt/boot/EFI
```
```bash
$ clear
$ lsblk 
```
Disklar shunday ko'rinishi kerak
`sda1 512M /mnt/boot/EFI
 sda2 RAMga teng [SWAP]
 sda3 /mnt`
## 7 Arch linuxni asosiy faylarini yuklaymiz
`/mnt` jildiga archni o'rtamaiz aytagimdek kabelli internet ulangan bo'lishi kerak
internte ishlayotganini tekshirish 
```bash
$ ping -c 3 google.com
```
Internet ishlayotgan bo'lsa paketlarni yangilaymiz
```bash
$ sudo pacman -Sy
```
Keyingi bosqichlarda mummo chiqmasligi uchun shu buyruqni yozing
```bash
$ sudo pacman -Sy archlinux-keyring
```
 ## Arch linuxni o'rnatamiz `/mnt`  jildiga 
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
chroot  huquq kerak bo'ladi `/mnt`  ga arch chrootni ulaymiz
```bash
$ arch-chroot /mnt
```
Hostname yozamiz yani Komyuterga Nom `ismoilovdev@MacbookPro` terminalga kirganimid shu chiqadi 
shu yerdan `MacbookPro `degan nomni host name dan olyapti
```bash
$ echo "kompyuternomi" > /etc/hostname
```
hostname yozish o'zingizga bog'liq hohlagan nomigzini bering
Root uchun parol yozamiz
```bash
$ passwd
```
`New password` deb chiqadi siz parol yozasiz yozgan parolingiz ko'rinmaydi
`Return New password` deb chiqadi bunga hozir yozgan parolingizni yozasiz
 ## Tizimga kirish uchun user ochib olishimiz kerak
```bash
$ useradd -mG wheel user_ism
```
`user_ism` degan joyiga userni kiritasiz asosan ism yoki nik
## User uchun parol qo'yamiz
```bash
$ passwd user_ism
```
Bu yerga hozirgi qo'shgan useringizni yozasiz
Parol yozamiz parol ko'rinmaydi enter bosamiz keyin yozgan parolimizni yana bir marta
qayta yozamiz
## 9 Asosiy Sozlamalar
`visudo` faylini  tahrirlaymiz
```bash
$ EDITOR=nano visudo
```
## visudo faylidan shunaqa kodni topamiz

-  `root ALL=(ALL) ALL`
- `##Uncomment to allow members of group wheel to execute any command`
- `#%whell ALL=(ALL) ALL`
kodning shu yerini topib olamiz bu yerda va manabu ko'rinishga o'zgartiramiz
`root ALL=(ALL) ALL`
-  `root ALL=(ALL) ALL`
- `##Uncomment to allow members of group wheel to execute any command`
Kodning shu yerini topib olamiz bu yerda va manabu ko'rinishga o'zgartiramiz
-  `root ALL=(ALL) ALL`
- `##Uncomment to allow members of group wheel to execute any command`
- `%whell ALL=(ALL) ALL`
shu kod `#%whell ALL=(ALL)` `ALL` `#` coometda bo'ladi biz shuni commentdan ochib qo'yamiz 
`#` ni olib tashlab
`ctrl+o` bosib saqlaymiz va enterni bosamiz keyin `ctrl+x` qilib chiqib ketamiz
```bash
$ clear
```
## 10 Kerakli dasturlarni ishga tushiramiz
Kerakli dasturlarni o'rnatib olamiz
```bash
$ pacman -S grub efibootmgr dosfstools mtools os-prober intel-ucode
```
sizda `AMD` protsessor bo'lsa `amd-ucode`deb yozing intel bo'lsa `intel-ucode `
`[Y/n]`chiqadi y bosamiz
Grub bu operatsion tizimni yuklovchi linuxni hard diskdan yuklovchi komyuter operatsion 
tizimi va BIOS ni ulab turuvchi dasturiy ta'minot
```bash
$ clear
```
Kernelni kompilatsiya qilamiz
```bash
$ mkinitcpio -p linux
```
## 11 Til sozlamalari
Men maslaxat berardim linuxni ingliz tilida ishlatishni boshqa tillarda qiyinchiliklar va 
muammolar bo'ladi
```bash
$ nano /etc/locale.gen
```
Bu yerdan `#en_US.UTF-8`  ni topib olamiz va oldidagi # olib tashlaymiz
 `#en_US.UTF-8` shunday bo'ladi
 `en_US.UTF-8`  shu holga keltiramiz
`ctrl+O` bosib saqlaymiz va enterni bosamiz keyin `ctrl+x`qilib chiqib ketamiz
```bash
$ clear
```
`locale.gen` ni ishga tushirib til binary faylini ishga tushirib tilni faylini
generatsiya qilamiz 
```bash
$ locale-gen
```
## 12 Shell almashtirish 
Hozir default holda `bash sheel` bo'ladi biz hozir boshqa shell qo'yamiz
```bash
$ pacman -S fish
```
shellni o'zgartiramiz
```bash
$ chsh -s /usr/bin/fish
$ fish
```
Operatsion Tizim tilini kiritamiz
```bash
$ nano /etc/locale.conf
```
bu yerga biz quyidagi kodni yozamiz
```bash
LANG=en_US.UTF-8
```
`ctrl+O` bosib saqlaymiz va enterni bosamiz keyin `ctrl+x`qilib chiqib ketamiz
Klavliatura tilini kiritamiz
```bash
$ echo "KEYMAP=en_US.UTF-8" > /etc/vconsole.conf
```
## 12 Soat sozlamalari
```bash
$ hwclock --systohc --utc
```
Joylashuvni va vaqt mintaqasini belgilashimiz kerak
```bash
$ ln -sf /usr/share/zoneinfo/Asia/Tashkent /etc/localtime
```
## Foydalanuvchi sozlamalari
```bash
$ su user_ism 
```
`user_ism` degan joyda qo'shgan useringizni yozasiz
Userdan shell ni almashtiramiz
```bash
$ chsh -s /usr/bin/fish
```
Parol so'raydi parolimizni kiritamiz
exit qilib userdan chiqami endi
```bash
$ exit
```
## Bootloader o'rnatamiz
```bash
$ lsblk
```
Kompyuter yonganida Arch linuxni hard diskdan yuklanishi uchun bootloader o'rnatamiz
```bash
$ grub-install --target=x86_64-efi --bootloader-id=GRUB --recheck
```
Grub o'rnatiladi endi Grubni configuratsiya qilamiz
```bash
$ grub-mkconfig -o /boot/grub/grub.cfg
```
Grub configuratsion fayli generatsiya qilinadi
## 13 Kerakli dasturlar va Sozlamalar
Kerakli dasturlar va utilatalarni o'rnatamiz
```bash
$ pacman -S neofetch python ranger firefox
```
`sshd.service `va `NetworkManager`ni yoqib qo'yamiz
Asosiy dasturlarni ishga tushirib yoqib qo'yamiz
```bash
$ sudo systemctl enable sshd.service && systemctl enable NetworkManager
```
O'rnatuvchidan chiqamiz
```bash
$ exit
$ exit
```
Barcha ulangan disklarni umount qilamiz
```bash
$ umount -a
```
Kompyuterni o'chirib yoqamiz
```bash
$ sudo reboot
```
Kompyuter O'chganidan keyin fleshkani olib tashlaysiz Operatsion sistema
hard diskdan yuklanadi
Kompyuter yonganidan keyin Grub ishga tushadi va enter bosamiz Arch linux 
odiy terminal rejimida ishga tushadi
`arch login:` deb chiqadi bunga biz userimizni kiritamiz
`Password:` bu yerga parolimizni yozamiz
```bash
$ neofetch
```
Internet ishlayotganini tekshirib ko'ring
```bash
$ ping -c 3 google.com
```
## Tabriklaymiz Sizda Arch linux muvafaqqiyatli o'rnatildi
Agar barchasini to'gri bajargan bo'lsangiz sizda muammosiz arch linux o'rnatilgan <br>
Endi navbat Arch linuxga DE (Desktop Environment) o'rnatishdir <br>
Qandaydir xato va kamchiliklar bo'lsa yozib qoldiring <br>
Telegram aloqa: [@ismoilovdev](https://t.me/ismoilovdev) <br>
Arch linux bo'yicha qo'llanmalar o'quv qo'llanmalari va foydali postlarni quyidagi kanaldan topishingiz mumkin <br>
Kanal: [Otabek Ismoilov](https://t.me/Otabek_Ismoilov) <br>
Muallif: Otabek Ismoilov <br>
Community: Xinux <br>
Websayt: [Xinux.uz](https://xinux.uz) <br>
Telegram Guruh: [@xinuxuz](https://t.me/xinuxuz)  <br>










