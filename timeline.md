# 건강관리 실습 앱 프로젝트 작업 기록

## 기록 범위

| 항목 | 값 |
| --- | --- |
| 프로젝트명 | 건강관리 실습 앱 |
| 원본 저장소 / 소유자 | KimChaeJun/mini_BodyCheck / KimChaeJun |
| 본인 소유 여부 / 확인 근거 | 소유 저장소. 연결 계정 KimChaeJun 및 GitHub owner 메타데이터 대조 (E01). 소유권과 코드 저작·개인 기여는 구별함. |
| 저장소 공개 범위 | 공개 |
| 기본 브랜치 / 문서 반영 브랜치 | main / main |
| 확인한 소스 커밋 / 조사 기준일 | a21e8559dea44f704f8d215600ba4d2c765015eb / 2026-11-05 (Asia/Seoul) |
| 기본 브랜치 루트 timeline.md 반영 상태 | 이 문서는 기본 브랜치 루트 timeline.md로 생성하는 기록. 문서 생성 커밋과 위 소스 확인 커밋은 다름. 사이트 등록·배포는 별도 작업. |
| 프로젝트 상태 / 실제 개발 기간 | 강의 제공 complete와 일부 미완성 practice가 공존. 개인 완성·운영 배포 여부 미확인 / 전체 개발 기간 미확인 |
| 본인 참여 기간 | 미확인. 커밋 날짜를 참여 시작·종료일로 사용하지 않음 (E91). |
| 개인·팀 / 팀 규모·역할 분담 | README가 강의 실습용 기반이라고 명시. 원 제공자·라이선스·개인 수정 범위와 개인·팀 여부 미확인 |
| 연혁 날짜 기준 | Git author timestamp를 Asia/Seoul로 변환한 변경 기록일. 문서 작성일과 실제 개발·배포 사건일을 구별함. |

## 포트폴리오 공개용 데이터

프로젝트 전체의 확인된 구현을 설명하는 전달용 JSON입니다. 본인의 역할·참여 기간은 확인 후 채웁니다. 문서 작성만으로 사이트에 자동 등록되지는 않습니다.

```json
{
  "slug": "mini-bodycheck",
  "title": "건강관리 실습 앱",
  "subtitle": "수분·운동·수면·식사 기록과 주간 리포트를 다루는 FastAPI 실습",
  "category": "LEARNING PROJECT · HEALTH TRACKING",
  "role": "",
  "roleTags": [],
  "year": "",
  "period": "",
  "award": "",
  "summaryLines": [
    "건강 기록 입력·조회와 대시보드·수분 리포트를 학습하는 FastAPI 프로젝트입니다.",
    "SQLite·Tortoise ORM과 Jinja 템플릿을 연결한 complete 예제를 제공합니다.",
    "practice에는 미완성 API와 목 데이터가 있어 학습 과제 범위를 구분합니다."
  ],
  "overviewLines": [
    "수분·운동·수면·식사 기록을 웹에서 다루는 강의 실습용 프로젝트입니다.",
    "complete는 완성 예제이고 practice는 일부 ORM·API가 비어 있는 학습용 코드입니다.",
    "서버 렌더링 화면과 JSON API를 함께 두고 수분 섭취 기록을 집계해 리포트 그림을 생성합니다."
  ],
  "tags": [
    "Python",
    "FastAPI",
    "Jinja2",
    "Tortoise ORM",
    "SQLite"
  ],
  "roles": [],
  "technologyStack": [
    {
      "category": "Backend",
      "description": "학습용 API와 서버 화면 진입점을 구성합니다.",
      "technologies": [
        "Python",
        "FastAPI",
        "Jinja2"
      ]
    },
    {
      "category": "Database",
      "description": "complete의 건강 기록을 저장합니다.",
      "technologies": [
        "Tortoise ORM",
        "SQLite"
      ]
    },
    {
      "category": "Reporting",
      "description": "수분 기록을 집계·그림으로 변환합니다.",
      "technologies": [
        "Pandas",
        "Matplotlib"
      ]
    }
  ],
  "metrics": [],
  "pipeline": [
    {
      "label": "INPUT",
      "description": "수분·운동·수면·식사 기록 화면 또는 API를 사용합니다."
    },
    {
      "label": "STORE",
      "description": "complete 예제에서 ORM과 SQLite에 기록을 저장합니다."
    },
    {
      "label": "VIEW",
      "description": "서버 렌더링 화면에서 기록과 요약을 조회합니다."
    },
    {
      "label": "REPORT",
      "description": "수분 기록을 집계해 리포트 차트와 통계를 표시합니다."
    }
  ],
  "improvements": [],
  "timeline": [
    {
      "date": "2026-06-17",
      "title": "저장소 초기 작업 기록",
      "description": "pjt start라는 제목의 초기 커밋을 확인했습니다. 실제 학습·참여 시작일로 확정하지 않습니다."
    },
    {
      "date": "2026-06-17",
      "title": "실습 기반 코드 가져오기",
      "description": "clone pjt base code라는 제목으로 기반 코드가 등록되었습니다. 직접 전체 구현한 이력으로 해석하지 않습니다."
    }
  ]
}
```

