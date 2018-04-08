--- 
title: "git 정리" 
layout: post 
date: 2017-10-16 18:00 
tag: tips-and-tricks 
blog: true 
draft: false 
author: sphilee 
summary: "git 정리" 
permalink: git-cleanup 
---

### git 은 무엇인가?
* git은 프로그램 등의 소스 코드 관리를 위한 분산 버전 관리 시스템이다.

### git 의 장점은 무엇일까?
* Branch and Merge
* Distributed
* Small and Fast
* Staging Area
* Open source

### git add는 무엇인가?
* git add명령은 Untracked 상태이거나 Modified 상태인 파일을 Staged 상태로 바꾸는 명령어이다.

### git commit 은 어떻게 하는가?
* git은 프로그램 등의 소스 코드 관리를 위한 분산 버전 관리 시스템이다.

### git 은 무엇인가?
```
git commit -m 'my commit message'
```
### git commit 은 얼마큼 자주 하는게 좋은가?
* 변경 사항에 따라 로직을 이해할 수 있는 수준의 단일 커밋 단위로 쪼개야 한다.

### commit message는 왜 작성하고 어떻게 작성하는게 좋을까?
* commit 메세지가 잘 작성해야 commit 메세지를 확인 하는 것만으로도 프로젝트의 히스토리를 파악 할 수 있다.
* 좋은 커밋 메시지는 패치에 관한 다음 세 가지 질문에 답을 할 수 있어야 한다
1. 왜 이 코드가 필요한가?
2. 어떻게 이슈를 해결했는가?
3. 패치가 어떤 영향을 만드는가?

### git은 github과 어떻게 다른가 ?
* git은 git 리포지토리라고 불리는 데이터 저장소에 소스 코드 등을 넣어서 이용하는것으로, 이러한 git 리포지토리를 인터넷상에서 제공하는 서비스(호스팅 서비스)가 gitHub이다. gitHub에서 공개되는 소스 코드는 모두 git으로 관리된다.

### git branch 는 왜 존재할까? 어떻게 생성하나?
* 개발을 하다 보면 코드를 여러 개로 복사해야 하는 일이 자주 생긴다. 코드를 통째로 복사하고 나서 원래 코드와는 상관없이 독립적으로 개발을 진행할 수 있는데, 이렇게 독립적으로 개발하는 것이 브랜치다.

### git branch는 언제 만드는 것이 좋을까?
* 개발을 하다 새로운 이슈를 처리해야 할때 주로 생성한다.

### git push 는 무엇인가?
* 리모트 저장소에 데이터를 추가할때 쓴다.

### git merge 는 언제 하는 것인가?
* 두개 이상의 개발 히스토리를 합치고 싶을때 사용한다.