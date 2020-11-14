# Paket ile Yükleme

Elinizde bulunan "**kaptan\_0.52.9\_amd64.deb**" veya tam sürümün yer aldığı deb paketini daha önce kurmuş olduğunuz işletim sistemi üzerine göndermeniz gerekmektedir.

## 1. DEB paketini sunucuya gönderme

### 1.a. GNU/Linux sistemden gönderme:

Kendi bilgisayarınız GNU/Linux temelli bir bilgisayar ise temin ettiğiniz deb paketini karşı sunucu üzerine aşağıdaki komut ile SSH protokolünü kullanarak gönderebilirsiniz:

```text
scp kaptan-paketversiyonu.deb sysadmin@sunucuipadresi:~/.
```

Bu komut kullanılırken "sysadmin" yerine sunucuya erişim sağladığınız kullanıcı adını, sunucuipadresi yerine ise kurduğunuz sunucunun IP Adresi veya DNS kaydı eklediyseniz DNS adresini yazmanız gerekmektedir. Ayrıca güncel paket kullanabilmek için paketadındaki "kaptan-**versiyonnumarası**.deb"'a dikkat etmek gerekmektedir.

Bu komutun çalışabilmesi için sunucunuzda openssh-server paketinin kurulu olması gerekmektedir ve varsayılanda bulunan güvenlik izinlerinin açık olması gerekmektedir.

### 1.b. Windows sistemden gönderme:

Henüz uygulanmadı. Özet olarak Winscp uygulaması ile gönderilebilmektedir.

## 2. DEB paketini kurma

DEB paketini gönderdikten sonra işletim sistemi bağımsız olarak uzaktan sunucuya erişmeniz gerekmektedir. Bunun için GNU/Linux üzerinden "SSH İstemcisi" ile bağlantı kurulabileceği gibi Windows üzerinden "Putty" ile giriş yapabilirsiniz.

Aşağıdaki komut ile SSH protokolü kullanarak giriş yapılır:

```text
ssh sysadmin@sunucuipadresi
```

Sunucuya giriş yaptıktan sonra yetkili kullanıcı yine aynı kullanıcı ise aşağıdaki komut ile kurulum başlatılır. Sunucunun yetkili kullanıcı olmasının dışında ilgili cihazın herhangi bir debian tabanlı depo sunucusuna erişebiliyor olması gerekmektedir. Depo sunucusuna erişim yoksa kurumsal destek alınması önerilmektedir.

```text
sudo apt install -y ./kaptan_0.52.9_amd64.deb
```

Kurulum sırasında sizden aşağıdaki gibi Samba veya Aktif Dizin için bir IP adresi talep edilmektedir. Burada herhangi bir Domain Kontrolcüsü için IP adresi girmeniz yeterlidir. Bu alanı boş bırakarak daha sonra yapılandırma dosyasından da düzenleme yapabilirsiniz.

```text
Created symlink /etc/systemd/system/multi-user.target.wants/smbd.service → 
/lib/systemd/system/smbd.service. Setting up kaptan (0.52.9) ... 
Enter AD server ip:

```

## 3. Kurulum Kontrolü

### 3.a. Servisin Varlığı ve aktifliği

Kurulum sonrasında systemctl status kaptan diyerek servisin açık olup olmadığı kontrol edilebilir. Eğer active\(running\) yazıyorsa servis başarılı ile başlamıştır. İlk açıldığında herhangi bir LDAP bilgisi girilmediği için aşağıdaki gibi bir hata döndürmektedir.

```text
Nov 14 11:53:37 kaptan02 kaptan[3652]: User Session info SQL Table Created Successfully
Nov 14 11:53:37 kaptan02 kaptan[3652]: credentials file can not be open
Nov 14 11:53:37 kaptan02 kaptan[3652]: Ldap bind crendentials not found
Nov 14 11:53:37 kaptan02 kaptan[3652]: can not get policy list from database
Nov 14 11:53:37 kaptan02 kaptan[3652]: Ldap bind crendentials not found
Nov 14 11:53:37 kaptan02 kaptan[3652]: credentials file can not be open
```

### 3.b. LDAP Servis kullanıcısı bilgisi girilmesi

Kaptan'ın domain ile ilişkisi sırasında kullanacağı bir servis hesabı girilmesi gerekmektedir. Bu servis hesabının ağaçta arama yapması dışında herhangi bir yetkisi olmasına gerek yoktur. Örneğin kaptankullanici isimli bir hesap için aşağıdaki gibi kullanıcı adı ve parola bilgileri girilerek kaptan'ın altyapısına kaydedilmesi sağlanır ve servis yeniden başlatılır.

```text
root@kaptan02:/home/test# kaptan -p kaptankullanici
Password: 
Password store success
root@kaptan02:/home/test# systemctl restart kaptan
```



