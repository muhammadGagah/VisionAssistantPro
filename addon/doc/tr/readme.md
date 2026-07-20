# Profesyonel Görsel Asistan Belgeleri

**Profesyonel Görsel Asistan**, NVDA için gelişmiş, çok modlu bir yapay zekâ asistanıdır. Akıllı ekran okuma, çeviri, sesli dikte ve belge analizi sağlamak için dünya çapında yapay zekâ motorlarından yararlanır.

**Bu eklenti, Dünya Engelliler Günü onuruna topluluğa sunulmuştur.**

## 1. Kurulum ve Yapılandırma

**NVDA Menüsü > Tercihler > Ayarlar > Profesyonel Görsel Asistan** yolunu izleyin.

### 1.1 Bağlantı Ayarları

* **Sağlayıcı:** Tercih ettiğiniz yapay zekâ hizmetini seçin. Desteklenen sağlayıcılar: **Google Gemini**, **OpenAI**, **Mistral**, **Groq** ve **Özel** (Ollama / LM Studio gibi OpenAI uyumlu sunucular).
* **Önemli Not:** En iyi performans ve doğruluk için (**özellikle resim/dosya analizi** konusunda) **Google Gemini** kullanmanızı şiddetle öneririz.
* **API Anahtarı:** Zorunludur. Otomatik döndürme için birden fazla anahtar (virgül veya yeni satırla ayrılmış) girebilirsiniz.
* **Modelleri Al:** API anahtarınızı girdikten sonra, sağlayıcıdan mevcut en güncel model listesini indirmek için bu düğmeye basın.
* **Yapay Zekâ Modeli:** Genel sohbet ve analiz için kullanılacak ana modeli seçin.

### 1.2 Gelişmiş Model Yönlendirme (Yerel Sağlayıcılar)

*Gemini, OpenAI, Groq ve Mistral için kullanılabilir.*

> **⚠️ Uyarı:** Bu ayarlar **yalnızca ileri düzey kullanıcılar** içindir. Belirli bir modelin ne yaptığından emin değilseniz, lütfen bunu **işaretlemeyin**. Bir görev için uyumsuz bir model seçmek (örneğin Görsel analiz için yalnızca metin modeli) hatalara yol açar ve eklentinin çalışmasını durdurur.

Ayrıntılı denetimi açmak için **“Gelişmiş Model Yönlendirme (Göreve özgü)”** seçeneğini işaretleyin. Bu, farklı görevler için açılır listeden belirli modeller seçmenize olanak tanır:

* **OCR / Görsel Model:** Görselleri analiz etmek için özel bir model seçin.
* **Konuşmadan Metne (STT):** Dikte için belirli bir model seçin.
* **Metinden Konuşmaya (TTS):** Ses üretimi için bir model seçin.
* **Yapay Zeka Operatör Modeli:** Otonom bilgisayar operasyon görevleri için belirli bir model seçin.
* **Video Modeli:** Video analizi ve sesli betimleme oluşturma için belirli bir model seçin.
  *Not: Desteklenmeyen özellikler (ör. Groq için TTS) otomatik olarak gizlenir.*

### 1.3 Gelişmiş Uç Nokta Yapılandırması (Özel Sağlayıcı)

*Yalnızca “Özel” seçildiğinde kullanılabilir.*

> **⚠️ Uyarı:** Bu bölüm manuel API yapılandırmasına izin verir ve yerel sunucular veya proxy’ler çalıştıran **ileri seviye kullanıcılar** için tasarlanmıştır. Hatalı URL’ler veya model adları bağlantıyı bozacaktır. Bu uç noktaların ne olduğunu tam olarak bilmiyorsanız, bunu **işaretlemeden bırakın**.

**“Gelişmiş Uç Nokta Yapılandırması”** seçeneğini işaretleyerek sunucu ayrıntılarını manuel olarak girin. Yerel sağlayıcılardan farklı olarak burada belirli URL’leri ve model adlarını **manuel olarak yazmanız** gerekir:

* **Model Listesi URL’si:** Mevcut modelleri almak için kullanılan uç nokta.
* **OCR/STT/TTS Uç Nokta URL’si:** Belirli hizmetler için tam URL’ler (ör. `http://localhost:11434/v1/audio/speech`).
* **Özel Modeller:** Her görev için model adını manuel olarak yazın (ör. `llama3:8b`).

### 1.3.1 Yerel YZ'yı Kurma (Tek Adımlı Yapılandırma)
Yerel ve tamamen çevrimdışı YZ entegrasyonunu son derece basit hale getirmek için, Özel Sağlayıcı Ayarları içinde özel bir **“Yerel YZ'yı Kur”** düğmesi bulunmaktadır.

Bilgisayarınızda yerel bir YZ modeli sunucusu çalıştırıyorsanız:
1. Sağlayıcı olarak **Özel**'i seçin.
2. **Yerel YZ'yı Kur** düğmesine basın.
3. Açılan iletişim kutusundan yerel YZ motorunuzu seçin:
   - **Ollama** (varsayılan olarak `http://127.0.0.1:11434`)
   - **LM Studio** (varsayılan olarak `http://127.0.0.1:1234`)
   - **Jan.ai** (varsayılan olarak `http://127.0.0.1:1337`)
   - **KoboldCPP** (varsayılan olarak `http://127.0.0.1:5001`)
4. Eklenti, doğru yerel URL'yi ve API türünü anında yapılandıracak ve **YZ Model** seçim kutusunu doldurmak için aktif çevrimdışı modellerinizi otomatik olarak getirecektir.

*Ağ ve Proxy'ler Hakkında Not:* Bu yerel bağlantı motoru, gelişmiş bir proxy atlama mekanizmasına sahiptir. Aktif bir sistem VPN'i veya TUN modu proxy'si çalıştırıyor olsanız bile, yerel AI istekleriniz bunu tamamen atlayarak 502 Bad Gateway hataları olmadan istikrarlı çevrimdışı bağlantılar sağlar.

### 1.4 Genel Tercihler

* **OCR Motoru:** Hızlı sonuçlar için **Chrome (Hızlı)** veya üstün düzen koruması için **Gemini (Biçimlendirilmiş)** seçeneklerinden birini seçin.
* **TTS Sesi:** Tercih ettiğiniz ses stilini seçin. Bu liste etkin sağlayıcıya göre dinamik olarak güncellenir.
* **Yaratıcılık (Sıcaklık):** Yapay zekânın rastgeleliğini kontrol eder. Düşük değerler doğru çeviri/OCR için daha uygundur.
* **Proxy URL’si:** Bölgenizde yapay zekâ hizmetleri kısıtlıysa yapılandırın ( `127.0.0.1` gibi yerel proxy’ler veya köprü URL’leri desteklenir).
* **Doğrudan Çıktı (Sohbet Penceresi Yok):** Yapay zekanın etkileşimli bir sohbet penceresi açmadan sonucu basitçe yüksek sesle okumasını istiyorsanız bunu işaretleyin.
* **Yapay zeka yanıtlarını panoya kopyala:** Kolay yapıştırma için her yapay zeka yanıtını sistem panonuza otomatik olarak kopyalar.
* **Sohbette İşaretlemeyi Temizle:** Temiz, biçimlendirilmiş metin görünümü yerine ham biçimlendirme sembollerini görmeyi tercih ediyorsanız bu seçeneğin işaretini kaldırın.

## 2. Komut Katmanı ve Kısayollar

Klavye çakışmalarını önlemek için bu eklenti bir **Komut Katmanı** kullanır.

