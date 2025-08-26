# 경영진 메인 페이지 분석

## 개요
경영진 메인 페이지 (`/manager`)는 경영진 사용자를 위한 주요 대시보드로, 결재 상태, Google Calendar 연동, Clip 카드, 서비스 바로가기에 대한 빠른 액세스를 제공합니다. 이 페이지는 데스크톱과 모바일 뷰를 위한 별도의 컴포넌트로 반응형 디자인을 구현합니다.

## 라우터 구성

| 속성 | 값 |
|----------|-------|
| **Path** | `/manager` |
| **Router Config** | `MAIN_ROUTER_CONFIG.FO_MAIN_MANAGER` |
| **Component** | `ManagementMainPage` |
| **Route Name** | `Main` |
| **Namespaces** | `['common', 'board', 'approval', 'menu']` |
| **Parameters** | 없음 |

## 페이지 아키텍처

```
ManagementMainPage (index.tsx)
├── ResponsiveWrapper
    ├── mobileComponent: ManagementMainPageMo
    │   ├── Google Calendar Section (HwMainSliderPc)
    │   ├── Clip Section (HwMainSliderPc)
    │   ├── Service Grid Mobile (ServiceGridMo)
    │   └── Floating Action Button (HwFloatingButton)
    │
    └── desktopComponent: ManagementMainPagePc
        ├── Header Section (Greeting + SearchForm)
        ├── Approval Status Section (HwInfoCard stats)
        ├── Google Calendar Section (HwMainSliderPc)
        ├── Clip Section (HwMainSliderPc)
        ├── Service Grid Desktop (ServiceGrid)
        └── Pledge Agreement Popup (PledgeAgreementPopupConfirm)
```

## 컴포넌트 매핑

| 컴포넌트 | 목적 | Props/데이터 소스 |
|-----------|---------|-------------------|
| **ResponsiveWrapper** | 반응형 컴포넌트 전환기 | `breakpoint: '(max-width: 768px)'` |
| **SearchForm** | 전역 검색 기능 | 검색 입력을 위한 Form 컴포넌트 |
| **HwInfoCard** | 결재 상태 통계 | `mockStatData` (4개 결재 상태 카드) |
| **HwMainSliderPc** | 콘텐츠용 캐러셀 슬라이더 | Calendar 이벤트, Clip 카드 |
| **HwStatisticCard** | 캘린더 이벤트 카드 | `mockCalendarEvents` |
| **HwClipCard** | Clip 카드 표시 | `useGetMainCardList()` API 데이터 |
| **ServiceGrid/ServiceGridMo** | 서비스 및 게시판 바로가기 | `mockBoardItems`, `mockServiceItems` |
| **HwFloatingButton** | 모바일 플로팅 액션 버튼 | 결재 상태용 `statusItems` |
| **PledgeAgreementPopupConfirm** | 서약서 동의 모달 | 컴플라이언스 팝업 |

## 데이터 흐름 및 API 통합

### API 호출
1. **useGetMainCardList()** 
   - **Endpoint**: `clipSv.getMainCardList()`
   - **목적**: 대시보드용 메인 clip 카드 가져오기
   - **새로고침**: 위치 변경 시, 30초마다
   - **반환 타입**: `IClipMainCard[]`

### 상태 관리
1. **게시판 항목 상태** (PC 전용)
   - `boardItems`: 게시판 바로가기용 로컬 상태
   - `handleBoardReorder`: 드래그 앤 드롭 재정렬 콜백
   
2. **서비스 항목 상태** (PC 전용) 
   - `serviceItems`: 서비스 바로가기용 로컬 상태
   - `handleServiceReorder`: 드래그 앤 드롭 재정렬 콜백

3. **서약서 동의** (모바일 전용)
   - `usePledgeAgreement()`: 사용자가 서약서에 서명했는지 확인
   - 서명하지 않은 경우 서약서 페이지로 리다이렉트

