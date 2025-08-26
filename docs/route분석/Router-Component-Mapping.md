---
sidebar_position: 1
---


# Router-Component 매핑 문서

## 개요
한진 프론트엔드 애플리케이션의 모든 라우터 설정과 URL-컴포넌트 매핑을 분석한 종합 문서입니다.

## 라우터 구조

### 1. 라우터 계층 구조
- **FO (Front Office)**: 일반 사용자 인터페이스
- **BO (Back Office)**: 관리자 인터페이스 (MGR)
- **Public**: 인증이 필요하지 않은 페이지

### 2. ResponsiveWrapper 구조
모든 FO 페이지는 ResponsiveWrapper를 통해 PC/Mobile 분리:
- **Desktop Component**: 768px 이상
- **Mobile Component**: 768px 이하

---

## URL → Component 매핑표

### 📁 Public Routes (인증 불필요)

| URL | Component | 설명 |
|-----|-----------|------|
| `/login` | LoginPage | 로그인 페이지 |
| `/hw-ui-kit` | UiKitPage | UI Kit 샘플 페이지 |
| `/hw-component` | ComponentPage | 컴포넌트 샘플 페이지 |
| `/*` | Page404 | 404 에러 페이지 |

---

### 🏠 Main Routes (메인)

#### URL 패턴
| URL | PC Component | Mobile Component | 설명 |
|-----|--------------|------------------|------|
| `/` | FieldStaffMainPagePc | OnsiteStaffMainPageMo | 현장직 메인 페이지 |
| `/manager` | ManagementMainPagePc | ManagementMainPageMo | 관리자 메인 페이지 |
| `/office-staff` | OfficeStaffMainPagePc | OfficeStaffMainPageMo | 사무직 메인 페이지 |
| `/hanboard-shortcut` | - | HanBoardShortcutMo | 한보드 바로가기 (모바일 전용) |
| `/add-hanboard` | - | AddHanBoardMo | 한보드 추가 (모바일 전용) |

#### Component 구조
```
📁 src/pages/main/
├── fieldStaff/
│   ├── index.tsx (ResponsiveWrapper)
│   ├── mainPagePc.tsx
│   └── mainPageMo.tsx
├── managementMain/
│   ├── index.tsx (ResponsiveWrapper)
│   ├── mainPagePc.tsx
│   ├── mainPageMo.tsx
│   ├── hanBoardShortcutMo.tsx
│   └── addHanBoardMo.tsx
└── officeStaff/
    ├── index.tsx (ResponsiveWrapper)
    ├── mainPagePc.tsx
    └── mainPageMo.tsx
```

---

### 📋 Board Routes (게시판)

#### URL 패턴
| URL | Component | PC/Mobile Split | 설명 |
|-----|-----------|-----------------|------|
| `/board/basic` | BasicBoardPage | ✅ | 기본 게시판 |
| `/board/album` | AlbumBoardPage | ✅ | 앨범 게시판 |
| `/board/link` | LinkBoardPage | ✅ | 링크 게시판 |
| `/board/news` | NewsBoardPage | ✅ | 뉴스 게시판 |
| `/board/qna` | QnABoardPage | ✅ | Q&A 게시판 |
| `/board/detail` | - | - | 게시판 상세 |
| `/board/edit/mo/:id` | - | - | 모바일 게시물 편집 |
| `/board/recent-posts` | RecentPostsPage | ✅ | 최근 게시물 |
| `/board/guide` | BoardGuidePage | - | 게시판 가이드 |
| `/board/general/free` | - | - | 자유게시판 |
| `/board/link/detail` | - | - | 링크 게시판 상세 |
| `/board/create` | - | - | 게시물 작성 |
| `/board/general/board-type` | - | - | 게시판 타입 |
| `/board/general/commons` | - | - | 공통 게시판 |
| `/board/general/navigation` | - | - | 게시판 네비게이션 |
| `/board/general/my-article` | MyArticlePage | ✅ | 내 게시물 |
| `/board/general/my-article?tab=my-post` | MyArticlePage | ✅ | 내가 쓴 글 |
| `/board/general/my-article?tab=my-comment` | MyArticlePage | ✅ | 내가 쓴 댓글 |
| `/board/general/my-article?tab=my-temporarily-saved` | MyArticlePage | ✅ | 임시 저장 글 |
| `/board/general/my-article/edit/:id` | - | - | 임시 저장 글 편집 |
| `/board/write/anonymous` | - | - | 익명 게시물 작성 |
| `/board/write/link` | - | - | 링크 게시물 작성 |

