# AI workflows and templates
AI 개발작업을 위한 workflow 와 templates (prompts, skills, references) 모음

## 1. Brainstorm-UI/UX max-Memorybank(BUM) AI workflow
### 1) 프롬프트
- 직접 작성하거나 brainstorming skill 사용
```
 # Install Globally
 npx skills add obra/superpowers@brainstorming 
```
- 작성한 프롬프트는 .prompt/ 폴더에 보관 (superpowers skill 사용시 docs/superpowers/specs 에 위치)
- 프롬프트: .prompt/request.md

### 2) PRD 문서화 (선택)
- 작성된 요구사항 문서를 PRD수준에 맞는 문서화 작업 필요시 (awesome-copilot skill 사용)
```
 npx skills add https://github.com/github/awesome-copilot --skill prd
 $prd (/prd) <작성한 requirement or brainstorming에 의해 생성된 design 문서>
```
- 기존 요구사항 문서가 PRD 형식에 맞도록 재 작성됨
- 프롬프트: 보관 필요없음

### 3) UI 디자인 (선택)
- UI가 필요한 기능인 경우. ui-ux-pro-max skill 사용
```
 # Install CLI globally
 npm install -g ui-ux-pro-max-cli
 # Go to your project and install for the AI agent
 cd /your project
 uipro init --ai claude (--ai codex)
```
- $ui-ux-pro-max <작성 요청 프롬프트> 로 요청. DESIGN.md 생성
```
 # 작성된 DESIGN.md 문서 포맷 정확도 확인 
 npx @google/design.md lint DESIGN.md
```
- 프롬프트: ./prompt/ui-ux-pro-max.md

### 4) AGENTS.md (CLAUDE.md) 생성 
- AI Agent는 항상 AGENTs.md (또는 CLAUDE.md)를 읽는다. 이점을 활용하여 새로 만들어진 요구사항, DESIGN.md 등을 항상 읽을 수 있도록 함
```
 AGENTS.md 를 만들고 그 동안 만들었던 DESIGN.md 와 스펙문서들을 추가해줘 
```
- 프롬프트: 보관 필요없음 

### 5) 메모리뱅크 workflow (Local skill)
- 작업 진행시 참고할 문서, 따라야할 지침, 진행과정 및 의사결정사항 기록, 작업 완료 기준, 검증 결과 등의 지침을 따르고 기록하기 위함
 - Read: 작업 전에 먼저 읽어야 할 문서
 - Summary: 현재 상태를 짧게 요약
 - Task card: 작업의 범위와 완료기준
 - Update: 검증결과 와 다음 작업기록
- 직접 만들거나 $skill-creator 사용
```
 $skill-creator <memory-bank-workflow 생성 프롬프트 문서>
```
- 프롬프트: ./prompt/skill-creator-memory-bank.md

### 6) 작업진행
- 지금까지 정리한 요구사항, 디자인, 작업지침 대로 개발작업 수행 
```
 $memory-bank-workflow 작업지침대로 개발을 진행해줘
```

### 7) AGENT.md (CLAUDE.md) 갱신
- 프로젝트 문서와 메모리 뱅크 가이드를 작업지침에 추가하기 위함. 
```
 AGENT.md 를 만들고 프로젝트 관련 문서를 안에서 참고할 수 있게 추가해줘 
 추가 기능 구현 및 수정이 필요하면 $memory-bank 참고하여 진행할 수 있도록 추가해줘
```

### 8) 이미지 생성 (선택)
- 마케팅 이미지 와 비디오 만들기 
- Codex의 $imagegen skill 사용 (기본 설치되어있음)
- 주의: image 생성시에는 반드시 xhigh 를 써야 품질좋은 이미지가 나온
```
 $imagegen <create-image 생성 프롬프트 문서>
```
- 프롬프트: ./prompt/create-image.md

### *) 레퍼런스 문서
```
/Reference/memory-bank-workflow/
  - request.md
  - ui-ux-pro-max.md
  - skill-creator-memory-bank.md
  - create-image.md
```
