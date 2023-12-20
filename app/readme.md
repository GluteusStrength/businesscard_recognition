# Android Business Card Recognition App

## 폴더 구조

- `business-card-recognition-app`
  - `app`
    - `src`
      - `main`
        - `java/com/example/businesscardrecognition`
          - `MainActivity.java`
          - `SendActivity.java`
          - `ResultActivity.java`
      - `res`
        - `layout`
          - `activity_main.xml`
          - `activity_send.xml`
          - `activity_result.xml`
    - `AndroidManifest.xml`

## 사용 방법

1. Android Studio를 열고 해당 프로젝트를 불러옵니다.

2. `MainActivity.java`, `SendActivity.java`, `ResultActivity.java` 파일을 확인하여 각각의 기능에 대한 코드를 이해합니다.

3. `res/layout` 폴더의 `activity_main.xml`, `activity_send.xml`, `activity_result.xml` 파일을 확인하여 UI 디자인을 파악합니다.

4. `AndroidManifest.xml` 파일을 열어 앱의 권한 및 구성을 확인합니다.

5. 프로젝트의 `build.gradle` 파일을 열어 `compileSdkVersion` 및 `targetSdkVersion`의 값을 34로 수정합니다.

```gradle
android {
    compileSdkVersion 34
    defaultConfig {
        applicationId "com.example.businesscardrecognition"
        // ...
    }
    // ...
}
수정 후 Sync Now 버튼을 클릭하여 변경 사항을 동기화합니다.

