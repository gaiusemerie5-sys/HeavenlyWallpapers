name: Build Heavenly Wallpapers APK

on:
  workflow_dispatch:

jobs:
  build:
    runs-on: ubuntu-24.04

    steps:
      - name: Checkout repository
        uses: actions/checkout@v4

      - name: Set up Java 17
        uses: actions/setup-java@v5
        with:
          distribution: temurin
          java-version: '17'

      - name: Set up Android SDK
        uses: android-actions/setup-android@v3

      - name: Install Android SDK packages
        run: |
          yes | sdkmanager --licenses > /dev/null || true
          sdkmanager "platform-tools" "platforms;android-35" "build-tools;35.0.0"

      - name: Install Gradle
        run: |
          curl -L -o gradle.zip https://services.gradle.org/distributions/gradle-8.9-bin.zip
          unzip -q gradle.zip

      - name: Extract Heavenly Wallpapers project
        run: |
          mkdir -p project
          unzip -q HeavenlyWallpapers-v1.3-source.zip -d project

      - name: Find project
        run: |
          find project -maxdepth 3 -type f -name "settings.gradle.kts" -o -name "build.gradle.kts"

      - name: Build APK
        working-directory: project/HeavenlyWallpapers-v1.3
        run: |
          $GITHUB_WORKSPACE/gradle-8.9/bin/gradle :app:assembleDebug --no-daemon --stacktrace

      - name: Upload APK
        uses: actions/upload-artifact@v4
        with:
          name: HeavenlyWallpapers-debug-apk
          path: project/HeavenlyWallpapers-v1.3/app/build/outputs/apk/debug/app-debug.apk
          if-no-files-found: error
