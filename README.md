# RFD900_Kullanim_kilavuzu
RFD900 ile point to point ve multi-point ağ kurma 
## RFD 900 Mödülü Nedir?
![rd900x](https://github.com/Numan-Aktas/RFD900_Kullan-m_k-lavuzu/blob/main/images/rfd900x.jpg)
RFD 900x, yüksek veri iletim hızları ve uzun menzil özelliklerine sahip kablosuz bir iletişim modülüdür. Bu modül, özellikle uzaktaki cihazlar arasında veri iletimi için tasarlanmıştır. RFD 900x, genellikle insansız hava araçları (İHA), robotlar, uzaktan algılama sistemleri, endüstriyel otomasyon, tarım uygulamaları ve diğer uzun mesafe kablosuz iletişim gereksinimlerini karşılamak için kullanılır.

RFD 900x'in Temel Özellikleri:

*Yüksek Veri İletim Hızları: RFD 900x, yüksek hızlarda veri iletimine izin verir(max 264 kbps), bu da büyük veri paketlerini hızlı bir şekilde aktarabilir.

*Uzun Menzil: Bu modül, geniş bir iletişim menziline sahiptir(max 40 km), bu da cihazların uzak noktalar arasında güvenilir iletişim kurmasını sağlar.

*Zayıf Sinyal Performansı: Zayıf sinyal koşullarında bile güvenilir bir bağlantı sunar, bu da zorlu çevresel koşullar altında kullanım için uygundur.

*Çeşitli Uygulamalar: RFD 900x, çeşitli uygulamalarda kullanılabilen çok yönlü bir iletişim çözümüdür. Tarım, endüstriyel otomasyon, uzaktan algılama ve daha birçok alanda kullanılabilir.

*Kolay Entegrasyon: RFD 900x, çeşitli cihazlara ve sistemlere entegre edilmesi kolaydır ve kullanıcıların hızlı bir şekilde çalışmaya başlamasını sağlar.

## Bağlantı şeması ve Besleme
RFD 900x modülünün bir bilgisayar veya diğer cihazlarla bağlantı kurma işlemi, tipik olarak seri iletişim (UART) veya diğer uygun arayüzler aracılığıyla gerçekleştirilir. Aşağıda, bir bilgisayar ve Pixhawk (insansız hava aracı denetim ünitesi) gibi cihazlarla RFD 900x'in bağlantı kurma sürecini adım adım açıklayacağım.
![rd900x_bağlanti](https://github.com/Numan-Aktas/RFD900_Kullan-m_k-lavuzu/blob/main/images/RFD900x_FTDI_SM.jpg)

RFD 900x modülünü bilgisayarınıza bağlamak için modülün seri port (UART) çıkışını bir USB-UART dönüştürücüsüne veya uygun bir ftdi bağlantı kablosuna takın.
![rd900x_kablo](https://github.com/Numan-Aktas/RFD900_Kullan-m_k-lavuzu/blob/main/images/ba%C4%9Flant%C4%B1.png)

Başka sistemler ile bağlantı yapmak için aşağıdaki resimdeki pinout yapısını kullanabilrsiniz.
#### Not : TX-RX eşleşecek şekilde kablolama yapınız.
![rd900x_pinout](https://github.com/Numan-Aktas/RFD900_Kullan-m_k-lavuzu/blob/main/images/pinout.png)

### !!ÖNEMLİ NOT!! : ANTENLERİ TAKMADAN ENERJİ VERMEYİNİZ

RFD 900x, genellikle 4V-5,5V DC (Volt doğru akım) ve 0,5A-1A (Amper) ile beslenir. Bu, modülün doğru bir şekilde çalışabilmesi için gereken nominal gerilim ve akımdır. Bu gerilim ve akım değeri dışındaki besleme gerilimleri modülün performansını olumsuz etkileyebilir veya zarar verebilir. Ayrıca Antenler takılmadan enerji verilirse cihaz ısınarak hasar alma ihtimali yüksektir.

# Point-to-Point
![p2p](https://github.com/Numan-Aktas/RFD900_Kullan-m_k-lavuzu/blob/main/images/p2p_connect.png)

Point-to-Point bağlantı, iki cihazın (örneğin, iki RFD 900x modülü) doğrudan ve özel bir iletişim bağlantısı kurduğu bir kablosuz iletişim türüdür. Bu bağlantı türü, iki nokta arasında veri aktarımı gerektiren birçok uygulamada kullanılır.

Yazılımları yüklemek için RFD Tools gereklidir. RFD 900x ve diğer benzer cihazlar için özelleştirilmiş bir yazılım araç setidir. Bu araç seti, bu tür cihazların yapılandırılması, izlenmesi ve verilerin işlenmesi için kullanılan çeşitli yazılım uygulamalarını içerir. P2P olarak ayarlamak için cihazınızla uyumlu RFD X hardware başlığı altındaki bin dosyasını indirmeniz gerekmektedir.
### uygulama indirme linki  https://files.rfdesign.com.au/tools/
### P2P FİRMWARE indirme linki https://files.rfdesign.com.au/firmware/

![rfd_tools](https://github.com/Numan-Aktas/RFD900_Kullan-m_k-lavuzu/blob/main/images/p2p_param.png)

RFD900 cihazını point to point kullanmak için RFDTools uygulmasını açıp doğru com portunu[1] ve baudrate[2] girdikten sonra connect butonuna[3] tıklayın. ardından upload firmware butonuna[4] tıklayarak yazılımı yükleyin. firmware yüklenince yeniden başlatıp bağlandıktan sonra load settings butonuna[5] basarak parametreleri çağırın. Cihazların biribiri ile iletişim kurması için bağlanacak cihazların NET ID[6] aynı olmak zorundadır. Anten modu[7] 1:TX 2:RX olacak şekilde ayarlanmalıdır. Ayrıca sisteminizin deseklediği en yüksek Baudrate[8] hızını ayarlayarak veri iletim hızı arttıralabir. Bağlantı kalitesini arttırmak için ise TX power[9] parametresini en yüksek değere ayarlayabilirsiniz. Tüm parametreleri ayarladıktan sonra save settings[10] butonuna basarak parametreleri kaydededbilirsiniz. iki cihazada aynı işlemleri uyguladıktan sonra iki cihazada güç verildiğinde cihazın yeşil ledi sabit ve kırmızı ledi hızlı yanıp sönmeye yanmaya başlayacaktır, bu durum cihazların bağlandığını ve veri iletimi gerçekleştirdiğini belirtmektedir.

### ekstra ayarlar
max windows(ms) kaç milisaniye bir veri iletimi olacağını belirtir.değer azaltılması durumunda daha sık veri iletimi gerçekleşir. mavlink parametersi ardupilot veya px4 vb yazılımların iletişm protokülüdür. Bu tip otopilotlardan veri alabilmek için parametre açık(ON) olarak ayarlanmalıdır. AES ENCRYPTİON(GELİŞMİŞ ŞİFRELEME) cihazların yayınladığı mesajlara 126 veya 256 karakterli bir şifre uygulayarak şifreleme yapar. AES Key sahip olmayan cihazlar mesajı çözemez ve bağlantı kuramaz. Cihazaların daha güvenli çalışabilmesi için bu parametre ayarlanabilir. Bu ayarları yaparken iki cihaz birbirine bağlıysa copy required to remote butonuna basarsanız iki cihazında tüm parametrelerini aynı yapar ve değişikleri iki cihaz içinde yapmanıza gerek kalmaz.

# Multipoint Bağlantısı

![MP](https://github.com/Numan-Aktas/RFD900_Kullan-m_k-lavuzu/blob/main/images/multipoint_connection.png)

Multipoint bağlantısı, bir merkezi cihazın (MAİN) birden çok uzak düğümlerle (NODE) kablosuz iletişim kurduğu bir iletişim türüdür. Bu, birçok uygulamada kullanılan yaygın bir kablosuz iletişim konseptidir ve RFD 900x gibi cihazlarla uygulanabilir. Multipoint bağlantısının merkezi noktası, genellikle bir baz istasyonu olarak adlandırılır. Baz istasyonu cihazı, birden çok uzak cihazla iletişim kurmak ve onları kontrol etmek için kullanılır.

Yazılımları yüklemek için RFD Tools gereklidir. RFD 900x ve diğer benzer cihazlar için özelleştirilmiş bir yazılım araç setidir. Bu araç seti, bu tür cihazların yapılandırılması, izlenmesi ve verilerin işlenmesi için kullanılan çeşitli yazılım uygulamalarını içerir. MultiPoint olarak ayarlamak için cihazınızla uyumlu RFD X Multipoint SİK başlığı altındaki bin dosyasını indirmeniz gerekmektedir.
### uygulama indirme linki  https://files.rfdesign.com.au/tools/
### Mulltipoint yazılımı indirme linki https://files.rfdesign.com.au/firmware/

![rfd_tools](https://github.com/Numan-Aktas/RFD900_Kullan-m_k-lavuzu/blob/main/images/mp.png)

RFD900 cihazını point to point kullanmak için RFDTools uygulmasını açıp doğru com portunu[1] ve baudrate[2] girdikten sonra connect butonuna[3] tıklayın. ardından upload firmware butonuna[4] tıklayarak yazılımı yükleyin. firmware yüklenince yeniden başlatıp bağlandıktan sonra load settings butonuna[5] basarak parametreleri çağırın. Cihazların biribiri ile iletişim kurması için bağlanacak cihazların NET ID[6] aynı olmak zorundadır. Anten modu[7] 1:TX 2:RX olacak şekilde ayarlanmalıdır. Ayrıca sisteminizin deseklediği en yüksek Baudrate[8] hızını ayarlayarak veri iletim hızı arttıralabir. Bağlantı kalitesini arttırmak için ise TX power[9] parametresini en yüksek değere ayarlayabilirsiniz. Her cihaza bir Düğüm numarası(NODE ID)[11] verilmelidir. Ana düğüme 1 değerini vermek zorunludur. diğer düğümlerin numaraları rastgele verilebilir. HEDEF KİMLİK(DEST ID)[12] cihazın hangi düğümlere veri ileteceğini ve alacağını belirtir. Ana düğümün tüm düğümlere bağlanabilmesi için 255 değeri ayarlanmalıdır. Özel bir düğüme bağlanmak için ise bağlanılacak düğümün numarası verilebilir. Diğer düğümler ise Ana düğüme bağlanabilmesi için 1 olarak ayarlanmalıdır. AĞ Sayısı(NET COUNT)[13] bir sistemdeki Ana Düğüm sayısını belirtir. Bu değer sistemde 1 istasyon varsa 1 olarak ayarlanmalıdır. Cihazların ne tür parametre gönderdiğine bağlı olarak RX Frame[14] ayarlanmalıdır. Tüm parametreleri ayarladıktan sonra save settings[10] butonuna basarak parametreleri kaydededbilirsiniz. Sistemin Çalışması için Ana düğüm için terminal kısmından ekstra parametreler ayarlanmalıdır. 

![rfd_term](https://github.com/Numan-Aktas/RFD900_Kullan-m_k-lavuzu/blob/main/images/terminal_code.png)
terminalde işlem yapılıp yapılamadığını kontrol etmek için +++ yazılır ve terminal +++ döndürmesi gerekir. AT&M0= 0, z kodu yazılır z yerine sistemdeki düğüm sayısının bir fazlası yazılır. işlemi yazdırmak için AT&W komutu çalıştırılır ve OK yazması beklenir. ATZ komutu ilede reboot atıp işlem tamamlanır. herhangi bir adım sırasında terminal yanıt döndürmezse kodu tekrar gönderin. Cihazalara güç verildiğinde cihazların yeşil ledi sabit ve kırmızı ledi hızlı yanıp sönmeye yanmaya başlayacaktır, bu durum cihazların bağlandığını ve veri iletimi gerçekleştirdiğini belirtmektedir.

#### daha fazlası için https://files.rfdesign.com.au adresini ziyaret edebilirsiniz.