### 모의 데이터 소스
- `mockBoardItems/mockBoardItemsMo`: 게시판 바로가기
- `mockServiceItems`: 서비스 애플리케이션 바로가기
- `mockCalendarEvents`: Google Calendar 이벤트
- `mockStatData`: 결재 통계
- `statusItems`: 플로팅 버튼 상태 카운트

## 주요 기능 체크리스트

### 데스크톱 기능
- [x] 사용자 이름을 포함한 개인화된 인사말
- [x] 전역 검색 기능
- [x] 결재 상태 통계 (4개 카드: 결재필요, 설명요, 진행중, 결재완료)
- [x] 슬라이더를 통한 Google Calendar 통합
- [x] 슬라이더를 통한 Clip 카드 관리
- [x] 확장/축소 기능을 포함한 드래그 가능한 서비스/게시판 그리드
- [x] 새 게시판/서비스 추가 기능
- [x] 서약서 동의 팝업

### 모바일 기능  
- [x] 가로 스크롤이 있는 Google Calendar 섹션
- [x] 정렬 옵션이 있는 Clip 카드 (주석 처리됨)
- [x] 게시판 바로가기 그리드 (4x2 레이아웃)
- [x] 결재 상태가 있는 플로팅 액션 버튼
- [x] 서약서 동의 유효성 검사
- [x] "더보기" 버튼이 있는 확장 가능한 게시판 그리드

### 공유 기능
- [x] 반응형 디자인 전환
- [x] 국제화 지원 (i18next)
- [x] 캘린더 및 clip 섹션의 빈 상태 처리
- [x] 외부 페이지로의 링크 네비게이션
- [x] 실시간 데이터 새로고침

## 네비게이션 플로우

### 데스크톱 네비게이션
```
Management Main → /manager
├── Search → 전역 검색 결과
├── Calendar Events → 외부 캘린더 애플리케이션
├── Clip Cards → /portal/clip/{cardId} (새 탭)
├── Clip Empty State → /portal/clip/CREATE (새 탭)
├── Board Items → 드래그 앤 드롭 재정렬
├── Service Items → 외부 서비스 애플리케이션
├── Add Board → AddHanBoardModal (모달)
└── Add Service → Business Setting Modal
```

### 모바일 네비게이션
```
Management Main → /manager
├── Calendar Events → 외부 캘린더 애플리케이션
├── Clip Cards → /portal/clip/{cardId} (새 탭)
├── Clip Empty State → /portal/clip/CREATE (새 탭)
├── Board Settings → /hanboard-shortcut
├── Floating Button → 상태 기반 네비게이션
└── Pledge Check → /portal/pledge/agreement (서명하지 않은 경우)
```

## 기술 구현 주의사항

### 반응형 디자인
- 768px에서 단점을 가진 `ResponsiveWrapper` 사용
- 데스크톱: 드래그 앤 드롭 기능을 갖춘 모든 기능을 갖춘 대시보드
- 모바일: 터치 최적화된 상호작용을 갖춘 단순화된 레이아웃

### 성능 최적화
- 캘린더와 게시판 컴포넌트의 레이지 로딩
- 콘텐츠 카드에 대한 메모이제이션된 렌더 함수
- 30초 간격으로 쿠리 캐싱
- 초기화 상태에 기반한 조건부 API 호출

### 오류 처리
- 누락된 데이터에 대한 빈 상태 컴포넌트
- API 훅의 try-catch 블록
- API 실패 시 빈 배열로 폴백
- TanStack Query를 통한 로딩 상태 관리

### 국제화
- 모든 텍스트 콘텐츠에 `useTranslation('main')` 사용
- i18next를 통한 다국어 지원
- 일관된 번역 키 구조

### 데이터 지속성
- 서비스 그리드 순서가 세션 동안 지속됨
- 위치 변경 시 Clip 데이터 새로고침
- 레이블 및 게시판 구성 캐시

이 페이지는 경영진 사용자를 위한 주요 대시보드 역할을 하며, 결재 워크플로우, 캘린더 통합, 작업 관리, 비즈니스 애플리케이션에 대한 빠른 액세스에 대한 종합적인 감시 기능을 제공합니다.