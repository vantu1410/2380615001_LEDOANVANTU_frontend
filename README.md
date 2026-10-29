# TuTime Flutter frontend

Flutter mobile client for the TuTime employee attendance application.

## Run

```powershell
flutter pub get
flutter run --dart-define=OFFICE_LAT=10.7769 --dart-define=OFFICE_LNG=106.7009
```

The app uses the deployed API at `https://ledoanvantu2-api.onrender.com` by default. Override it with `--dart-define=API_BASE_URL=https://your-api-host` when building for another deployment.

The app supports email registration/login with OTP, role-based admin and employee views, employee CRUD for administrators, attendance history and review, QR check-in, GPS distance and accuracy review, and atmospheric-pressure sensor readings. The regular shift is 08:00–17:00; checkout after 17:00 is marked as overtime.

No credentials or provider API keys belong in this repository. Configure secrets only in the API hosting environment.