#### Component 구조
```
📁 src/pages/board/
├── basic/
│   ├── index.tsx (ResponsiveWrapper)
│   ├── basicBoardPc.tsx
│   └── basicBoardMo.tsx
├── album/
│   ├── index.tsx (ResponsiveWrapper)
│   ├── albumBoardPc.tsx
│   └── albumBoardMo.tsx
├── link/
│   ├── index.tsx (ResponsiveWrapper)
│   ├── linkBoardPc.tsx
│   └── linkBoardMo.tsx
├── news/
│   ├── index.tsx (ResponsiveWrapper)
│   ├── newsBoardPc.tsx
│   └── newsBoardMo.tsx
├── qna/
│   ├── index.tsx (ResponsiveWrapper)
│   ├── qnaBoardPc.tsx
│   └── qnaBoardMo.tsx
├── recentPost/
│   ├── index.tsx (ResponsiveWrapper)
│   ├── recentPostsPc.tsx
│   └── recentPostsMo.tsx
├── myArticle/
│   ├── index.tsx (ResponsiveWrapper)
│   ├── myArticlePc.tsx
│   └── myArticleMo.tsx
└── guide/
    └── index.tsx
```

---

### 📝 Approval Routes (전자결재)

#### Write (기안작성)
| URL | Component | PC/Mobile Split | 설명 |
|-----|-----------|-----------------|------|
| `/approval-write/guide` | ApprovalWriteGuidePage | - | 기안작성 가이드 |
| `/approval-write/draft-writing` | DraftWritingPage | ✅ | 기안작성 |
| `/approval-write/draft-writing/:id` | DraftWritingInformationPage | ✅ | 문서 정보 |
| `/approval-write/draft-writing/create` | DraftWritingCreatePage | ✅ | 문서 작성 |
| `/approval-write/draft-writing/template` | - | - | 문서 템플릿 |
| `/approval-write/draft-writing/document` | DraftDocumentPage | ✅ | 문서 생성 테스트 |

#### Management (전자결재 관리)
| URL | Component | PC/Mobile Split | 설명 |
|-----|-----------|-----------------|------|
| `/approval-management/guide` | ApprovalGuidePage | - | 전자결재 가이드 |
| `/approval-management/need` | NeedPage | ✅ | 결재필요 |
| `/approval-management/need/detail/:id` | NeedDetailsPage | ✅ | 결재필요 상세 |
| `/approval-management/payment/unconnected` | UnconnectedPage | ✅ | 결재 필요 문서 |
| `/approval-management/payment/unconnected/detail/:id` | UnconnectedDetailsPage | ✅ | 결재 필요 문서 상세 |
| `/approval-management/payment/expected-document` | ExpectedDocumentPage | ✅ | 결재 예상 문서 |
| `/approval-management/drafts/document-processing` | DraftsProcessPage | ✅ | 진행중 문서 |
| `/approval-management/drafts/document-completed` | DraftsProcessPage | ✅ | 완결문서 |
| `/approval-management/drafts/document-rejected` | DraftsProcessPage | ✅ | 부결 문서 |
| `/approval-management/drafts/document-need-explanation` | DraftsProcessPage | ✅ | 설명요 문서 |
| `/approval-management/drafts/document-related` | DocumentRelatedPage | ✅ | 결재 문서 |
| `/approval-management/drafts/document-line` | - | - | 결재선 문서 |
| `/approval-management/drafts/document-line/:id` | - | - | 결재선 문서 정보 |
| `/approval-management/drafts/document-create` | - | - | 문서 생성 |
| `/approval-management/drafts/document-detail/:id` | DraftDocumentDetailsPage | ✅ | 문서 상세 |

#### User Settings (사용자 설정)
| URL | Component | PC/Mobile Split | 설명 |
|-----|-----------|-----------------|------|
| `/approval-management/user-settings/settings` | SettingPage | ✅ | 결재설정 |
| `/approval-management/user-settings/personal-management` | PersonalManagementPage | ✅ | 개인 결재선 관리 |
| `/approval-management/user-settings/account` | AccountSettingsPage | ✅ | 개인함 관리 |
| `/approval-management/user-settings/competition` | ApprovalCompetitionPage | ✅ | 대결설정 |

#### Individual (개인함)
| URL | Component | PC/Mobile Split | 설명 |
|-----|-----------|-----------------|------|
| `/approval-management/individual/consumables-disposal` | ConsumableDisposalPage | ✅ | 개인함 2 |
| `/approval-management/individual/scrap-book-mark` | ScrapBookMarkPage | ✅ | 스크랩함 |

#### History (문서함)
| URL | Component | PC/Mobile Split | 설명 |
|-----|-----------|-----------------|------|
| `/approval-history/guide` | ApprovalHistoryGuidePage | - | 문서함 가이드 |
| `/approval-history/trip-report` | HistoryTripReportPage | ✅ | 국내출장보고서 |
| `/approval-history/transfer` | HistoryTransferPage | ✅ | 신청서 |

#### Others
| URL | Component | PC/Mobile Split | 설명 |
|-----|-----------|-----------------|------|
| `/approval/popups` | PopupContentsPage | ✅ | 팝업 컨텐츠 |
| `/approval/demo-select-approvers` | DemoSelectApproversPage | ✅ | 결재자 선택 데모 |

