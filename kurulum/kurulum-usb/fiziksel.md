# Fiziksel cihazda USB ile başlatma

Fiziksel cihazları USB ile başlatabilmek teknik olarak bilgi güvenliği açısından sakıncalı bir olaydır. Bu nedenle genellikle "boot order" olarak belirlenen veya "BIOS Ayarları" gibi kısımlar kurumsal ortamlara parolalı olarak giriş yapılabilmektedir.

BIOS üzerinde parola yoksa veya parolayı biliyorsanız fiziksel cihazınız açılırken BIOS'unuzun özelliğine göre bir klavye tuşuyla "boot menu"'ye giriş yapılabilmektedir. Bu tuş genellikle F8 ile F12 arasındaki tuşlardan birisi olarak belirlenmektedir.

İşletim sistemi kurulması için internetten Boot olabilir ISO dosyasını indirip USB belleğe yazdırmanız gerekmektedir. Daha sonra cihazınızın USB portuna bu belleği taktıktan sonra bilgisayarı açmaya başladığınızda BIOS ekranı belirdiğinde boot menü tuşuna bastığınızda aşağıdaki gibi görsel çıkacaktır.

![](../../.gitbook/assets/bootmenu.png)

Boot menu üzerinde USB Devices, Removable Devices gibi ifadeler başta olmadığı durumda klavyeden yön tuşları ile bu seçeneği seçip &lt;ENTER&gt; tuşuna basarak bilgisayarınızı USB Bellek üzerinden başlatabilirsiniz. Bu adımda USB Bellekte bir problem bulunmadığı durumda kurmak istediğiniz işletim sisteminin boot ekranı açılmaya başlayacaktır.

