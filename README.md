# BD Price Finder Android Project

Android WebView wrapper for the BD Price Finder web app. The app loads its bundled HTML from Android's secure `appassets` HTTPS origin so camera APIs can work inside WebView.

## Features
- Live product price search through the configured Cloudflare Worker
- Barcode scanning (native `BarcodeDetector` when available, ZXing browser fallback otherwise)
- Camera photo selection and Gemini photo recognition through the Worker
- Product result cards with images and source links

## Before building
1. Deploy your Cloudflare Worker and confirm its GET health check returns `BD Price Finder API is running`.
2. In Cloudflare Worker Settings → Variables and Secrets, set `TAVILY_API_KEY` and `GEMINI_API_KEY`. Do not put API keys in this Android project.
3. If your Worker URL changes, update `API_URL` near the top of `app/src/main/assets/index.html`.

## Build APK with GitHub Actions
1. Create a GitHub repository.
2. Upload the **contents** of this folder to the repository root (not the containing folder itself).
3. Commit and push to `main` or `master`.
4. Open the repository's **Actions** tab.
5. Open **Build BD Price Finder APK** and wait for the run to finish successfully.
6. Open the completed run and download the artifact named `BD-Price-Finder-debug-apk`.
7. Extract the ZIP; install `app-debug.apk` on your Android phone. Allow installation from the browser/file manager if Android asks.

You can also start a build manually from Actions → Build BD Price Finder APK → Run workflow.

## Notes
- The project uses Android Gradle Plugin 8.7.3, Gradle 8.9, JDK 17, and compile SDK 35.
- Camera permission is requested when the app first uses the scanner.
- Barcode scanning fallback loads ZXing from a CDN, so the phone needs internet access.
- The debug APK is for testing. A signed release APK can be configured later.


## App branding assets
- Custom BD Price Finder launcher icon is included in all standard Android densities.
- Android 8+ adaptive launcher icon is included.
- A branded green-and-white opening splash screen is configured as the launch window background.