#### Component 구조
```
📁 src/pages/approval/
├── write/
│   ├── guide/
│   ├── draftWriting/
│   │   ├── index.tsx (ResponsiveWrapper)
│   │   ├── draftWritingPc.tsx
│   │   ├── draftWritingMo.tsx
│   │   ├── information/ (lazy loaded)
│   │   └── form/ (lazy loaded)
│   └── draftDocument/ (lazy loaded)
├── management/
│   ├── guide/
│   ├── need/
│   │   ├── index.tsx (ResponsiveWrapper)
│   │   └── details/ (lazy loaded)
│   ├── payment/
│   │   ├── unconnected/ (lazy loaded)
│   │   └── expectedDocument/ (lazy loaded)
│   ├── drafts/
│   │   ├── index.tsx (ResponsiveWrapper)
│   │   ├── details/ (lazy loaded)
│   │   └── documentRelated/ (lazy loaded)
│   ├── userSettings/
│   │   ├── settings/ (lazy loaded)
│   │   ├── personalManagement/ (lazy loaded)
│   │   ├── account/ (lazy loaded)
│   │   └── competition/ (lazy loaded)
│   └── individual/
│       ├── scrapBookMark/ (lazy loaded)
│       └── consumableDisposal/ (lazy loaded)
├── history/
│   ├── guide/ (lazy loaded)
│   ├── tripReport/ (lazy loaded)
│   └── transfer/ (lazy loaded)
├── popupContents/ (lazy loaded)
└── demoSelectApprovers/ (lazy loaded)
```

---

### 🌐 Portal Routes (포털)

#### Main Portal
| URL | Component | PC/Mobile Split | 설명 |
|-----|-----------|-----------------|------|
| `/search` | SearchPage | ✅ | 검색 |
| `/portal/favorite` | FavoritePage | ✅ | 즐겨찾기 |
| `/portal/feed` | FeedPage | ✅ | 피드 |
| `/portal/recent-history` | RecentHistoryPage | ✅ | 최근 기록 |

#### Settings (설정)
| URL | Component | PC/Mobile Split | 설명 |
|-----|-----------|-----------------|------|
| `/portal/setting` | - | - | 포털 설정 |
| `/portal/setting/basic-information` | - | - | 기본 정보 설정 |
| `/portal/setting/basic-information/edit` | - | - | 기본 정보 편집 |
| `/portal/setting/feed` | - | - | 피드 설정 |
| `/portal/setting/favorite` | - | - | 즐겨찾기 설정 |
| `/portal/setting/board` | - | - | 게시판 설정 |
| `/portal/setting/pledge` | - | - | 서약서 설정 |
| `/portal/setting/pledge/:id` | - | - | 서약서 상세 |

#### Clip (클립)
| URL | Component | PC/Mobile Split | 설명 |
|-----|-----------|-----------------|------|
| `/portal/clip` | ClipPage | ✅ | 클립 |
| `/portal/clip/archive` | - | - | 클립 아카이브 |
| `/portal/clip/:id` | - | - | 클립 액션 |
| `/clip/publish/clip` | - | - | 클립 발행 |
| `/clip/publish/archive` | - | - | 아카이브 발행 |

#### Pledge (서약)
| URL | Component | PC/Mobile Split | 설명 |
|-----|-----------|-----------------|------|
| `/portal/pledge/agreement` | PledgePage | ✅ | 서약서 동의 |

#### Component 구조
```
📁 src/pages/portal/
├── favorite/
│   ├── index.tsx (ResponsiveWrapper)
│   ├── favoritePc.tsx
│   └── favoriteMo.tsx
├── feed/
│   ├── index.tsx (ResponsiveWrapper)
│   ├── feedPc.tsx
│   └── feedMo.tsx
├── clip/
│   ├── index.tsx (ResponsiveWrapper)
│   ├── clipPc.tsx
│   └── clipMo.tsx
├── pledge/
│   ├── index.tsx (ResponsiveWrapper)
│   ├── pledgePc.tsx
│   └── pledgeMo.tsx
├── recentHistory/
│   ├── index.tsx (ResponsiveWrapper)
│   ├── recentHistoryPc.tsx
│   └── recentHistoryMo.tsx
└── businessSetting/
    └── businessSetting.tsx
```

---

### 📦 Workbox Routes (워크박스)

| URL | Component | PC/Mobile Split | 설명 |
|-----|-----------|-----------------|------|
| `/workbox` | WorkboxPage | ✅ | 워크박스 메인 |
| `/workbox/workbox-todo-list` | - | - | 할 일 목록 |
| `/workbox/workbox-list-task` | - | - | 작업 목록 |
| `/workbox/workbox-requested-list` | - | - | 요청 목록 |

#### Component 구조
```
📁 src/pages/workbox/
└── index.tsx (ResponsiveWrapper 추정)
```

