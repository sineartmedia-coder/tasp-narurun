# 🍹 Meyve Suyu AR Projesi

WebAR projesi — A-Frame + MindAR Image Tracking.

## Proje Yapısı

```
/
├── index.html       ← Ana AR sayfası (tüm kod burada)
├── armut.png        ← Armut görseli (sol tarafa yansıtılır)
├── elma.png         ← Elma görseli (sağ tarafa yansıtılır)
└── targets.mind     ← Hedef görsel (oluşturman gerekiyor ↓)
```

---

## 🔧 Adım 1 — targets.mind Dosyasını Oluştur

1. Meyve suyu kutusunun **ön yüzünü** telefonunla veya kamerayla fotoğrafla.
   - Düz açı, parlak ışık, bulanık olmayan net bir görsel olsun.

2. Şu siteye git:  
   👉 **https://hiukim.github.io/mind-ar-js-doc/tools/compile**

3. Fotoğrafı sürükle-bırak → **Compile** → İndirilen dosyayı bu klasöre `targets.mind` adıyla kaydet.

---

## 🖼️ Adım 2 — Görselleri Kontrol Et

`armut.png` ve `elma.png` zaten bu klasörde bulunuyor.  
İstersen kendi görsellerinle değiştirebilirsin (aynı isimler olmalı).

---

## 🌐 Adım 3 — Netlify'a Ücretsiz Deploy Et (En Kolay Yol)

### Yöntem A — Sürükle Bırak (0 teknik bilgi)
1. **https://netlify.com** adresine git → ücretsiz üye ol.
2. "Sites" sekmesine gel.
3. Bu klasörün **tamamını** tarayıcıya **sürükle & bırak**.
4. Netlify anında `https://xxxxx.netlify.app` gibi bir URL verir — bitti! ✅

### Yöntem B — GitHub + Vercel
1. Bu klasörü GitHub'a yükle (yeni repo oluştur).
2. **https://vercel.com** → "New Project" → GitHub repoyu seç.
3. Build ayarı yok, direkt Deploy.
4. `https://proje-adi.vercel.app` linki hazır. ✅

---

## 📱 Adım 4 — Test Et

1. Deploy edilen HTTPS linkini telefonunda aç.
2. Kamera izni iste → kabul et.
3. Meyve suyu kutusunu kameraya tut.
4. **Sol tarafta Armut, Sağ tarafta Elma, Üstte Bilgi Paneli belirer!** 🎉

---

## ⚠️ Önemli Notlar

| Konu | Açıklama |
|------|----------|
| **HTTPS zorunlu** | Kamera erişimi yalnızca HTTPS'de çalışır. `localhost` geliştirme için muaf, ama gerçek kullanımda HTTPS şart. Netlify/Vercel otomatik SSL verir. |
| **Mobil uyumluluk** | Chrome (Android), Safari (iOS 12+) destekler. Firefox Android'de sorun çıkabilir. |
| **Işık koşulları** | Görsel tanıma kötü aydınlatmada başarısız olabilir. İyi ışıkta dene. |
| **targets.mind boyutu** | .mind dosyası büyük olabilir (1-5 MB), bu normal. |

---

## 🎨 AR İçeriğinin Konumu Değiştirme

`index.html` içinde aşağıdaki değerleri düzenleyebilirsin:

```html
<!-- SOL TARAF (Armut): x eksenini küçült → daha sola -->
<a-entity id="armut-group" position="-0.55 0 0.05">

<!-- SAĞ TARAF (Elma): x eksenini büyüt → daha sağa -->
<a-entity id="elma-group"  position=" 0.55 0 0.05">

<!-- ÜST PANEL: y eksenini büyüt → daha yukarı -->
<a-entity id="info-panel"  position="0 0.55 0.05">
```

**Koordinat rehberi:**
- `x`: Sağ → artı (+), Sol → eksi (-)
- `y`: Yukarı → artı (+), Aşağı → eksi (-)
- `z`: Kameraya yakın → artı (+), Uzak → eksi (-)

---

## 🛠️ Yerel Test (Node.js varsa)

```bash
npx serve .
# → http://localhost:3000
# Kamera için HTTPS lazım, ngrok ile tünel aç:
npx ngrok http 3000
```
