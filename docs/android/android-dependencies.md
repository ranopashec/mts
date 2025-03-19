# Android Dependencies

## 1. Prerequisites
- Install **Android Studio** ([Download](https://developer.android.com/studio)).
- Install **Java Development Kit (JDK 11+)**.
- Set up **Android SDK** and **NDK**.

## 2. Dependency Management
- Use **Gradle** for dependency management.
- Fetch dependencies from **Maven, JCenter, and Google Play Services**.
- Define dependencies in `build.gradle.kts`:

```kotlin
dependencies {
    implementation("androidx.core:core-ktx:1.9.0")
    implementation("com.squareup.retrofit2:retrofit:2.9.0")
    implementation("com.google.dagger:hilt-android:2.44")
    kapt("com.google.dagger:hilt-compiler:2.44")
}
