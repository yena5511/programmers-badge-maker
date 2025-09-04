# programmers-badge-maker

**Programmers-badge-maker**는 프로그래머스 통계 뱃지를 제공하여 GitHub 프로필 README를 꾸밀 수 있도록 도와줍니다.

간단한 디자인의 뱃지 👇

![](https://gaoooon.github.io/programmers-badge-maker/result/badge.svg)

Inspired by https://github.com/tomy8964/Programmers_Badge_Generator

## 사용 방법

### 사전 준비

[Baekjoon Hub](https://chromewebstore.google.com/detail/%EB%B0%B1%EC%A4%80%ED%97%88%EB%B8%8Cbaekjoonhub/ccammcjdkpgjmcpijpahlehmapgmphmk?hl=ko&pli=1)와 연결된 코딩 테스트 저장소가 있어야 합니다.

### Step 1

이 레포지토리를 `fork` 합니다.

### Step 2

다음 GitHub Secrets를 등록합니다.

- `GH_PAT` - GitHub Personal Access Token
- `GIT_EMAIL` - GitHub 이메일
- `GIT_NAME` - GitHub 이름
- `PROGRAMMERS_EMAIL` - 프로그래머스 이메일
- `PROGRAMMERS_PASSWORD` - 프로그래머스 비밀번호

#### GitHub Personal Access Token 발급 방법

1. 프로필 사진 클릭
2. `Settings` 클릭
3. `Developer settings` 클릭
4. `Personal access tokens` 클릭
5. `Tokens (classic)` 클릭
6. `Generate new token` 클릭
7. `Generate new token (classic)` 클릭
8. Expiration → `No expiration` 설정
9. `repo` 및 `workflow` 권한 선택
10. `Generate token` 클릭

### Step 3

GitHub Actions를 활성화합니다.

1. `Actions` 탭 클릭
2. `I understand my workflows, go ahead and enable them` 버튼 클릭

### Step 4

GitHub Pages 설정을 통해 호스팅을 진행합니다.

1. `Settings` 클릭
2. `Pages` 클릭
3. Branch → `main` 으로 설정
4. `Save` 클릭

### Step 5

코딩 테스트 저장소에 아래 yml 파일을 추가합니다.

1. `Actions` 클릭
2. `set up a workflow yourself` 클릭
3. 아래 코드를 복사 & 붙여넣기

```yml
name: dispatch-workflow

on:
  push:
    branches:
      - main

jobs:
  dispatch:
    runs-on: ubuntu-latest
    steps:
      - name: Trigger repository dispatch
        uses: peter-evans/repository-dispatch@v1
        with:
          token: ${{ secrets.GH_PAT }}
          repository: {your github name}/programmers-badge-maker
          event-type: trigger-workflow
```

### Step 6

코딩 테스트 저장소에도 GitHub Secret을 등록합니다.

- GH_PAT - GitHub Personal Access Token

### Step 7

프로그래머스 문제를 풉니다.

### Step 8

GitHub 프로필 README에 아래 코드를 추가합니다.

```
![](https://{your github name}.github.io/programmers-badge-maker/result/badge.svg)
```
