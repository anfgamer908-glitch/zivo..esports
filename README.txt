ZIVO eSports Android package — ONLINE + PHOTO UPLOAD FIX

Package: com.zivo.esports

Important fixes in this version:
1. Bundled HTML is served through WebViewAssetLoader using
   https://appassets.androidplatform.net/assets/index.html instead of
   file:///android_asset/index.html. This fixes Supabase fetch/XHR failures
   caused by the file:// origin in Android WebView.
2. Android WebChromeClient.onShowFileChooser is enabled so HTML
   <input type="file"> opens Gallery/Files and returns selected images.
3. INTERNET permission remains enabled.
4. Existing ZIVO eSports HTML, Supabase URL/key, tournament features,
   withdrawal, QR/photo fields and other app logic are kept unchanged.

Build:
Open this project in Android Studio, let Gradle sync, then
Build > Build APK(s).

This is a source project, not a prebuilt APK.

PHOTO + SUPABASE FIX NOTES
- MainActivity uses WebViewAssetLoader on the Supabase hostname so bundled HTML and Supabase REST share an HTTPS origin.
- Native WebChromeClient file chooser supports Android Gallery/Files via ACTION_OPEN_DOCUMENT with ACTION_GET_CONTENT fallback.
- IMPORTANT: uninstall the old APK before installing a build from this project, then rebuild so the updated MainActivity is packaged.


FINAL FIX NOTES
- Supabase REST requests are routed through a native Android HTTPS bridge to avoid WebView CORS/origin failures.
- File chooser uses native Android picker for image/* inputs.
- Online warning is non-blocking so file inputs remain tappable even during a temporary network failure.
- Build a fresh APK after uninstalling the previous APK and cleaning the project.
