# fithub server

fithub2 서버 리포지토리 입니다

| 역할     | 이름  |
|--------|-----|
| Server | 최용욱 |
| Server | 김대휘 |

# Stack

SpringBoot, JPA, MySQL, Elastic Beanstalk, JWT, SpringSecurity, Spring batch, AWS, Redis

## 협업 전략

### 커밋 , 머지 전략

1. 가장먼저 이슈를 만든다.
2. (jira가 있다면) jira에서 브랜치를 만든다.
    1. 이슈에 jira에서 만든 브랜치를 연결한다.
    2. 로컬에서 반드시 "develop" 브랜치에서 새 브랜치를 만든다.
        1. 주의 : 반드시 develop으로 이동해서 git pull origin develp을 한다.
    3. 해당 브랜치로 원격에 푸시 후 PR 급한게 아니라면 코드 리뷰 후 merge
3. (jira가 없다면) 이슈에서 브랜치를 만든다.
    1. 똑같이 로컬에서 "develop" 브랜치에서 새 브랜치를 만든다.
        1. 위와 동일하게 develop에서 브랜치 만들기 전에 git pull origin develop
    2. 해당 브랜치로 원격에 푸시 후 PR 급한게 아니라면 코드 리뷰 후 merge

### CI/CD 전략

develop : 개발 서버 배포용, 이 브랜치로 merge 시 github action을 통해
개발 인프라 서버로 자동 배포
이 브랜치로의 merge는 기능 개발 브랜치 5종류에서 merge

main : 실제 서비스를 위한 배포용, 이 브랜치로 merge 시 github action을 통해
릴리즈 인프라 서버로 자동 배포
이 브랜치로의 merge는 develop에서 merge

### 브랜치 전략

| 브랜치 이름                           | 사용 목적                                     |
|----------------------------------|-------------------------------------------|
| main 👑                          | 초기 세팅, 릴리즈 용도로 사용                         |
| develop 🏗️                      | 개발용 배포 서버 대상 브랜치                          |
| feature/N ✨                      | 새로운 기능 개발을 하기 위한 브랜치, N은 이슈 번호            |
| refactor/N :recycle:             | 이미 있는 기능에 대한 수정을 위한 브랜치, N은 이슈 번호         |
| bug/N      :bug:                 | 버그를 고치기 위한 브랜치, N은 이슈 번호                  |
| docs/N     :memo:                | swagger 명세, 혹은 주석 등의 작업만 하는 브랜치, N은 이슈 번호 |
| ci/N       :construction_worker: | 배포 관련 작업을 위한 브랜치, N은 이슈 번호                |
| jira 브랜치 명 + 위의 5개 규칙       🪄   | jira 사용시 jira와 연동을 위한 브랜치, N은 이슈 번호       |

### 커밋컨벤션

| 태그이름                       | 내용                                          |
|----------------------------|---------------------------------------------|
| :sparkles: `Feat`          | 새로운 기능을 추가할 경우                              |
| :bug:`Fix `                | 버그를 고친 경우                                   |
| :bug:`!HOTFIX`             | 급하게 치명적인 버그를 고쳐야하는 경우                       |
| `Style`                    | 코드 포맷 변경, 세미 콜론 누락, 코드 수정이 없는 경우            |
| :recycle:`Refactor`        | 코드 리팩토링                                     |
| :memo:`Comment`            | 필요한 주석 추가 및 변경                              |
| :memo:`Docs`	              | 문서, Swagger 를 수정한 경우                        |
| :hammer:`Test`             | 테스트 추가, 테스트 리팩토링(프로덕션 코드 변경 X)              |
| `Chore`	                   | 빌드 태스트 업데이트, 패키지 매니저를 설정하는 경우(프로덕션 코드 변경 X) |
| `Rename`                   | 파일 혹은 폴더명을 수정하거나 옮기는 작업만인 경우                |
| `Remove`                   | 파일을 삭제하는 작업만 수행한 경우                         |
| :construction_worker: `Ci` | 배포 방식 수정 및 새로 추가                            |
| :green_heart: `Ci`         | 기존 배포 스크립트 수정                               |
