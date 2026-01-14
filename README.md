## Teknolojik Yemekler – Pizza Landing Page

Bu proje, **Teknolojik Yemekler** markası için hazırlanmış; tamamen HTML ve CSS ile kodlanmış, tek sayfalık bir pizza & fast food tanıtım sitesidir.  
Odak noktası; tasarım dosyasına sadık kalarak hem masaüstü hem de mobil cihazlarda şık ve tutarlı bir kullanıcı arayüzü sunmaktır.

---

## İçerik
- [Özellikler](#özellikler)
- [Teknolojiler](#teknolojiler)
- [Proje Yapısı](#proje-yapısı)
- [Çalıştırma](#çalıştırma)
- [Responsive Davranış](#responsive-davranış)
- [Kod Tarzı ve Alınan Kararlar](#kod-tarzı-ve-alınan-kararlar)

---

## Özellikler

- **Statik Single Page Tasarım**
  - Üstte tam ekran **header** (arka planda pizza görseli, “KOD ACIKTIRIR / PIZZA, DOYURUR” başlığı ve “Acıktım” CTA butonu).
  - Header altında **kategori nav bar** (pizza, burger, kızartmalar vb. ikonlu menü).
  - **Special Offers / Kampanyalar** bölümü:
    - Büyük kırmızı kart – “Özel Lezzetus” kampanyası.
    - Sağda iki küçük kart – “Hackathlon Burger Menü” ve “Çoooook hızlı npm gibi kurye”,
      ikincisinde **iki katmanlı görsel yapı** (arka plan + overlay kurye illüstrasyonu).
  - **En Çok Paketlenen Menüler** başlığı, altına sıralanmış ürün kartları.
  - **Footer**: logo, iletişim bilgileri, hot menu listesi, Instagram grid’i ve alt barda copyright + Twitter ikonu.

- **Responsive Tasarım (max-width: 600px breakpoint’i)**  
  Masaüstü tasarımını bozmadan, 600px ve altı ekranlarda şu düzenlemeler yapılmıştır:
  - Header için özel mobil arka plan (`responsive-pizza.png`) ve hizalamalar.
  - Category nav 2 sütunlu yapıya geçer (ikon + metinler hizalı kalır).
  - Kampanya kartları ve ürün kartları dikey dizilime geçer.
  - Footer tamamen dikey kolon yapısına döner.

- **Taşma Kontrolleri ve Container Mantığı**
  - Ana bölümler için `width: 100% + max-width` yaklaşımı kullanıldı
    (ör. `max-width: 1068px`, `max-width: 1296px` vb.).
  - Kenar boşlukları için sabit `padding: 0 2rem` yerine
    `padding: 0 clamp(1rem, 4vw, 2rem)` gibi formüllerle
    **desktop görünümü korunurken**, dar ekranda yumuşak küçülme sağlandı.

---

## Teknolojiler

- **HTML5**
- **CSS3**
  - Flexbox
  - CSS Grid (bazı responsive layout’larda)
  - Media Queries (`@media (max-width: 600px)`)
  - `clamp()` ile uyumlu padding ayarları

---

## Proje Yapısı

- `index.html`  
  Sayfanın tüm HTML yapısı:
  - `header.header-section` – hero alanı
  - `nav.category-nav` – kategori menüsü
  - `section.special-offers` – kampanya kartları
  - `section.product-section-header` – ürün bölüm başlığı
  - `nav.category-tabs` – menü filtre sekmeleri (statik)
  - `section.product-cards-section` – ürün kartları
  - `footer.footer-section` – üç sütunlu footer + alt footer

- `style.css`  
  Tüm stil tanımları tek dosyada:
  - En üstte **CSS değişkenleri** (`:root` – renk paleti).
  - Global reset (`* { margin:0; padding:0; box-sizing:border-box; }`).
  - Masaüstü stilleri (header, nav, kartlar, footer).
  - En altta `@media (max-width: 600px)` içinde mobil düzenlemeler.

- `public/assets/...`  
  - `iteration-1` – header banner ve logo.
  - `iteration-2/cta` – kampanya kartlarına ait görseller.
  - `iteration-2/icons` – kategori ikonları.
  - `iteration-2/pictures` – responsive header ve özel kart görselleri
    (`responsive-pizza.png`, `beige-card-1/2.png` vb.).
  - `iteration-2/footer` – footer ikonları ve Instagram görselleri.

---

## Çalıştırma

1. Repoyu klonla veya indir:
   ```bash
   git clone <repo-url>
   cd fsweb-s4-bonus-challenge-html-pizza
   ```
2. `index.html` dosyasını doğrudan tarayıcıda aç.
    - VS Code kullanıyorsan Live Server ile çalıştır:
     ```text
     Sağ tık → “Open with Live Server”
     ```

Tarayıcıda desktop görünümünü kontrol ettikten sonra, **Geliştirici Araçları → mobil görünüm** (ör. 375×667) ile responsive tasarımı inceleyebilirsin.

---

## Responsive Davranış

- **Breakpoint:**  
  Tüm mobil düzenlemeler tek breakpoint altında toplanmıştır:
  ```css
  @media (max-width: 600px) { ... }
  ```

- **Header:**
  - Mobilde farklı bir görsel (`responsive-pizza.png`) ve özel hizalamalar kullanılır.
  - Başlık “KOD ACIKTIRIR / PIZZA, DOYURUR” satırlara bölünerek okunabilirlik artırılır.

- **Kategori Nav (Category List):**
  - Desktop: yatay flex menü (`justify-content: space-around`, geniş padding).
  - Mobil: 2 sütunlu, grid tabanlı düzen; `margin: 0 auto` ile tam ortada kalır.

- **Kampanya Kartları:**
  - Desktop: solda büyük kart, sağda iki küçük kart – yatay align.
  - Mobil: kartlar dikey dizilir, iç hizalamalar mobil ölçülere göre yeniden konumlandırılır.

- **Ürün Kartları ve Footer:**
  - Desktop: yan yana kartlar / üç sütunlu footer yapısı.
  - Mobil: her şey dikey stack olacak şekilde yeniden hizalanır.

---

## Kod Tarzı ve Alınan Kararlar


- **Sabit + Relative Hibrit Yaklaşım:**  
  - Piksel hassasiyeti gerektiren yerlerde (`height`, bazı `width`ler, tipografi)
    **px değerleri korunurken**, layout’u yöneten container ve padding’lerde
    `width: 100% + max-width` ve `clamp()` tercih edildi.
  - Böylece taslak görseldeki masaüstü görünümü bozulmadan,
    farklı ekran genişliklerine adaptasyon sağlandı.

    