---

## 🔧 MGR Routes (관리자)

### Dashboard
| URL | Component | 설명 |
|-----|-----------|------|
| `/mgr` | DashboardPage | 관리자 대시보드 |

---

### 📝 MGR Approval Routes (전자결재 관리)

#### 기본환경설정
| URL | Component | 설명 |
|-----|-----------|------|
| `/mgr/approval/payment-default-settings` | PaymentDefaultSettingsPage | 결재기본설정 |
| `/mgr/approval/tl-doc-settings` | TLDocSettingsPage | TLOver 설정 |
| `/mgr/approval/doc-number-settings` | DocNumberSettingsPage | 문서번호 설정 |
| `/mgr/approval/document-number-management` | DocumentNumberManagementPage | 문서채번 관리 |
| `/mgr/approval/seal-signature-management` | SealSignatureManagementPage | 인장서명관리 |

#### 결재프로세스 관리
| URL | Component | 설명 |
|-----|-----------|------|
| `/mgr/approval/process/type` | ApprovalTypePage | 결재유형설정 |

#### 결재양식 관리
| URL | Component | 설명 |
|-----|-----------|------|
| `/mgr/approval/form-type` | FormTypeManagementPage | 양식분류 관리 |
| `/mgr/approval/payment/item-management` | ApprovalItemManagementPage | 결재항목 관리 |
| `/mgr/approval/draft-form-management` | DraftFormManagementPage | 기안양식 관리 |

#### 양식 등록/수정
| URL | Component | 설명 |
|-----|-----------|------|
| `/mgr/approval/form-registration/basic` | SettingRegisterPage | 기본 등록 |
| `/mgr/approval/form-registration/form-settings` | SettingRegisterPage | 양식설정 |
| `/mgr/approval/form-registration/approval-process` | SettingRegisterPage | 결재프로세스 |
| `/mgr/approval/form-registration/form-api-integration` | SettingRegisterPage | 양식 API 연동 |
| `/mgr/approval/form-registration/edit/:id` | SettingRegisterPage | 기본 편집 |
| `/mgr/approval/form-registration/form-settings/edit/:id` | SettingRegisterPage | 양식설정 편집 |
| `/mgr/approval/form-registration/approval-process/edit/:id` | SettingRegisterPage | 결재프로세스 편집 |
| `/mgr/approval/form-registration/form-api-integration/edit/:id` | SettingRegisterPage | 양식 API 연동 편집 |

#### 결재문서함/문서관리
| URL | Component | 설명 |
|-----|-----------|------|
| `/mgr/approval/inbox/document-management` | InboxDocumentManagement | 결재문서함 관리 |
| `/mgr/approval/transfer-document-management` | TransferDocumentManagement | 이관문서관리 |
| `/mgr/approval/transfer-document-management/detail` | DetailTransferDocumentManagement | 이관 결재문서 상세 |
| `/mgr/approval/payment/document-management` | PaymentDocumentManagementPage | 결재문서관리 |
| `/mgr/approval/payment/document-management/detail/:id` | DocumentViewDetailsPage | 결재문서 상세 |
| `/mgr/approval/payment/document-detail/revision-history` | PaymentDocumentDetailRevisionHistoryPage | 결재문서 상세 |

#### 권한 및 설정
| URL | Component | 설명 |
|-----|-----------|------|
| `/mgr/approval/copy-document-view-permission` | CopyDocumentViewPermissionPage | 문서별 조회권한복사 |
| `/mgr/approval/approval-process-management/approval-exception` | ApprovalExceptionPage | 권한 예외자 설정 |
| `/mgr/approval/document-view-permission-copy` | DocumentViewPermissionCopyPage | 문서조회권한복사 |
| `/mgr/approval/substitute-person` | SubstitutePersonPage | 대결설정 |
| `/mgr/approval/payment-confrontation` | PaymentConfrontationPage | 대결 설정 |

#### 통계
| URL | Component | 설명 |
|-----|-----------|------|
| `/mgr/approval/payment-use-status` | PaymentUseStatusPage | 결재사용현황 |

---

### 📋 MGR Board Routes (게시판 관리)

| URL | Component | 설명 |
|-----|-----------|------|
| `/mgr/board/base-settings` | - | 게시판 기본설정 |
| `/mgr/board/management` | - | 게시판 관리 |
| `/mgr/board/template` | - | 게시판 템플릿 |
| `/mgr/board/group` | - | 게시판 그룹 |
| `/mgr/board/form` | - | 게시판 양식 |
| `/mgr/board/form/detail/:id` | - | 게시판 양식 상세 |
| `/mgr/board/form/edit/:id` | - | 게시판 양식 편집 |
| `/mgr/board/form/create` | - | 게시판 양식 생성 |
| `/mgr/board/statistics` | - | 게시판 통계 |
| `/mgr/board/post/general` | - | 일반 게시물 관리 |
| `/mgr/board/post/general/create` | - | 일반 게시물 생성 |
| `/mgr/board/post/general/edit/:id` | - | 일반 게시물 편집 |
| `/mgr/board/post/general/detail` | - | 일반 게시물 상세 |
| `/mgr/board/comment` | - | 댓글 관리 |
| `/mgr/board/create/qna` | - | Q&A 생성 |
| `/mgr/board/qna/detail` | - | Q&A 상세 |
| `/mgr/board/qna/edit/:id` | - | Q&A 편집 |
| `/mgr/board/qna/answer/:id` | - | Q&A 답변 |

