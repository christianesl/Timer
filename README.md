# Boxing Timer

Browser-based boxing and exercise timers with two interfaces for different training setups.

## Start

Open [index.html](index.html) in a browser and choose the timer you want to use.

You can also open either timer directly:

- [Boxing Timer Pro](main_timer.html): full desktop timer with presets, trainer callouts, sound controls, wake lock, and fullscreen mode.
- [Cornerman](mobile_timer.html): compact timer designed for mobile-sized screens.

## Files

- `index.html` is the timer selection page.
- `main_timer.html` is the full-featured timer.
- `mobile_timer.html` is the compact mobile timer.

No build step or installation is required. Fonts, icons, and the Tailwind runtime are bundled in `vendor/`, so the pages can run from local files without an internet connection. The vendor files are also ready to be included in an Android WebView or Capacitor APK.

## Android APK

The project includes a Capacitor Android wrapper. Build the debug APK with:

```bash
npm run build:apk
```

The APK is generated at:

`android/app/build/outputs/apk/debug/app-debug.apk`

To create the named APK used for phone installation:

```bash
mkdir -p ~/Downloads
cp android/app/build/outputs/apk/debug/app-debug.apk ~/Downloads/Cornerman-Boxing-Timer.apk
```

The build uses the workspace-local Android SDK in `.android-sdk/` and JDK 21 in `.jdk21/`. A custom launcher icon is defined at `android/app/src/main/res/drawable/cornerman_icon.xml`.

The Android app starts at `www/index.html`; `npm run cap:sync` copies the current browser files and bundled assets into the native Android project before building.
