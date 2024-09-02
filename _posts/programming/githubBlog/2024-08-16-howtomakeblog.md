---
title: Chirpy 테마로 Github 블로그 생성
date: 2024-08-16 20:30:00 +0900
categories: [Programming, Github Blog]
tags: [notice]     # TAG names should always be lowercase
math: true
mermaid: true
pin: true
---

Jekyll 테마 중 Chirpy 테마를 이용하여 깃허브 블로그를 생성하였다. Chirpy 테마로 블로그 만들기를 검색해보면 많은 게시글이 나왔지만, 그 과정들을 따라가다보면 꼭 한 두가지씩은 막히는 방법이 있었다. 공식 문서에는 Chirpy Starter를 사용하는 방법과 fork 해오는 방법 두 가지가 나와있었는데, Starter를 이용해서 생성하면 커스터마이징 하기가 조금 귀찮아진다고 하여 fork 하는 방식을 선택하였다.

### Prerequisites

---

1. Ruby 설치 -> Mac OS 사용중이라 건너뛰려 했으나, 아래 2번 명령어를 실행하다가 다음과 같은 에러가 발생하였다. `You don't have write permissions for the /Library/Ruby/Gems/2.7.2 directory.` 그래서 구글링을 통해 brew를 통해 rbenv를 대신 설치해주었다. (homebrew는 기존에 설치한 상태)

2. Jekyll 설치: 터미널에 `gem install jekyll bundler` 입력

3. Node.js 설치: 터미널에 `brew install node` 입력

### Github Fork

---

1. 먼저 공식 가이드대로 [fork **Chirpy**](https://github.com/cotes2020/jekyll-theme-chirpy/fork) 사이트에서 fork를 해왔다. 이 때 레포지토리 이름을 `USERNAME.github.io` 로 지정하여 나의 깃허브 블로그로 생성하였다. 이후 나의 로컬 저장소로 복제하였다. (`git clone https://github.com/USERNAME/USERNAME.github.io`)

2. 터미널에 `tools/init.sh` 명령어를 입력하여 초기화 작업을 진행해주었다. 이 과정에서 필요없는 파일들이 삭제되고, 깃허브 관련 설정 파일들이 일부 수정되며 이 과정들에 대한 커밋을 생성한다.

3. 위의 커밋들은 레포지토리에서 숨기고 싶어서 해당 파일을 로컬에 가지고 있는 상태로 fork가 되어있는 원격 저장소를 삭제하였다. 그리고 `USERNAME.github.io` 레포지토리를 다시 생성했다. 로컬에 남아있는 폴더에서 .git 파일을 삭제한 후, 아래 과정을 통해 이 파일을 새로운 레포지토리에 푸시해주었다.
```bash
git init
git add .
git commit -m "first commit"
git remote add origin https://github.com/USERNAME/USERNAME.github.io.git
git branch -m main
git push -u origin main
```

### Deployment

레포지토리의 Settings - Pages 에서 Build and Deployment의 Source 설정을 **Github Actions**로 바꿔주었더니 자동 배포 설정까지 완료하였다. 앞으로는 로컬에서 글을 작성한 후 `git push origin main` 만 입력하면 자동으로 페이지가 수정된다.