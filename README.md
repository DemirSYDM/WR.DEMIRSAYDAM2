# Klugvion – Website

Bu depo, Klugvion'un tek sayfalık web sitesini içerir (`index.html` + `logo.png`).
Ekstra bir kurulum, build adımı veya sunucu gerekmez — GitHub Pages direkt bu dosyaları yayınlayabilir.

## GitHub Pages ile yayınlama (adım adım)

### 1. Yeni bir repo oluştur
- GitHub'da sağ üstten **+ → New repository**
- İsim ver, örn: `klugvion-website`
- **Public** seç (GitHub Pages ücretsiz kullanım için repo public olmalı, ücretli planların hepsinde private de çalışır)
- "Add a README" kutucuğunu **işaretleme** (biz zaten README getiriyoruz)
- **Create repository**

### 2. Dosyaları yükle
En kolay yol — tarayıcıdan:
- Yeni repo sayfasında **"uploading an existing file"** linkine tıkla
- Bu klasördeki üç dosyayı sürükle-bırak: `index.html`, `logo.png`, `.nojekyll`
- Alt kısımda **Commit changes**

Veya terminalden (git yüklüyse):
```bash
cd klugvion-repo
git init
git add .
git commit -m "Klugvion website"
git branch -M main
git remote add origin https://github.com/KULLANICI_ADIN/klugvion-website.git
git push -u origin main
```

### 3. GitHub Pages'i aç
- Repo sayfasında **Settings → Pages** (sol menüde)
- **Build and deployment → Source** kısmından **Deploy from a branch** seç
- **Branch:** `main`, klasör: `/ (root)` seç → **Save**
- 1-2 dakika içinde site şu adreste yayına girer:
  ```
  https://KULLANICI_ADIN.github.io/klugvion-website/
  ```
  (GitHub, Settings → Pages sayfasında sana tam linki de gösterecek)

### 4. Kendi alan adını bağlamak istersen (opsiyonel)
Örn. `klugvion.de` gibi bir alan adın varsa:
- Aynı **Settings → Pages** sayfasında **Custom domain** kutusuna alan adını yaz
- Alan adı sağlayıcında (Namecheap, GoDaddy, IONOS vb.) şu DNS kaydını ekle:
  - **CNAME** kaydı → `www` → `KULLANICI_ADIN.github.io`
  - Kök alan adı (`klugvion.de`) için 4 tane **A kaydı** eklemen gerekir, GitHub'ın resmi dokümanındaki IP'ler:
    `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
- DNS yayılması birkaç saat sürebilir.

## Dosya yapısı
```
index.html   → Tüm site (HTML + CSS + JS tek dosyada)
logo.png     → Klugvion logosu (index.html içinden ./logo.png olarak çağrılıyor)
.nojekyll    → GitHub Pages'in dosyaları Jekyll ile işlemesini engeller (gerekli)
```

⚠️ `logo.png` dosyasının her zaman `index.html` ile **aynı klasörde** kalması gerekiyor, yoksa logo görünmez.

## Canlıya almadan önce güncellemen gerekenler
Sitede şu an **placeholder (örnek) bilgiler** var, gerçek verilerle değiştirmelisin:
- **Impressum / Datenschutz / AGB** (footer'daki linkler) — gerçek şirket bilgilerin, adresin ve yasal metinlerin ile değiştir. Almanya'da Impressum yasal zorunluluktur.
- **Kontakt** bölümündeki e-posta, telefon ve adres (`hallo@klugvion.de`, `+49 (0)30 1234 567`, `Musterstraße 12, 10115 Berlin`)
- **Karte / Lehrer finden** bölümündeki öğretmen listesi şu an örnek (demo) veridir — gerçek öğretmenlerle değiştirmek istersen `index.html` içinde `const tutors = [...]` kısmını düzenleyebilirsin, ya da ileride gerçek bir veritabanına bağlamamız gerekir.

## Değişiklik yapmak istersen
`index.html` tek dosya — düz metin editörüyle (VS Code, Notepad++ vb.) açıp içindeki yazıları, renkleri veya fiyatları değiştirebilirsin. Değişiklikten sonra dosyayı tekrar GitHub'a yükleyip commit etmen (veya `git push` yapman) yeterli, site otomatik güncellenir.
