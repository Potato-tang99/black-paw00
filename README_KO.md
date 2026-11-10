# BLACK PAW APK 빌드용 파일

이 폴더는 BLACK PAW V6 손그림 라인 디자인을 Android APK로 빌드하기 위한 최소 프로젝트입니다.

## 포함 파일
- `index.html`: 앱 진입 화면
- `src/main.js`: 타이머, 세트 카운터, 공부 고양이 UI, 사운드, 알림/진동 로직
- `src/styles.css`: 검정 배경 및 손그림 애니메이션 스타일
- `public/`: 앱 아이콘과 웹앱 메타데이터
- `package.json`: Capacitor/Vite 의존성
- `capacitor.config.json`: 앱 ID와 앱 이름
- `vite.config.js`: 웹 빌드 설정
- `.github/workflows/android-apk.yml`: GitHub Actions APK 자동 빌드 설정
- `APK_BUILD_GUIDE_KO.md`: 설치·빌드 상세 안내

## 현재 빌드 대상
테스트용 Android **debug APK**입니다. Play 스토어 배포용 release APK/AAB는 별도 서명 설정이 필요합니다.
