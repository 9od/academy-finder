# 수지구 학원 찾기

경기도 공공데이터 API를 활용한 학원 검색 사이트입니다.

## 사용 방법

### 1. GitHub Pages 배포

1. GitHub에 새 repository 생성 (예: `academy-finder`)
2. `index.html` 파일 업로드
3. Settings → Pages → Source: `main` 브랜치 선택
4. `https://[your-id].github.io/academy-finder` 로 접속

### 2. API 키 입력

- 사이트 접속 후 왼쪽 **API 인증키** 입력란에 발급받은 키를 붙여넣기
- 키는 브라우저 localStorage에만 저장되며, GitHub 코드에는 포함되지 않습니다

### 3. 검색

- 과목 선택 → 지역 선택 → 검색하기
- 결과에서 학원명으로 추가 필터링 가능

## CORS 오류 해결

경기도 API는 브라우저 직접 호출 시 CORS 오류가 발생할 수 있습니다.
이 경우 아래 방법 중 하나를 사용하세요.

### 방법 A: CORS Anywhere 프록시 (간단)

`index.html` 내 `doSearch()` 함수의 url 변수를 아래와 같이 수정:

```js
const PROXY = 'https://corsproxy.io/?';
const url = PROXY + encodeURIComponent(`https://openapi.gg.go.kr/TninsttInstutM?KEY=${key}&Type=json&pIndex=1&pSize=${pSize}&SIGUN_NM=${sigun}`);
```

### 방법 B: GitHub Actions로 데이터 캐싱 (안정적)

매일 자동으로 데이터를 받아 `data.json`으로 저장해두는 방식.
필요하시면 별도로 설정 파일을 만들어 드립니다.

## API 정보

- 제공: 경기도 공공데이터 포털 (openapi.gg.go.kr)
- 데이터셋: 학원 및 교습소 정보 (TninsttInstutM)
- 갱신 주기: 수시

## 파일 구조

```
academy-finder/
└── index.html   ← 전체 사이트 (단일 파일)
```
