## Next.js 라우팅 및 클라이언트 사이드 렌더링 관련 키워드 정리

### Active Link 관련 Hooks

- **useSelectedLayoutSegment**
    - 현재 레이아웃 기준 바로 아래 한 단계의 segment를 문자열로 반환합니다.
    - 예시: `/dashboard/settings` 경로에서 `dashboard` 레이아웃에서 호출하면 `'settings'` 반환.

- **useSelectedLayoutSegments**
    - 현재 레이아웃 기준 그 아래 모든 segment를 배열로 반환합니다.
    - 예시: `/dashboard/settings/profile` 경로에서 `dashboard` 레이아웃에서 호출하면 `['settings', 'profile']` 반환.

---

### 클라이언트 사이드 전용 코드

- **useHook, eventListener**
    - SSR(서버사이드 렌더링) 환경에서는 브라우저 API(`window`, `document`, `localStorage` 등)를 사용할 수 없습니다.
    - 이런 코드는 반드시 `use client` 지시어를 파일 최상단에 선언하여 CSR(클라이언트 사이드 렌더링) 환경에서만 실행해야 합니다.
    - 서버에는 브라우저 객체가 없어 ReferenceError가 발생할 수 있습니다.

---

### React Context

- **useContext**
    - 전역 상태 관리나 컴포넌트 간 데이터 전달에 사용합니다.
    - Next.js에서도 클라이언트 컴포넌트에서 주로 활용됩니다.

---

### classNames 유틸리티

- **classNames**
    - 여러 조건에 따라 동적으로 CSS 클래스를 조합할 때 사용하는 유틸 함수입니다.
    - 예시: `classNames('btn', isActive && 'btn-active')` → `btn btn-active` (isActive가 true일 때)

---

## 연관 정보 요약

- **use client 지시어**
    - Next.js 13(app 디렉토리 기준)에서 클라이언트 전용 컴포넌트를 명시할 때 사용합니다.
    - 브라우저 API, 상태 관리, 이벤트 핸들러 등은 반드시 클라이언트 컴포넌트에서만 사용해야 합니다.

---

> **Tip:**  
> 브라우저 전용 API를 사용하는 코드는 항상 클라이언트 컴포넌트(`use client`)에서만 작성해야 하며, 서버 컴포넌트에서는 순수 렌더링 로직만 작성하는 것이 Next.js의 권장 패턴입니다.
>
> 라우팅 관련 hook들은 동적 네비게이션, 활성화된 메뉴 표시 등에 유용하게 활용할 수 있습니다.
