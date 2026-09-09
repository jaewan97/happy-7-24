# Happy 7/24

유연근무 출·퇴근 체크 &amp; 스케줄 관리 웹앱입니다. 순수 HTML/CSS/JS로 만들어져 있어 별도의 빌드 과정 없이 정적 사이트로 바로 배포할 수 있습니다.

## 폴더 구조

```
happy-7-24-app/
├── index.html      # 앱 전체 (마크업 + 스타일 + 스크립트)
├── vercel.json      # Vercel 정적 배포 설정
├── .gitignore
└── README.md
```

## 1. GitHub 저장소에 올리기

```bash
cd happy-7-24-app
git init
git add .
git commit -m "Happy 7/24 초기 버전"
git branch -M main
git remote add origin https://github.com/<본인계정>/<저장소이름>.git
git push -u origin main
```

GitHub 웹사이트에서 새 저장소를 먼저 만든 뒤(New repository), 위 `origin` 주소를 본인 저장소 주소로 바꿔서 실행하세요.

## 2. Vercel로 배포하기

### 방법 A — Vercel 대시보드에서 바로 연결 (권장)
1. https://vercel.com 에 로그인 (GitHub 계정으로 로그인 가능)
2. **Add New → Project** 클릭
3. 방금 만든 GitHub 저장소 선택 → **Import**
4. Framework Preset은 **Other**로 두면 됩니다 (별도 빌드 명령 필요 없음, `index.html`을 자동으로 인식)
5. **Deploy** 클릭 → 몇 초 후 `https://프로젝트이름.vercel.app` 주소로 바로 접속 가능

### 방법 B — Vercel CLI로 배포
```bash
npm i -g vercel
cd happy-7-24-app
vercel        # 첫 배포 (질문에 답하며 진행)
vercel --prod # 프로덕션 배포
```

## 3. 배포 후 확인할 점
- 모바일 브라우저에서 접속하면 반응형으로 화면 크기에 맞춰 자동 조정됩니다.
- 현재 데이터(근무 패턴, 스케줄)는 **브라우저 세션 메모리**에만 저장되며 새로고침 시 초기화됩니다. 데이터를 계속 유지하려면 로컬 스토리지 또는 백엔드/DB 연동이 추가로 필요합니다.
- 커스텀 도메인을 연결하려면 Vercel 프로젝트의 **Settings → Domains**에서 도메인을 추가하세요.

## 다음 단계로 고려할 수 있는 것들
- 데이터 영속화: Supabase, Firebase, 또는 Vercel Postgres/KV 연동
- 실제 브라우저 푸시 알림: Web Push API + Service Worker 등록
- PWA로 전환: `manifest.json` 추가 + 서비스 워커로 홈 화면에 설치 가능하게 만들기