---

### 👥 MGR Organizational Routes (조직 관리)

#### 조직도
| URL | Component | 설명 |
|-----|-----------|------|
| `/mgr/organizational/department` | - | 부서 관리 |
| `/mgr/organizational/employment` | - | 직원 관리 |
| `/mgr/organizational/resignation` | - | 퇴사 관리 |
| `/mgr/organizational/hr-link` | - | HR 연동 |

#### 공통코드
| URL | Component | 설명 |
|-----|-----------|------|
| `/mgr/organizational/common/position` | - | 직위 관리 |
| `/mgr/organizational/common/job` | - | 직무 관리 |
| `/mgr/organizational/common/rank` | - | 직급 관리 |
| `/mgr/organizational/common/job-code` | - | 직무코드 관리 |
| `/mgr/organizational/common/communication-code` | - | 소통코드 관리 |
| `/mgr/organizational/common/user-classification-code` | - | 사용자 분류코드 관리 |

#### 기타
| URL | Component | 설명 |
|-----|-----------|------|
| `/mgr/organizational/history` | - | 이력 관리 |
| `/mgr/organizational/user-group` | - | 사용자 그룹 관리 |

---

### 🔐 MGR Menu Permission Routes (메뉴 권한 관리)

| URL | Component | 설명 |
|-----|-----------|------|
| `/mgr/menu-permission/menu` | - | 메뉴 관리 |
| `/mgr/menu-permission/permission` | - | 권한 관리 |
| `/mgr/menu-permission/role` | - | 역할 관리 |

---

### 🌐 MGR Portal Routes (포털 관리)

#### 기본설정
| URL | Component | 설명 |
|-----|-----------|------|
| `/mgr/portal/setting/base` | - | 기본설정 |
| `/mgr/portal/setting/company-information` | - | 회사정보 설정 |
| `/mgr/portal/setting/group-company-information` | - | 계열회사정보 설정 |

#### 팝업관리
| URL | Component | 설명 |
|-----|-----------|------|
| `/mgr/portal/popup-management` | - | 팝업 관리 |
| `/mgr/portal/popup-management/create` | - | 팝업 생성 |
| `/mgr/portal/popup-management/edit/:id` | - | 팝업 편집 |

#### 통계
| URL | Component | 설명 |
|-----|-----------|------|
| `/mgr/portal/statistics/access-accumulation` | - | 접속 누적 통계 |
| `/mgr/portal/statistics/access-log` | - | 접속 로그 |
| `/mgr/portal/statistics/mail-approval-log` | - | 메일 결재 로그 |
| `/mgr/portal/statistics/mail-log` | - | 메일 로그 |
| `/mgr/portal/statistics/monitoring-mail-delivery` | - | 메일 전송 모니터링 |

#### 서약관리
| URL | Component | 설명 |
|-----|-----------|------|
| `/mgr/portal/pledge/inquiry` | - | 서약 조회 |
| `/mgr/portal/pledge/inquiry/create` | - | 서약 생성 |
| `/mgr/portal/pledge/inquiry/edit/:id` | - | 서약 편집 |
| `/mgr/portal/pledge/inquiry/detail/:id` | - | 서약 상세 |
| `/mgr/portal/pledge/form-box` | - | 서약 양식함 |
| `/mgr/portal/pledge/form-box/edit/:id` | - | 서약 양식 편집 |
| `/mgr/portal/pledge/form-box/create` | - | 서약 양식 생성 |

#### 배너관리
| URL | Component | 설명 |
|-----|-----------|------|
| `/mgr/portal/banner/header` | - | 헤더 배너 관리 |
| `/mgr/portal/banner/header/create` | - | 헤더 배너 생성 |
| `/mgr/portal/banner/header/edit/:id` | - | 헤더 배너 편집 |
| `/mgr/portal/banner/right` | - | 우측 배너 관리 |
| `/mgr/portal/banner/right/create` | - | 우측 배너 생성 |
| `/mgr/portal/banner/right/edit/:id` | - | 우측 배너 편집 |

#### 업무연동
| URL | Component | 설명 |
|-----|-----------|------|
| `/mgr/portal/business-link` | - | 업무연동 관리 |
| `/mgr/portal/business-link/create` | - | 업무연동 생성 |
| `/mgr/portal/business-link/edit/:id` | - | 업무연동 편집 |

