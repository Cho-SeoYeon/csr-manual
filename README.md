# 지사회 CSR 응대 매뉴얼

CAPI 지역사회건강조사 전화 응대용 매뉴얼 사이트입니다.
`index.html` 파일 하나로 동작하며, 서버·DB·빌드 과정이 필요 없습니다.

## GitHub Pages로 배포하기

1. GitHub에서 새 저장소를 **Public**으로 만듭니다. (예: `csr-manual`)
2. 이 폴더의 `index.html`, `README.md`를 저장소에 올립니다.
3. 저장소 **Settings → Pages**로 이동합니다.
4. **Source**: `Deploy from a branch`, **Branch**: `main` / `/ (root)` 선택 후 **Save**.
5. 1~2분 뒤 `https://<GitHub아이디>.github.io/csr-manual/` 주소로 접속됩니다.

### 내 도메인 연결 (선택)

1. **Settings → Pages → Custom domain**에 도메인 입력 (예: `csr.example.com`) 후 Save.
2. 도메인 업체 DNS 설정에서 `CNAME` 레코드를 `<GitHub아이디>.github.io`로 추가.
3. DNS가 반영되면 **Enforce HTTPS** 체크.

## 내용 수정

- 모든 내용은 `index.html` 안의 `const DATA = {...}` 에 들어 있습니다.
- 수정 후 저장소에 다시 올리면 1~2분 뒤 사이트에 반영됩니다.

## 공개용 버전 안내

누구나 접속할 수 있는 사이트이므로 아래 정보는 넣지 않았습니다.
관리자 계정 정보, 서버명·설정 파일 경로, 사내 네트워크 경로, 확인용 SQL 쿼리, 담당자 이름.