## 문제와 설계 배경

- 대상·문제: 건강 기록 CRUD와 ORM·템플릿·집계 리포트를 연습하는 학습 프로젝트입니다 (E02).
- 제공 범위: README가 complete를 전체 완성본, practice를 일부 백엔드 미완성 실습용으로 구분합니다.
- 구조: FastAPI 진입점이 API와 페이지 라우터를 연결하고 SQLite·Tortoise ORM으로 기록을 저장합니다 (E03).
- 리포트: complete 페이지에서 Pandas·Matplotlib로 수분 기록을 집계·시각화합니다 (E04).
- 학습 과제: practice API에는 수분 외 운동·수면·식사 API를 추가하라는 TODO가 남아 있고 목 데이터 모듈이 있습니다 (E05).
- 한계: 제공 코드의 저작·라이선스와 개인 수정·완성 범위를 확인하기 전에는 포트폴리오 개인 구현 성과로 확대하지 않습니다.

## 본인 역할과 기여

대표 직무는 아직 확정하지 않았습니다. 다음은 현재 구현에서 확인한 **담당 범위 확인 후보**이며, 프로젝트 전체 기능을 본인의 기여로 단정하지 않습니다. Git 작성자는 변경 추적의 단서로만 사용합니다 (E91).

| 영역 | 확인한 구현·의사결정과 개인 확인 범위 | 개인·팀 경계 | 근거 |
| --- | --- | --- | --- |
| 강의 기반 가져오기·환경 구성 | 저장소에 기반 코드가 등록되어 있음. 강의 원본과 개인 수정 diff를 먼저 분리해야 함. | 개인·팀별 담당 미확인 | E02, E20, E21 |
| 실습 API·ORM | complete 기능과 practice TODO를 구분함. 본인이 완성한 API·모델·예외 처리 범위 미확인. | 개인·팀별 담당 미확인 | E03, E05 |
| 화면·리포트 | 제공된 템플릿·수분 집계 구현 존재. 개인 UI·리포트 기여 여부는 미확인. | 개인·팀별 담당 미확인 | E04 |

## 기술별 사용 내역

기술명은 확인한 코드·문서·매니페스트에서 실제 사용 맥락이 드러나는 항목만 기록했습니다. 아래 목록은 저장소 스택이며 개인 숙련도 목록이 아닙니다.

| 그룹 | 기술 | 용도·사용 위치 | 본인 사용 여부 | 상태 | 근거 |
| --- | --- | --- | --- | --- | --- |
| Backend | Python | 기록 API·페이지 처리; [complete/app/routers/api.py](complete/app/routers/api.py) | 확인 필요 | 확인 커밋에서 사용; 현재 운영 여부 미확인 | E03 |
| Backend | FastAPI | 앱·페이지·API 라우팅; [complete/app/main.py](complete/app/main.py) | 확인 필요 | 확인 커밋에서 사용; 현재 운영 여부 미확인 | E03 |
| Backend | Jinja2 | 건강 기록·리포트 서버 렌더링; [complete/app/routers/pages.py](complete/app/routers/pages.py), [complete/app/templates/report.html](complete/app/templates/report.html) | 확인 필요 | 확인 커밋에서 사용; 현재 운영 여부 미확인 | E04 |
| Database | Tortoise ORM | 모델 등록·비동기 초기화·조회; [complete/app/db.py](complete/app/db.py) | 확인 필요 | 확인 커밋에서 사용; 현재 운영 여부 미확인 | E03 |
| Database | SQLite | 로컬 파일 DB 연결; [complete/app/db.py](complete/app/db.py) | 확인 필요 | 확인 커밋에서 사용; 현재 운영 여부 미확인 | E03 |
| Reporting | Pandas | 기록 집계·데이터프레임 생성; [complete/app/routers/pages.py](complete/app/routers/pages.py) | 확인 필요 | 확인 커밋에서 사용; 현재 운영 여부 미확인 | E04 |
| Reporting | Matplotlib | 수분 리포트 이미지 생성; [complete/app/routers/pages.py](complete/app/routers/pages.py) | 확인 필요 | 확인 커밋에서 사용; 현재 운영 여부 미확인 | E04 |

