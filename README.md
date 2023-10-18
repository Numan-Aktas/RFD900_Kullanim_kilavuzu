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
#### Not : TX-RX eşlecek şekilde kablolama yapınız.
![rd900x_pinout](https://github.com/Numan-Aktas/RFD900_Kullan-m_k-lavuzu/blob/main/images/pinout.png)

### !!ÖNEMLİ NOT!! : ANTENLERİ TAKMADAN ENERJİ VERMEYİNİZ

RFD 900x, genellikle 4V-5,5V DC (Volt doğru akım) ve 0,5A-1A (Amper) ile beslenir. Bu, modülün doğru bir şekilde çalışabilmesi için gereken nominal geril ve akımdır. Bu gerilim ve akım değeri dışındaki besleme gerilimleri modülün performansını olumsuz etkileyebilir veya zarar verebilir. Ayrıca Antenler takılmadan enerji verilirse cihaz ısınarak hasar alma ihtimali yüksektir.

# Point-to-Point

Point-to-Point bağlantı, iki cihazın (örneğin, iki RFD 900x modülü) doğrudan ve özel bir iletişim bağlantısı kurduğu bir kablosuz iletişim türüdür. Bu bağlantı türü, iki nokta arasında veri aktarımı gerektiren birçok uygulamada kullanılır.

Yazılımları yüklemek için RFD Tools gereklidir. RFD 900x ve diğer benzer cihazlar için özelleştirilmiş bir yazılım araç setidir. Bu araç seti, bu tür cihazların yapılandırılması, izlenmesi ve verilerin işlenmesi için kullanılan çeşitli yazılım uygulamalarını içerir
### uygulama indirme linki  https://files.rfdesign.com.au/tools/

