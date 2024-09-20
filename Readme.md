## Android App Shortcuts Module

This module provides a reference implementation for integrating Android App Shortcuts (Static, Dynamic, and Pinned) into your Android projects using Kotlin and Jetpack Compose.

### Features

- **Static Shortcuts**: Predefined shortcuts that are declared in the app's manifest.
- **Dynamic Shortcuts**: Shortcuts that can be added, updated, and removed at runtime.
- **Pinned Shortcuts**: Shortcuts that can be pinned to the launcher by the user.

### Requirements

- **Android Studio**: Koala | 2024.1.1
- **Kotlin**: 1.8
- **Gradle**: 7.0+
- **Android API Level**: 21+

### Setup

1. **Clone the repository**:
    ```sh
    git clone <repository-url>
    ```

2. **Open the project in Android Studio**:
    - Open Android Studio.
    - Select `File > Open` and navigate to the cloned repository.

3. **Sync the project with Gradle**:
    - Click on `Sync Project with Gradle Files` in the toolbar.

### Usage

1. **Add the module to your project**:
    - Include the module in your `settings.gradle` file:
      ```groovy
      include ':appshortcuts'
      project(':appshortcuts').projectDir = new File('path/to/appshortcuts')
      ```

2. **Add dependencies**:
    - Add the module as a dependency in your app's `build.gradle` file:
      ```kotlin
      dependencies {
          implementation(project(":appshortcuts"))
      }
      ```

3. **Declare Static Shortcuts**:
    - Define static shortcuts in your `AndroidManifest.xml`:
      ```xml
      <manifest ...>
          <application ...>
              <meta-data
                  android:name="android.app.shortcuts"
                  android:resource="@xml/shortcuts" />
          </application>
      </manifest>
      ```

4. **Use Dynamic and Pinned Shortcuts**:
    - Refer to the `MainActivity.kt` for implementation details on how to add dynamic and pinned shortcuts.

### Code Overview

- **MainActivity.kt**: Handles the creation and management of dynamic and pinned shortcuts.
- **MainViewModel.kt**: Manages the state of the shortcut type.
- **Theme.kt**: Defines the theme and color schemes for the app.

### Example

```kotlin
// Adding a dynamic shortcut
private fun addDynamicShortcut() {
    val shortcut = ShortcutInfoCompat.Builder(applicationContext, "dynamic")
        .setShortLabel("Call Mum")
        .setLongLabel("Clicking this will call your mum")
        .setIcon(IconCompat.createWithResource(
            applicationContext, R.drawable.baseline_baby_changing_station_24
        ))
        .setIntent(
            Intent(applicationContext, MainActivity::class.java).apply {
                action = Intent.ACTION_VIEW
                putExtra("shortcut_id", "dynamic")
            }
        )
        .build()
    ShortcutManagerCompat.pushDynamicShortcut(applicationContext, shortcut)
}
```

### License

This project is licensed under the MIT License. See the `LICENSE` file for more details.

### Contributing

Contributions are welcome! Please open an issue or submit a pull request for any changes.

### Contact

For any inquiries, please contact `harshsingh-io` on GitHub.