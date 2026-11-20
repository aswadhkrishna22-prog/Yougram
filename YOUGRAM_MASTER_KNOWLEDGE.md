# Yougram — Master Knowledge & Architecture Base (A to Z)

> [!IMPORTANT]
> **Permanent Project Memory:** This document is the single source of truth for the **Yougram** project.
> Any change, feature addition, UI tweak, bug fix, dependency bump, CI/CD update, or release MUST be immediately documented in this file under the [7. Changelog & Project Updates](#7-changelog--project-updates) section.

---

## 1. Project Background & Identity
- **Repository:** [`https://github.com/aswadhkrishna22-prog/Yougram.git`](https://github.com/aswadhkrishna22-prog/Yougram.git)
- **Local Path:** `/data/data/com.termux/files/home/Yougram`
- **Application Name:** **Yougram**
- **Package / Application ID:** `app.yougram.android`
- **Version:** `1.0.0` (VersionCode: `1`)
- **Target SDK / Min SDK:** `compileSdk = 36`, `targetSdk = 36`, `minSdk = 26` (Android 8.0+)
- **Core Concept:** An open-source, 100% ad-free YouTube Android client featuring Telegram aesthetics (Cyan Blue + OLED Pitch Black), SponsorBlock auto-skipping, background/PiP playback, direct media downloader, and Return YouTube Dislike (RYD) integration.
- **Upstream Foundation:** Built on top of [LibreTube](https://github.com/libre-tube/LibreTube), powered by Piped and NewPipeExtractor for stream extraction.

---

## 2. Critical Operational Rules
1. **Phone Overheating Constraint (STRICT):**
   - The user develops and manages projects directly on an Android device via Termux.
   - **NEVER run local Gradle builds, assemble tasks, local lint, or heavy tests** (e.g. `./gradlew assembleDebug` or `./gradlew test`) on the device.
   - All builds, compilation checks, and APK releases **MUST strictly run via GitHub Actions CI** (`.github/workflows/ci.yml`).
   - Monitor workflow runs using GitHub CLI: `gh run list --limit 5` or `gh run watch`.
2. **Master Knowledge Synchronization Rule (STRICT):**
   - Whenever any file is modified, a feature is added, a bug is fixed, a workflow is touched, or a release is created, this file (`YOUGRAM_MASTER_KNOWLEDGE.md`) **MUST be updated** with the details, timestamp, and commit reference.
3. **Branching & Git Workflow:**
   - Default branch: `main`.
   - Keep commits structured with conventional commits (`feat:`, `fix:`, `refactor:`, `chore:`, `docs:`).

---

## 3. Technology Stack & Architecture
- **Language:** Kotlin
- **Build System:** Gradle (Kotlin DSL: `build.gradle.kts`, `settings.gradle.kts`, Version Catalogs `gradle/libs.versions.toml`)
- **Stream Extraction:**
  - [Piped](https://github.com/TeamPiped/Piped) API Instances
  - [NewPipe Extractor](https://github.com/TeamNewPipe/NewPipeExtractor)
- **Playback Engine:**
  - AndroidX Media3 / ExoPlayer with background audio playback and system notification controls
  - Picture-in-Picture (PiP) support
- **Integrated Services:**
  - **SponsorBlock:** Community-driven database to detect and skip sponsored segments, intros, outros, and subscription reminders.
  - **Return YouTube Dislike (RYD):** Restores YouTube dislike counts via RYD API.
- **Local Persistence & Data:**
  - Room Database with KSP (`exportSchema = true`)
  - Protocol Buffers (Protobuf) for datastore / state
- **Downloader Engine:**
  - Direct video (up to 4K/1080p) and audio (MP3/M4A) streams download without third-party web scrapers.

---

## 4. UI Design System & Masterpiece YouTube + Liquid Glass Aesthetics
The interface combines YouTube's signature Red & White / Deep Dark visual identity with modern frosted glass (liquid glass) styling:

| Token / Role | Hex Code / Drawable | Purpose / Usage |
|---|---|---|
| **Primary Accent (YouTube Red)** | `#FF0000` (Light) / `#FF0033` (Dark) | Active tabs, play buttons, progress bars, Shorts badge, brand logo |
| **Dark Secondary Accent** | `#AAAAAA` | Video metadata (channel name, views, time ago) |
| **Light Canvas (Pure White)** | `#FFFFFF` | Light mode clean background and surfaces |
| **Dark Canvas (YouTube Dark)** | `#0F0F0F` | Modern YouTube dark mode canvas |
| **OLED Pure Black** | `#000000` | Pure Black theme background |
| **Liquid Glass App Bar** | `@drawable/liquid_glass_appbar_bg` | Translucent top bar with subtle bottom glass stroke |
| **Liquid Glass Bottom Nav** | `@drawable/liquid_glass_nav_bg` | Frosted dock navigation with 18dp rounded top corners & glass border |
| **Liquid Glass Duration Badge** | `#CC000000` (`@color/duration_background_color`) | Frosted black pill badge on thumbnail corner |
| **YouTube Shorts Badge** | `#E6FF0033` + `@drawable/ic_shorts` | Red glass pill overlay indicating Shorts |
| **Full-Width Video Cards** | `14dp` Corner Radius, 16:9 ratio | Modern YouTube Android app edge-to-edge thumbnail styling |

---

## 5. CI/CD & Automated Release Pipeline
All automated pipelines are located in `.github/workflows/`:
- **`ci.yml`**:
  - Triggers on push to `main` and pull requests.
  - Runs JDK 21 setup, Gradle cache, and builds `assembleDebug`.
  - Automatically creates a GitHub Pre-release (`tag: nightly`) with the compiled `Yougram.apk`.
- **`build-release.yml`**:
  - Handles production signing and release builds when tag versioning is triggered.
- **`codeql-analysis.yml`**:
  - Automated security and vulnerability scanning.

---

## 6. Live Release & Artifact Registry

| Release Tag | Release Type | Published Date | Artifact | Size | SHA256 Checksum Preview |
|---|---|---|---|---|---|
| `nightly` | Pre-release | 2026-11-20 14:23 UTC | `Yougram.apk` | ~20.52 MiB | `c9ab7ddb65eb215a1508ccc88...` |

Direct Nightly URL: `https://github.com/aswadhkrishna22-prog/Yougram/releases/tag/nightly`

---

## 7. Changelog & Project Updates

### [2026-11-20] — Masterpiece Red & White UI + Liquid Glass Transformation
- **YouTube Red & White Palette:** Upgraded default accent color to vibrant YouTube Red (`#FF0000` Light / `#FF0033` Dark), crisp white background (`#FFFFFF`), and authentic YouTube Dark background (`#0F0F0F`).
- **Liquid Glass Effects:**
  - Added `@drawable/liquid_glass_nav_bg.xml`: Translucent floating bottom navigation with 18dp rounded top corners and frosted glass border.
  - Added `@drawable/liquid_glass_appbar_bg.xml`: Translucent top bar with frosted bottom separator.
  - Added `@drawable/ic_shorts.xml`: Vector icon for YouTube Shorts.
- **Masterpiece Thumbnails & Cards (`trending_row.xml`):**
  - Upgraded thumbnail cards to `14dp` corner radius with 16:9 aspect ratio matching the official YouTube Android app.
  - Added dedicated YouTube Shorts badge (`shorts_badge_card`) with red glass pill.
  - Added 3-dots more menu button (`@+id/more_options`) for 1-tap options sheet.
  - High-contrast typography (`15sp` bold title, `12sp` channel & view stats).
- **Trending / Explore Tab:**
  - Enabled Trending on the bottom navigation bar (`bottom_menu.xml`) so users can access Trending / Explore right from the main dock.
  - Enhanced category tabs in `fragment_trends.xml` with YouTube Red indicators and smooth ripple.
- **Search Experience:**
  - Refined `suggestion_row.xml` with sleek liquid glass spacing, crisp typography, and subtle ripples.

### [2026-11-20] — Initial Release & Master Knowledge Setup
- **Initial Release:** Created and pushed initial project release with 100% ad-blocking, SponsorBlock, PiP, background play, and RYD.
- **CI Build:** GitHub Actions completed the first build (`✓ CI elapsed 5m 55s`).
- **Release:** Published `Yougram Nightly 20-11-2026` with `Yougram.apk` (20.52 MiB).
- **Knowledge Base:** Initialized `YOUGRAM_MASTER_KNOWLEDGE.md` as the permanent architecture and project memory.
