# Alribal Althahabi Visits (Android)

Sales-visit tracking app for Android (Kotlin, Jetpack Compose, Room, Google Play Services Location).
Arabic and English with right-to-left layout. Works offline; all data is stored on the phone.

## How to build the APK

1. Install **Android Studio** (Koala or newer) with Android SDK 34.
2. Open this folder (`AlribalVisits`) in Android Studio and let Gradle sync (needs internet the first time).
3. Connect an Android phone with USB debugging on, or start an emulator, then press **Run**.
4. For an APK to share: **Build > Build Bundle(s) / APK(s) > Build APK(s)**.
   The file is created in `app/build/outputs/apk/debug/`.

Minimum Android version: 8.0 (API 26).

## What it does

- **Clients**: name, company, contact person, phone, address, saved GPS location, opportunity status, expected value, notes. Call, WhatsApp and Navigate buttons. Search.
- **Visits**: plan a visit (client, date, time, purpose). Tabs for Today, Upcoming, Completed.
- **Trip tracking**: *Start trip* records the departure time and position and starts live GPS tracking (foreground notification).
  Arrival is detected automatically within 100 m of the client's saved location, or the rep taps *I have arrived*.
  The app records travel time (departure to arrival), visit duration, and distance travelled.
- **Visit report**: outcome, notes, next action, and update of the opportunity status when the visit ends.
- **Dashboard**: visits today, completed in 7 days, average travel time, average visit duration, total distance, opportunity pipeline by status and value, CSV export (opens in Excel).
- **Fake GPS detection**: trips with mock locations are flagged and the mock points are ignored.

## Notes and settings

- WhatsApp links turn local numbers (starting with 0) into international format using `DEFAULT_COUNTRY_CODE = "964"` (Iraq) in `ui/Common.kt`.
- The 100 m arrival radius is `GEOFENCE_METERS` in `TripService.kt`.
- App name is set in `res/values/strings.xml` (English) and `res/values-ar/strings.xml` (Arabic).
- Save each client's location once (Edit client > *Use my current location*, standing at the client's shop). Without a saved location, arrival is manual.

## Not included yet

This version is a single-phone app. There is no login, no shared server, and no manager live map, because those need a backend (for example Firebase or your own API). Natural next steps:

1. Backend sync so all reps' visits appear in one manager dashboard and live map.
2. Rep login and roles (rep, supervisor, admin).
3. Photos and voice notes in the visit report.
4. Late-arrival alerts, targets, and route optimization.