1. Katmanı etkinleştirmek için **NVDA + Shift + V** (Ana Tuş) kombinasyonuna basın (bir bip sesi duyarsınız).
2. Tuşları bırakın ve ardından aşağıdaki tek tuşlardan birine basın:

| Tuş           | İşlev                    | Açıklama                                                                              |
| ------------- | ------------------------ | ------------------------------------------------------------------------------------- |
| **Shift + A** | **Yapay Zeka Operatörü**         | **Otonom Operasyon:** Yapay zekaya ekranınızda bir görev gerçekleştirmesini söyleyin.      |
| **E**         | **Kullanıcı Arayüzü Gezgini**          | **Etkileşimli Tıklama:** Herhangi bir uygulamadaki kullanıcı arayüzü öğelerini tanımlar ve tıklar.        |
| **T**         | Akıllı Çeviri          | Dolaşım imleci altındaki metni veya seçimi çevirir.                                    |
| **Shift + T** | Panodan Çeviri           | Panodaki içeriği çevirir.                                                             |
| **R**         | Metin İyileştirici       | Özetleme, dilbilgisi düzeltme, açıklama veya **Özel İstemler** çalıştırır.            |
| **V**         | Nesne Görsel Analizi     | Geçerli Dolaşım nesnesini betimler.                                                     |
| **O**         | Tam Ekran Görsel Analizi | Tüm ekran düzenini ve içeriğini analiz eder.                                          |
| **Shift + V** | Çevrim İçi Video Analizi | **YouTube**, **Instagram**, **TikTok** veya **Twitter (X)** videolarını analiz eder.  |
| **Control + V** | Yerel Video Kaydı  | Ekranınızın sessiz bir videosunu kaydeder ve eylemleri ve düzeni analiz eder.  |
| **D**         | Belge Okuyucu            | Sayfa aralığı seçimi olan PDF ve görseller için gelişmiş okuyucu.                     |
| **F**         | **Akıllı Dosya Eylemi**    | Seçilen görüntü, PDF veya TIFF dosyalarından bağlama duyarlı tanıma.          |
| **A**         | Ses Dökümü               | MP3, WAV veya OGG dosyalarını metne dönüştürür.                                       |
| **C**         | CAPTCHA Çözücü           | CAPTCHA’ları yakalar ve çözer (Kamu portalları desteklenir).                          |
| **S**         | Akıllı Dikte             | Konuşmayı metne dönüştürür. Başlatmak için basın, durdurmak/yazmak için tekrar basın. |
| **Kontrol+L** | **Live Assistant**       | **Gerçek Zamanlı Yardımcı Pilot (yalnızca Gemini):** Yapay zeka asistanıyla canlı sesli ve ekran görüşmesini başlatır veya bitirir. |
| **I**         | Durumu Seslendir          | Geçerli durumu bildirir (ör. “Taranıyor…”, “Boşta”).                                  |
| **L**         | **Nesne Etiketleme**         | **Anlamsal Yapay Zeka Etiketleme:** Odaklanılan geçerli öğeyi/simgeyi kalıcı olarak etiketler. |
| **Shift + L** | **Etiketleri Yönet/Tara**   | Etiket Yöneticisini açar (etiketler varsa) veya uygulamayı adsız öğelere karşı tarar. |
| **U**         | Güncellemeleri Denetle      | Eklentinin en son sürümü için GitHub’ı manuel olarak kontrol eder.                    |
| **Boşluk Çubuğu**     | Son Sonucu Çağır         | Son yapay zekâ yanıtını inceleme veya devam için sohbet penceresinde gösterir.        |
| **H**         | Komut Yardımı            | Komut katmanındaki tüm kısayolların listesini gösterir.                               |
| **Alt + S**   | Ayarlar                 | Profesyonel Görsel Asistan Ayarları iletişim kutusunu açar.                             |
| **Alt + Q**   | Günlük kotası tükenmiş anahtarları bildirir. | Günlük kotasını aşan Gemini API anahtarlarının sayısını ve sıfırlama sürelerini bildirir. |
| **Alt + M**   | Yönlendirme Denetimi            | Gelişmiş yönlendirmede seçili olan YZ modellerini bildirir.               |

## 3. Yapay Zekâ Operatörü - Otonom Bilgisayar Kontrolü

**Yapay Zekâ Operatörü**, Profesyonel Görsel Asistan'ı pasif bir okuyucudan bilgisayarınızla sizin adınıza etkileşim kurabilen aktif bir asistana dönüştürür. Ekranı betimlemesini isteyebilir, gördükleri hakkında sorular sorabilir veya hatta kontrolü devralmasını sağlayabilirsiniz; düğmelere tıklayabilir, öğeleri sürükleyebilir, metin yazabilir ve doğal dil komutlarını kullanarak uygulamalar arasında dolaşabilir.

En büyük avantajı ne mi? Tamamen erişilemez yazılımlarda kusursuz şekilde çalışır. Özel bir uygulamada, uzak masaüstünde veya ekran okuyucunuzun tamamen sustuğu bir web sitesinde takılıp kaldıysanız, operatör için bu bir sorun değildir. Çünkü ekranı görsel olarak "gördüğü" için erişilebilirlik etiketi bulunmayan öğeleri bulabilir, okuyabilir ve onlarla etkileşim kurabilir.

### Nasıl Çalışır

1. **NVDA + Shift + V** tuşlarına basın, ardından Yapay Zekâ Operatörü iletişim kutusunu açmak için **Shift + A** tuşuna basın (veya doğrudan kısayolu kullanın).
2. Yapmak istediğiniz işlemi düz bir dille yazın (örneğin, "Kaydet düğmesine tıkla", "Hata iletisinde ne yazıyor?" veya "Dosyanın adını final.pdf olarak değiştir").
3. Yapay zekâ ekranınızı analiz edecek, ilgili öğeleri belirleyecek ve işlemi gerçekleştirecek veya yanıtı sağlayacaktır. Bir görev birden fazla adım gerektiriyorsa, operatör görev tamamlanana kadar çalışmaya devam eder.
4. Devam eden bir işlemi anında durdurmak için istediğiniz zaman tekrar **Shift + A** tuşuna basın.

### Desteklenen İşlemler

Operatör çok çeşitli komutları anlayabilir:

* **Betimleme ve Yanıtlama:** "Ekran düzenini Betimle" veya "Hata iletisinde ne yazıyor?"
* **Tıklama:** "Kaydet düğmesine tıkla"
* **Sağ Tıklama:** "Dosyaya sağ tıkla"
* **Çift Tıklama:** "Belgeye çift tıkla"
* **Sürükle ve Bırak:** "Belgeyi Arşiv klasörüne sürükle"
* **Yazma:** "Arama kutusuna 'Merhaba Dünya' yaz"
* **Kaydırma:** "Üç kez aşağı kaydır"
* **Tuş Basımı:** "Enter tuşuna bas", "Tab tuşuna bas", "Escape tuşuna bas"
* **Çok Adımlı Görevler:** "Dosya Gezgini'ni aç, raporu bul ve adını final.pdf olarak değiştir"

### Önemli Notlar

