# Olauncher Fanmod

An **unofficial fanmod** of [Olauncher](https://github.com/tanujnotes/Olauncher) — the minimal, ad-free Android launcher by **[tanujnotes](https://github.com/tanujnotes)**.

All the credit for this launcher goes to him. This repository only adds a handful of personal
tweaks on top of his work. If you like it, **please support the original developer** rather than
this fork:

- [GitHub Sponsors](https://github.com/sponsors/tanujnotes)
- [Buy Me a Coffee](https://www.buymeacoffee.com/tanujnotes)
- [PayPal](https://www.paypal.me/tanujnotes)
- Install the original from [F-Droid](https://f-droid.org/packages/app.olauncher) or [Play Store](https://play.google.com/store/apps/details?id=app.olauncher), and rate it there
- Check out his [Pro Launcher](https://play.google.com/store/apps/details?id=app.prolauncher)

Contact the original author: [X/Twitter](https://x.com/tanujnotes) • [Reddit](https://reddit.com/user/tanujnotes/) • [Bluesky](https://bsky.app/profile/tanujnotes.bsky.social)

> This is not affiliated with or endorsed by tanujnotes. It installs alongside the original as a
> separate app (`app.olauncher.fanmod`), so it will never overwrite or interfere with it.

##

## Modifications

Modified from [Olauncher v6.9.1](https://github.com/tanujnotes/Olauncher) since September 2026:

- **Your own wallpaper** — pick any image from the gallery and set it as the wallpaper, straight
  from the settings. Turns off the daily wallpaper so the two do not fight over the same slot,
  scales the image to the screen and honours the EXIF orientation of camera photos.
- **Font picker** — nine fonts, each preview rendered in its own typeface: the four system
  families plus bundled Inter, Manrope, Outfit, Space Grotesk and Lexend.
- **Bold font actually works everywhere** — it now drives the variable weight axis instead of
  only swapping the light/regular cut, so it applies to every font and to every screen.
- **Linear text size** — Android 14+ scales `sp` non-linearly, which made large text on the home
  screen stop growing past a scale of about 1.2. Text sizes are now applied to the views directly,
  so the setting stays proportional across its whole range.
- **Back button in the settings**, and the font panel stays open while you compare fonts instead
  of dropping you on the home screen after every pick.
- **Different defaults**: text size 1.5, Lexend, bold on, 6 apps on the home screen.

##

## Building

Requires **JDK 17** and an Android SDK with the platform matching `compileSdk` (currently 36).

```bash
git clone https://github.com/Kappowicz/Olauncher-Fanmod.git
cd Olauncher-Fanmod

export JAVA_HOME=$(/usr/libexec/java_home -v 17)   # macOS; elsewhere point it at any JDK 17
export ANDROID_HOME=/path/to/android-sdk           # must contain platforms/android-36

./gradlew assembleDebug
```

The APK lands in `app/build/outputs/apk/debug/app-debug.apk`. Install it with
`adb install -r app/build/outputs/apk/debug/app-debug.apk`.

A few things worth knowing:

- Gradle 8.11 does not support the newest JDKs. If the build fails with a Java version error,
  check that `JAVA_HOME` really points at a JDK 17 (`$JAVA_HOME/bin/java -version`).
- If the build complains about a missing platform, install it with
  `sdkmanager "platforms;android-36"`.
- `assembleRelease` produces an **unsigned** APK, because this repository ships no signing
  config. Use the debug build for testing, or add your own keystore before releasing.

##

## Licenses

This fork is released under the **[GNU GPLv3](https://www.gnu.org/licenses/gpl-3.0.en.html)**, the
same license as the original Olauncher. See [LICENSE](LICENSE).

The bundled fonts are licensed under the **SIL Open Font License 1.1**; their license files ship
with the app in `app/src/main/assets/licenses/`.

| Font | Copyright |
| --- | --- |
| [Inter](https://github.com/rsms/inter) | The Inter Project Authors |
| [Manrope](https://github.com/sharanda/manrope) | The Manrope Project Authors |
| [Outfit](https://github.com/Outfitio/Outfit-Fonts) | The Outfit Project Authors |
| [Space Grotesk](https://github.com/floriankarsten/space-grotesk) | The Space Grotesk Project Authors |
| [Lexend](https://github.com/googlefonts/lexend) | The Lexend Project Authors |