## 성과와 검증

| 항목·값 | 측정일·환경·집계 대상 | 방법·출처 | 제한·근거 |
| --- | --- | --- | --- |
| complete·practice 차이 | 확인 커밋의 양쪽 코드와 README | 수분 API와 운동·수면·식사 TODO·목 데이터 비교 | 제공 완성본을 개인 완성 결과로 쓰지 않음 (E02, E03, E05). |
| 리포트 경로 | complete 페이지·템플릿 | 집계·그림 저장·템플릿 출력 코드 확인 | 브라우저·DB 실행·그림 재생성 미수행 (E04). |
| 성과·테스트 | 실행 로그 미확인 | 학습 예제의 구조만 정적 확인 | metrics=[]; 임상·사용자·운영 성과 없음 (E92). |

신규 실행 결과나 개선율은 없습니다. 코드·문서로 확인한 범위와 과거 기록의 한계를 구별하며, 서로 다른 테스트 집합을 합산하지 않습니다 (E92).

### 수상·외부 평가

수상 이력 없음. 2026-11-05 사용자 확인에 근거하며 공개 JSON의 award는 빈 문자열로 유지합니다 (E90). 외부 평가나 고객·사용자 수는 확인되지 않았습니다.

## 문제 해결과 개선

| 문제·제약 | 확인된 접근·변경과 이유 | 정적 검증 범위 | 남은 한계·근거 |
| --- | --- | --- | --- |
| API·페이지·DB 연결 학습 | FastAPI 라우터와 ORM 초기화를 분리한 예제를 제공 | complete 진입점·모델·API 대조 | 본인 설계·구현으로 확정할 근거 없음 (E03). |
| 기록을 요약 정보로 표현 | Pandas 집계와 Matplotlib 차트를 Jinja 리포트로 연결 | 페이지 함수·템플릿 확인 | 정량 효과·실행 성공·개인 기여는 별도 확인 (E04). |
| 완성본과 실습 과제의 혼동 | complete·practice·목 데이터·TODO를 별도로 기록 | 실제 API 차이와 README 대조 | 실습 완성 여부·원본 라이선스 확인 필요 (E05). |

상기 내용은 설계 선택과 현재 구현을 설명합니다. 비교 가능한 과거 구현·전후 측정이 부족하므로 공개 JSON의 improvements는 빈 배열로 두었습니다.

## 상세 작업 기록

날짜는 모두 연도를 포함한 KST 변경 기록일입니다. 조사한 대표 커밋만 수록하며 전체 개발 기간이나 모든 작업을 뜻하지 않습니다.

### 2026-06-17 / 저장소 초기 작업 기록

- 상태: 코드 이력 확인. 실제 실행·배포 성공 여부는 별도 검증하지 않았습니다.
- 기록된 작업: pjt start라는 제목의 초기 커밋을 확인했습니다. 실제 학습·참여 시작일로 확정하지 않습니다.
- 수행 주체: 저장소 변경 기록입니다. 개인 담당 범위는 아래 기여 확인 항목과 구별합니다.
- 산출물·근거: `6cdc7a569317647cdb4caaf0cfcf0d59f4df52d6` (E20). 커밋 메시지와 현재 구현·문서 범위에서 확인했습니다.

### 2026-06-17 / 실습 기반 코드 가져오기

- 상태: 코드 이력 확인. 실제 실행·배포 성공 여부는 별도 검증하지 않았습니다.
- 기록된 작업: clone pjt base code라는 제목으로 기반 코드가 등록되었습니다. 직접 전체 구현한 이력으로 해석하지 않습니다.
- 수행 주체: 저장소 변경 기록입니다. 개인 담당 범위는 아래 기여 확인 항목과 구별합니다.
- 산출물·근거: `a21e8559dea44f704f8d215600ba4d2c765015eb` (E21). 커밋 메시지와 현재 구현·문서 범위에서 확인했습니다.

### 2026-11-05 / 프로젝트 기록 작성

- 상태: 문서 작성.
- 수행 내용: 기본 브랜치의 README·구현 코드·매니페스트·Git 기록을 대조하고 공개용 JSON, 기술 사용 내역, 근거 색인과 확인 항목을 작성했습니다.
- 검증: JSON 파싱·필수 키·배열 항목 구조·근거 경로를 검사했습니다. 애플리케이션 실행이나 과거 테스트 재실행은 수행하지 않았습니다.
- 수상: 사용자가 수상 이력이 없다고 확인한 내용을 반영했습니다 (E90).

