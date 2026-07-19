# MÊ anything — bản tải & landing page

Repo **public** chứa trang tải và file cập nhật cho app [MÊ anything](https://github.com/mittohoa/me-anything) (source ở repo private).

## Nội dung
- `index.html` — landing page (bật GitHub Pages để phục vụ).
- `version.json` — manifest cập nhật (app đọc file này để biết có bản mới).
- `me-anything-<version>.apk` — file cài Android.

## Quy trình mỗi lần release
1. Ở repo source: tăng `version` trong `pubspec.yaml` (vd `1.0.1+2`) rồi
   `flutter build apk --release --split-per-abi`.
2. Copy `app-arm64-v8a-release.apk` → đổi tên `me-anything-<version>.apk`, đặt vào repo này.
3. Cập nhật `version.json`: tăng `versionCode` (= build number), sửa `versionName`, `apkUrl`, `notes`.
4. Commit & push. App đang cài sẽ tự phát hiện bản mới → tải nền → cài.

> `versionCode` trong `version.json` PHẢI bằng build number (số sau dấu `+` trong pubspec)
> của APK tương ứng, và lớn hơn bản đang cài thì app mới báo cập nhật.
