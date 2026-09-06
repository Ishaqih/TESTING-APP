# MENA-ME Android

A minimal secure Android WebView wrapper for:

https://hr.uop.edu.jo

## Security behavior

- HTTPS-only traffic.
- Uses the Android system trust store.
- Does not bypass SSL certificate errors.
- Cleartext HTTP is disabled.
- WebView debugging is disabled.
- File/content access is disabled.
- Mixed HTTP/HTTPS content is blocked.
- Only the University HR host is kept inside the WebView.
- Other HTTPS links open in the device browser.
- No username/password is stored by the app.

## Build APK with GitHub Actions

1. Create a new empty GitHub repository.
2. Upload **all contents** of this project to the repository root.
   - Important: `.github` must be at the repository root.
   - Do not upload the outer `MENA-ME-Android` folder as an extra nested folder.
3. Commit to the `main` branch.
4. Open **Actions**.
5. Choose **Build MENA-ME APK**.
6. If it did not start automatically, click **Run workflow**.
7. Wait for the build to complete.
8. Open the successful run.
9. Under **Artifacts**, download **MENA-ME-APK**.
10. Extract the downloaded ZIP.
11. Install `app-debug.apk` on the Android device.

## Important

The generated debug APK is signed automatically with Android's debug signing key and is suitable for internal testing.

For controlled long-term internal distribution, create a release keystore and sign all future versions with the same private key.

## If login redirects outside hr.uop.edu.jo

This project intentionally opens external HTTPS domains in the normal browser. If the MENA-ME login flow depends on another trusted domain that must stay inside the WebView, add that domain to the allowed-host logic in `MainActivity.java`.