## 다음 계획

아래는 자료에서 확인한 미수행 계획 또는 기록 보완 과제입니다. 완료 이력·성과에 포함하지 않습니다.

- 강의 원본·라이선스·본인 수정 diff를 확인하고 포트폴리오에 소개할 기여 범위를 정합니다.
- practice의 미완성 API·모델·목 데이터 의존성과 본인이 수행한 실습 결과를 별도 검증합니다.

## 공개 자료

| 항목 | 값 | 공개 여부·한계 |
| --- | --- | --- |
| 서비스·데모 URL (liveUrl) | 빈 값 | 현재 유효한 공개 운영 주소를 검증하지 않음. 로컬·임시·사내 주소는 공개 URL로 옮기지 않음. |
| 공개 저장소 URL (githubUrl) | https://github.com/KimChaeJun/mini_BodyCheck | GitHub 공개 저장소 메타데이터 확인 |
| 대표 이미지 (coverImage) | 빈 값 | README의 assets/dashboard.png는 제공 자료일 수 있어 대표 이미지로 확정하지 않았습니다. 개인 캡처·재사용 권한 확인이 필요합니다. |
| 이미지 대체 텍스트 / 시연·발표 자료 | 미확인 | 검증한 공개 대표 자료가 없으면 링크·설명을 생성하지 않음 |

## 근거 색인

소스 위치는 위 확인 커밋을 기준으로 읽습니다. 비공개 원문의 코드·비밀값·사내 주소는 복사하지 않고 최소한의 상대 경로와 커밋만 기록합니다. 공개용 문자열에는 근거 ID나 구현 경로를 넣지 않습니다.

| ID | 뒷받침하는 필드·주장 | 출처 종류·참조 | 출처 시점 | 확인 내용·한계 | 공개 범위 |
| --- | --- | --- | --- | --- | --- |
| E01 | slug, title, 기록 범위와 소유·브랜치·버전 | GitHub 저장소 메타데이터·기본 브랜치 파일 목록 | 2026-11-05 | 소유자 KimChaeJun, 확인 커밋 a21e8559dea44f704f8d215600ba4d2c765015eb; 전체 트리 비절단, 조사 당시 timeline.md 없음. 저장소 생성일·push일은 참여 기간으로 사용하지 않음. | 공개 |
| E02 | subtitle, category, summaryLines, overviewLines, pipeline, 문제 배경 | 문서·코드 / [README.md](README.md), [complete/app/main.py](complete/app/main.py), [complete/app/routers/api.py](complete/app/routers/api.py), [practice/app/routers/api.py](practice/app/routers/api.py) | a21e8559dea4 | complete의 제공된 완성 기능과 practice의 학습 과제를 구별함. 최초 커밋 제목 clone pjt base code를 개인 개발 실적으로 바꾸지 않음. | 공개 |
| E03 | technologyStack[0~1], complete 기능 | 문서·코드 / [complete/app/main.py](complete/app/main.py), [complete/app/db.py](complete/app/db.py), [complete/app/routers/api.py](complete/app/routers/api.py), [complete/app/models/user.py](complete/app/models/user.py), [complete/requirements.txt](complete/requirements.txt) | a21e8559dea4 | FastAPI 라우터·Tortoise SQLite 초기화·건강 기록 API·모델을 확인함. 제공된 완성본 범위이며 개인 구현 실적 아님. | 공개 |
| E04 | technologyStack[2], 서버 화면·리포트 | 문서·코드 / [complete/app/routers/pages.py](complete/app/routers/pages.py), [complete/app/templates/report.html](complete/app/templates/report.html), [complete/requirements.txt](complete/requirements.txt) | a21e8559dea4 | Jinja2 페이지, Pandas 집계·Matplotlib 이미지 저장과 수분 리포트 템플릿 확인. 실제 실행 결과·의학적 효과는 검증하지 않음. | 공개 |
| E05 | 실습 공백·원본 구분 | 문서·코드 / [practice/app/routers/api.py](practice/app/routers/api.py), [practice/app/models/user.py](practice/app/models/user.py), [practice/app/services/mock_data.py](practice/app/services/mock_data.py), [README.md](README.md) | a21e8559dea4 | practice의 운동·수면·식사 API TODO, 제한된 모델·목 데이터와 강의 제공 설명 확인. complete와 합쳐 개인 완료 기능으로 세지 않음. | 공개 |
| E20 | timeline[0], 상세 작업 기록 | Git commit / 6cdc7a569317647cdb4caaf0cfcf0d59f4df52d6 | 2026-06-17 KST | 커밋 기록: pjt start. 변경 기록일이며 착수·배포·수상일 또는 개인 수행 확정 근거로 확대하지 않음. | 공개 |
| E21 | timeline[1], 상세 작업 기록 | Git commit / a21e8559dea44f704f8d215600ba4d2c765015eb | 2026-06-17 KST | 커밋 기록: clone pjt base code. 변경 기록일이며 착수·배포·수상일 또는 개인 수행 확정 근거로 확대하지 않음. | 공개 |
| E90 | award, 수상·외부 평가 | 사용자 진술 / 이 작업의 채팅 | 2026-11-05 KST | 사용자가 선택한 8개 프로젝트에 수상 이력이 없다고 확인함. award는 빈 문자열이며 미확인 수상을 만들지 않음. | 사용자 확인 사실; 대화 원문은 복사하지 않음 |
| E91 | role, roleTags, roles, year, period와 개인 기여 | 자료 공백 / 확인한 문서·코드·Git 이력의 범위 | 2026-11-05 | 담당 직무·전체 참여 기간·개인/팀 규모는 별도 확인이 필요함. Git 작성자 계정, 저장소 소유권, 제공 코드의 존재만으로 직접 기여를 확정하지 않음. | 미확인 |
| E92 | metrics, 성과와 검증 | 정적 조사 / 본 문서 작성 절차 | 2026-11-05 | 애플리케이션 실행·모델 학습·외부 API 호출·운영 환경 변경은 수행하지 않음. 문서의 JSON 형식·필수 키·근거 경로를 검증함. 과거 문서 수치는 아래 한계와 함께 보존하며 신규 실측값으로 표시하지 않음. | 검증 범위 공개 가능 |

