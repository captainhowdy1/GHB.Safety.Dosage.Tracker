# G Safety Tracker

A deliberately simple harm-reduction logger for doses of GHB, GBL, or 1,4-BDO that have **already been taken**.

## What it does
- Logs amount in mL, substance, and exact time.
- Shows live elapsed time since the most recent logged dose.
- Shows number of logged doses within the rolling previous 60 minutes.
- Shows recent mL totals by substance rather than adding unlike substances together.
- Before a third (or later) entry inside 60 minutes, displays a full-screen high-risk warning.
- The warning lets the user cancel if the dose was not taken, or log it if it was already taken so the history remains accurate.
- Stores data locally on the device. No account or network is required by the Android wrapper.
- Can export history as CSV in normal browsers. WebView download behavior varies by Android version.

## Safety design
This app intentionally does **not** estimate drug concentration in the body, recommend a dose, convert between GHB/GBL/BDO, or tell the user when another dose is safe. Those estimates would be unreliable and could create false reassurance.

## PWA version
The `pwa` folder is a complete installable Progressive Web App. Host the folder over HTTPS, open it in Chrome on Android, then choose **Install app** / **Add to Home screen**. Once installed it works offline.

For a quick same-network test from a computer:

```bash
cd pwa
python -m http.server 8080
```

Then open `http://COMPUTER-IP:8080` on the Android phone while both devices are on the same Wi-Fi. Browser PWA installation usually requires HTTPS, though the app itself can still be tested over local HTTP.

## Native Android wrapper
The `android` folder is a small native Android project that wraps the exact same interface in an offline WebView. It requires no Internet permission.

Current project configuration:
- Android Gradle Plugin 9.4.0
- compileSdk 36
- targetSdk 36
- minSdk 26
- Java source, no third-party libraries

Open the `android` folder in Android Studio Quail 4 (2026.1.4) or another compatible version. Let Android Studio install the requested SDK/Gradle components, then use **Build > Build APK(s)**. The debug APK will normally be generated under `app/build/outputs/apk/debug/`.
