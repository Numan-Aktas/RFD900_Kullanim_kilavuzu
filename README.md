# RFD900 Kullanım Kılavuzu

RFD900 ile point-to-point ve multi-point ağ kurma işlemlerini açıklayan bu kılavuz, RFD900X modülünün nasıl kullanılacağına dair adım adım talimatlar sunmaktadır.

## RFD 900 Modülü Nedir?

![rfd900x](https://github.com/Numan-Aktas/RFD900_Kullan-m_k-lavuzu/blob/main/images/rfd900x.jpg)

RFD900X, yüksek veri iletim hızları ve uzun menzil özelliklerine sahip kablosuz bir iletişim modülüdür. Genellikle insansız hava araçları (İHA), robotlar, uzaktan algılama sistemleri ve endüstriyel otomasyon gibi uzun mesafe kablosuz iletişim gereksinimlerini karşılamak için kullanılır.

### RFD900X'in Temel Özellikleri:
- **Yüksek Veri İletim Hızları**: RFD900X, maksimum 264 kbps hızında veri iletebilir.
- **Uzun Menzil**: 40 km'ye kadar güvenilir iletişim sağlar.
- **Zayıf Sinyal Performansı**: Zayıf sinyal koşullarında bile güvenilir bir bağlantı sunar.
- **Çeşitli Uygulamalar**: Tarım, endüstriyel otomasyon ve uzaktan algılama gibi birçok alanda kullanılabilir.
- **Kolay Entegrasyon**: Farklı sistem ve cihazlara entegrasyonu kolaydır.

---

## Bağlantı Şeması ve Besleme

RFD900X modülünün bir bilgisayar veya başka cihazlarla bağlantısı seri iletişim (UART) kullanılarak yapılır. Aşağıda bilgisayar ve Pixhawk gibi cihazlarla bağlantı şeması gösterilmektedir:

![rd900x_bağlanti](https://github.com/Numan-Aktas/RFD900_Kullan-m_k-lavuzu/blob/main/images/RFD900x_FTDI_SM.jpg)

Modül, seri port çıkışı (UART) üzerinden bir USB-UART dönüştürücüsüne bağlanarak bilgisayara entegre edilir.

![rd900x_kablo](https://github.com/Numan-Aktas/RFD900_Kullan-m_k-lavuzu/blob/main/images/ba%C4%9Flant%C4%B1.png)

Bağlantı yaparken pinout yapısını aşağıdaki şemaya göre gerçekleştirin. 
**Not**: TX ve RX pinlerinin doğru eşleştirildiğinden emin olun.

![rd900x_pinout](https://github.com/Numan-Aktas/RFD900_Kullan-m_k-lavuzu/blob/main/images/pinout.png)

### ÖNEMLİ NOT: ANTENLERİ TAKMADAN ENERJİ VERMEYİNİZ

RFD900X, 4-5.5V DC gerilim ve 0.5-1A akım ile beslenmelidir. Antenler takılmadan enerji verilmesi, cihazın zarar görmesine neden olabilir.

---

## Point-to-Point Bağlantısı

![p2p](https://github.com/Numan-Aktas/RFD900_Kullan-m_k-lavuzu/blob/main/images/p2p_connect.png)

Point-to-point bağlantı, iki RFD900X modülü arasında doğrudan iletişim sağlayan bir kablosuz bağlantı türüdür. Bu bağlantı, iki nokta arasında güvenilir veri iletimi için kullanılır.

### Gerekli Yazılımlar ve Firmware:
RFD900X modülünü yapılandırmak için RFD Tools ve uygun firmware dosyaları gerekmektedir.
- **Uygulama İndirme Linki**: [RFD Tools](https://files.rfdesign.com.au/tools/)
- **P2P Firmware İndirme Linki**: [P2P Firmware](https://files.rfdesign.com.au/firmware/)

![rfd_tools](https://github.com/Numan-Aktas/RFD900_Kullan-m_k-lavuzu/blob/main/images/p2p_param.png)

### Point-to-Point Bağlantı Ayarları:
1. RFD Tools uygulamasını açın, doğru COM portunu ve baudrate'i seçin, ardından **Connect** butonuna tıklayın.
2. **Upload Firmware** butonuna basarak gerekli P2P yazılımını yükleyin.
3. **Load Settings** butonuna tıklayarak cihaz parametrelerini yükleyin.
4. Her iki cihazın **NET ID**'sini aynı yapın ve anten modunu ayarlayın (1: TX, 2: RX).
5. Sisteminizin desteklediği en yüksek baudrate değerini girin ve **TX Power**'ı maksimum seviyeye ayarlayın.
6. Ayarlar tamamlandığında **Save Settings** butonuna basarak parametreleri kaydedin.

### Ek Ayarlar:
- **Max Windows (ms)**: Veri iletim sıklığını belirler.
- **MAVLink Parameters**: ArduPilot ve PX4 gibi otopilot sistemlerinin veri alışverişi için kullanılır.
- **AES Encryption**: İletilen verilerin şifrelenmesi için kullanılır.

---

## Multi-Point Bağlantısı

![MP](https://github.com/Numan-Aktas/RFD900_Kullan-m_k-lavuzu/blob/main/images/multipoint_connection.png)

Multipoint bağlantı, merkezi bir cihazın (MAIN) birden fazla düğüm (NODE) ile kablosuz iletişim kurduğu bir yapıdadır. Bu yapı, baz istasyonu cihazı olarak da bilinir ve birçok uzak düğümle veri iletimi sağlar.

### Gerekli Yazılımlar ve Firmware:
Multipoint bağlantıyı ayarlamak için uygun firmware gereklidir:
- **Uygulama İndirme Linki**: [RFD Tools](https://files.rfdesign.com.au/tools/)
- **Multipoint Firmware İndirme Linki**: [Multipoint Firmware](https://files.rfdesign.com.au/firmware/)

![rfd_tools](https://github.com/Numan-Aktas/RFD900_Kullan-m_k-lavuzu/blob/main/images/mp.png)

### Multi-Point Bağlantı Ayarları:
1. RFD Tools'u açın, COM portu ve baudrate'i seçerek **Connect** butonuna basın.
2. **Upload Firmware** ile uygun yazılımı yükleyin ve cihazı yeniden başlatın.
3. **Load Settings** butonu ile parametreleri yükleyin.
4. **NET ID** aynı olacak şekilde tüm düğümleri ayarlayın ve her düğüme bir **Node ID** verin (Ana düğüm için Node ID=1).
5. **DEST ID**: Ana düğüm için 255 olarak ayarlayın (tüm düğümlerle iletişim için).
6. **NET COUNT**: Sistemde kaç ana düğüm olduğunu belirtir. Tek baz istasyonu varsa bu değer 1 olmalıdır.

### Terminal Üzerinden Ekstra Ayarlar:
Terminale **+++** yazarak bağlandığınızı kontrol edin, ardından:
- **AT&M0=0,z** komutunu kullanın. Z yerine sistemdeki düğüm sayısının bir fazlasını yazın.
- Ayarları kaydetmek için **AT&W** komutunu çalıştırın.
- **ATZ** komutu ile cihazı yeniden başlatın.

![rfd_term](https://github.com/Numan-Aktas/RFD900_Kullan-m_k-lavuzu/blob/main/images/terminal_code.png)

Ayarlar doğru şekilde yapıldığında, cihazların yeşil ledi sabit yanacak ve kırmızı ledi hızlı yanıp sönmeye başlayacaktır. Bu, cihazların başarılı şekilde bağlandığını ve veri iletimi yaptığını gösterir.

---

## Daha Fazlası İçin
Daha fazla bilgi ve indirmeler için [RFD Design](https://files.rfdesign.com.au) sayfasını ziyaret edebilirsiniz.
