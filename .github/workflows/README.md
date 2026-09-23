# Heavenly Wallpapers — Android v1.2

A native Kotlin + Jetpack Compose Christian wallpaper app foundation.

## What works
- Dark cinematic UI
- Home / Explore / Favorites / Downloads / Settings
- Search across wallpaper title/category
- Six wallpaper scenes rendered locally (no remote server required)
- Persistent Favorites using SharedPreferences
- 4K-oriented wallpaper generation for downloads
- Save generated wallpaper images to Pictures/Heavenly Wallpapers on modern Android
- Set generated scene as a static wallpaper
- Actual Android `WallpaperService` live wallpaper
- Live wallpaper selection is persisted and rendered by the service
- Smooth lightweight procedural animation in the live wallpaper

## Build
Open this project folder in Android Studio with an Android SDK installed. Let Gradle sync, connect an Android device with USB debugging enabled, and press Run.

For a release APK: Android Studio → Build → Generate App Bundles or APKs → Generate APKs.

## Production roadmap
- Replace procedural scenes with commissioned/AI-generated 4K artwork.
- Add Media3/video or OpenGL particle layers for richer live scenes.
- Add Room/DataStore for richer offline state.
- Add a remote catalog/API and admin content dashboard.
- Add subscriptions/ads only after defining the business model and privacy requirements.
- Add privacy policy, terms, app icon, splash artwork, store screenshots, and release signing.
