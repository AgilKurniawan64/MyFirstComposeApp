# Homework 6 — My First Compose App

## Task 3: Colour and Spacing
- **Colour used:** LightGray
- **Padding kept:** 24.dp
- **What changed / what stayed the same:**
  When changing padding from 8 dp to 48 dp, the content (texts and image) moves further inward from the screen borders, leaving a wider colored background margin around the elements. What stays the same is the background color of the `Surface` and the internal spacing between the text components inside the `Column`.

## Task 4: Build Error
- **First error message:**
  `error: invalid resource directory name: .../res/drawable/My-Picture.png` or `File name must contain only lowercase a-z, 0-9, or underscores.`
- **Cause:** Android resource files strictly require lowercase letters, digits, and underscores. Uppercase letters and hyphens (`-`) are illegal in resource file names.
- **Why other errors appear:** Because the resource naming fails during the resource compilation phase, Android Studio fails to generate the corresponding `R.drawable.My_Picture` reference in the `R.java` class, causing secondary "Unresolved reference" errors in Kotlin code.
- **Fix:** Renamed `My-Picture.png` back to `my_picture.png` and rebuilt the project.

## Task 5: Explore the Project
- **(a) MainActivity:** `app/src/main/java/com/example/myfirstcomposeapp/MainActivity.kt` — Contains the main entry point and UI layout logic of the Android application.
- **(b) Gradle file:** `app/build.gradle.kts` — Configures module-level build settings, target/min SDKs, and dependencies for the `app` module.
- **(c) Launcher image line:** `painter = painterResource(id = R.drawable.ic_launcher_foreground)` — References the launcher icon vector drawable stored in the resources folder.

## Task 6: Preview vs Run
Changing text in `@Composable` updates the Preview panel immediately because the Compose Preview tooling re-renders the UI code in real time within Android Studio. However, the app on the physical device or emulator does not change because it is running a previously compiled APK installed on the target system. To update the running app, you must re-compile and install the project using the **Run** button.

## Task 7: Views vs Compose
1. In the traditional **Imperative (Views)** approach, developers create layout XMLs and manually mutate UI states step-by-step using methods like `findViewById()` and `setText()`. In the **Declarative (Compose)** approach, developers describe what the UI should look like for a given state using Kotlin `@Composable` functions, and the framework automatically updates and redraws the UI when state changes.

2. **Library Layers & Packages:**

| Composable | Package | Library layer |
|---|---|---|
| `Column` | `androidx.compose.foundation.layout` | Foundation Layout |
| `Text` | `androidx.compose.material3` | Material 3 |
| `Image` | `androidx.compose.foundation` | Foundation |