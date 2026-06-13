<div align="center">

# Vexa

**LLM Wiki 워크플로우를 품은 로컬 우선 마크다운 지식 관리 도구**

위키링크로 연결되는 마크다운 에디터에 *LLM Wiki 워크플로우*를 결합했습니다.
당신은 소스를 모으고 질문하고, LLM 은 요약·교차참조·북키핑을 맡습니다.

![version](https://img.shields.io/badge/version-0.9.10-blue)
![platform](https://img.shields.io/badge/platform-Windows%20%7C%20macOS-lightgrey)
![license](https://img.shields.io/badge/license-Proprietary-red)
![stack](https://img.shields.io/badge/Tauri%202%20%2B%20Svelte%205-orange)

[다운로드](#-다운로드) · [주요 기능](#-주요-기능) · [LLM Wiki](#-llm-wiki-워크플로우) · [단축키](#-단축키) · [라이선스](#-라이선스--이용-조건)

</div>

---

## 📥 다운로드

최신 릴리스는 [**Releases**](https://github.com/thewinmaker-fishwater/vexa/releases) 페이지에서 받을 수 있습니다.

| 플랫폼 | 파일 | 비고 |
|--------|------|------|
| **Windows** | `Vexa_x.x.x_x64-setup.exe` (NSIS) | Windows 10/11 |
| **macOS** | `Vexa_x.x.x_aarch64.dmg` | Apple Silicon |

> 설치 후 첫 실행에서 **Vault(마크다운 폴더)를 열면** 바로 사용할 수 있습니다. 모든 데이터는 로컬 파일로만 저장되며 외부 서버로 전송되지 않습니다.

---

## ✨ 주요 기능

### 📝 편집 & 렌더링
- **CodeMirror 6 에디터** + Lezer 트리 기반 **라이브 프리뷰**(WYSIWYG 스타일)
- 위키링크 `[[노트]]` · `[[노트|별칭]]` · `[[노트#제목]]` + 자동완성 · 호버 미리보기
- **KaTeX** 수식, **Mermaid** 다이어그램, 코드 신택스 하이라이팅
- 콜아웃, 체크박스, 블록 ID `^id`, 신뢰도 마커 `[CONF: HIGH/MED/LOW]`
- 깊이별 순서 목록 글리프, 스마트 리스트 편집, 우클릭 컨텍스트 메뉴

### 🔗 지식 연결
- **백링크 패널** — 현재 노트를 참조하는 노트 목록
- **그래프 뷰** — Canvas 2D 기반(Barnes-Hut 시뮬레이션 + 커뮤니티 감지), 대용량에서도 가볍게
- **태그 시스템** `#태그`, **아웃라인**, **속성(Frontmatter) 패널**

### 🗂 생산성
- 탭 + 좌우/상하 분할 뷰, **워크스페이스**(탭 묶음 저장·복원)
- 빠른 열기, 명령 팔레트, 북마크, 최근 파일
- **데일리 노트** · 템플릿 시스템 · **달력 패널**
- 읽기/편집 모드 **인페이지 검색**, **인쇄·PDF 내보내기**(테마 그대로 출력)
- **프레젠테이션 모드**(마크다운 → 슬라이드)

### 🔐 일기 (Journal)
- argon2 기반 **UI 잠금**, 달력 별색 표시, 전용 템플릿, 인덱스·검색·그래프에서 자동 분리

### 🔄 동기화 & 가져오기
- **Git 동기화 헬퍼**(패널 + `.gitignore` 빌더), 웹 클리퍼, HTML/PDF/ZIP 내보내기

### 🎨 커스터마이징 · 다국어
- 라이트/다크 + 컬러 테마 + 커스텀 폰트, 단축키 커스터마이징
- **5개 언어**: 한국어 · English · 日本語 · 简体中文 · 繁體中文

---

## 🧠 LLM Wiki 워크플로우

Vexa 의 핵심 철학은 **단순 RAG 가 아니라, LLM 이 점진적으로 유지하는 영속 위키**입니다.

```
_raw/      ← Layer 1: 사용자가 모은 원본 (불변, LLM 읽기 전용)
_wiki/     ← Layer 2: LLM 이 작성·유지 (요약·엔티티·개념·분석 페이지)
  AGENTS.md ← Layer 3: 스키마 (페이지 4종 / 신뢰도 마커 / 워크플로우 정의)
```

세 가지 작업이 끊기지 않게 유지됩니다:

- **Ingest** — 새 소스를 읽어 요약 페이지 생성 + 관련 엔티티/개념 페이지 갱신 + 인덱스·로그 갱신
- **Query** — 인덱스에서 관련 페이지를 찾아 **인용 포함** 답변, 좋은 답변은 위키에 *pinning*
- **Lint** — 모순·고아 페이지·stale claim·누락 교차참조 검출 → 건강 리포트

> 인간은 큐레이션·질문·방향을, LLM 은 요약·교차참조·북키핑을 담당합니다.

---

## ⌨ 단축키

| 단축키 | 동작 |
|--------|------|
| `Ctrl+P` | 빠른 열기 |
| `Ctrl+Shift+P` | 명령 팔레트 |
| `Ctrl+N` | 새 노트 |
| `Ctrl+S` | 저장 |
| `Ctrl+E` | 편집/보기 전환 |
| `Ctrl+F` | 검색 (편집·읽기 모드) |
| `Ctrl+G` | 그래프 뷰 |
| `Ctrl+B` | 북마크 토글 |
| `Ctrl+Shift+D` | 데일리 노트 |
| `Ctrl+Shift+J` | 일기(Journal) |
| `Ctrl+Shift+C` | 활성 파일 경로 복사 |
| `Ctrl+\` | 사이드바 토글 |
| `F2` | 트리 항목 이름 변경 |
| `F10` | 설정 |

> 단축키는 설정에서 커스터마이징할 수 있습니다.

---

## 🛠 기술 스택

| 구분 | 기술 |
|------|------|
| 데스크톱 | Tauri 2.x + Rust |
| 프론트엔드 | Svelte 5 + Vite 5 |
| 에디터 | CodeMirror 6 (Lezer) |
| 마크다운 | remark / unified 11 |
| 그래프 | Canvas 2D (Barnes-Hut) |
| 수식·다이어그램 | KaTeX · Mermaid |
| 저장소 | 로컬 마크다운 + SQLite 인덱스 |

---

## 📄 라이선스 · 이용 조건

**© 2026 7peaks. All Rights Reserved.** — Vexa 는 7peaks 의 **독점(proprietary) 소프트웨어**이며 오픈소스가 아닙니다.

다음 행위는 **사전 서면 허가 없이 금지**됩니다:

- ❌ 무단 **복제 · 재배포 · 재판매 · 대여 · 공유**
- ❌ 공식 빌드를 **사칭**하거나, "Vexa" 이름 · 로고 · 브랜딩의 무단 사용
- ❌ **크랙 · 우회 · 라이선스 회피** 도구의 제작 · 사용 · 배포
- ❌ **리버스 엔지니어링 · 디컴파일 · 디스어셈블** (관련 법이 강행적으로 허용하는 범위 제외)

다음은 **허용**됩니다:

- ✔ 본 [Releases](https://github.com/sevenpeaksone/vexa/releases) 에서 받은 **공식 빌드의 개인적 사용**
- ✔ 개인 백업 목적의 **사본 1부** 보관

> ⚠️ 본 섹션은 요약입니다. 정식 약관은 [`LICENSE`](LICENSE) (EULA) 가 우선합니다.
> 라이선스 · 배포 · 제휴 문의: **(연락처 입력)**

---

<div align="center">
<sub>Vexa — 에디터는 IDE, LLM 은 프로그래머, 위키는 코드베이스.</sub>
</div>
