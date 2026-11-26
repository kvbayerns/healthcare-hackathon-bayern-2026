# Development

## Environment Setup

What we need (from https://ionicframework.com/docs/intro/environment):

* [Git](https://git-scm.com/) - for sharing and versioning files and code
* [Node & npm](https://nodejs.org/) - as runtime for tools
* [Java Development Kit (JDK)](https://adoptium.net/) - as runtime for Android SDK
* [Android SDK](https://developer.android.com/studio) - for building and deploying App to smartphone
* [Ionic Framework](https://ionicframework.com/) - as platform independent mobile app framework
* [Capacitor](https://capacitorjs.com/) - to be able to use smartphone features from app
* [Visual Studio Code](https://code.visualstudio.com/) + [WebNative Plugin](https://marketplace.visualstudio.com/items?itemName=WebNative.webnative) (or another IDE you are comfortable with) - for hacking!
* [Angular](https://angular.dev/) - for UI

### Visual Studio Code

[Download and Install](https://code.visualstudio.com/download)

### Git

#### Installation under Windows

* Download "x64 version of Git for Windows" from https://git-scm.com/download/win.
* Execute downloaded EXE-file and install with default settings

#### Configuration

```shell
git config --system core.autocrlf true
git config --system credential.helper store
git config --system core.longpaths true

git config --global user.name your_username
git config --global user.email your.email@mail.xy
```

#### Usage

Clone repository:

```shell
cd projects
git clone https://github.com/kvbayerns/healthcare-hackathon-bayern-2026.git
```

### Java Development Kit (JDK)

* Download OpenJDK version "Eclipse Temurin JDK" ("25 LTS x64 version for Windows") from https://adoptium.net/de/temurin/releases
* Execute downloaded MSI-file and install with default settings.

### Android SDK

We just install the Android SDK command line tools without Android Studio.
(If you already installed and are familiar with Android Studio, just keep going :-)).

Documentation here: https://developer.android.com/tools/sdkmanager

* Download Android SDK command line tools from https://developer.android.com/studio#command-line-tools-only
* Unzip downloaded ZIP-file into a target directory, e.g. `~\dev\android_sdk`, resulting in directory `~\dev\android_sdk\cmdline-tools`
* In the unzipped `cmdline-tools` directory, create a sub-directory called latest.
* Move the original `cmdline-tools` directory contents, including the `lib` directory, `bin` directory, `NOTICE.txt` file, and `source.properties` file, into the newly created `latest` directory. You can now use the command-line tools from this location.

Install an Android SDK:

You can use the sdkmanager (new command: `android`, see https://d.android.com/tools/agents/android-cli) to list installed and available packages, install packages, and update packages.

```shell
cd ~\dev\android_sdk\cmdline-tools\latest\bin
.\android update

.\android sdk list --all
Installed packages:
  (no installed packages)
Available packages:
  add-ons/addon-google_apis-google-10                                                     2.0.0                  Google APIs
  ...
  platform-tools                                                                          37.0.0                 Android SDK Platform-Tools
  platforms/android-10                                                                    2.0.0                  Android SDK Platform 10
  platforms/android-11                                                                    2.0.0                  Android SDK Platform 11
  ...
```

Install the platform of your target device, e.g. Android 16 (API Level 37) (see https://developer.android.com/tools/releases/platforms):

```shell
# Example: Installing SDK packages for API Level 37 (Android 16)

.\android sdk install "platform-tools" "platforms;android-37.2" "build-tools;37.0.0" "system-images;android-37.2;google_apis_ps16k;x86_64"
```

List installed SDK:

```shell
.\android sdk list
Installed packages:
  build-tools/36.0.0                                  36.0.0      Android SDK Build-Tools 36
  emulator                                            36.6.11     Android Emulator
  platform-tools                                      37.0.0      Android SDK Platform-Tools
  platforms/android-36                                2.0.0       Android SDK Platform 36
  system-images/android-36/google_apis/x86_64         7.0.0       Google APIs Intel x86_64 Atom System Image
```

All SDKs are installed into `C:\Users\<your-username>\AppData\Local\Android\Sdk` or `C:\Users\<your-username>\DEV\android_sdk`

#### Configuration

* Set user environment variables:
  * `ANDROID_HOME` (the path to the SDK installation directory) to `C:\Users\eichira\AppData\Local\Android\Sdk` (or `C:\Users\<your-username>\DEV\android_sdk`)
  * `PATH`: add 
* Add to environment variable PATH: `%ANDROID_HOME%\platform-tools`


### Node & npm

#### Installation

Install with NVM that gives the flexibility to install several versions of Node+npm and switch between them.

* Download latest `nvm-setup.exe` (v1.2.2) from https://github.com/coreybutler/nvm-windows/releases
* Execute `nvm-setup.exe` and install it to a target directory, e.g. `~\dev\nvm`
* Directory for symlink is subdirectory `nodejs`, e.g. `~\dev\nvm\nodejs`

Installation sets environment variables being active after reboot.

Start an **administrator** shell and execute:

```shell
> nvm -v
1.2.2
> nvm current
No current version. Run 'nvm use x.x.x' to set a version.
```

If behind a proxy, configure it, e.g.:

```shell
> nvm proxy http://your.proxy.de:8080/
```

As **normal uder** (not admin) install latest LTS versions:

```shell
> nvm install lts
Downloading node.js version 24.18.0 (64-bit)...
Extracting node and npm...
Complete
Installation complete.
If you want to use this version, type:

nvm use 24.18.0
```

Use it (asks for admin credentials):

```shell
> nvm use 24.18.0
Now using node v24.18.0 (64-bit)
> node -v
v24.18.0
> npm -v
11.16.0
```

#### Usage

```shell
> nvm list
...
> nvm list available
...
> nvm install ...
...
> nvm use 24.18.0
```

### Angular Cli

#### Installation

```shell
> npm install -g @angular/cli
```

## Project Setup

    IMPORTANT: This section is for your reference only.
    -> Skip it, we did this in advance and checked in the project in this repository!

### Create project directory

```shell
mkdir hackathon-2026
```

### Ionic Framework & Capacitor

Install Ionic Framework (from https://ionicframework.com/docs/angular/quickstart):

```shell
npm install -g @ionic/cli
```

For new Ionic projects, Capacitor is already installed in new Ionic apps by default.

### Ionic Angular Project creation

    NOTE: This step can be skipped, we did this in advance and checked in the project in this repository!

Create an Ionic Angular project skeleton (from https://ionicframework.com/docs/angular/quickstart):

```shell
> cd healthcare-hackathon-bayern-2026

> ionic start app blank --type angular
? Would you like to build your app with Standalone Components or NgModules?
 Standalone components are the default way to build with Angular that simplifies the way you build your app.
 To learn more, visit the Angular docs:
 https://angular.dev/guide/components

 Standalone
[INFO] Existing git project found (C:/Laufwerk_D/projects/healthcare-hackathon-bayern-2026). Git operations are disabled.
√ Preparing directory .\app in 1.32ms
√ Downloading and extracting blank starter in 3.69s
> ionic integrations enable capacitor --quiet -- app io.ionic.starter
> npm.cmd i --save -E @capacitor/core@latest
...
> npm.cmd i --save -E @capacitor/haptics @capacitor/app @capacitor/keyboard @capacitor/status-bar
...
? Create free Ionic account? No

Your Ionic app is ready! Follow these next steps:

- Go to your new project: cd .\app
- Run ionic serve within the app directory to see your app in the browser
- Run ionic capacitor add to add a native iOS or Android project using Capacitor
- Generate your app icon and splash screens using cordova-res --skip-config --copy
- Explore the Ionic docs for components, tutorials, and more: https://ion.link/docs
- Building an enterprise app? Ionic has Enterprise Support and Features: https://ion.link/enterprise-edition

> cd app
> ionic serve
...

[INFO] Development server running!

       Local: http://localhost:8100

       Use Ctrl+C to quit this process
```

The basic skeleton ("Hello World") is running and opened in browser! :-)

Files (see https://ionicframework.com/docs/angular/quickstart):

```shell
└── src/
    └── app
        ├── app.component.html
        ├── app.component.scss
        ├── app.component.ts
        ├── app.routes.ts
        └── home/
            ├── home.page.html
            ├── home.page.scss
            ├── home.page.spec.ts
            └── home.page.ts
```

## Run on a Device

(from https://ionicframework.com/docs/angular/quickstart#run-on-a-device)

Ionic's components work everywhere: on iOS, Android, and PWAs. To deploy to mobile, use Capacitor:

```shell
ionic build
ionic cap add android
ionic cap add ios
```

Open the native projects in their IDEs:

```
ionic cap open android
ionic cap open ios
```

Without Android Studio we get an error.

### Compile your native binary

see https://capacitorjs.com/docs/basics/workflow#compiling-your-native-binary

#### Release version

Compile your app in a terminal or in CI environments to build the native project. For Android, `cap build` creates a signed release artifact and requires signing options (keystore path, keystore password, key alias, key password):

```shell
cd C:/Laufwerk_D/projects/hackathon-2026/app
npx cap build android --keystorepath C:/path/to/release-keystore.jks --keystorepass <keystore-password> --keystorealias <key-alias> --keystorealiaspass <key-password>
```

#### Testing version on connected device

For local device testing without release signing, use the run flow instead:

```shell
npx cap run android
√ Copying web assets from www to android\app\src\main\assets\public in 40.26ms
√ Creating capacitor.config.json in android\app\src\main\assets in 1.47ms
[info] Inlining sourcemaps
√ copy android in 67.74ms
√ Updating Android plugins in 4.91ms
[info] Found 4 Capacitor plugins for android:
       @capacitor/app@8.1.1
       @capacitor/haptics@8.0.2
       @capacitor/keyboard@8.0.5
       @capacitor/status-bar@8.0.3
√ update android in 75.17ms
[info] No devices found.
```

#### Testing installable APK

* Create APK

If you want an installable APK without release signing and without a connected device, build the debug variant with Gradle:

```shell
cd C:/Laufwerk_D/projects/hackathon-2026/app/android
.\gradlew.bat assembleDebug
```

The APK will be created at `app/android/app/build/outputs/apk/debug/app-debug.apk`.

* Install on Smartphone for Testing

Use the generated debug APK to test on a real Android phone:

1. Copy `app-debug.apk` to the smartphone, for example by USB file transfer, email, or cloud storage.
2. On the phone, allow installing apps from unknown sources for the app you use to open the file, if Android asks for it.
3. Open the APK on the phone and confirm the installation.
4. After installation, start the app from the launcher like any other app.

If you prefer USB installation from the computer, connect the phone with USB debugging enabled and run:

```shell
adb install -r app/build/outputs/apk/debug/app-debug.apk
```

## Troubleshooting

### How to Unblock android.exe or use sdkmanager

Problem:

"Error occurred during initialization of VM
Unable to load native library: Eine Anwendungssteuerungsrichtlinie hat diese Datei blockiert"

Solution:

Option 1: Turn off Smart App Control (Personal PC)

* Press Win + I to open Settings.
* Go to Privacy & security > Windows Security > App & browser control.
* Click Smart App Control settings and switch it to Off.

Option 2: Keep Using sdkmanager.bat (No Security Changes)

```
cd ~\DEV\android_sdk\cmdline-tools\latest\bin
.\sdkmanager.bat --update
.\sdkmanager.bat --list
.\sdkmanager.bat --install "platform-tools" "platforms;android-37.2" "build-tools;37.0.0" "system-images;android-37.2;google_apis_ps16k;x86_64"
.\sdkmanager.bat --list_installed
```

If you prefer to leave Smart App Control enabled, you can continue using .\sdkmanager.bat for installing and updating SDK packages. Despite the deprecation and JDK 25 warnings, it runs cleanly through your signed Temurin JDK.

## Gradle 8 conflicts with Java 25

Problem:

Solution:

Upgrade to Gradle 9 and Capacitor 9:

```
cd app
npm install -D @capacitor/cli@next
npm install @capacitor/core@next @capacitor/android@next @capacitor/app@next @capacitor/haptics@next @capacitor/keyboard@next @capacitor/status-bar@next
npx cap migrate
Remove-Item -Recurse -Force android
npx cap add android
npx cap sync android
```