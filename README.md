
# Kakao + No-Label Basemap (GitHub Pages 템플릿)

이 저장소는 **카카오 지도 엔진**을 사용하면서 **글씨(라벨)가 없는 일반지도 타일**을 베이스로 쓰는 최소 예제입니다.
GitHub Pages에 올려두면 어느 컴퓨터에서든 URL만으로 열 수 있습니다.

## 1) Kakao 개발자 콘솔 설정
1. https://developers.kakao.com → 내 애플리케이션 생성
2. (좌측) **플랫폼 → Web** → **Site domain**에 **배포될 도메인** 등록  
   - 예: `https://yourusername.github.io`
   - 로컬 테스트가 필요하면 `http://localhost:8080`, `http://127.0.0.1:5500` 등도 추가 등록 가능
3. (좌측) **Kakao Map** 사용 설정(ON)
4. **JavaScript 키** 복사

## 2) index.html 수정
- `index.html`의 스크립트 태그에서 `YOUR_APP_KEY`를 **본인 카카오 JavaScript 키**로 교체하세요.
- 필요하면 `TILE_URL`, 초기 중심/레벨 등을 수정합니다.

## 3) GitHub Pages 배포
1. GitHub에서 새 저장소 생성 (예: `map-test`)
2. 이 파일들과 `index.html` 업로드
3. 저장소 **Settings → Pages**  
   - **Build and deployment**: *Deploy from a branch*  
   - **Branch**: `main` / **Folder**: `/ (root)`
4. 상단에 표시되는 **Pages URL**로 접속 (예: `https://yourusername.github.io/map-test/`)

> `index.html`은 **저장소 루트**(또는 선택한 폴더)의 최상단에 있어야 기본 진입이 됩니다.

## 4) 자주 겪는 문제
- **"This domain is not registered on the dev console!"**  
  → 도메인 화이트리스트에 `https://yourusername.github.io`가 **정확히 등록**되어 있는지 확인하세요.
- **Mixed content(혼합 콘텐츠) 차단**  
  → 타일 URL은 **반드시 `https://`** 이어야 합니다.
- **지도가 빈 화면**  
  → 브라우저 콘솔에서 에러 메시지를 확인하세요.  
  → `YOUR_APP_KEY` 교체 여부, `TILE_URL` 오탈자, 레벨 범위(min/maxZoom) 등을 점검하세요.
- **타일 뒤집힘/좌표 틀어짐**  
  → Kakao Tileset은 TMS 기준이므로 코드에서 `y = (2^z - 1) - y` 변환을 적용합니다(이미 반영되어 있음).

## 5) 라이선스/출처
- 타일: CARTO Positron (no-labels) / 데이터: © OpenStreetMap contributors
- 인쇄 및 보고서 삽입 시 출처 문구를 유지하세요.
- OSM/CARTO의 속도/정책은 제공사 상황에 따라 달라질 수 있습니다. 필요 시 자체 타일 서버나 다른 no-label 제공처를 사용하세요.

## 6) 기타
- **Leaflet 대체 예제(`leaflet.html`)**도 포함되어 있습니다. (Kakao 키 없이도 열람 가능)
- 고해상도 인쇄가 필요하면 QGIS에서 같은 no-label 타일을 호출해 A1/A0, 300–600dpi로 내보내는 것을 권장합니다.