---

### 📦 MGR Workbox Routes (워크박스 관리)

| URL | Component | 설명 |
|-----|-----------|------|
| `/mgr/workbox/management` | - | 워크박스 관리 |
| `/mgr/workbox/management/create` | - | 워크박스 생성 |
| `/mgr/workbox/management/edit/:id` | - | 워크박스 편집 |
| `/mgr/workbox/status` | - | 워크박스 상태 |
| `/mgr/workbox/form` | - | 워크박스 양식 |
| `/mgr/workbox/form/detail/:id` | - | 워크박스 양식 상세 |
| `/mgr/workbox/form/create` | - | 워크박스 양식 생성 |
| `/mgr/workbox/form/edit/:id` | - | 워크박스 양식 편집 |

---

## 📁 MGR Component 구조

```
📁 src/pages/mgr/
├── index.tsx (Dashboard)
├── approval/
│   ├── environmentSetting/
│   ├── process/
│   ├── form/
│   ├── documentBox/
│   ├── documentTransfer/
│   ├── copyDocumentViewPermission/
│   ├── exceptionAuthorization/
│   ├── copyDocumentPermission/
│   ├── setting/
│   ├── statistics/
│   └── document/
├── board/
│   ├── management/
│   ├── template/
│   ├── form/
│   ├── statistics/
│   ├── postsGeneral/
│   └── comment/
├── menuPermission/
│   ├── menu/
│   ├── permission/
│   └── role/
├── organizational/
│   ├── department/
│   ├── employment/
│   ├── resignation/
│   ├── hrLink/
│   ├── common/
│   ├── history/
│   └── userGroup/
├── portal/
│   ├── setting/
│   ├── popupManagement/
│   ├── statistics/
│   ├── pledge/
│   ├── banner/
│   └── businessLink/
└── workbox/
    ├── management/
    ├── status/
    └── form/
```

---

## 🔄 라우터 매개변수 (Route Parameters)

### Dynamic Routes
| Pattern | Example | 설명 |
|---------|---------|------|
| `/:id` | `/approval-management/need/detail/123` | 일반적인 ID 매개변수 |
| `/edit/:id` | `/mgr/approval/form-registration/edit/456` | 편집 페이지 ID |
| `/detail/:id` | `/mgr/workbox/form/detail/789` | 상세 페이지 ID |

### Query Parameters
| URL | Query Parameters | 설명 |
|-----|------------------|------|
| `/board/general/my-article` | `?tab=my-post` | 탭 선택 |
| `/board/general/my-article` | `?tab=my-comment` | 댓글 탭 |
| `/board/general/my-article` | `?tab=my-temporarily-saved` | 임시저장 탭 |

---

## 🎯 특수 구조 패턴

### 1. ResponsiveWrapper 패턴
대부분의 FO 페이지는 다음 패턴을 따름:
```tsx
const ComponentName = () => (
  <ResponsiveWrapper 
    mobileComponent={<ComponentNameMo />} 
    desktopComponent={<ComponentNamePc />} 
  />
)
```

### 2. Lazy Loading 패턴
성능 최적화를 위해 대부분 컴포넌트가 lazy loading 적용:
```tsx
const ComponentName = lazy(() => import('@/pages/path/to/component'))
```

### 3. Layout 구조
- **FO (Front Office)**: ResponsiveLayout → ResponsiveWrapper → PC/Mobile Components
- **BO (Back Office)**: BoLayouts → Direct Components
- **Public**: Direct Components

### 4. Breadcrumb 지원
많은 FO 페이지가 breadcrumb 네비게이션을 지원:
```tsx
{
  breadcrumb: true,
  useTitleOnBreadcrumb: true,
  breadcrumbBookmark: true
}
```

---

## 팝업/모달 컴포넌트 매핑

### 1. 라우트 기반 팝업 컴포넌트

#### FO (Front Office) 팝업 Routes
| URL | Component | PC/Mobile Split | 설명 | 호출 방식 |
|-----|-----------|-----------------|------|-----------|
| `/approval/popups` | PopupContentsPage | ✅ | 전자결재 팝업 컨텐츠 데모 | 라우팅 |
| `/approval/demo-select-approvers` | DemoSelectApproversPage | ✅ | 결재자 선택 데모 | 라우팅 |

#### BO (Back Office) 팝업 Routes
| URL | Component | 설명 | 호출 방식 |
|-----|-----------|------|-----------|
| `/mgr/portal/popup-management` | PopupManagementPage | 팝업 관리 (목록) | 라우팅 |
| `/mgr/portal/popup-management/create` | PopupManagementCreateUpdatePage | 팝업 생성 | 라우팅 |
| `/mgr/portal/popup-management/edit/:id` | PopupManagementCreateUpdatePage | 팝업 편집 | 라우팅 |

