# Yapay Zeka Kullanımı

JS oyun projesinin yapım ve yüklenim aşamalarında çeşitli yapay zeka araçlarından(https://chatgpt.com/,https://www.deepseek.com/,https://grok.com/...) yardımlar alınmış ve promptlara verilen  sonuçlar karşılaştırılıp en optimize olanı ile devam edilmiştir.

## Kullanım Amaçları

- JavaScript ile portal oluşturma fonksiyonunun açıklanması
- HTML'de oyun ekranına tuş bilgisi ekleme yöntemi
- Müzik ve resim ekleme yöntemleri
- GitHub Pages yayını hakkında rehberlik
- README  içerik örnekleri

  -> 500+ satır kod içeren tam oyun dosyası + bu oyunun github readme sayfasını nasıl yazabilirm?
  
  Oyun için README sayfası yazmak oldukça önemli! İşte adım adım yapabileceğin şeyler:
            README'nin İçermesi Gerekenler
            Oyun Başlığı ve Açıklama
            
            Oyunun adı ve kısa bir tanımı
            Hangi tür oyun olduğu (aksiyon, puzzle, RPG vb.)
            Temel oynanış mekaniği
            
            Kurulum Talimatları
            
            Hangi platformlarda çalışır (Windows, Mac, Linux)
            Sistem gereksinimleri
            İndirme ve kurulum adımları
            Gerekli bağımlılıklar (Unity, .NET Framework vb.)
            
            Nasıl Oynanır
            
            Temel kontroller (klavye/mouse tuşları)
            Oyun hedefleri
            Önemli oyun mekanikleri
            
            Ekran Görüntüleri
            
            2-3 adet oyundan görsel
            GIF formatında kısa gameplay videosu olursa daha iyi
            
            Teknik Detaylar
            
            Hangi programlama dili/motor kullandığın
            Proje yapısı (klasör organizasyonu)
            Kaynak kod hakkında bilgi
            
            Kredi ve Teşekkürler

            Kullandığın asset'ler, müzikler
            Yardım eden kişiler
            Referans aldığın oyunlar
  
  ->  oyun dosyalarımı github a nasıl yüklerim?


             GitHub'a oyun dosyalarını yüklemek için şu adımları takip edebilirsin:
          GitHub'da Repository Oluşturma
          
          GitHub.com'a git ve hesabına giriş yap
          "New Repository" butonuna tıkla (yeşil buton)
          Repository adını gir (oyunun adı)
          Public veya Private seç (public herkese açık)
          "Add a README file" kutucuğunu işaretle
          "Create repository" butonuna tıkla
          
          Dosyaları Yükleme (Web Üzerinden - Kolay Yol)
          
          Yeni oluşturduğun repository sayfasına git
          "Add file" > "Upload files" tıkla
          Oyun dosyalarını sürükle-bırak yap veya "choose your files" ile seç
          Alt kısımda commit mesajı yaz ("İlk oyun dosyaları" gibi)
          "Commit changes" tıkla
          
          Git ile Yükleme (Gelişmiş Yol)
          Eğer Git kullanmayı biliyorsan:
          bashgit clone [repository-url]
          cd oyun-klasörü
          # Dosyaları kopyala
          git add .
          git commit -m "Oyun dosyaları eklendi"
          git push origin main
          Önemli Notlar
          
          Büyük dosyalar (100MB+) sorun çıkarabilir, bunları LFS ile yüklemen gerekebilir
          Executable dosyalar (.exe) bazen sorun çıkarır
          Kaynak kod ve build edilmiş dosyaları ayrı tutmak daha iyi
          .gitignore dosyası oluşturup gereksiz dosyaları hariç tut
          
          Hangi oyun motoru kullanıyorsun? Unity, Unreal, yoksa başka bir şey mi? Bu bilgiye göre daha spesifik yardım edebilirim.RetryClaude does not have the ability to run the code it generates yet.Claude can make mistakes. Please double-check responses.

-> kodlarımı gönderdim ve yanınca game over ekranı gelmiyor hata nerde bana yardımcı olur musun?
        Bu sorunu inceledim ve birkaç sorun tespit ettim. Game over ekranının gelmemesinin ana sebebi, yanma durumunda gameOver() fonksiyonunun çağrılmasında ve bazı mantık hatalarında.
        İşte düzeltmeleri:  

-> Hala sorun çözülmedi Retry ekranını nasıl gösterebilirim?
        
          Kodunuza baktığımda retry ekranının görünmemesinin birkaç sebebi olabilir. Ana sorunlar şunlar:
      
      Portal çarpışma kontrolü eksik - Oyuncu portallarla çarpıştığında yanma efekti başlıyor ama oyun bitişi tetiklenmiyor
      
      Zorluk artış sistemi eksik - Kodda portal ve böcek sayısı artışı için değişkenler var ama aktif kullanılmıyor 
      Game over koşulları belirsiz
      İşte düzeltilmiş versiyonu: 

-> Oyunuma Kurbaga yandıgı anda bi retry kodu ekler misin ?

İşte kodun problemini buldum! Sonda bir kaç syntax hatası var:
Eksik parantezler ve süslü parantezler:

23. satırdaki if bloğu kapatılmamış - eksik }
Ana fonksiyonun süslü parantezi eksik - eksik }

