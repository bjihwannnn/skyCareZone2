# 코드 리뷰 (요약)

## 강점
- Astro 컴포넌트가 서비스별로 명확히 분리되어 있어 재사용성과 유지보수성이 좋습니다. (`HeroSection`, `ProcedureSection`, `NoticeListSection` 등)
- 글로벌 유틸리티(`.section-title`, 색상 유틸리티, `animate-fade-up`)를 통해 일관된 타이포그래피와 인터랙션이 유지됩니다.
- 메타 태그, Open Graph, 구조화 데이터(로컬 비즈니스)가 기본 제공되어 SEO 기본기가 갖춰져 있습니다.【F:src/layouts/BaseLayout.astro†L5-L48】

## 위험 요소 및 개선 제안
1. **글로벌 스타일 블록 누락으로 인한 CSS 파싱 오류 가능성**: `html, body` 블록이 세미콜론 없이 끝나며 닫힘 중괄호가 없어 CSS가 중단될 수 있었습니다. 세미콜론을 추가해 수정했습니다.【F:src/styles/global.css†L75-L82】
2. **내비게이션 유지보수 및 접근성**: 데스크톱/모바일 메뉴가 별도 마크업으로 중복되어 있어 링크 추가·수정 시 동기화 누락 위험이 있습니다. `aria-current`가 없어 현재 위치 표시도 되지 않습니다. 하나의 링크 소스를 공유하도록 추출하고 `aria-current="page"`(또는 `aria-current="true"`)를 조건부로 부여하세요.【F:src/layouts/BaseLayout.astro†L72-L95】
3. **모바일 메뉴 상호작용 한계**: 토글 스크립트가 ESC 키, 포커스 트래핑, 외부 영역 클릭을 처리하지 않아 키보드 사용자가 메뉴를 닫기 어렵습니다. `keyup`(Escape) 및 `focusout`/`pointerdown` 리스너를 추가해 접근성을 강화하세요.【F:src/layouts/BaseLayout.astro†L60-L118】
4. **절차/유의사항의 시맨틱 마크업 개선**: 단계와 유의사항이 단순 `div`/`ul` 구조지만 단계 번호를 표현할 때 `ol`을 활용하면 스크린리더가 순서를 전달할 수 있습니다. 또한 Astro에서는 `key` 속성이 DOM에 그대로 출력되므로 제거하고, 데이터 속성이나 리스트 키 관리용 배열 컴포넌트를 사용하는 편이 깔끔합니다.【F:src/components/ProcedureSection.astro†L8-L24】【F:src/components/NoticeListSection.astro†L5-L18】
5. **히어로 섹션의 폭 처리**: `w-[100vw] left-[calc(50%-50vw)]` 설정은 풀블리드 연출에 유용하지만, 수평 스크롤 억제를 위해 상위 컨테이너의 `overflow-x: hidden`이 필수입니다. 글로벌 스타일에 해당 속성을 유지했으니 제거되지 않도록 주의하세요.【F:src/components/HeroSection.astro†L10-L33】【F:src/styles/global.css†L75-L82】

## 단기 우선순위 제안
- 모바일 메뉴의 포커스/키보드 대응 보완(ESC 닫기, 포커스 이동, 외부 클릭 닫기).
- 내비게이션 링크 데이터를 배열로 분리하여 데스크톱·모바일이 동일 소스를 사용하도록 리팩터링.
- 단계/목록 섹션을 `ol`/`li` 기반 구조로 전환하고 불필요한 `key` 속성 제거.
- Lighthouse/axe 등으로 접근성 스캔을 돌려 히어로 대비, 포커스 스타일 등을 확인.
