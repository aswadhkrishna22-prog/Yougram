# Yougram 🚀

<div align="center">
  <h3>An open-source, 100% ad-free YouTube Android client with Telegram aesthetics</h3>

  <p>
    <a href="https://github.com/aswadhkrishna22-prog/Yougram/releases"><img src="https://img.shields.io/badge/Release-Nightly-2AABEE?style=for-the-badge&logo=android&logoColor=white" alt="Nightly Release"></a>
    <a href="https://github.com/aswadhkrishna22-prog/Yougram/actions"><img src="https://img.shields.io/badge/CI-Automated%20Builds-success?style=for-the-badge&logo=githubactions&logoColor=white" alt="CI"></a>
    <a href="LICENSE"><img src="https://img.shields.io/badge/License-GPL--3.0-000000?style=for-the-badge" alt="License"></a>
  </p>
</div>

---

## ✨ Features

- 🚫 **100% Ad-Free**: Completely blocks YouTube video pre-roll, mid-roll, and home banner ads.
- ⏭️ **SponsorBlock**: Automatically skips sponsored segments, creator shoutouts, intros, and outros embedded in video streams.
- 🎧 **Background Playback & PiP**: Keep listening with your screen turned off, or watch in a floating Picture-in-Picture window.
- 🎨 **Telegram Blue + Pitch Black Aesthetic**: Built for OLED displays with deep blacks (`#000000`) and Telegram Cyan Blue (`#2AABEE`) accents.
- 📥 **Direct Media Downloader**: Download 1080p/4K video or high-bitrate MP3 audio without any third-party websites or tools.
- 👎 **Return YouTube Dislike**: Accurate dislike counts restored using the RYD API.
- 🕵️ **Privacy First**: Zero tracking, no Google Play Services required, and no forced Google sign-in.
- ⚡ **Lightweight & Battery Efficient**: Optimized native Kotlin architecture designed to run cool and smooth on all Android devices.

---

## 🎨 Theme & Design Specs

| Token | Hex Code | Visual Preview |
|---|---|---|
| **Primary Accent (Telegram Blue)** | `#2AABEE` | ![#2AABEE](https://via.placeholder.com/15/2AABEE/000000?text=+) |
| **Dark Secondary** | `#5288C1` | ![#5288C1](https://via.placeholder.com/15/5288C1/000000?text=+) |
| **OLED Pitch Black** | `#000000` | ![#000000](https://via.placeholder.com/15/000000/000000?text=+) |
| **Telegram Card Surface** | `#17212B` | ![#17212B](https://via.placeholder.com/15/17212B/000000?text=+) |
| **Telegram Surface Variant** | `#0E1621` | ![#0E1621](https://via.placeholder.com/15/0E1621/000000?text=+) |

---

## 📥 Download & Installation

1. Go to the [**Releases**](https://github.com/aswadhkrishna22-prog/Yougram/releases) tab.
2. Download the latest `Yougram.apk`.
3. Install the APK on your Android phone (Android 8.0+ supported).
4. Enjoy unlimited ad-free streaming!

---

## 🛠️ Building From Source

Yougram is automatically compiled and packaged using GitHub Actions CI/CD to prevent phone overheating and resource exhaustion.

To build manually:
```bash
./gradlew assembleDebug
```
The output APK will be available at `app/build/outputs/apk/debug/Yougram.apk`.

---

## 📜 Credits & License

- Built on top of the open-source [LibreTube](https://github.com/libre-tube/LibreTube) project.
- Stream extraction powered by [Piped](https://github.com/TeamPiped/Piped) & [NewPipe Extractor](https://github.com/TeamNewPipe/NewPipeExtractor).
- Sponsor segment skipping powered by [SponsorBlock](https://sponsor.ajay.app/).
- Dislike estimation powered by [Return YouTube Dislike](https://returnyoutubedislike.com/).
- Licensed under the [GNU General Public License v3.0](LICENSE).