## 확인 필요 / 해당 없음

| 항목 | 상태 | 현재 알려진 사실 | 추가 확인 |
| --- | --- | --- | --- |
| 대표 역할·개인 기여 | 미확인 | role은 빈 문자열, roleTags·roles는 빈 배열. 아래 후보 영역을 개인 실적으로 확정하지 않음. | 본인이 수행한 기능·설계·검증·협업 범위 확인 |
| 참여·개발 기간 / year | 미확인 | year·period는 빈 문자열. 소스 연혁은 별도로 보존. | 실제 시작·종료 또는 진행 중 여부와 참여 기간 확인 |
| 팀 규모·역할 분담 | 미확인 | README가 강의 실습용 기반이라고 명시. 원 제공자·라이선스·개인 수정 범위와 개인·팀 여부 미확인 | 원 팀원 수와 역할 분담표 확인 |
| 수상 | 해당 없음 | 사용자 확인에 따라 수상 이력 없음 (E90). | 없음 |
| 성과 수치 / metrics | 미확인 | 신규 실측값 없음. metrics는 빈 배열이며 미측정 수치를 0으로 대체하지 않음. | 동일 조건의 측정 로그·기간·환경·집계 대상 확인 |
| 실행·테스트 | 미실행 | 이번 작업은 정적 조사와 문서 검증. 테스트 코드의 존재를 통과 결과로 바꾸지 않음 (E92). | 필요한 실행 환경에서 별도 재현 |
| 제공 코드·개인 기여 | 미확인 | 강의 제공 complete·practice라는 README와 기반 코드 가져오기 이력만 확인. | 원본 출처·사용 조건·본인 수정 diff |
| 실습 완성 상태 | 미완성 항목 존재 | practice API에 운동·수면·식사 TODO와 목 데이터가 남아 있음. | 본인 완료 기능·실행 화면·검증 결과 |
| 이미지 재사용 권한 | 미확인 | README가 assets/dashboard.png를 사용함. 제공 자료의 별도 재사용 조건 미확인. | 원본 이미지 사용 조건 |

## 사이트 반영 메모

- 문서 위치: 소유 저장소 기본 브랜치 `main`의 루트 `timeline.md`. 해당 브랜치에 생성된 문서가 사이트 수록 여부를 검토할 근거입니다.
- 역할·기여·참여 기간·팀 규모는 확인 후 공개 데이터를 보완합니다. AI PM은 선택하지 않았으므로 추가하지 않았습니다.
- 수상 표시와 미측정 성과 카드는 숨겨야 하며, 빈 문자열·빈 배열을 가상의 값으로 대체하지 않습니다.
- 공개 URL·대표 이미지가 확인되기 전에는 관련 링크·일러스트를 임의로 만들지 않습니다.
- 이번 작업은 해당 저장소 문서 작성입니다. 포트폴리오 데이터 수정·사이트 등록·배포는 수행 범위에 포함하지 않습니다.
