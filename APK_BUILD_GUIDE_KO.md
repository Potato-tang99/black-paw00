# BLACK PAW APK 만들기 — 갤럭시 태블릿 설치 안내

가장 쉬운 방법은 GitHub Actions에서 APK를 자동으로 빌드하는 것입니다. PC 없이 태블릿의 브라우저에서도 진행할 수 있지만, 파일 업로드는 PC가 더 편합니다.

## A. GitHub에 소스 올리기

1. `https://github.com`에 로그인하거나 계정을 만듭니다.
2. 우측 상단 `+` → `New repository`를 누릅니다.
3. 저장소 이름을 `black-paw`로 입력합니다.
4. `Public` 또는 `Private`를 선택하고 `Create repository`를 누릅니다.
5. 이 ZIP 파일을 먼저 기기에 다운로드한 다음 압축을 풉니다.
6. 압축을 푼 **폴더 안의 파일과 폴더 전체**를 GitHub 저장소에 올립니다. ZIP 파일 하나만 업로드하면 안 됩니다.
7. 특히 숨김 폴더 `.github`와 그 안의 `workflows/android-apk.yml`이 업로드됐는지 확인합니다. 안드로이드 파일 선택기에서 숨김 폴더가 보이지 않으면 아래 9번의 수동 생성 방법을 사용하세요.
8. GitHub 저장소 첫 화면에 `index.html`, `package.json`, `src`, `public`이 보여야 합니다.
9. `.github` 폴더가 업로드되지 않았다면 저장소에서 `Add file` → `Create new file`을 누르고 파일 이름 칸에 `.github/workflows/android-apk.yml`을 입력합니다. ZIP 안의 `GITHUB_WORKFLOW_COPY.txt` 내용을 복사해 붙여넣고 `Commit changes`를 누릅니다.

### 파일 구조 확인

```text
black-paw/
├── .github/
│   └── workflows/
│       └── android-apk.yml
├── public/
│   ├── icons/
│   │   ├── icon-192.png
│   │   └── icon-512.png
│   └── manifest.webmanifest
├── src/
│   ├── main.js
│   └── styles.css
├── capacitor.config.json
├── index.html
├── package.json
└── vite.config.js
```

## B. APK 자동 빌드

1. GitHub 저장소 상단의 `Actions` 탭을 엽니다.
2. 왼쪽 목록에서 `Build BLACK PAW Android APK`를 선택합니다.
3. `Run workflow` 버튼을 누르고 다시 초록색 `Run workflow`를 선택합니다.
4. 실행 항목이 나타나면 클릭합니다.
5. 빌드가 끝날 때까지 기다립니다. 성공하면 초록색 체크 표시가 나옵니다.

저장소에 소스를 처음 올릴 때 `main` 브랜치로 커밋하면 자동 빌드가 시작될 수도 있습니다. 자동 실행이 시작됐다면 중복으로 `Run workflow`를 누르지 않아도 됩니다.

## C. APK 다운로드

1. 성공한 Actions 실행 페이지 아래쪽 `Artifacts`로 이동합니다.
2. `BLACK-PAW-debug-apk`를 누릅니다.
3. 다운로드된 ZIP을 압축 해제합니다.
4. 안에 있는 `app-debug.apk`가 설치 파일입니다.
5. APK를 갤럭시 탭으로 다운로드하거나 옮깁니다.

## D. 갤럭시 탭 설치

1. 태블릿에서 `내 파일` 앱을 열고 `app-debug.apk`를 누릅니다.
2. 보안 안내가 나오면 다운로드한 파일이 본인이 실행한 GitHub Actions 빌드에서 나온 것인지 확인합니다.
3. 설치가 차단되면 설정에서 해당 파일을 연 앱(예: 내 파일 또는 Chrome)에 한해 `이 출처 허용`을 켭니다.
4. 설치를 마친 뒤 다시 해당 권한을 끄는 것을 권장합니다.
5. BLACK PAW를 실행하고 설정에서 `알림 권한 확인`을 눌러 허용합니다.

## E. 설치 후 확인할 항목

- 집중시간/휴식시간 변경 및 자동 전환
- 세트 완료 표시
- 고양이 손그림 애니메이션
- 집중/휴식별 카페·장작·비·비행기 소리
- 단계 전환 알림 및 진동
- 전체 초기화 → 확인창에서 `아니요` / `예` 동작
- 날짜가 바뀐 뒤 앱을 다시 열었을 때 전날 진행 상태 정리

## 꼭 알아둘 점

- 이 절차로 생성되는 파일은 개인 기기 테스트용 **debug APK**입니다. Play 스토어 배포용 서명 APK/AAB가 아닙니다.
- Android 알림은 권한, 무음/방해 금지, 절전 및 제조사 정책의 영향을 받습니다. 실제 태블릿에서 테스트해야 합니다.
- 앱을 강제 종료했을 때의 알림 전달은 기기별로 차이가 날 수 있습니다. 설치 후 5분 집중/5분 휴식으로 짧게 테스트하세요.
- 현재 카페/장작/비/비행기 소리는 Web Audio로 만든 생성형 음향입니다. 실제 현장 녹음과 동일한 음원은 아닙니다.
- GitHub Actions 실행 로그나 저장소를 공개로 설정할 경우 소스 코드가 공개됩니다. 개인정보나 비밀키를 소스에 넣지 마세요.
