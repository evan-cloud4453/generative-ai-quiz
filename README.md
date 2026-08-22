# 생성형 인공지능 입문 — 퀴즈 학습기
### Generative AI · Quiz Trainer

> 2026학년도 1학기 K-MOOC 「생성형 인공지능 입문」 수업의 주차별 퀴즈를
> 반복해서 풀고, 틀린 문제만 골라 다시 풀 수 있게 만든 시험 대비 학습기입니다.

**▶ 바로 풀어보기 : https://evan-cloud4453.github.io/generative-ai-quiz/**

![GitHub Pages](https://img.shields.io/badge/GitHub%20Pages-live-2ea44f?logo=github)
![HTML5](https://img.shields.io/badge/HTML5-single%20file-E34F26?logo=html5&logoColor=white)
![Vanilla JS](https://img.shields.io/badge/Vanilla%20JS-no%20build-F7DF1E?logo=javascript&logoColor=black)
![Questions](https://img.shields.io/badge/questions-215-5ad1a8)

---

<details>
<summary><b>English Summary</b> — click to expand</summary>

<br>

A single-file, dependency-free quiz trainer built to prepare for the *Introduction to
Generative AI* course (K-MOOC, Spring 2026). It holds **215 multiple-choice questions
in two banks**: 85 original items taken from the weekly course quizzes, plus 130
harder "variant" items generated with a generative-AI assistant to test conceptual
understanding rather than recall.

- **Two banks, two tabs** — original (weeks 1–15) and variant (weeks 1–7, 9–14)
- **A wrong-answer notebook that maintains itself** — every item you miss is queued for
  review and drops out automatically once you get it right in a later attempt
- **Optional shuffling** of question order and of choice order
- **Attempt history and cumulative accuracy**, stored in `localStorage`
- **No build step, no backend, no dependencies** — just open `index.html`

Question items come from the weekly quizzes and answer keys distributed in the
*Introduction to Generative AI* course and are used for non-commercial study only.

</details>

---

## 시작하게 된 계기

「생성형 인공지능 입문」은 주차마다 퀴즈가 나오고, 중간·기말고사도 그 퀴즈 범위에서
크게 벗어나지 않는 과목이었습니다. 문제는 **시험 직전에 PDF와 해설지를 스크롤하며
훑는 방식이 전혀 효율적이지 않았다는 것**입니다. 이미 아는 문제를 계속 다시 읽게 되고,
정작 반복해서 틀리는 문제는 따로 관리되지 않았습니다.

따라서 필요한 것은 요약 자료가 아니라 **틀린 문항만 선별해 반복 출제하는 구조**였고,
이 학습기의 설계는 전부 그 요구에서 출발했습니다.

- 문제를 풀면 **틀린 문항이 자동으로 오답 노트에 쌓이고**,
- 나중에 그 문제를 맞히면 **오답 노트에서 알아서 빠집니다.**
- 시험 직전에는 `오답 노트만 다시 풀기`만 반복하면 남은 취약 문항이 정리됩니다.

여기에 더해, 기출을 그대로 외워버리는 것을 막기 위해 **같은 개념을 다른 각도에서
묻는 변형 문제 130문항**을 따로 만들어 두 번째 은행으로 두었습니다.
기본 문제은행이 "기억나는가"를 묻는다면, 변형 문제은행은 "이해했는가"를 묻습니다.

---

## 주요 기능

### 두 개의 문제은행
- **기본 (85문항 · 1~15주차)** — 수업에서 나온 주차별 퀴즈와 기출 문제
- **변형 (130문항 · 1~7, 9~14주차)** — 같은 개념을 이해 중심으로 다시 묻는 심화 문제.
  보기 하나하나가 짧은 설명문이라, 보기를 읽는 것만으로도 개념 정리가 되도록 구성했습니다.
- 두 은행은 상단 **탭**으로 분리되어 있고, 오답 노트와 통계도 각각 따로 관리됩니다.

### 오답 노트 (핵심 기능)
- 응시 기록 전체를 훑어 **문항별 "가장 최근 정오"** 를 계산합니다.
- 마지막에 틀린 문항만 오답 노트에 남고, **나중에 맞히면 자동으로 빠집니다.**
- `오답 노트만 다시 풀기` / `변형 오답만 다시 풀기` 버튼으로 즉시 재응시할 수 있습니다.
- 결과 화면의 `틀린 것만 다시` 버튼은 **방금 세트에서 틀린 문항만** 골라 바로 재도전합니다.

### 출제 옵션
- **문항 순서 섞기** (기본 ON) — 순서를 외워버리는 것을 방지합니다.
- **보기 순서 섞기** (기본 OFF) — 정답 위치를 외워버리는 것을 방지합니다.
- 주차별 응시 / `전체 한 번에` 응시 모두 지원합니다.

### 기록과 통계
- 응시 횟수 · **누적 정답률** · 현재 오답 노트 문항 수를 항상 상단에 표시합니다.
- `기록 열람` 탭에서 지난 응시를 접었다 펼 수 있고, 각 응시의 **틀린 문항 카드**
  (문항 / 내가 고른 답 / 정답)를 그대로 다시 볼 수 있습니다.
- 점수에 따라 색이 달라집니다 — 80% 이상 민트, 50% 이상 노랑, 그 미만 빨강.
- 모든 기록은 **내 브라우저 안에만** 저장됩니다 (`localStorage`). 서버로 나가는 데이터가 없습니다.

---

## 문제 구성

| 주차 | 주제 | 기본 | 변형 |
|:--:|---|:--:|:--:|
| 1 | 생성형 AI 개요 · LLM과 ChatGPT | 5 | 10 |
| 2 | RNN · LSTM · seq2seq와 어텐션 | 5 | 10 |
| 3 | 신경망 기초 · 활성화 함수 · 최적화 | 5 | 10 |
| 4 | 트랜스포머와 Self-Attention | 5 | 10 |
| 5 | ViT(Vision Transformer)와 U-Net | 5 | 10 |
| 6 | 사전학습 · 전이학습 · 미세조정 · 휴먼 피드백 학습 | 5 | 10 |
| 7 | GAN — 적대적 학습 · 잠재공간 · 모드 붕괴 | 5 | 10 |
| 8 | ★ **중간고사 대비** | 10 | — |
| 9 | 스타일 전이 · CycleGAN · 성능 평가지표 | 5 | 10 |
| 10 | 인코더-디코더 · 차원 축소와 특징 표현 | 5 | 10 |
| 11 | 디퓨전 모델 · DALL·E | 5 | 10 |
| 12 | CLIP과 DALL·E 2 | 5 | 10 |
| 13 | 강화학습 · Decision Transformer | 5 | 10 |
| 14 | 자율주행 — BEV · 센서 퓨전 · ChauffeurNet | 5 | 10 |
| 15 | ★ **기말고사 대비** | 10 | — |
| | **합계** | **85** | **130** |

**총 215문항 · 전 문항 4지선다**

---

## 사용 방법

### 온라인 (권장)
아래 링크로 접속하면 끝입니다. 설치도, 로그인도 없습니다.

**https://evan-cloud4453.github.io/generative-ai-quiz/**

### 로컬에서 실행

```bash
git clone https://github.com/evan-cloud4453/generative-ai-quiz.git
```

클론한 폴더의 `index.html`을 브라우저로 열면 됩니다. 서버가 필요 없습니다.

### 권장 학습 순서

1. **처음에는 주차별로** — `시작` 탭에서 배운 주차를 하나씩 풀어 오답 노트를 채웁니다.
2. **그다음에는 오답 노트만** — 시험 전날까지 `오답 노트만 다시 풀기`를 반복합니다.
   오답 노트 문항 수가 0이 되면 해당 범위를 한 차례 정리한 것입니다.
3. **마지막에 변형 문제로 점검** — 기출을 외운 것인지 개념을 이해한 것인지 확인합니다.

> 💡 **변형 문제를 풀 때는 `보기 순서 섞기`를 켜는 것을 권합니다.**
> 변형 문항은 정답 보기가 특정 위치에 몰려 있어서, 섞지 않으면 내용을 읽지 않고도
> 위치만으로 정답을 선택할 수 있습니다.

> 기록은 브라우저별·기기별로 따로 저장됩니다. PC에서 쌓은 오답 노트는 휴대폰에
> 따라오지 않습니다. 시크릿 모드에서 풀면 창을 닫는 순간 기록이 사라집니다.

---

## 기술 구성

| 항목 | 내용 |
|---|---|
| 구조 | **단일 HTML 파일** (`index.html`, 약 875줄) — 마크업 · 스타일 · 로직 · 문항 215개가 모두 인라인 |
| 프레임워크 | 없음. **Vanilla JavaScript** (빌드 · 번들러 · 패키지 매니저 · 백엔드 전부 불필요) |
| 스타일 | CSS 변수 기반 다크 테마(민트 액센트 `#5ad1a8`), CSS Grid 주차 선택, 시스템 폰트 스택 |
| 저장 | 브라우저 `localStorage` (키: `genai_quiz_v1`) — 응시 이력 전체를 누적 저장 |
| 오답 판정 | 전체 응시 이력을 훑어 문항 id별 **최근 정오 상태**를 재계산하는 방식 |
| 셔플 | Fisher-Yates 셔플. 보기 셔플은 원본 인덱스 매핑을 따로 유지해 정답 판정이 어긋나지 않게 처리 |
| 배포 | GitHub Pages (`main` 브랜치 루트) |

```
generative-ai-quiz/
└── index.html      # 앱 전체 (UI + 로직 + 기본 85문항 + 변형 130문항)
```

단일 파일 구조는 의도한 선택입니다. 시험 기간에 실행 환경을 구성하는 데 시간을 쓰지 않아야
했고, 링크만으로 어느 기기에서든 즉시 열려야 했기 때문입니다.

---

## 문항 데이터 구조

문항은 두 개의 배열로 관리되고, 로드 시점에 `id`(예: `w3q2`, `v11q7`)가 자동으로 부여됩니다.

```js
// 기본 문제은행 — w: 주차, q: 문항, c: 보기 배열, a: 정답 인덱스(0-based)
const BANK = [
  { w:1, q:"ChatGPT는 OpenAI에서 개발한 초거대 언어모델 _____ 입니다.",
    c:["CNN","DALL-E","Large Language Model(LLM)","GAN"], a:2 },
  // ...
];

// 변형 문제은행 — 구조는 동일, id 접두사만 "v"
const BANK_V = [
  { w:1, q:"GPT 모델은 트랜스포머의 인코더와 디코더 중 어떤 구조를 주로 사용하며, ... [1주차]",
    c:[ /* 설명형 보기 4개 */ ], a:1 },
  // ...
];
```

- 문항을 추가하려면 해당 배열에 객체를 하나 넣으면 됩니다. id는 자동으로 붙습니다.
- 새 주차를 추가하면 주차 선택 그리드에 **자동으로 칩이 생깁니다** (`weeks`를 데이터에서 유도).
- 보기 개수는 4개로 고정되어 있지 않아, 5지선다나 O/X로도 수정 없이 확장됩니다.

---

## 변형 문제는 어떻게 만들었나

변형 문제은행 130문항은 **기본 문항과 강의 내용을 근거로, 생성형 AI를 활용해 변형·심화한
것**입니다. 목표는 기출 문장을 외운 상태와 개념을 이해한 상태를 구분해 내는 것이었습니다.

그래서 변형 문항은 정답 하나만 구별되는 형태가 아니라, **네 개의 보기가 모두 그럴듯한 설명문**이
되도록 만들었습니다. 예를 들어 "VAE와 GAN의 차이"를 물을 때 오답 보기에도 실제로 존재하는
개념(적대적 학습, 확률 분포 근사, 노이즈 제거)을 배치해, 개념을 혼동하고 있는 경우
반드시 오답을 선택하도록 구성했습니다.

> ⚠️ 변형 문항은 생성형 AI로 만든 학습 보조 자료입니다. 표현이나 세부 사실에 오류가
> 있을 수 있으니, 최종적인 근거는 반드시 강의 자료와 수업 내용을 따라 주세요.
> 기본 문제은행 중에도 해설지 자체가 모호했던 문항 하나에는 본문에 주석을 달아 두었습니다.

---

## 저작권 및 이용 안내

- **문항 출처 : K-MOOC 「생성형 인공지능 입문」(2026학년도 1학기) 강의의 주차별 퀴즈·기출
  문제와 정답 해설지.** 해당 문항의 저작권은 강의 제작자에게 있으며, 이 저장소는
  수강생의 복습·시험 대비라는 **비영리 교육 목적**으로만 이용합니다.
- 변형 문제 130문항은 위 자료를 바탕으로 생성형 AI를 활용해 작성한 2차 학습 자료입니다.
- 문의나 삭제 요청은 이 저장소의 Issues로 남겨 주시면 신속히 처리하겠습니다.

---

## 앞으로 개선하면 좋을 것들

- **변형 문제은행의 정답 위치 편중** — 130문항 중 상당수가 정답이 같은 번호에 몰려 있습니다.
  변형 탭에서는 `보기 순서 섞기`를 기본 ON으로 두거나, 데이터 자체의 정답 위치를
  고르게 재배치하는 편이 좋습니다.
- `전체 한 번에` 버튼의 라벨이 "전체 14주차"로 되어 있지만 실제로는 중간·기말 세트를 포함한
  15개 주차 전부가 출제됩니다. 라벨 정리 필요.
- 문항별 **해설 필드 추가** — 현재는 오답일 때 정답 보기만 보여 줍니다.
- 주차별 정답률을 모아 **취약 주차를 자동으로 짚어 주는 통계**
- 오답 노트를 기기 간에 옮길 수 있는 **JSON 내보내기 / 가져오기**