* **⚠️ API Kullanım Uyarısı:** Operatörün ekranda tam olarak neler olduğunu "görebilmesi" gerektiğinden, her adımda yüksek çözünürlüklü bir ekran görüntüsü gönderilir. Sık kullanım, standart metin tabanlı özelliklere kıyasla API kotanızı çok daha hızlı tüketecektir.
* **Yönetici Uygulamaları:** NVDA yönetici ayrıcalıklarıyla çalışmıyorsa, operatör yükseltilmiş izinler gerektiren pencerelerle etkileşim kuramayabilir. Bu, Windows'un güvenlik sınırlamasıdır, eklentideki bir hata değildir.
* **En İyi Uygulamalar:** En iyi sonuçlar için açık ve belirgin komutlar verin. "Formun altındaki mavi Gönder düğmesine tıkla" komutu, yalnızca "Düğmeye tıkla" demekten neredeyse her zaman daha iyi sonuç verir.

## 4. Video Analizi ve Sesli Betimleme

> **Not:** Video Analizi ve Sesli Betimleme özellikleri yalnızca **Google Gemini** sağlayıcısı tarafından desteklenmektedir. Eklenti ayarlarında etkin sağlayıcınızın Google Gemini olarak ayarlandığından emin olun.

Profesyonel Görsel Asistan, özellikle kör kullanıcılar için tasarlanmış güçlü video işleme yetenekleri sunar. Hem çevrim içi videoları hem de yerel ekran kayıtlarını analiz ederek son derece ayrıntılı görsel betimlemeler sağlayabilir ve profesyonel Sesli Betimleme betikleri (SRT) oluşturabilir.

### 4.1 Yerel Ekran Kaydı (Control + V)

Ekranınızda sessiz bir video, animasyon veya eğitim videosuyla karşılaşırsanız, bunu doğrudan kaydedebilirsiniz:

1. Komut Katmanına girmek için **NVDA + Shift + V** tuşlarına basın, ardından **Control + V** tuşlarına basın.
2. Eklenti ekranınızı arka planda sessizce kaydetmeye başlayacaktır.
3. Kaydı durdurmak için tekrar **Control + V** tuşlarına basın.
4. Yapay zekâ daha sonra kaydedilen video bölümünü analiz edecek ve sahne, karakterler ve eylemler hakkında son derece ayrıntılı bir betimleme sunacaktır.

### 4.2 Video Analizi (Shift + V)

Hem yerel video dosyalarını hem de çevrim içi videoları analiz edebilirsiniz. Windows Gezgini'nde bir yerel video dosyası seçin veya çevrim içi bir video bağlantısını panonuza kopyalayın. Ayrıca herhangi bir yerde (örneğin bir medya oynatıcısının içinde) **Shift + V** tuşlarına basarak bir video dosyası seçebileceğiniz veya bir URL'yi el ile yapıştırabileceğiniz bir iletişim kutusu açabilirsiniz.

* **Desteklenen Çevrim İçi Platformlar:** YouTube, Instagram, TikTok ve Twitter (X).
* Yapay zekâ yerel dosyayı veya URL'yi otomatik olarak algılayacak, videoyu işleyecek ve kapsamlı bir görsel betimleme ile sesli özet sunacaktır.

### 4.3 Sesli Betimleme Oluşturma (SRT)

Daha yapılandırılmış bir deneyim için eklenti, standart SubRip (SRT) biçiminde profesyonel Sesli Betimleme betikleri oluşturabilir.

* **Akıllı Boşluk Zamanlaması:** Yapay zekâ ses parçasını dinler ve görsel açıklamalarını özellikle doğal duraklamalara ve sessiz boşluklara yerleştirerek diyalog çakışmalarını akıllıca en aza indirir.
* **Karakter Takibi:** Motor, değişmeyen yüz özelliklerine göre farklı karakterleri çıkarmak için ön analiz gerçekleştirir. Farklı sahnelerde karakterleri karışıklık olmadan doğru şekilde takip edip etiketlemek için genel bir sözlük oluşturur.
* **Bire Bir Metin OCR:** Ekranda görünen tüm metinler (tabelalar, telefonlar, jenerikler) bire bir alıntılanır.
* **Nasıl Kullanılır:** Oluşturulan altyazıyı dinlemek için `.srt` dosyasını video dosyanızla aynı klasöre yerleştirin ve tam olarak aynı adı verin. Ardından medya oynatıcınızı (örneğin VLC veya PotPlayer), oynatma sırasında altyazı metnini doğrudan ekran okuyucunuza veya TTS motorunuza yönlendirecek şekilde yapılandırın.

### 4.4 Eşzamanlı Sesli Betimleme (MP3 Dışa Aktarma)

Eklenti yalnızca metin tabanlı SRT dosyaları oluşturmakla kalmaz, aynı zamanda betimlemeleri konuşmaya dönüştürüp videoyla birleştirerek eksiksiz bir Sesli Betimleme üretim aracı olarak çalışır. Yerel video dosyaları için MP3 oluştururken birden fazla karıştırma modu kullanılabilir:

* **Standart AD (Sesi Karıştır):** Betimleme doğrudan videonun sesi üzerine eklenir. Betimlemenin net olmasını sağlamak için **Ses Bastırma (Audio Ducking)** uygulanmasını isteyip istemediğiniz sorulacaktır (betimlemeler sırasında arka plan sesinin azaltılması).
* **Genişletilmiş AD (Sesi Duraklat):** Motor, betimlemeler sırasında videonun orijinal sesini duraklatır ve böylece ne orijinal diyaloğun ne de yapay zekâ anlatımının tek bir kelimesini bile kaçırmazsınız.
* **YouTube Videoları:** YouTube kaynakları için (yerel olarak indirilmeyen videolar), MP3 dışa aktarma yalnızca eşzamanlı yapay zekâ ses parçasını içerir, arka plan video sesi bulunmaz.

## 5. Gelişmiş Belge ve Görüntü Okuyucu

Profesyonel Görsel Asistan, çok sayfalı PDF'ler, karmaşık görüntüler ve hatta iPhone HEIC biçimleri için tasarlanmış son derece optimize edilmiş bir Belge Okuyucu içerir.

### 5.1 Toplu İşleme ve Devam Etme

Büyük bir belgeyi tek seferde okumak zorunda değilsiniz. Bir sayfa aralığı girin (örneğin, `1-20`), yapay zekâ tüm sayfaları arka planda işleyecektir. NVDA çökerse veya taramayı keserseniz, eklenti ilerlemenizi hatırlayacak ve tam olarak kaldığı yerden **Devam Etmeyi** önerecektir!

### 5.2 Akıllı Dosya İşlemi

Belgeyi her zaman önce açmanız gerekmez. Windows Dosya Gezgini'nde bir PDF veya görüntü dosyasını seçin ve Komut Katmanında **D** (Belge Okuyucu) veya **F** (Akıllı Dosya İşlemi) tuşuna basın. Eklenti dosya iletişim kutusunu anında atlayacak ve seçili dosyayı işlemeye başlayacaktır.

### 5.3 Belge Görüntüleyici Kısayolları

Belge Okuyucu penceresi açıkken aşağıdaki kısayolları kullanabilirsiniz:

* **Ctrl + Sayfa Aşağı:** Sonraki sayfaya gider.
* **Ctrl + Sayfa Yukarı:** Önceki sayfaya gider.
* **Alt + A:** Belge hakkında soru sormak için sohbet penceresi açar.
* **Alt + R:** Etkin sağlayıcıyı kullanarak **Yapay Zekâ ile Yeniden Tarar**.
* **Alt + G:** Yüksek kaliteli bir ses dosyası (WAV/MP3) oluşturur ve kaydeder. *Sağlayıcı TTS desteklemiyorsa gizlenir.*
* **Alt + S / Ctrl + S:** Çıkarılan metni TXT veya HTML olarak kaydeder.

## 6. Anlamsal Yapay Zekâ Etiketleme ve Arayüz Gezgini

