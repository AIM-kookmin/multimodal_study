# 멀티모달 논문 스터디 — 8주 커리큘럼

**논문 1편을 2주씩, 총 4편을 8주 동안 공부합니다.** VQA → Transformer → ViT → CLIP 순서로 문제 정의, attention, 이미지 토큰화, 이미지–텍스트 대조학습을 익힙니다.

각자 **2주마다 논문 리딩 자료를 Markdown으로 정리하고, 본인 브랜치에 commit·push한 뒤 `main`을 대상으로 Pull Request(PR)를 제출**합니다. 8주 동안 개인별 정리 문서 4개와 PR 4개를 남깁니다.

- [논문별 학습 가이드](docs/study-guide.md): 핵심 개념, 읽을 부분, 확인 질문, 계산·실습 해설
- [논문 정리 템플릿](templates/paper-review-template.md): 각 논문을 읽으며 복사해서 작성할 양식
- [PR 템플릿](.github/pull_request_template.md): 제출 요약과 리뷰 요청 항목

## 1. 학습 목표와 준비

학습을 마치면 처음 보는 논문에서도 **입력 → 특징 추출 → 정보 결합 → 출력 → 학습 목표 → 실험 근거**를 따라가며 설명할 수 있어야 합니다.

시작 전에는 행렬 곱, 신경망 학습, softmax, 분류 손실, CNN과 텍스트 임베딩의 기본 역할을 점검하세요. 필요한 용어는 [학습 가이드](docs/study-guide.md)에 정리되어 있습니다. 실습은 작은 계산과 Python 예제로 진행할 수 있으며, 대규모 모델 학습이나 GPU 사용은 필수가 아닙니다.

## 2. 읽을 논문

