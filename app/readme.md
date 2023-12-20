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

## 주요 기능

### MainActivity

1. **앱의 메인 화면을 담당합니다.**
   - 명함 촬영이나 불러오기 등의 기능을 제공합니다.
   ![Main Activity 1](https://github.com/Seeing-AI/businesscard_recognition/blob/main/app/img/KakaoTalk_20231213_000500533_03.jpg)
   ![Main Activity 2](https://github.com/Seeing-AI/businesscard_recognition/blob/main/app/img/KakaoTalk_20231213_000500533_02.jpg)

### SendActivity

2. **촬영한 명함을 서버에 전송하는 기능을 담당합니다.**
   - 서버로부터 인식 결과를 받아오는 등의 기능을 포함합니다.
   ![Send Activity](https://github.com/Seeing-AI/businesscard_recognition/blob/main/app/img/KakaoTalk_20231213_000500533_01.jpg)

### ResultActivity

3. **명함 인식 결과를 표시하는 화면을 담당합니다.**
   - 인식된 이름, 번호, 직책 등을 사용자에게 제공합니다.
   ![Result Activity](https://github.com/Seeing-AI/businesscard_recognition/blob/main/app/img/KakaoTalk_20231213_000500533.jpg)


## 사용 방법

1. Android Studio를 열고 새로운 프로젝트를 시작합니다.

2. `MainActivity.java`, `SendActivity.java`, `ResultActivity.java`로 java 파일을 교체합니다.

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