Her yerde "etiketsiz düğme" bulunan bir uygulamada mı takıldınız? Anlamsal Yapay Zekâ Etiketleme motoru bunu kalıcı olarak çözer.

### 6.1 Kalıcı Nesne Etiketleme (L)

Ekran okuyucunuzun odağını etiketsiz bir grafik veya düğme üzerine getirin ve Komut Katmanında **L** tuşuna basın. Yapay zekâ düğmeye görsel olarak bakacak, işlevini belirleyecek ve kalıcı bir etiket uygulayacaktır.
*Eski ekran okuyucu etiketleme araçlarının aksine, bu eklenti gelişmiş hibrit bir "Nesne İmzası" sistemi (AutomationId/ControlID) kullanır. Özel etiketleriniz pencere boyutu değişikliklerinden, monitör değiştirmeden ve uygulama güncellemelerinden etkilenmeden korunacaktır!*

### 6.2 Tam Uygulama Taraması (Shift + L)

Tüm etkin pencereyi tek seferde taramak için **Shift + L** tuşuna basın. Yapay zekâ tüm etiketsiz öğeleri bulacak ve hepsini tek seferde akıllıca adlandıracaktır. Daha sonra bu etiketleri yerleşik Etiket Yöneticisi üzerinden yönetebilir, yeniden adlandırabilir veya toplu olarak silebilirsiniz.

### 6.3 Arayüz Gezgini (E)

Bir öğeyle ona el ile gitmeden etkileşim kurmanız mı gerekiyor? Arayüz Gezginini etkinleştirmek için **E** tuşuna basın. Yapay zekâ ekranı tarayacak ve tıklanabilir tüm öğelerin erişilebilir bir listesini oluşturacaktır (görev çubuğu gibi sistem gürültülerini yok sayarak). Listeden bir öğe seçin; eklenti sizin için anında o öğeye tıklayacaktır.

## 7. Canlı Sesli Asistan

Canlı Asistan, Profesyonel Görsel Asistan'ı gerçek zamanlı, etkileşimli bir yardımcı pilota dönüştürür.
*(Not: Bu özellik yalnızca Google Gemini ve Gemini uyumlu Özel sağlayıcılara özeldir.)*

* **Etkinleştirme:** Canlı Asistan iletişim kutusunu açmak için Komut Katmanında **Control + L** tuşlarına basın.
* **Gerçek Zamanlı Etkileşim:** Mikrofonunuz aracılığıyla doğal şekilde konuşun. Yapay zekâ aynı anda hem sesinizi dinleyecek hem de etkin ekranınıza bakacaktır. "Şu anda neye bakıyorum?" veya "Üçüncü paragrafı bana oku." gibi sorular sorabilirsiniz.
* **Özelleştirme:** İletişim kutusu içinde yapay zekânın Ses Stilini (örneğin Profesyonel, Samimi, Enerjik) değiştirebilir ve yanıt vermeden önce ne kadar derin düşündüğünü kontrol etmek için "Düşünme Derinliğini" ayarlayabilirsiniz.

## 8. Özel İstemler ve Değişkenler

İstemleri **Ayarlar > İstemler > İstemleri Yönet…** yolundan yönetebilirsiniz.

### Desteklenen Değişkenler

* `[selection]`: Geçerli seçili metin.
* `[clipboard]`: Pano içeriği.
* `[clipboard_image]`: Şu anda panoda olan resim.
* `[screen_obj]`: Gezgin nesnesinin ekran görüntüsü.
* `[screen_fg_obj]`: Etkin ön plan penceresinin ekran görüntüsü.
* `[screen_full]`: Tam ekran görüntüsü.
* `[file_ocr]`: Metin çıkarımı için görsel/PDF dosyası seç.
* `[file_read]`: Okuma için belge seç (TXT, Kod, PDF).
* `[file_audio]`: Analiz için ses dosyası seç (MP3, WAV, OGG).
* `{target_lang}`: Geçerli hedef dil.
* `{source_lang}`: Geçerli kaynak dil.
* `{response_lang}`: Mevcut YZ yanıt dili.
* `{swap_target}`: Akıllı takas çevirisi için yedek dil.
* `{swap_instruction}`: Akıllı takas çeviri talimat bloğu.

## 9. Gerçek Dünya Kullanım Senaryoları (Hangi özelliği kullanmalıyım?)

Profesyonel Görsel Asistan gelişmiş araçlarla doludur. Doğru özelliği seçmenize yardımcı olmak için işte bazı yaygın senaryolar:

* **Senaryo: Karmaşık bir pencerenin veya erişilemeyen bir uygulamanın tüm düzenini anlamak istiyorsunuz.**
  *Çözüm:* **O** tuşuna basın (Tam Ekran Görüşü). Yapay zekâ tüm ekranı analiz edecek ve öğelerin, metinlerin ve düğmelerin tam olarak nerede bulunduğunu açıklayacaktır.

* **Senaryo: Bir web sayfasında bir resim veya bir belgede etiketsiz bir grafik buldunuz.**
  *Çözüm:* Gezgin nesnenizi grafiğin üzerine getirin ve **V** tuşuna basın (Nesne Görüşü). Yapay zekâ bu görüntünün tam olarak neler içerdiğini açıklayacaktır.

* **Senaryo: Bir filmi veya video klibi sesli betimlemeyle izlemek istiyorsunuz.**
  *Çözüm:* Videonuz üzerinde **Shift + V** tuşlarına basın ve **"Sesli Betimleme Oluştur (SRT Dosyası)"** seçeneğini seçin. İşlem tamamlandığında **"Eşzamanlı Anlatım Oluştur (MP3)"** seçeneğine tıklayın ve **"Genişletilmiş AD"** seçeneğini belirleyin. Eklenti, görsel sahneleri açıklamak için filmin diyaloglarını akıllıca duraklatan bir ses parçası oluşturacaktır.

* **Senaryo: Tamamı "etiketsiz düğmelerle" dolu bir uygulamayla karşılaştınız.**
  *Çözüm:* Belirli düğmeyi yapay zekâ kullanarak kalıcı olarak etiketlemek için **L** tuşuna basın. Ya da tüm pencereyi tek seferde tarayıp etiketlemek için **Shift + L** tuşlarına basın. Yalnızca hızlıca bir öğeye tıklamak istiyorsanız, tıklanabilir tüm öğelerin listesini almak için **E** tuşuna basın (Arayüz Gezgini).

* **Senaryo: Erişilemeyen bir CAPTCHA'yı aşmanız gerekiyor.**
  *Çözüm:* **C** tuşuna basın (CAPTCHA Çözücü). Yapay zekâ CAPTCHA'yı otomatik olarak yakalayacak, çözecek ve yanıtı doğru alana girecektir.

* **Senaryo: 50 sayfalık uzun bir PDF belgesini okumak istiyorsunuz.**
  *Çözüm:* **D** tuşuna basın (Belge Okuyucu), sağlayıcınızı Google Gemini olarak ayarlayın ve `1-50` sayfa aralığını girin. Eklenti metni arka planda doğru şekilde çıkaracaktır.

* **Senaryo: Ekranınızda sessiz bir eğitim videosu veya animasyon izliyorsunuz.**
  *Çözüm:* Ekran kaydını başlatmak için **Control + V** tuşlarına basın. Eğitimin oynatılmasına izin verin, ardından tekrar **Control + V** tuşlarına basın. Yapay zekâ tam olarak nelerin gösterildiğini açıklayacaktır.

---

