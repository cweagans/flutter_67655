# flutter_67655

Repro/testing for https://github.com/flutter/flutter/issues/67655

# Env info

`flutter --version`:

```
Flutter 2.2.2 • channel stable • https://github.com/flutter/flutter.git
Framework • revision d79295af24 (3 days ago) • 2021-06-11 08:56:01 -0700
Engine • revision 91c9fc8fe0
Tools • Dart 2.13.3
```

---

`flutter doctor`:

```
[✓] Flutter (Channel stable, 2.2.2, on macOS 11.4 20F71 darwin-x64, locale en-US)
[✓] Android toolchain - develop for Android devices (Android SDK version 29.0.2)
[✓] Xcode - develop for iOS and macOS
[✓] Chrome - develop for the web
[✓] Android Studio (version 3.5)
[✓] VS Code (version 1.57.0)
[✓] Connected device (1 available)

• No issues found!
```

## Test process

For each case:

```bash
rm -rf .dart_tool build .packages
flutter pub get
flutter build web
pushd build/web
devd .
```

(open browser to http://localhost:8000/ and record result)

```bash
popd
rm -rf .dart_tool build .packages
flutter pub get
flutter run
```

(wait for chrome to open and record result)

## Test cases

Works = both images show up
Doesn't work = any other behavior

* Test 1: `assets/` dir and `assets/more_assets/` dir
    * `flutter build web`: Works
    * `flutter run`: Works