### 2. 서비스 기반 모달/팝업 컴포넌트

#### 모달 서비스 컴포넌트
| 컴포넌트 경로 | 컴포넌트명 | 용도 | 호출 방식 |
|-------------|------------|------|-----------|
| `/src/components/hwModal/index.tsx` | HwModal | 범용 모달 컴포넌트 | 직접 사용 |
| `/src/components/hwModal/modal.tsx` | Modal | 기본 모달 래퍼 | 직접 사용 |
| `/src/components/hwModal/modalGlobal.tsx` | GlobalModalConfirm | 전역 확인 모달 | ModalService |
| `/src/components/hwModal/modalService.ts` | ModalService | 모달 서비스 클래스 | 서비스 호출 |
| `/src/components/hwModal/useModalInstance.tsx` | useModalInstance | 모달 인스턴스 훅 | Hook 사용 |

#### Push-Up 서비스 컴포넌트 (모바일 전용)
| 컴포넌트 경로 | 컴포넌트명 | 용도 | 호출 방식 |
|-------------|------------|------|-----------|
| `/src/components/hwPushUp/index.tsx` | HwPushUp | 모바일용 푸시업 팝업 | 직접 사용 |
| `/src/components/hwPushUp/pushUpGlobal.tsx` | GlobalPushUpConfirm | 전역 푸시업 확인 | PushUpService |
| `/src/components/hwPushUp/pushUp.ts` | PushUpService | 푸시업 서비스 클래스 | 서비스 호출 |

#### Drawer 서비스 컴포넌트
| 컴포넌트 경로 | 컴포넌트명 | 용도 | 호출 방식 |
|-------------|------------|------|-----------|
| `/src/layouts/fo/rightDrawer.tsx` | RightDrawer | FO 우측 드로어 | DrawerProvider |
| `/src/components/uiKit/hwDrawer.tsx` | HwDrawer | 범용 드로어 컴포넌트 | 직접 사용 |
| `/src/components/drawerProvider.tsx` | DrawerProvider | 드로어 컨텍스트 제공자 | Context API |

### 3. 도메인별 특수 팝업 컴포넌트

#### 전자결재 관련 팝업
| 컴포넌트 경로 | 컴포넌트명 | PC/Mobile | 용도 |
|-------------|------------|-----------|----------|
| `/src/pages/approval/popupContents/popups/approvalModal.tsx` | ApprovalModal | PC | 결재 승인 모달 |
| `/src/pages/approval/popupContents/popups/documentHistoryModal.tsx` | DocumentHistoryModal | PC | 문서 이력 모달 |
| `/src/pages/approval/popupContents/popups/documentHistoryModalMo.tsx` | DocumentHistoryModalMo | Mobile | 문서 이력 모달 (모바일) |
| `/src/pages/approval/popupContents/popups/paymentStatus.tsx` | PaymentStatus | Both | 결재 상태 팝업 |
| `/src/pages/approval/popupContents/popups/documentInfomation.tsx` | DocumentInformation | Both | 문서 정보 팝업 |
| `/src/pages/approval/popupContents/popups/registeredRulesModal.tsx` | RegisteredRulesModal | PC | 등록된 규칙 모달 |
| `/src/components/approval/selectApproverOrViewers/selectApproverOrViewersDrawerMo.tsx` | SelectApproverOrViewersDrawerMo | Mobile | 결재자/참조자 선택 드로어 |
| `/src/components/approval/textareaPopup/index.tsx` | TextareaPopup | Both | 텍스트 영역 팝업 |
| `/src/components/approval/header/changesReasonPopup.tsx` | ChangesReasonPopup | Both | 변경 사유 팝업 |

#### 메인 페이지 알림 팝업
| 컴포넌트 경로 | 컴포넌트명 | PC/Mobile | 용도 |
|-------------|------------|-----------|------|
| `/src/pages/main/popupNotify/popupNotifyPc.tsx` | PopupNotifyPc | PC | 메인 알림 팝업 (PC) |
| `/src/pages/main/popupNotify/popupNotifyMo.tsx` | PopupNotifyMo | Mobile | 메인 알림 팝업 (모바일) |
| `/src/pages/main/managementMain/addHanBoardModal.tsx` | AddHanBoardModal | Both | 한보드 추가 모달 |

#### 게시판 관련 드로어/팝업
| 컴포넌트 경로 | 컴포넌트명 | PC/Mobile | 용도 |
|-------------|------------|-----------|------|
| `/src/pages/board/general/detailBoard/detailBoardPc/detailBoardDrawer.tsx` | DetailBoardDrawer | PC | 게시판 상세 드로어 |
| `/src/pages/board/general/detailBoard/detailBoardMo/contentPushUp.tsx` | ContentPushUp | Mobile | 게시판 내용 푸시업 |
| `/src/pages/board/qna/detailBoardQnA/detailQnADrawer.tsx` | DetailQnADrawer | PC | Q&A 상세 드로어 |

