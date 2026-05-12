# LDF Comparator

İki LDF (LIN Description File) dosyasını karşılaştırarak aralarındaki farkları görsel olarak gösteren, tarayıcı tabanlı bir araç.

## Nasıl Kullanılır?

1. `LDF_COMPARATOR.html` dosyasını tarayıcıda aç.
2. Sol tarafa **eski** LDF dosyasını, sağ tarafa **yeni** LDF dosyasını sürükle-bırak ya da seç.
3. **Karşılaştır** butonuna tıkla.
4. Farklar bölüm bölüm listelenir.

Kurulum gerekmez, internet bağlantısına gerek yoktur (CDN bağımlılıkları ilk açılışta yüklenir).

---

## Ne Gösterir?

| Renk / Etiket | Anlam |
|---|---|
| Kırmızı — **Silindi** | Eski dosyada vardı, yenisinde yok |
| Yeşil — **Eklendi** | Yeni dosyada var, eskisinde yok |
| Sarı — **Değişti** | Satır var ama içeriği değişmiş |

### Akıllı Karşılaştırma

Araç, LDF formatını anlayarak bazı değişiklikleri daha anlamlı şekilde gösterir:

- **Master / Slaves:** Düğüm adı değişmişse "silindi + eklendi" yerine "değişti" olarak işaretler.
- **Sinyal gönderici ECU:** Hangi ECU'nun gönderdiği değişmişse "göndericisi değişti" olarak gösterir.
- **Sinyal alıcı ECU:** Alıcı listesi değişmişse "alıcısı değişti" olarak gösterir.
- **Frame yayıncısı:** Frame'i yayınlayan ECU değişmişse ayrıca belirtir.
- **Schedule delay:** Gecikme süresi değişmişse farkı `+X ms` / `−X ms` şeklinde gösterir.

---

## Bölümler ve Filtreler

Karşılaştırma sonuçları LDF bloklarına göre ayrı **sekmeler** halinde gruplandırılır:
`Nodes`, `Signals`, `Frames`, `Schedule_tables`, `Signal_encoding_types`, `Node_attributes` vb.

Her sekmenin başlığına tıklayarak o bölümü açıp kapatabilirsin.  
`Frames` bölümü içinde her frame kendi alt başlığında gösterilir; alt başlığa tıklayarak o frame'in değişikliklerini de gizleyebilirsin.

Sayfanın üstündeki **filtre çipleri** ile şu kategorileri gösterip gizleyebilirsin:

| Filtre | Açıklama |
|---|---|
| Delay | Schedule delay değişiklikleri |
| Gönderici | Sinyal / frame gönderici ECU değişiklikleri |
| Alıcı | Sinyal alıcı ECU değişiklikleri |
| Silindi | Tamamen silinen satırlar |
| Eklendi | Tamamen eklenen satırlar |

---

## Dil Seçeneği

Sağ üst köşedeki **TR / EN** butonuyla arayüz dilini Türkçe ve İngilizce arasında geçirebilirsin.

---

## Teknik Notlar

- Tek dosya uygulaması: `LDF_COMPARATOR.html`
- Harici kütüphane gerektirmez; Tailwind CSS ve Material Symbols CDN üzerinden yüklenir.
- Diff algoritması LCS (En Uzun Ortak Alt Dizi) tabanlıdır.
- Saf JavaScript, framework kullanılmamıştır.
