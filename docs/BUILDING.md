# Building MAVIS APK

Three ways to build the Android APK.

## Option 1: GitHub Actions (Easiest)

No setup required. Every push to `main` automatically builds the APK.

**Steps:**
1. Push to `main` branch
2. Go to **Actions** tab on GitHub
3. Find the "Build Android APK" workflow run
4. Download the `MAVIS-APK` artifact
5. Transfer to Android device and install

## Option 2: Build Locally with Capacitor

**Prerequisites:**
- Node.js 16+
- Android SDK (via Android Studio or command-line tools)
- Gradle

**Step-by-step:**

```bash
git clone https://github.com/kelbrictech/MAVIS.git
cd MAVIS
npm install -g @capacitor/cli
npm install
npx cap init MAVIS com.mavis.pagegen --web-dir .
npx cap add android
npx cap sync
cd android
./gradlew build
cd ..
```

APK location: `android/app/build/outputs/apk/debug/app-debug.apk`

**To run directly on connected device:**
```bash
npx cap run android
```

## Option 3: Cordova (Alternative)

```bash
npm install -g cordova
cordova create mavis-build com.mavis.pagegen MAVIS
cd mavis-build
cordova platform add android
cp ../index.html www/
cordova build android
```

APK: `platforms/android/app/build/outputs/apk/debug/app-debug.apk`

## Troubleshooting

### "gradlew: command not found"
Make sure you're in the `android/` directory:
```bash
cd android
./gradlew build
```

### "Java version not compatible"
Install Java 11 and set `JAVA_HOME` appropriately.

### "SDK location not found"
Create `local.properties` in the `android/` directory with your Android SDK path.

### APK won't install
Ensure your Android device allows installation from unknown sources, or sideload via ADB.

## Signing the APK (for release)

To publish to Google Play, generate a keystore and build a signed release APK. Keep signing credentials out of this public repository.
