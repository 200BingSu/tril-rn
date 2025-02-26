# apk 관련

## 1. QR 생성하기

- https://me-qr.com/ko/qr-code-generator/link

## 2. 마켓에 등록하지 않은 상태로 외부인에게 앱파일을 전달하는 경우

```bash
cd android
```

```bash
./gradlew assembleRelease
```

- apk 별도 생성 작업
- android/app/build/outputs/apk/release/app-release.apk 복사
- /test/test.apk로 변경
