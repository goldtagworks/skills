<div align="center">

# 🛠️ Skills

**내가 만들고 사용할 Claude Code 스킬 모음**

_반복 작업을 자동화하고, AI에게 일관된 결과를 시키기 위한 개인 스킬 & 프롬프트 라이브러리_

[![Claude Code](https://img.shields.io/badge/Claude-Code-D4A373?style=for-the-badge&logo=anthropic&logoColor=white)](https://claude.com/claude-code)
[![Skills](https://img.shields.io/badge/Skills-Collection-2D6A4F?style=for-the-badge)](https://github.com/goldtagworks/skills)
[![Prompts](https://img.shields.io/badge/Prompts-Library-7B2CBF?style=for-the-badge)](https://github.com/goldtagworks/skills/tree/main/prompt)
[![License](https://img.shields.io/badge/License-MIT-blue?style=for-the-badge)](LICENSE)

</div>

---

## 📖 소개

이 저장소는 **Claude Code**와 다양한 AI 도구에서 반복적으로 사용하는 워크플로우를 **스킬(Skill)** 또는 **프롬프트(Prompt)** 형태로 정리해두는 개인 라이브러리입니다.

> 💡 **스킬(Skill)이란?** Claude Code가 특정 상황에서 자동으로 불러와 실행하는 재사용 가능한 작업 절차입니다.  
> `SKILL.md` 안에 트리거 조건과 워크플로우가 정의되어 있어, 같은 컨텍스트를 매번 다시 설명할 필요가 없습니다.

이 저장소에는 **계속해서 새로운 스킬과 프롬프트가 추가될 예정**입니다.  
각자 다른 도메인(디자인, 글쓰기, 코드 리뷰, 자동화 등)을 다루며, 필요할 때마다 가져다 쓸 수 있도록 정리합니다.

---

## 📦 수록 콘텐츠

### 🎨 Skills

| 스킬 | 카테고리 | 설명 |
|------|----------|------|
| [`character-sheet-designer/`](./character-sheet-designer/) | Design / Image | 캐릭터 특징을 입력하면 일관된 캐릭터를 설계하고 4분할 캐릭터 시트(턴어라운드) 이미지 생성용 브리프를 만들어주는 스킬 |

### 📝 Prompts

| 프롬프트 | 카테고리 | 설명 |
|----------|----------|------|
| [`prompt/character-sheet-designer.md`](./prompt/character-sheet-designer.md) | Design / Image | Character Sheet Designer의 원본 한국어 프롬프트 (GPT Image 2 등 범용 사용) |

> _스킬과 프롬프트는 앞으로 계속 추가됩니다. 새 항목은 PR 또는 커밋으로 반영됩니다._

---

## 🙏 Credits & Sources

이 저장소의 일부 콘텐츠는 외부에서 영감을 받았으며, 그 위에 제가 직접 **Claude Code 스킬로 재구현**한 것들입니다.

| 항목 | 원본 출처 | 비고 |
|------|-----------|------|
| `prompt/character-sheet-designer.md` & `character-sheet-designer/` 스킬 | [YouTube — @AI_Freemium](https://www.youtube.com/@AI_Freemium) | 원본 프롬프트는 해당 채널 영상에서 소개된 내용을 참고했고, Claude Code 스킬 구조(SKILL.md, 워크플로우, 트리거)는 본인이 직접 구현 |

> _정확한 영상 URL이 기억나지 않는 항목은 채널 링크로만 크레딧을 표기합니다. 영상 URL이 확인되면 추후 보강합니다._

---

## 🚀 사용 방법

### 1. Claude Code 스킬로 사용

```bash
# 저장소 클론
git clone https://github.com/goldtagworks/skills.git

# 원하는 스킬을 Claude Code 스킬 디렉토리로 복사
cp -r skills/character-sheet-designer ~/.claude/skills/

# Claude Code 재실행 후 자연어로 호출
#   예) "판타지 엘프 마법사 캐릭터 시트 만들어줘"
```

### 2. `.skill` 패키지로 설치

`.skill` 파일이 제공되는 경우 Claude Code에서 직접 임포트할 수 있습니다.

### 3. 프롬프트만 가져다 쓰기

`prompt/` 디렉토리의 `.md` 파일을 ChatGPT, Gemini 등 어떤 LLM에든 그대로 붙여넣어 사용할 수 있습니다.

---

## 🗂️ 디렉토리 구조

```
skills/
├── <skill-name>/                # 스킬 단위 디렉토리
│   ├── SKILL.md                 # 스킬 정의 (frontmatter + 워크플로우)
│   └── references/              # 보조 참고 자료
├── <skill-name>.skill           # 패키지된 스킬 파일 (선택)
├── prompt/                      # raw 프롬프트 모음 (범용 LLM용)
│   └── <topic>.md
└── README.md
```

각 스킬 디렉토리는 독립적으로 동작하므로, 필요한 것만 골라 쓰면 됩니다.

---

## 🧩 새 스킬 추가 규칙 (Self Note)

새로운 스킬을 추가할 때 따르는 개인 규칙:

1. **이름은 kebab-case** — `character-sheet-designer`, `pr-reviewer` 등
2. **`SKILL.md`에 frontmatter 필수** — `name`, `description`을 명확히
3. **트리거 조건을 description에 풍부하게** — 자연어 변형도 함께 (예: "캐릭터 시트", "turnaround", "레퍼런스 이미지")
4. **워크플로우는 번호 매긴 단계로** — Claude가 순서를 지키도록
5. **README의 표에 한 줄로 등록** — 카테고리 + 한 줄 설명

---

## 🤝 기여 & 피드백

이 저장소는 개인용 큐레이션이지만, 좋은 아이디어나 개선 제안은 언제든 환영합니다.  
이슈를 열거나 PR을 보내주세요.

---

## 📄 라이선스

MIT License — 자유롭게 가져다 쓰세요. 단, 사용에 따른 책임은 본인에게 있습니다.

---

<div align="center">

_Crafted with ❤️ by [@goldtagworks](https://github.com/goldtagworks)_

</div>