**Not:** Tüm yapay zekâ özellikleri için etkin bir internet bağlantısı gereklidir. Çok sayfalı belgeler otomatik olarak işlenir.

## 10. Destek ve Topluluk

En son haberler, özellikler ve sürümlerden haberdar olun:

* **Telegram Kanalı:** [https://t.me/VisionAssistantPro](https://t.me/VisionAssistantPro)
* **GitHub Issues:** Hata bildirimleri ve özellik istekleri için.

## 11. Proje Destekçileri

Cömert mali katkılarıyla bu projenin sürekli geliştirilmesini ve sürdürülmesini destekleyen topluluk üyelerimize yürekten teşekkür ederiz:

* **@Alyabani94**
*   **Ali Alamri**
*   **Ilya**
*   **Anonim Destekçi** (`UQDd...CnMY`)
*   **leonardo0216**
*   **Sergei Fleytin**
*   **Suman Gayen**

*Projeye finansal olarak destek olmak istiyorsanız ve adınızı burada görmek istiyorsanız, **Bağış Yap** seçeneğini NVDA Araçlar menüsünde (Profesyonel Görsel Asistan alt menüsü) veya kurulum sonrasında kurulum sürecinde bulabilirsiniz.*


---

## 2026.07.15 için değişiklikler

* **Akıllı API Model Filtreleme**: Model filtreleme sistemi, beyaz liste yaklaşımı yerine tamamen kara liste yaklaşımını kullanacak şekilde baştan sona yenilendi. Ana sohbet modeli açılır listesinin kusursuz şekilde temiz ve geleceğe hazır kalmasını sağlamak için daha güçlü filtreleme anahtar sözcükleri (`embedding`, `bison`, `gecko`, `audio`, `realtime`, `babbage`, `moderation`, `deep`, `antigravity`, `computer`) eklendi. Buna karşın tüm uzmanlaşmış modeller, Gelişmiş Yönlendirme bölümünde erişilebilir olmaya devam ediyor.
* **Gelişmiş Yönlendirme Araması**: Tüm Gelişmiş Model Yönlendirme açılır listeleri (OCR, STT, TTS, Operatör, Video, Canlı) ile eSpeak Varyant seçicisi artık tamamen aranabilir. İstediğiniz modeli veya varyantı hızlıca bulmak için yazmaya başlayarak filtreleme yapabilirsiniz.
* **Yeni Komut Katmanı Kısayolları**:
  * **Ayarlar (`Alt + S`)**: Profesyonel Görsel Asistan ayarlar iletişim kutusunu anında açar.
  * **Kotası Tükenen Anahtarları Bildir (`Alt + Q`)**: Günlük kotasını aşmış Gemini API anahtarlarının tam sayısını bildirir, hangi modelde kotalarının tükendiğini belirtir ve tam sıfırlanma zamanlarını sesli olarak duyurur.
  * **Yönlendirme Denetimi (`Alt + M`)**: Mevcut Gelişmiş Yönlendirme yapılandırmanızı denetler ve varsayılan ayarlar atlanarak, uzmanlaşmış görevler için etkin olarak seçilmiş modelleri sesli olarak bildirir.
* **Video Analizi Tamamen Yenilendi**: Video Analizi baştan sona dönüştürüldü! Önceden yalnızca çevrimiçi videolar için temel bir açıklama sunarken, artık görme engelli kullanıcılar için tasarlanmış kapsamlı bir video işleme paketine dönüştü:
  * **Yerel Ekran Kaydı (`Control+V`)**: Artık ekranınızdan doğrudan sessiz videolar kaydedebilirsiniz. Yapay zekâ, kaydedilen bölümü analiz ederek sahneyi, yerleşimi ve gerçekleşen eylemleri son derece ayrıntılı şekilde betimler.
  * **Sesli Betimleme Oluşturma (SRT)**: Eklenti artık videolar için son derece ayrıntılı Sesli Betimleme metinleri (standart SRT biçiminde) oluşturabilir. Bu işlem, betimlemeleri ses parçasındaki doğal duraklamalara akıllıca yerleştiren akıllı boşluk zamanlaması ile ekrandaki tüm metinler için birebir OCR çıktısını içerir.
  * **Eşzamanlı Sesli Anlatım (MP3 Dışa Aktarma)**: Metin tabanlı altyazıların ötesinde, eklenti Sesli Betimlemeyi konuşmaya dönüştürebilir, bunu videonun özgün ses parçasıyla otomatik olarak birleştirebilir, ses azaltma (betimlemeler sırasında arka plan sesini düşürme) uygulayabilir ve son eşzamanlı sonucu MP3 dosyası olarak dışa aktarabilir.
  * **Akıllı Video Dosyası Eylemi**: Yerel bir video dosyasına odaklanıp video kısayoluna bastığınızda, eklenti bunu otomatik olarak algılar ve dosyayı doğrudan işler.
  * **Gelişmiş Karakter Takibi**: Yapay zekâ artık ön işlem olarak karakter çıkarımı gerçekleştirir. Genel bir karakter sözlüğü oluşturur ve karakterleri bölüm bölüm kimliklerini karıştırmadan doğru şekilde takip eder.
  * **Video Analizi Yapılandırması**: SRT parça boyutlarını, karakter altyazılamasını ve sorumluluk reddi bildirimlerini denetlemek için yeni ayarlar eklendi.
  * **Genişletilmiş Model Yönlendirmesi**: Artık Gelişmiş Model Yönlendirme ayarlarından video için özelleşmiş modelleri (`gemini_video_model`, `custom_video_model`) açıkça seçebilirsiniz.
* **Akıllı API Kota Yönetimi**: 429 (Günlük Limit) hatalarının işlenmesi, model bazında kota takibi yapacak şekilde geliştirildi. Bir API anahtarı belirli bir modelde günlük limitine ulaştığında, yalnızca o model için akıllıca karantinaya alınır; böylece aynı anahtar diğer modellerle kullanılmaya devam edebilir.

## 7.0.0 için değişiklikler

* **Yarım Kalan Taramaları Sürdürme**: Belge Okuyucu ve Akıllı Dosya İşlemleri için devam ettirme özelliği eklendi. Bir tarama herhangi bir nedenle kesintiye uğrarsa, artık baştan başlamak yerine kaldığı yerden devam edebilirsiniz.
* **Yeni `[screen_fg_obj]` Değişkeni**: Tüm ekran yerine yalnızca etkin ön plan penceresinin ekran görüntüsünü alabilen yeni bir özel istem değişkeni eklendi.
* **Akıllı Yeniden Deneme ve API Anahtarı Değiştirme**: Sunucuda geçici yoğunluk (örneğin "high demand") veya hatalı yanıtlar oluştuğunda eklenti artık aynı API anahtarıyla sessizce en fazla 5 kez yeniden deneme yapar. Bu denemeler başarısız olursa, listedeki bir sonraki API anahtarına otomatik olarak geçer.
* **Ekran Perdesi Algılama**: Ekran Perdesi etkin durumdayken (kalıcı olarak açık ya da kısayol tuşuyla geçici olarak etkinleştirilmiş olsa bile) ekran görüntüsü alınmasını engelleyen bir kontrol eklendi. Bu durumda kullanıcı uyarılır ve işlem durdurulur. Böylece siyah ekran görüntülerinin gönderilmesi ve API belirteçlerinin (token) boşa harcanması önlenir.
* **Belge Okuyucu İyileştirmeleri**: PDF sayfa aralığı iletişim kutusu artık varsayılan hedef dili eklenti ayarlarınızdan otomatik olarak seçer. Ayrıca, Belge Okuyucu kapatıldığında arka planda çalışan görevlerin düzgün şekilde sonlandırılmasını sağlamak için iş parçacığı (thread) yönetimi iyileştirildi.
* **Yerleşik Mistral OCR Entegrasyonu**: Mistral'ın yerleşik Belge OCR API'si entegre edildi. Çok sayfalı belgeler artık otomatik olarak birleştirilir, yüklenir ve Mistral'ın özel `/v1/ocr` uç noktası kullanılarak toplu olarak işlenir. Tek sayfalı görseller ise gereksiz PDF dönüştürmeleri yapılmadan doğrudan işlenir.
* **Dinamik Özel URL İşleyicileri**: Özel API URL'si değiştirildiğinde önbelleğe alınmış model listesi anında temizlenir ve manuel model giriş kutusu yeniden etkinleştirilir. Bu sayede standart `/v1/models` uç noktasını desteklemeyen özel servislerle (örneğin Cloudflare AI Gateway) tam uyumluluk sağlanır.
* **Yapay Zekâ Operatörü Girdi Motoru Baştan Yazıldı**: AI Operator için kullanılan fare ve klavye benzetim sistemi tamamen yeniden geliştirildi. Eski `mouse_event` API'si yerine modern Windows `SendInput` API'si kullanılarak güncel uygulamalar, UAC korumalı pencereler ve yüksek DPI ekranlarla çok daha yüksek uyumluluk sağlandı.
* **Sürükle ve Bırak İşlemleri Düzeltildi**: AI Operator'deki sürükle ve bırak işlemleri artık tamamen kararlı ve güvenilir çalışmaktadır. Yeni motor; doğal hareket eğrileri (easing), hassas imleç konumlandırması, optimize edilmiş zamanlama ve akıllı bir "nudge" tekniği kullanarak Windows'un ve uygulamaların sürükle-bırak hareketlerini doğru şekilde algılamasını ve işlemin yarıda kesilmeden tamamlanmasını sağlar.
* **Çoklu Monitör Desteği**: YZ Operatör artık çoklu monitör kurulumlarını tam olarak desteklemektedir. `MOUSEEVENTF_VIRTUALDESK` bayrağı kullanılarak fare hareketleri ve tıklamalar tüm monitörlerde doğru şekilde çalışır; böylece hedef uygulama hangi monitörde olursa olsun imleç doğru konumlandırılır.
* **Geliştirilmiş Klavye taklidi**: Tuş gönderme sistemi, Genişletilmiş Tuşları (Extended Keys) tam olarak destekleyecek şekilde geliştirildi. Buna yön tuşları, Home, End, Page Up, Page Down, Insert, Delete ve F1-F12 tuşları dahildir. Böylece YZ Operatör tarafından gönderilen gezinme ve kısayol komutları tüm uygulamalarda sorunsuz çalışır.
* **HEIC/HEIF Görsel Desteği**: iPhone fotoğraf biçimleri için yerel destek eklendi. Artık `.heic` ve `.heif` dosyalarını önceden dönüştürmeye gerek kalmadan doğrudan yapay zekâ ile görsel açıklama, OCR veya Belge Okuyucu işlemleri için seçebilirsiniz.

## 6.5.0 Sürümündeki Değişiklikler

*   **Live Assistant**: Yalnızca Google Gemini sağlayıcısı (veya Gemini uyumlu özel sağlayıcılar) için kullanılabilen bir gerçek zamanlı sesli ve ekran asistanı özelliği eklendi. Bu özellik, ayarların değiştirilmesi durumunda otomatik yeniden bağlanma ile birlikte, doğrudan diyalog içinde etkileşimli ses ve düşünme derinliği özelleştirme seçeneklerini içerir.
*   **MiniMax AI Sağlayıcı**: MiniMax, tam multimodal destek (sohbet, görme, OCR), 300'den fazla dinamik ses kullanan özel TTS ve çıktılardan akıl yürütme bloklarının (ör. `<think>...</think>`) otomatik olarak çıkarılması özellikleriyle eş sağlayıcı olarak entegre edildi.
*   **Belge Görüntüleyici Çevirisi**: Yerelleştirilmiş dil adı yerine standart 2 harfli dil kodunun Google Translate'e gönderilmesini sağlayarak, İngilizce olmayan NVDA kullanıcıları için sessiz çeviri hatası düzeltildi.
*   **PDF Toplu Tarama Yeniden Denemesi**: Gereksiz yüklemeleri önlemek ve yeniden denemeler sırasında rahatsız edici hata pencerelerinin açılmasını engellemek için, PDF belge toplu taraması için yüksek düzeyde optimize edilmiş, ayrı ve sessiz bir yeniden deneme mantığı uygulandı.
*   **Belge Görüntüleyici Durumu**: Uzun belge taramaları sırasında eklentinin genel durumunun (`I` ile kontrol edilir) “Toplu İşleme Başladı” durumunda takılı kalmasına neden olan bir hata düzeltildi.
*   **İş Parçacığı Çökmesi Çözüldü**: Arka plan iş parçacığından belgeler açılırken ortaya çıkan ciddi bir `IsMain() failed in wxTimerImpl` iş parçacığı onaylama çökmesi, GUI geri arama kuyruğunun `wx.CallAfter`'a geçirilmesiyle düzeltildi.

## 6.1.0 Sürümündeki Değişiklikler

*   **Evrensel Yerel YZ Entegrasyonu (Yerel YZ'yı Kur)**: Özel Sağlayıcı Ayarları'na yeni bir **“Yerel AI'yı Kur”** düğmesi eklendi. Kullanıcılar artık **Ollama**, **LM Studio**, **Jan.ai** ve **KoboldCPP** dahil olmak üzere yerel AI motorlarını anında otomatik olarak yapılandırabilir.
*   **Akıllı Yerel Proxy Atlama**: Bağlantı mantığı, gelişmiş bir proxy atlama mekanizmasıyla yeniden oluşturuldu. Eklenti artık yerel loopback bağlantıları için Windows sistem proxy'lerini tamamen atlayacak kadar akıllıdır ve VPN/TUN modu etkin olsa bile istikrarlı yerel AI bağlantıları sağlar.
*   **Yapay Zeka Operatörü Acil Durum İptali (Shift+A)**: Çok talep edilen bir durdurma/iptal güvenlik tetikleyicisi eklendi. Otonom bir işlem çalışırken AI Operatörü komutuna (komut katmanı içinde **Shift+A**) basıldığında döngü anında iptal edilir ve *"AI Operatörü durduruldu"* duyurusu yapılır.
*   **Ultra Kararlı YZ Etiketleme (v2)**: Mutlak ekran koordinat anahtarları, gelişmiş, hibrit bir **Nesne İmzası** sistemi ile değiştirildi. Etiketler artık programlama tanımlayıcılarına (UIA **AutomationId** veya Win32 **ControlID**) ve pencereye göre koordinatlara dayanıyor; bu sayede özel etiketleriniz pencere boyutlandırma, taşıma, monitör değiştirme veya ölçeklendirmeye karşı tamamen dayanıklı hale geliyor.
*   **Sorunsuz Otomatik Etiket Taşıma**: Yükseltme işlemi tamamen şeffaftır. Eklenti, ilk odaklandığında eski koordinat tabanlı etiketlerinizi arka planda yeni kararlı parmak izi formatına otomatik olarak taşır ve veri kaybı yaşanmaz.
## 6.0 Sürümündeki Değişiklikler

*   **Anlamsal YZ Etiketleme Özelliği**: Kullanıcılar artık YZ kullanarak isimsiz düğmeleri ve simgeleri kalıcı olarak etiketleyebilir. **L** tuşuna basarak mevcut gezgin nesnesini etiketleyebilir (hem Sekme tuşuyla odaklanma hem de nesne gezintisi desteklenir) veya **Shift+L** tuşlarına basarak tüm uygulamayı tek seferde tarayıp etiketleyebilirsiniz.
*   **Akıllı Etiket Yönetimi**: Özel etiketleri görüntülemek, yeniden adlandırmak veya toplu olarak silmek için yeni, tamamen erişilebilir bir Etiket Yöneticisi iletişim kutusu eklendi (etiketler varsa **Shift+L** tuşlarıyla erişilebilir).
*   **Doğrudan Dosya Analizi (Dosya İletişim Kutusunu Atla)**: Eklenti artık, Windows Dosya Gezgini'nde bir PDF veya görüntü dosyasına odaklandığınızı algılayacak kadar akıllıdır. Vurgulanan bir dosya üzerinde **F (Akıllı Dosya Eylemi)** veya **D (Belge Okuyucu)** tuşuna basıldığında, standart “Aç” iletişim kutusu tamamen atlanarak dosya hemen işlenir.

## 5.6 İçin Değişiklikler

*   **“Yok (Metin Katmanını Ayıkla)” OCR Motoru eklendi**: Kullanıcılar artık YZ kredisi kullanmadan aranabilir PDF'lerden doğrudan metin ayıklayabilir; bu da metin tabanlı belgelerde hızı ve gizliliği önemli ölçüde artırır.
*   **UI Gezgini Doğruluğu İyileştirildi**: UI Gezgini istemini, öğe türlerini (Liste Öğeleri gibi) daha iyi tanımlayacak ve Görev Çubuğu ve Saat gibi Windows sistem bileşenlerini yok sayarak “(İşaretli)”, “(Seçili)” veya “(Genişletilmiş)” gibi durumları doğru bir şekilde bildirecek şekilde iyileştirildi.
*   **Kurulum Ayarları Hatırlatıcısı**: Kurulumdan sonra, kullanıcıları API anahtarlarını ve tercihlerini yapılandırmak için ayarlar menüsüne yönlendiren bir bildirim eklendi.

## 5.5.2 için değişiklikler

* **Yapay Zeka Operatörü Yazma Sorunu Düzeltildi:** Belirli sistemlerde metin yapıştırmak yerine 'v' harfinin yazılmasına neden olan bir hata çözüldü. Bu düzeltme, yüksek sistem yükü sırasında meydana gelen zamanlama çakışmalarını giderir.
* **Gelişmiş Kararlılık:** Sistem panosu diğer uygulamalar tarafından geçici olarak kilitlendiğinde eklentilerin çökmesini önlemek amacıyla pano işlemlerine yönelik güçlü hata yönetimi eklendi.
* **Zamanlama Optimizasyonu:** Farklı sistem hızlarında daha yüksek güvenilirlik ve üçüncü taraf Pano Yöneticileriyle daha iyi uyumluluk sağlamak amacıyla klavye olaylarına yönelik dahili gecikmeler ayarlandı.

## 5.5 İçin Değişiklikler (Otomasyon Güncellemesi)

*   **Yapay Zeka Operatörü (Otonom Kontrol - Shift+A):** Bu, v5.5'in en önemli özelliğidir. Profesyonel Görsel Asistan, pasif bir asistan olmaktan çıkıp kişisel **Yapay Zeka Operatörünüz** haline geldi. Yalnızca ekranı betimlemez; komut gerektirir.
   * *Nasıl çalışır:* Artık bilgisayarınızı çalıştırmak için sözlü talimatlar verebilirsiniz. Örneğin, ekran okuyucunuzun sessiz kaldığı, tamamen erişilemeyen bir uygulamada **Shift+A** tuşlarına basıp şunu yazabilirsiniz: *"Ayarlar düğmesine tıklayın"* veya *"Arama alanını bulun, 'Son Haberler' yazın ve enter tuşuna basın."* Yapay zeka, öğeleri görsel olarak betimler, fareyi hareket ettirir ve görevi sizin için yürütür.
    *   *Performans Notu:* Bu özellik **Gemini 3.0 Flash (Önizleme)** için optimize edilmiştir ve en karmaşık kullanıcı arayüzü düzenlerini bile işleyebilecek inanılmaz derecede hızlı ve akıllı yanıtlar sunar.
    *   **⚠️ API Kullanım Uyarısı:** Yapay Zeka Operatörünün doğru olması için tam olarak ne olduğunu "görmesi" gerektiğinden, her adımda yüksek çözünürlüklü bir ekran görüntüsü gönderir. Sık kullanımın API kotanızı standart metin tabanlı görevlere göre çok daha hızlı tüketeceğini lütfen unutmayın.
*   **Görsel Kullanıcı Arayüz Gezgini (E):** "Etiketlenmemiş düğmeler" arasında gezinmekten bıktınız mı? UI Explorer'ı etkinleştirmek için **E** tuşuna basın. Yapay zeka tüm pencereyi tarayacak ve simgeler, grafikler ve menüler dahil gördüğü her tıklanabilir öğenin bir listesini oluşturacaktır. Listeden bir öğe seçmeniz yeterlidir; yapay zeka Operatörü sizin için o öğeye tıklayacaktır. Bu, herhangi bir uygulamanın üstünde "erişilebilir bir katmana" sahip olmak gibidir.
*   **Bağlama Duyarlı Akıllı Dosya Eylemi (F):** "F" tuşu tamamen elden geçirildi. Artık yalnızca OCR istediğinizi varsaymıyor. Tek bir görsel seçtiğinizde artık akıllı bir şekilde amacınızı soruyor: Sahneyi anlamak için **Ayrıntılı Görsel Açıklama** veya okumak için **Yapılandırılmış Metin Çıkarma (OCR)** seçebilirsiniz. Menü, dosya türüne ve aktif AI motorunuza göre dinamik olarak uyarlanır.
*   **Çekirdek Optimizasyonu:** Eklentinin dahili mantığında derinlemesine bir temizlik gerçekleştirdik, kullanılmayan eski işlevleri ve gereksiz kodları kaldırdık. Bu, tüm kullanıcılar için daha yalın, daha hızlı ve daha güvenilir bir deneyimle sonuçlanır.

## 5.0 için Değişiklikler

* **Çoklu Sağlayıcı Mimarisi**: Google Gemini’ye ek olarak **OpenAI**, **Groq** ve **Mistral** için tam destek eklendi. Kullanıcılar artık tercih ettikleri yapay zekâ arka ucunu seçebilir.
* **Gelişmiş Model Yönlendirme**: Yerel sağlayıcı kullanıcıları (Gemini, OpenAI vb.) artık farklı görevler (OCR, STT, TTS) için açılır listeden belirli modelleri seçebilir.
* **Gelişmiş Uç Nokta Yapılandırması**: Özel sağlayıcı kullanıcıları, yerel veya üçüncü taraf sunucular üzerinde ayrıntılı denetim için belirli URL’leri ve model adlarını manuel olarak girebilir.
* **Akıllı Özellik Görünürlüğü**: Ayarlar menüsü ve Belge Okuyucu arayüzü, seçilen sağlayıcıya göre desteklenmeyen özellikleri (TTS gibi) otomatik olarak gizler.
* **Dinamik Model Getirme**: Eklenti, mevcut model listesini doğrudan sağlayıcının API’sinden alır; böylece yeni modeller yayınlanır yayınlanmaz uyumluluk sağlanır.
* **Hibrit OCR ve Çeviri**: Chrome OCR kullanılırken hız için Google Translate, Gemini/Groq/OpenAI motorları kullanılırken yapay zekâ destekli çeviri tercih edecek şekilde mantık optimize edildi.
* **Evrensel “Yapay Zekâ ile Yeniden Tara”**: Belge Okuyucu’nun yeniden tarama özelliği artık yalnızca Gemini ile sınırlı değil; etkin olan herhangi bir yapay zekâ sağlayıcısını kullanır.

## 4.6 için Değişiklikler

* **Etkileşimli Sonuç Geri Çağırma:** Komut katmanına **Boşluk** tuşu eklendi; böylece “Doğrudan Çıktı” modu etkin olsa bile son yapay zekâ yanıtı takip soruları için anında yeniden açılabilir.
* **Telegram Topluluk Merkezi:** NVDA Araçlar menüsüne “Resmî Telegram Kanalı” bağlantısı eklendi.
* **Yanıt Kararlılığı Artışı:** Çeviri, OCR ve Görsel analiz özelliklerinin çekirdek mantığı optimize edildi.
* **Geliştirilmiş Arayüz Yönlendirmesi:** Ayar açıklamaları ve belgeler, yeni geri çağırma sistemini daha iyi anlatacak şekilde güncellendi.

## 4.5 için Değişiklikler

* **Gelişmiş İstem Yöneticisi:** Varsayılan sistem istemlerini ve kullanıcı tanımlı istemleri yönetmek için özel bir iletişim kutusu eklendi.
* **Kapsamlı Proxy Desteği:** Kullanıcı tarafından yapılandırılan proxy ayarlarının tüm API isteklerine eksiksiz uygulanması sağlandı.
* **Otomatik Veri Geçişi:** Eski istem yapılandırmaları, ilk çalıştırmada veri kaybı olmadan v2 JSON formatına otomatik yükseltilir.
* **Güncellenmiş Uyumluluk (2025.1):** Belge Okuyucu gibi gelişmiş özellikler nedeniyle minimum NVDA sürümü 2025.1 olarak ayarlandı.
* **Ayarlar Arayüzü Optimizasyonu:** İstem yönetimi ayrı bir iletişim kutusuna taşındı.
* **İstem Değişkenleri Rehberi:** [selection], [clipboard] gibi değişkenleri tanıtan yerleşik rehber eklendi.

## 4.0.3 için Değişiklikler

* **Geliştirilmiş Ağ Dayanıklılığı:** Kararsız bağlantılar için otomatik yeniden deneme mekanizması eklendi.
* **Görsel Çeviri Penceresi:** Uzun çevirileri satır satır okumaya uygun yeni pencere eklendi.
* **Birleştirilmiş Biçimlendirilmiş Görünüm:** İşlenen tüm sayfalar tek bir pencerede, net başlıklarla gösterilir.
* **OCR İş Akışı Optimizasyonu:** Tek sayfalı belgelerde sayfa aralığı seçimi atlanır.
* **API Kararlılığı İyileştirmeleri:** Daha sağlam kimlik doğrulama yöntemine geçildi.
* **Hata Düzeltmeleri:** Eklenti kapanışı ve sohbet penceresi odak sorunları giderildi.

## 4.0.1 için Değişiklikler

* **Gelişmiş Belge Okuyucu:** PDF ve görseller için sayfa aralığı seçimi ve arka plan işleme.
* **Yeni Araçlar Alt Menüsü:** NVDA Araçlar menüsüne “Vision Assistant” alt menüsü eklendi.
* **Esnek Özelleştirme:** OCR motoru ve TTS sesi ayarlardan seçilebilir.
* **Çoklu API Anahtarı Desteği:** Birden fazla Gemini anahtarı desteği.
* **Alternatif OCR Motoru:** Kota sınırlarında güvenilir tanıma.
* **Akıllı API Anahtarı Döndürme:** En hızlı çalışan anahtara otomatik geçiş.
* **Belgeden MP3/WAV:** Okuyucu içinde ses dosyası oluşturma.
* **Instagram Hikâyeleri Desteği**
* **TikTok Desteği**
* **Yeniden Tasarlanan Güncelleme Penceresi**
* **Birleşik Durum ve UX**

## 3.6.0 için Değişiklikler

* **Yardım Sistemi:** Komut katmanına (`H`) yardım eklendi.
* **Çevrim İçi Video Analizi:** **Twitter (X)** videoları desteği eklendi.
* **Projeye Katkı:** Bağış iletişim kutusu eklendi.

## 3.5.0 için Değişiklikler

* **Komut Katmanı:** Varsayılan `NVDA+Shift+V`.
* **Çevrim İçi Video Analizi:** YouTube ve Instagram URL analizi.

## 3.1.0 için Değişiklikler

* **Doğrudan Çıktı Modu**
* **Pano Entegrasyonu**

## 3.0 için Değişiklikler

* **Yeni Diller:** **Farsça** ve **Vietnamca**
* **Genişletilmiş Yapay Zekâ Modelleri**
* **Dikte Kararlılığı İyileştirmeleri**
* **Dosya İşleme Düzeltmeleri**
* **İstem Optimizasyonu**

## 2.9 için Değişiklikler

* **Fransızca ve Türkçe çeviriler eklendi.**
* **Biçimlendirilmiş Görünüm**
* **Markdown Ayarı**
* **İletişim Kutusu Yönetimi**
* **Kullanıcı Deneyimi İyileştirmeleri**

## 2.8 için Değişiklikler

* İtalyanca çeviri eklendi.
* **Durum Bildirimi**
* **HTML Dışa Aktarma**
* **Ayarlar Arayüzü İyileştirmeleri**
* **Yeni Modeller**
* **Yeni Diller**
* **Dikte İyileştirmeleri**
* **Güncelleme Ayarları**
* Kod temizliği.

## 2.7 için Değişiklikler

* Resmî NV Access Eklenti Şablonuna geçiş.
* HTTP 429 için otomatik yeniden deneme.
* Çeviri istemleri optimizasyonu.
* Rusça çeviri güncellemesi.

## 2.6 için Değişiklikler

* Rusça çeviri desteği.
* Hata iletileri güncellendi.
* Varsayılan hedef dil İngilizce yapıldı.

## 2.5 için Değişiklikler

* Yerel Dosya OCR Komutu.
* “Sohbeti Kaydet” düğmesi.
* Tam yerelleştirme desteği.
* NVDA ton modülüne geçiş.
* Gemini Dosya API’sine geçiş.
* Süslü parantez hatası düzeltildi.

## 2.1.1 için Değişiklikler

* [file_ocr] değişkeni düzeltildi.

## 2.1 için Değişiklikler

* Tüm kısayollar NVDA+Control+Shift standardına alındı.

## 2.0 için Değişiklikler

* Otomatik güncelleme sistemi.
* Akıllı çeviri önbelleği.
* Sohbet belleği.
* Panoya özel çeviri komutu.
* Yapay zekâ istemleri optimizasyonu.
* Özel karakter çökmesi düzeltildi.

## 1.5 için Değişiklikler

* 20’den fazla yeni dil desteği.
* Etkileşimli iyileştirme penceresi.
* Akıllı dikte.
* NVDA Girdi Hareketleri kategorisi.
* COMError çökme düzeltmeleri.
* Otomatik yeniden deneme.

## 1.0 için Değişiklikler

* İlk sürüm.
