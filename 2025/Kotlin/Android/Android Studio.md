## 환경 & 구조 이해
**app/src/main/java**
- 앱의 실제 코드가 들어있는 폴더다.
- 화면 동작, 이벤트 처리, 데이터 로직이 이곳에서 구현된다.

**app/src/main/res**
- 앱의 `리소스 파일`이 모여 있다.
- `layout/` → 화면 구조 XML 파일
- `drawable/` → 이미지, 벡터, shape
- `values/` → colors.xml, strings.xml, styles.xml 등

**AndroidManifest.xml**
- 앱의 `메타데이터와 권한`을 정의한다.
- 앱 이름, 아이콘, 실행 액티비티, 인터넷 권한 등이 여기서 설정된다.

**Gradle 설정 파일**
- `build.gradle(project)` → 프로젝트 전역 설정 (플러그인, 저장소)
- `build.gradle(Module: app)` → 앱 단위 설정 (SDK 버전, 라이브러리 의존성)

## UI 구성과 레이아웃
안드로이드 화면은 XML 기반 레이아웃으로 만든다.
- **LinearLayout** → 위/아래(세로), 왼/오(가로) 방향 배치
- **RelativeLayout** → 다른 뷰를 기준으로 배치
- **ConstraintLayout** → 제약 조건으로 자유롭게 배치 (최근 가장 많이 사용)
- **FrameLayout** → 하나의 뷰 또는 겹치는 뷰 배치
- **GridLayout** → 격자 형태 배치