Diğer syntax hataları:

Bir string literal kapatılmamış (tırnak işareti eksik)
Noktalı virgül eksik
Değişken tanımında virgül fazla

Bu tür hatalar genellikle kodun sonunda birikerek IDE'nin hata vermesine neden olur. Kod editörünüzün parantez eşleştirme özelliğini kullanarak bu hataları kolayca tespit edebilirsiniz.


->function createPortals() {
  portals = [];
  for(let i = 0; i < PORTAL_COUNT; i++) {
    const angle = (i / PORTAL_COUNT) * Math.PI * 2;
    const distance = 400 + Math.random() * 300; // 400-700 piksel mesafe
    const portal = {
      x: Math.cos(angle) * distance,
      y: Math.sin(angle) * distance,
      size: 25 + Math.random() * 15, // 25-40 arası boyut
      rotationSpeed: 0.3 + Math.random() * 0.4, // Farklı dönüş hızları
      pulseOffset: Math.random() * Math.PI * 2 // Farklı nabız fazları
    };
    portals.push(portal);
  }
}

function addNewPortal() {
  const angle = Math.random() * Math.PI * 2;
  const distance = 500 + Math.random() * 400;
  const portal = {
    x: frog.x + Math.cos(angle) * distance,
    y: frog.y + Math.sin(angle) * distance,
    size: 25 + Math.random() * 15,
    rotationSpeed: 0.3 + Math.random() * 0.4,
    pulseOffset: Math.random() * Math.PI * 2
  };
  portals.push(portal);
}  portal sayılarını nasıl arttırım?




    Portal Sayısını Artırmak İçin
1. PORTAL_COUNT Değerini Değiştir
Başlangıçta oluşturulacak portal sayısını artırmak için:

js
Kopyala
Düzenle
const PORTAL_COUNT = 10; // Örneğin 10'dan 20'ye çıkar
Bu değer arttıkça, createPortals() daha fazla portal oluşturur.

2. addNewPortal()'ı Daha Sık Çağırmak
Oyunun içinde zamanla veya belli bir olay sonucu portal eklemek istiyorsan:

js
Kopyala
Düzenle
// Her 5 saniyede bir portal ekle
setInterval(addNewPortal, 5000);
ya da bir tuşa basınca:

js
Kopyala
Düzenle
document.addEventListener('keydown', (e) => {
  if (e.key === 'p') {
    addNewPortal();
  }
});


->müzik nasıl eklicem?
 2. HTML ile Arka Plan Müziği Eklemek
En basit yöntem:

html
Kopyala
Düzenle
<audio id="bgMusic" src="background.mp3" loop autoplay></audio>
autoplay: Sayfa açıldığında çalmasını sağlar

loop: Sonsuza kadar tekrar eder

🎧 Ancak modern tarayıcılar kullanıcı etkileşimi olmadan otomatik müzik çalmaya izin vermez! Bu yüzden kullanıcı bir tuşa bastığında başlatmak daha güvenilirdir.

✅ 3. JavaScript ile Müzik Başlatma (Tavsiye Edilen Yöntem)
HTML:

html
Kopyala
Düzenle
<audio id="bgMusic" src="background.mp3" loop></audio>
<button id="startBtn">Oyunu Başlat</button>
JS:

js
Kopyala
Düzenle
document.getElementById('startBtn').addEventListener('click', () => {
  const music = document.getElementById('bgMusic');
  music.play();
  // oyunu da burada başlatabilirsin
});


-> github hesabımdaki linkte sadece readme dosyası görünüyor nasıl düzeltirim?
          Anladım Elif! GitHub Pages linkinde sadece README dosyası görünüyorsa, büyük ihtimalle projedeki index.html dosyası ya yoktur ya da yanlış klasörde duruyordur. Bu yüzden web sitesi çalışmıyor gibi görünür. Aşağıdaki adımları uygularsan sorun çözülür 👇
      
      ✅ Sorunu Çözmek İçin Adımlar
      🔍 1. index.html dosyası yüklü mü?
      GitHub'da repo sayfana git ve şunlara bak:
      
      index.html dosyası ana dizinde (yani root'ta) olmalı.
      
      README.md, game.js, style.css gibi dosyaların yanında görünmeli.
      
      📌 index.html bir klasörün içindeyse (örneğin public/index.html), GitHub Pages onu açmaz.
      
      🔁 2. Eksikse index.html'i yükle:
      Yöntem 1: Tarayıcıdan yükleme
      Repo sayfana git.
      
      Add file > Upload files seç.
      
      Bilgisayarındaki index.html, game.js, style.css ve diğer tüm dosyaları seç.
      
      En altta “Commit changes” butonuna tıkla.
      
      Yöntem 2: Tüm klasörü zip'leyip tek tek yüklemen de mümkün.
      ✅ 3. Yüklendikten Sonra:
      Ayarları tekrar yapmana gerek yok. Pages kısmında ayarladığın gibi kalmalı.
      
      Sadece birkaç dakika sonra şu link çalışmaya başlar:
      
      arduino
      Kopyala
      Düzenle
      https://elifyadairem.github.io/REPO-ADI/





  
