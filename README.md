# 지역사회건강조사 매뉴얼

- **CAPI 전화 응대 매뉴얼**: 증상 → 원인 → 대처법 + 표준 응대 멘트
- **지사회 업무 매뉴얼**: 기능 변경, 홈페이지 콘텐츠, 연간 정기 작업, 회의 결정사항

읽기는 누구나, 등록·수정·삭제는 관리자 계정 하나만 할 수 있습니다.
데이터는 Supabase DB에 저장되고, DB 연결이 안 되면 `index.html`에 내장된 데이터로 보여 줍니다.

## 파일

| 파일 | 내용 |
|---|---|
| `index.html` | 사이트 전체 (GitHub Pages에 올리는 파일) |
| `supabase/schema.sql` | DB 테이블과 권한 설정 |
| `supabase/seed.sql` | 기존 데이터 1,346개 항목 (2017–2026) |

## 처음 한 번만 하는 설정

### 1. 테이블 만들기
1. Supabase 대시보드 왼쪽 메뉴 **SQL Editor** → **New query**
2. `supabase/schema.sql` 내용을 붙여넣고, 맨 아래 `YOUR_EMAIL` 두 군데를 **관리자 로그인에 쓸 이메일**로 바꾼 뒤 **Run**

### 2. 기존 데이터 넣기
1. SQL Editor에서 새 쿼리를 열고 `supabase/seed.sql` 내용을 붙여넣은 뒤 **Run**
2. **Table Editor → cases** 에 1,346개 행이 보이면 성공

### 3. 관리자 계정 만들기
1. **Authentication → Users → Add user → Create new user**
2. 1번에서 넣은 이메일과 비밀번호 입력, **Auto Confirm User** 체크 후 생성
3. **Authentication → Sign In / Providers** 에서 **Allow new users to sign up** 끄기 (다른 사람이 가입하지 못하게)

### 4. 사이트에 키 넣기
1. **Project Settings → API Keys** 에서 `anon` `public` 키 복사
   (새 화면이면 **Legacy API Keys** 탭의 `anon public` 키)
2. `index.html`을 열어 위쪽의 아래 줄에 붙여넣기

   ```js
   const SUPABASE_ANON_KEY = '여기에 붙여넣기';
   ```
3. GitHub 저장소에 `index.html` 올리기

> anon 키는 공개돼도 괜찮은 키입니다. 읽기만 가능하고, 쓰기는 DB 권한 설정으로 관리자 이메일만 허용됩니다.
> `service_role` 키는 절대 넣지 마세요.

## 사용법

- 사이트 맨 아래 **관리자 로그인** → 로그인하면 왼쪽 메뉴에 **＋ 케이스 등록**이 생깁니다.
- 증상을 입력하면 비슷한 기존 케이스를 찾아 보여 줍니다.
  - 같은 문제면 **기존 케이스에 합치기**: 건수 +1, 새 대처법이 있으면 추가
  - 아니면 **새 케이스로 등록**
- 로그인 상태에서 케이스를 펼치면 **수정** 버튼이 있습니다. 삭제는 수정 화면에서 할 수 있습니다.

## GitHub Pages 배포

1. 저장소 **Settings → Pages** → Branch `main` / `/ (root)` → Save
2. 1~2분 뒤 `https://<GitHub아이디>.github.io/<저장소이름>/` 로 접속