#### 포털 관련 팝업
| 컴포넌트 경로 | 컴포넌트명 | 용도 |
|-------------|------------|------|
| `/src/pages/portal/clipPublish/components/modalClipView.tsx` | ModalClipView | 클립 보기 모달 |
| `/src/pages/portal/clipPublish/components/modalClipForm.tsx` | ModalClipForm | 클립 폼 모달 |
| `/src/pages/portal/clipPublish/components/modalClipDetail.tsx` | ModalClipDetail | 클립 상세 모달 |
| `/src/pages/portal/clip/component/modalCardDetail.tsx` | ModalCardDetail | 카드 상세 모달 |

#### MGR 관리자 팝업/모달
| 컴포넌트 경로 | 컴포넌트명 | 용도 |
|-------------|------------|------|
| `/src/pages/mgr/portal/statistics/mailApprovalLog/popupDetail.tsx` | PopupDetail | 메일 결재 로그 팝업 상세 |
| `/src/pages/mgr/portal/banner/header/previewBanner/index.tsx` | PreviewBanner | 배너 미리보기 팝업 |
| `/src/pages/mgr/portal/pledge/inquiry/popupUserJoinList.tsx` | PopupUserJoinList | 사용자 참여 목록 팝업 |
| `/src/pages/mgr/approval/form/setting/process/additionalModal/index.tsx` | AdditionalModal | 추가 설정 모달 |
| `/src/pages/mgr/approval/document/document/addViewPermissionModal.tsx` | AddViewPermissionModal | 조회 권한 추가 모달 |

### 4. 팝업 호출 패턴 분석

#### 라우트 기반 (URL 변경)
- 별도 URL로 접근 가능한 팝업 페이지
- 브라우저 뒤로 가기 지원
- 새 탭에서 열기 가능
- 예: `/approval/popups`, `/mgr/portal/popup-management`

#### 서비스 기반 (Overlay)
- **ModalService**: 전역 모달 관리 서비스
- **PushUpService**: 모바일 푸시업 팝업 서비스
- **DrawerProvider**: 드로어 컨텍스트 제공
- 상태 기반으로 동적 표시/숨김

#### 컴포넌트 직접 사용
- `isOpen` prop으로 표시 제어
- 부모 컴포넌트에서 상태 관리
- 특정 용도에 최적화된 팝업들

### 5. 팝업 컴포넌트 구조 특징

#### PC vs Mobile 분리 패턴
- **PC**: Modal/Drawer 형태가 주로 사용됨
- **Mobile**: PushUp/Drawer 형태가 주로 사용됨
- **Responsive**: 화면 크기에 따라 자동 전환

#### 서비스 계층 구조
```
📁 팝업/모달 아키텍처
├── 📋 라우트 기반 (URL 변경)
│   ├── FO Popup Routes
│   └── BO/MGR Popup Routes
├── 🔧 서비스 기반 (Overlay)
│   ├── ModalService (PC 위주)
│   ├── PushUpService (Mobile 전용)
│   └── DrawerProvider (Context)
└── 🎯 직접 사용 (Component)
    ├── 도메인별 특수 팝업
    ├── 범용 UI 컴포넌트
    └── 상태 기반 제어
```

---

## 📊 통계

### Component 분포
- **총 라우트 수**: ~200+ 개
- **FO Routes**: ~80개 (대부분 PC/Mobile 분리)
- **BO/MGR Routes**: ~120개 (관리자 전용)
- **Public Routes**: ~4개
- **팝업/모달 컴포넌트**: ~50+ 개

### PC/Mobile 분리 현황
- **Approval**: 대부분 분리
- **Board**: 모두 분리
- **Portal**: 대부분 분리
- **Main**: 모두 분리
- **MGR**: 분리 없음 (BO Layout 사용)
- **팝업/모달**: 주요 팝업 대부분 분리

### Lazy Loading 현황
- **Approval**: 90% lazy loading
- **Board**: 50% lazy loading
- **Portal**: 일부 lazy loading
- **MGR**: 대부분 lazy loading
- **팝업**: 대부분 lazy loading

### 팝업 호출 방식 분포
- **라우트 기반**: ~5개 (독립 URL)
- **서비스 기반**: ~15개 (Modal/PushUp/Drawer Service)
- **직접 사용**: ~30개 (컴포넌트 state 기반)

---

## 📝 결론

한진 프론트엔드는 체계적인 라우터 구조를 가지고 있으며, FO/BO 분리, PC/Mobile 대응, Lazy Loading 등 모던 웹 애플리케이션의 특징을 잘 구현하고 있습니다. 특히 ResponsiveWrapper를 통한 PC/Mobile 분리는 사용자 경험을 크게 향상시키는 구조입니다.

---

*문서 작성일: 2025-08-26*  
*마지막 업데이트: Router 설정 파일 기준*