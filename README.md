# SunnahSource Islamic API — Quran API, Hadith API, Prayer Times API & more

[![Website](https://img.shields.io/badge/website-sunnahsource.org-802b55)](https://sunnahsource.org/)
[![Free Quran API](https://img.shields.io/badge/Quran%20API-free-2ea44f)](https://sunnahsource.org/apis/quran-translations/)
![JSON](https://img.shields.io/badge/format-JSON-blue)
![Languages](https://img.shields.io/badge/languages-9-orange)

**[SunnahSource](https://sunnahsource.org/)** is an **Islamic API** platform for developers building Muslim apps and websites. It provides authentic, structured JSON for the Quran, Hadith, Duas, Azkar, Tafseer, Prayer Times, the Hijri Calendar and more, with the original Arabic and translations in **English, Urdu, Russian, Malay, Indonesian, French, German, Turkish and Chinese**.

- ✅ **Free Quran API**: Arabic text with verse-by-verse translations in 9 languages
- 📚 **Hadith API**: Sahih Bukhari, Sahih Muslim, and 22 major hadith books
- 🕌 **Prayer Times API**: Fajr to Isha for any city, multiple calculation methods
- 🤲 Duas, Azkar, Six Kalmas, 99 Names of Allah, Seerah, Sahaba, Stories of the Prophets
- 🧩 Works with Flutter, React Native, Android, iOS, React/Next.js, PHP, Node.js and Python

> Built by [Hafiz Developers](https://hafizdeveloper.online/). Need a full Islamic app? We build those too: [sunnahsource.org](https://sunnahsource.org/).

---

## Available APIs

| API | What you get | Access | Docs & live preview |
|---|---|---|---|
| Quran Translations | Arabic Quran + 9-language translations, verse by verse | **Free** | [Quran API](https://sunnahsource.org/apis/quran-translations/) |
| Word by Word Quran | Word-level Arabic, transliteration, meaning | Premium | [Word by Word Quran API](https://sunnahsource.org/apis/word-by-word-quran/) |
| Topics in Quran | Quran themes mapped to ayahs | **Free** | [Quran Topics API](https://sunnahsource.org/apis/quran-topics/) |
| Tafseer | Verse-by-verse commentary, 50+ tafaseer | Premium | [Tafseer API](https://sunnahsource.org/apis/tafseer/) |
| Tarweel Tajweed | Real-time recitation mistake detection | Premium | [Tajweed API](https://sunnahsource.org/apis/tarweel/) |
| Hadith Collections | Bukhari & Muslim with narrator + translations | Premium | [Hadith API](https://sunnahsource.org/apis/hadith/) |
| Hadith — 22 Books | 22 major collections with grading | Premium | [Hadith Books API](https://sunnahsource.org/apis/hadith-22-books/) |
| Islamic Duas | 300+ duas, Arabic + transliteration | Premium | [Duas API](https://sunnahsource.org/apis/duas/) |
| Azkar | Morning / evening / after-prayer adhkar | Premium | [Azkar API](https://sunnahsource.org/apis/azkar/) |
| Six Kalmas | All 6 kalimas with translations | Premium | [Kalmas API](https://sunnahsource.org/apis/kalmas/) |
| Stories of the Prophets | Qasas al-Anbiya in 9 languages | Premium | [Prophets API](https://sunnahsource.org/apis/ambiya/) |
| Seerat un Nabi (SAW) | Seerah timeline chapters | Premium | [Seerah API](https://sunnahsource.org/apis/seerat-nabi/) |
| Sahaba | Biographies of the companions | Premium | [Sahaba API](https://sunnahsource.org/apis/sahaba/) |
| 99 Names of Allah | Asma ul Husna with meanings | Premium | [Asma ul Husna API](https://sunnahsource.org/apis/asma-ul-husna/) |
| Noorani Qaida (voice) | Lessons with audio pronunciation | Premium | [Noorani Qaida API](https://sunnahsource.org/apis/noorani-qaida/) |
| Hijri Calendar | Hijri date, months, Islamic events | Premium | [Hijri Calendar API](https://sunnahsource.org/apis/hijri-calendar/) |
| Prayer Times | Salah times for any city | Premium | [Prayer Times API](https://sunnahsource.org/apis/prayer-times/) |
| Islamic Names | Muslim boy & girl names with meanings | Premium | [Islamic Names API](https://sunnahsource.org/apis/islamic-names/) |
| Zakat | Nisab values, rate, calculation guide | Premium | [Zakat API](https://sunnahsource.org/apis/zakat/) |

## Getting an API key

1. Open **[sunnahsource.org](https://sunnahsource.org/#apply)** (or any API page) and fill in the *Get API Access* form.
2. The team reviews your request and emails your **API key, production endpoint and docs within 12–24 hours**.
3. The Quran Translations and Quran Topics APIs are free.

## Try the sample data right now

Every API page has a live preview powered by a public sample file. You can load the same sample JSON to prototype your UI before you get a key:

```
GET https://sunnahsource.org/data/json/quran-translations.json
GET https://sunnahsource.org/data/json/hadith.json
GET https://sunnahsource.org/data/json/prayer-times.json
```

> These sample files only show a preview (for example, Surah Al-Fatiha). The full datasets are served from your production endpoint once your key is approved.

### Sample response (Hadith API, shortened)

```json
{
  "title": "Hadith Collections",
  "description": "Authentic hadith with translations in 9 languages",
  "is_free": false,
  "items": [
    {
      "id": 1,
      "collection": "Sahih Bukhari",
      "book": 1,
      "hadith_number": 1,
      "arabic": "إِنَّمَا الأَعْمَالُ بِالنِّيَّاتِ",
      "narrator": "Umar ibn Al-Khattab (RA)",
      "translations": {
        "en": "Actions are judged by intentions, and every person will get what they intended.",
        "ur": "اعمال کا دارومدار نیتوں پر ہے..."
      }
    }
  ]
}
```

## Code examples (using the public sample file)

### JavaScript (Node 18+ / server-side)
```js
const res = await fetch("https://sunnahsource.org/data/json/quran-translations.json");
const data = await res.json();
console.log(data.surah.name_english);
data.ayahs.forEach(a => console.log(a.arabic, "—", a.translations.en));
```

### Python
```python
import requests
data = requests.get("https://sunnahsource.org/data/json/hadith.json", timeout=10).json()
for h in data["items"]:
    print(h["collection"], h["hadith_number"], "-", h["translations"]["en"])
```

### Flutter / Dart
```dart
import 'dart:convert';
import 'package:http/http.dart' as http;

Future<void> loadPrayerTimes() async {
  final res = await http.get(Uri.parse('https://sunnahsource.org/data/json/prayer-times.json'));
  final data = jsonDecode(utf8.decode(res.bodyBytes));
  print('${data['city']}: Fajr ${data['times']['fajr']}, Maghrib ${data['times']['maghrib']}');
}
```

### PHP
```php
<?php
$data = json_decode(file_get_contents('https://sunnahsource.org/data/json/duas.json'), true);
foreach ($data['items'] as $dua) {
    echo $dua['arabic'] . PHP_EOL;
}
```

> When you receive your key, swap the sample URL for the production endpoint from your welcome email and send the key exactly as the docs describe.

## Use cases
Quran reader apps · Hadith of the Day widgets · prayer time & adhan apps · masjid display screens · Islamic learning and kids' apps · dua / azkar apps · Islamic chatbots · WordPress plugins.

## Custom data or a complete app
Need a dataset we don't list yet, or a full Islamic app built for you? Use the [Custom API request](https://sunnahsource.org/custom-request.html) page or [contact us](https://sunnahsource.org/contact.html).

## Contact
- Website: https://sunnahsource.org/
- Email: sunnahsourceofficial@gmail.com
- Built by [Hafiz Developers](https://hafizdeveloper.online/)

---
*Keywords: islamic api, quran api, free quran api, hadith api, sahih bukhari api, prayer times api, duas api, azkar api, tafseer api, hijri calendar api, muslim app api, quran json.*


---

## Also available at QuraniAPI (quranicapi.online)

The same Quran and Islamic datasets are also documented on **[QuraniAPI](https://quranicapi.online/)**, a developer portal focused on the Quran API:

- [Free Quran API — Quran translation JSON in 9 languages](https://quranicapi.online/api/quran-translations)
- [Word by Word Quran API](https://quranicapi.online/api/word-by-word-quran)
- [Tafseer API](https://quranicapi.online/api/tafseer)
- [Hadith API](https://quranicapi.online/api/hadith)
- [Quran API documentation](https://quranicapi.online/docs.html)
