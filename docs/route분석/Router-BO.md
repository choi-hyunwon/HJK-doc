---
sidebar_position: 2
---


# Router-BO 문서

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

*문서 작성일: 2025-08-26*  
*마지막 업데이트: Router 설정 파일 기준*