| 기간 | 논문 | 발표 | 연결할 핵심 질문 |
| --- | --- | --- | --- |
| 1–2주차 | [VQA: Visual Question Answering](https://openaccess.thecvf.com/content_iccv_2015/html/Antol_VQA_Visual_Question_ICCV_2015_paper.html) | ICCV 2015 | 이미지와 질문을 어떻게 함께 사용해 답을 구하는가? |
| 3–4주차 | [Attention Is All You Need](https://papers.neurips.cc/paper_files/paper/2017/hash/3f5ee243547dee91fbd053c1c4a845aa-Abstract.html) | NIPS 2017 | 토큰들이 서로 어떤 정보를 참조하는가? |
| 5–6주차 | [An Image Is Worth 16x16 Words: Transformers for Image Recognition at Scale](https://arxiv.org/abs/2010.11929) | ICLR 2021 | 이미지를 Transformer가 처리할 토큰으로 어떻게 바꾸는가? |
| 7–8주차 | [Learning Transferable Visual Models From Natural Language Supervision (CLIP)](https://proceedings.mlr.press/v139/radford21a.html) | ICML 2021 | 이미지와 텍스트 표현을 어떻게 대응시키는가? |

기존 사전지식 3편에 CLIP을 추가해 8주를 구성했습니다. Transformer의 학회 발표 연도는 2017년입니다.

## 3. 주차별 커리큘럼

| 주차 | 논문·주제 | 읽을 범위와 활동 | 주차별 결과물 |
| --- | --- | --- | --- |
| **1주차** | VQA: 문제와 데이터 | Abstract·Introduction, Sections 3–4. 문제 정의, 질문·답변 수집, 평가 기준, 데이터 편향 이해 | 템플릿 복사, 문제·입출력 정리 초안, 직접 만든 시각 질문 3개 |
| **2주차** | VQA: 모델과 baseline | Section 5와 Table 2. CNN·질문 표현, 특징 연결·원소별 곱, Question-only와 Q+I 비교 | 모델 흐름도, baseline 비교, 한계와 토론 질문을 보완해 **PR #1 제출** |
| **3주차** | Transformer: 구조와 attention | Sections 3.1–3.2, Figures 1–2. Q·K·V, self-/cross-attention, multi-head attention | 구조 정리 초안, attention 수식 해석, 입출력 차원 표 |
| **4주차** | Transformer: 학습과 실험 | Sections 3.3–3.5, 4, 6.1–6.2. FFN·위치 정보·mask, 작은 attention 실습, 실험 비교 조건 해석 | 실습 결과 또는 손계산, 실험 근거와 한계를 보완해 **PR #2 제출** |
| **5주차** | ViT: 이미지 토큰화 | Figure 1, Sections 3.1–3.2. Patch embedding, class token, 위치 임베딩, encoder | 구조 정리 초안, 이미지부터 토큰까지 shape 표시, 패치 수 계산 |
| **6주차** | ViT: 데이터 규모와 비용 | Sections 4.1–4.4. 사전학습 데이터·모델 규모와 성능, CNN 비교 조건, 패치 크기별 계산 비용 | 실험 표·그림 해석, 패치 크기 비교, Transformer와의 연결을 보완해 **PR #3 제출** |
| **7주차** | CLIP: 두 encoder와 대조학습 | Section 2, Figures 1·3. 이미지·텍스트 encoder, 정규화, 배치 내 양성·음성 쌍, 양방향 손실 | 구조 정리 초안, `N × N` 유사도 표, 작은 배치의 정답·손실 계산 |
| **8주차** | CLIP: zero-shot과 전체 연결 | Sections 3.1–3.2, 6. Zero-shot 분류, 프롬프트, linear probe, 한계와 네 논문 비교 | 평가 절차·실험 근거, 네 논문의 입력·출력·학습 목표 비교표를 포함해 **PR #4 제출** |

**PR #1~#4는 개인별 제출 순서입니다. GitHub에서 실제로 배정되는 PR 번호와는 다릅니다.** 읽을 범위는 핵심 안내이며, 실험 해석에 필요한 데이터·학습 설정은 해당 절과 부록을 추가로 확인하세요.

## 4. 스터디 운영 방식

### 논문마다 반복하는 2주 과정

| 시점 | 개인 학습 | 모임·리뷰 |
| --- | --- | --- |
| 첫째 주: 1·3·5·7주차 | 최신 `main`에서 해당 논문용 개인 브랜치를 만들고, 템플릿에 문제·배경·구조 초안 작성 | 핵심 개념을 서로 설명하고 이해되지 않는 부분 공유 |
| 둘째 주: 2·4·6·8주차 | 실험·한계·직접 계산한 내용을 보완하고, **모임 전까지 Markdown을 commit·push한 뒤 PR 제출** | PR을 보며 논문 핵심과 실험 근거 토론 |
| 둘째 주 모임 후 | 리뷰 의견을 반영해 **같은 브랜치에 추가 commit·push** | 운영자 또는 지정 리뷰어가 확인 후 `main`에 merge |

제출일의 실제 날짜와 모임 시각은 운영자가 시작 전에 공지합니다. 첫째 주 초안은 본인 브랜치에 수시로 commit할 수 있습니다. 정식 PR 제출 주기는 2주입니다.

### 정리와 리뷰 기준

- 각자 템플릿을 사용해 **자신의 설명으로** 정리합니다. 논문 내용, 본인의 해석, 아직 확인하지 못한 추측을 구분하세요.
- 모델 흐름도, 핵심 수식·차원 설명, 실험 표 또는 그림의 해석, 한계, 토론 질문을 포함합니다.
- 직접 해본 계산이나 실습을 하나 이상 기록합니다. 논문 전체 재현 대신 가이드의 작은 예제를 사용해도 됩니다.
- 논문에 해당하지 않는 항목은 `해당 없음`과 이유를 적습니다. 모르는 부분은 확인한 범위와 질문을 남깁니다.
- 매 회차 다른 참여자의 PR 하나 이상에 구체적인 질문이나 피드백을 남기는 것을 권장합니다. 오탈자뿐 아니라 수식의 의미, 비교 조건, 주장과 근거를 함께 살펴보세요.
- 한 PR에는 해당 논문의 본인 정리 파일과 필요한 자료만 포함합니다. 제출 완료는 PR 생성, 학습 마무리는 리뷰 반영과 merge로 구분합니다.

## 5. 파일과 브랜치 규칙

아래 `notes/` 하위는 학생들이 제출하면서 생성할 구조의 예시입니다. `your-github-id`는 본인의 GitHub 아이디로 바꾸세요.

```text
.
├── README.md
├── docs/
│   └── study-guide.md
├── templates/
│   └── paper-review-template.md
├── .github/
│   └── pull_request_template.md
└── notes/
    └── your-github-id/
        ├── 01-vqa.md
        ├── 02-transformer.md
        ├── 03-vit.md
        ├── 04-clip.md
        └── assets/                 # 이미지·실습 파일이 있으면 생성
            └── 01-vqa/
                └── model.png
```

| 제출 주차 | 논문 ID | 정리 파일 | 개인 브랜치 |
| --- | --- | --- | --- |
| 2주차 | `01-vqa` | `notes/your-github-id/01-vqa.md` | `study/your-github-id/01-vqa` |
| 4주차 | `02-transformer` | `notes/your-github-id/02-transformer.md` | `study/your-github-id/02-transformer` |
| 6주차 | `03-vit` | `notes/your-github-id/03-vit.md` | `study/your-github-id/03-vit` |
| 8주차 | `04-clip` | `notes/your-github-id/04-clip.md` | `study/your-github-id/04-clip` |

**본인 브랜치는 학생·논문 조합마다 하나씩 만듭니다.** 다음 논문은 최신 `main`에서 새 브랜치로 시작하므로 이전 PR이 리뷰 중이어도 변경 사항이 섞이지 않습니다. `main`에는 직접 push하지 않고 PR로 반영합니다.

이미지를 넣는다면 논문별 `assets/논문-ID/`에 저장하고 정리 문서에서 `![모델 구조](assets/01-vqa/model.png)`처럼 상대 경로로 연결하세요. 가져온 그림·수치에는 원문 링크와 그림·표 번호를 표시합니다.

## 6. 제출 절차: 브랜치 → commit → push → PR

### 시작 전 저장소 준비

운영자는 GitHub 스터디 저장소를 준비하고, 이 문서와 템플릿을 기본 브랜치인 `main`에 올린 뒤 참여자에게 쓰기 권한을 부여합니다. 아래 절차는 **공용 저장소에 본인 브랜치를 push하는 방식**입니다. 참여자는 Git과 GitHub 인증을 준비하고 저장소 주소를 전달받습니다.

처음 한 번 저장소를 복제합니다. `OWNER/REPOSITORY`를 운영자가 안내한 실제 경로로 바꾸세요.

```bash
git clone https://github.com/OWNER/REPOSITORY.git multimodal-study
cd multimodal-study
```

이후 명령은 복제한 저장소의 루트 폴더에서 실행합니다.

### 1단계. 논문별 개인 브랜치와 정리 파일 만들기

아래는 첫 번째 논문 예시입니다. `your-github-id`를 본인 아이디로 바꾸세요. 다음 논문을 시작할 때는 `paper_id`를 위 표의 값으로 바꾸고 같은 절차를 반복합니다. 새 터미널에서는 두 변수를 다시 설정하세요.

```bash
student_id="your-github-id"
paper_id="01-vqa"

git switch main
git pull --ff-only origin main
git switch -c "study/$student_id/$paper_id"
mkdir -p "notes/$student_id"
cp templates/paper-review-template.md "notes/$student_id/$paper_id.md"
```

이 단계는 **해당 논문을 처음 시작할 때 한 번만** 실행합니다. 이미 작성 중인 브랜치라면 `git switch "study/$student_id/$paper_id"`로 돌아가 기존 파일을 이어서 작성하세요. 템플릿을 다시 복사하면 작성한 내용을 덮어쓰므로 반복하지 않습니다.

### 2단계. Markdown 작성 후 commit·push

복사한 Markdown을 편집하고 미리보기에서 수식, 표, 이미지 경로를 확인합니다. 아래 명령으로 이번 정리 파일만 stage하고 변경 내용을 확인하세요.

```bash
git status --short
git add "notes/$student_id/$paper_id.md"
git diff --cached
git commit -m "docs: add $paper_id review by $student_id"
git push -u origin "study/$student_id/$paper_id"
```

이번 논문에 첨부 파일이 있다면 commit **전에** `git add "notes/$student_id/assets/$paper_id/"`도 실행하세요. `git diff --cached`에서 본인 제출 자료만 포함되어 있는지 확인합니다.

### 3단계. GitHub에서 `main`으로 PR 생성

1. GitHub 저장소에서 **Pull requests → New pull request**를 엽니다.
2. **base를 `main`**, **compare를 `study/본인아이디/논문-ID`**로 선택합니다.
3. 변경 파일을 확인하고 제목과 본문을 작성합니다.
4. 제목은 `[01–02주차][VQA] 본인아이디 논문 정리`처럼 주차·논문·작성자를 표시합니다.
5. 자동으로 표시되는 PR 템플릿에 정리 파일 경로, 핵심 내용, 리뷰받고 싶은 질문을 작성하고 PR을 생성합니다.

주차·논문 표기는 각각 `[01–02주차][VQA]`, `[03–04주차][Transformer]`, `[05–06주차][ViT]`, `[07–08주차][CLIP]`을 사용합니다. Base/compare 설정은 [GitHub의 PR 생성 안내](https://docs.github.com/en/pull-requests/how-tos/create-pull-requests/creating-a-pull-request)를 참고하세요.

PR 템플릿은 기본 브랜치에 등록되어 있어야 자동으로 표시됩니다. 표시되지 않으면 [PR 템플릿 파일](.github/pull_request_template.md)의 내용을 직접 복사하세요. ([GitHub 템플릿 안내](https://docs.github.com/en/communities/using-templates-to-encourage-useful-issues-and-pull-requests/creating-a-pull-request-template-for-your-repository))

### 4단계. 리뷰 반영

리뷰받은 파일을 **같은 개인 브랜치에서** 수정한 후 추가 commit·push합니다. 이미 열린 PR에 변경 사항이 반영되므로 새 PR을 만들 필요가 없습니다.

```bash
git switch "study/$student_id/$paper_id"
# 정리 문서를 수정한 뒤 실행
git add "notes/$student_id/$paper_id.md"
git diff --cached
git commit -m "docs: address feedback for $paper_id by $student_id"
git push
```

첨부 파일을 수정했다면 해당 경로도 stage합니다. 운영자 또는 지정 리뷰어가 확인 후 merge하며, 다음 논문은 1단계에서 최신 `main`을 받아 새 브랜치로 시작합니다. 브랜치를 이동하기 전 작성 중인 변경 사항은 해당 브랜치에 commit해 두세요.

## 7. 제출 전 체크리스트

- [ ] 이번 주차의 논문을 템플릿에 맞춰 정리했다.
- [ ] 문제 정의, 모델 구조, 학습 목표, 실험 근거, 한계를 내 말로 설명했다.
- [ ] 수식·차원·작은 실습 중 하나 이상을 직접 확인하고 결과를 기록했다.
- [ ] 인용한 자료의 링크와 그림·표 번호를 표시했다.
- [ ] 문서 미리보기에서 표, 수식, 이미지 경로를 확인했다.
- [ ] 본인 자료만 해당 개인 브랜치에 commit·push했다.
- [ ] PR의 base는 `main`, compare는 해당 논문의 본인 브랜치다.
- [ ] PR 본문에 핵심 내용과 리뷰 요청 질문을 적었다.

8주차에는 `04-clip.md`에 네 논문의 입력, 출력, 특징 처리 방식, 학습 목표를 비교하는 표를 추가해 전체 학습을 연결합니다.
