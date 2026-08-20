# Boxing Timer

Browser-based boxing and exercise timers with three interfaces for different training setups.

## Start

Open [index.html](index.html) in a browser and choose the timer you want to use.

You can also open a timer directly:

- [Boxing Timer Pro](main_timer.html): full desktop timer with boxing presets, round settings, sound controls, Screen Lock, fullscreen mode, and workout history.
- [Cornerman](mobile_timer.html): compact timer designed for mobile-sized screens.
- [Tabata Timer](tabata_timer.html): interval timer with Tabata, HIIT, EMOM, and cardio presets.

## Files

- `index.html` is the timer selection page.
- `main_timer.html` is the full-featured timer.
- `mobile_timer.html` is the compact mobile timer.
- `tabata_timer.html` is the configurable interval timer.

No build step or installation is required for the browser version. Fonts, icons, and the Tailwind runtime are bundled in `www/vendor/`. Root HTML files reference those assets through `./www/vendor/`, while the synchronized `www/` copies use `./vendor/` for Android WebView loading.

The main timer's `Screen Lock` control uses the browser Screen Wake Lock API to keep the display awake during a workout when supported. The Tabata timer includes mute controls, editable interval settings, quick presets, and a footer link back to timer selection.

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
cp android/app/build/outputs/apk/debug/app-debug.apk ~/Downloads/Cornerman-Boxing-Timer-debug.apk
```

The build uses the workspace-local Android SDK in `.android-sdk/` and JDK 21 in `.jdk21/`. A custom launcher icon is defined at `android/app/src/main/res/drawable/cornerman_icon.xml`.

The Android app starts at `www/index.html`; `npm run cap:sync` copies the synchronized browser files and bundled assets into the native Android project before building. Keep the root HTML files and their `www/` counterparts synchronized when making changes.
