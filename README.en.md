# programmers-badge-maker

**Programmers-badge-maker** provides a programmers stats badge that you can use to decorate your GitHub profile README.

simple design badge👇

![](https://gaoooon.github.io/programmers-badge-maker/result/badge.svg)

Inspired by https://github.com/tomy8964/Programmers_Badge_Generator

## How to use

### Prerequisites

There must be a coding test repository connected to [Baekjoon Hub](https://chromewebstore.google.com/detail/%EB%B0%B1%EC%A4%80%ED%97%88%EB%B8%8Cbaekjoonhub/ccammcjdkpgjmcpijpahlehmapgmphmk?hl=ko&pli=1).

### step 1

fork this repository

### step 2

register secret

- GH_PAT - your gitHub personal access token
- GIT_EMAIL - your github email
- GIT_NAME - your github name
- PROGRAMMERS_EMAIL - your programmers email
- PROGRAMMERS_PASSWORD - your programmers password

#### how to get gitHub personal access token

a. click your github profile image <br>
b. click `Settings` button <br>
c. click `Developer settings` button <br>
d. click `Personal access tokens` button <br>
e. click `Tokens (classic)` button <br>
f. click `Generate new token` button <br>
g. click `Generate new token (classic)` button <br>
h. set Expiration to No expiration <br>
i. select repo scope and workflow scope <br>
j. click `Generate token`

### step 3

register github actions

a. click `Actions` <br>
b. click `I understand my workflows, go ahead and enable them` button

### step 4

hosting repository

a. click `Settings` button <br>
b. click `Pages` button <br>
c. set Branch to main <br>
d. click `save` button

### step 5

add below yml to your coding test repository

a. click `Actions` button <br>
b. click `set up a workflow yourself` <br>
c. ctrl + c & ctrl + v

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

### step 6

register secret

- GH_PAT - your gitHub personal access token

### step 7

solve programmers coding test

### step 8

add github readme

```
![](https://{your github name}.github.io/programmers-badge-maker/result/badge.svg)
```
