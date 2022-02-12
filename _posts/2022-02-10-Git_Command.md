---
layout: single
title: 깃 명령어
subtitle: 
categories: [git]
tag: [git, github, command]
toc: true
toc_sticky: true
---

# Git 명령어 모음  

## Git 의 작업 흐름  

git 은 작업하는 파일을 버전별로 관리해주는 툴입니다. 현재 작업중인 디렉토리(Working Directory)에서 수정된 내용을 Staging Area 에 올려서 임시로 저장을 합니다. 임시로 저장하는 파일은 내가 원하는 파일만 올릴 수도 있고, 임시로 저장한 파일을 다시 원위치에 내릴 수도 있습니다(Unstaging). 임시 저장된 파일들을 최종적으로 저장을 하게되면 수정된 내역이 Local Repository에 저장이 됩니다. Local Repository에 저장이 될 때마다 일련번호(hash)가 생성이 되며, 이 일련번호(hash)를 이용해서 그 시점으로 되돌아 갈 수도 있습니다. git 을 이용해서 파일을 버전별로 관리를 하다가 컴퓨터에 이상이 생기게 되면 저장된 파일이 모두 날아가는 경우가 있기 때문에 이를 원격 저장소(Github)에 저장할 필요가 있습니다. Github는 클라우드 저장소라고 생각하면 됩니다. Github에 파일을 저장하게 되면 내 컴퓨터가 문제가 생기더라도 언제든지 저장한 파일을 다시 다운로드 받을 수가 있습니다. 이제 git 을 사용하기 위한 명령어들을 알아보겠습니다.  

![Git Work Flow](https://github.com/morisYu/morisyu.github.io/blob/master/assets/images/git/git_workflow.png?raw=true)  

## `git init`  

현재 폴더에서 "`.git`" 폴더를 새로 생성하여 초기화를 합니다. "`.git`" 폴더는 현재 폴더에서 수정되는 파일들에 대한 수정내역의 버전들을 관리해주게 됩니다. 따라서 작업을 하는 폴더에서 초기화를 진행해주어야 본인이 작업하는 파일들을 git 으로 관리를 할 수 있습니다. 만약 "`.git`" 폴더를 삭제하게 되면 더이상 현재 폴더는 git 으로 관리를 할 수가 없으며, 이전 기록들도 모두 사라지게 됩니다.  

> 형식

```
git init [-q | --quiet] [--bare] [--template=<template-directory>]
	  [--separate-git-dir <git-dir>] [--object-format=<format>]
	  [-b <branch-name> | --initial-branch=<branch-name>]
	  [--shared[=<permissions>]] [<directory>]
```  

> 사용방법

```
$ git init
```

<br>

##  `git config`  

git 으로 버전관리를 할 때 현재 버전은 누가 수정했는지에 대한 기록도 남게되는데, "사용자명" 과 "사용자이메일" 을 설정하게 되면 버전 관리 시 해당 사용자의 정보가 저장이 됩니다. --global 옵션을 하게되면 시스템 전체에서 해당 사용자의 정보가 저장이 됩니다.

> 형식

```
git config [<file-option>] [--type=<type>] [--fixed-value] [--show-origin] [--show-scope] [-z|--null] <name> [<value> [<value-pattern>]]

git config [<file-option>] [--show-origin] [--show-scope] [-z|--null] [--name-only] -l | --list

etc...
```  

> 사용방법

```java
/* git 으로 버전관리를 할 때 현재 버전은 누가 수정했는지에 대한 기록도 남게되는데, "사용자명" 과 "사용자이메일" 을 설정하게 되면 버전 관리 시 해당 사용자의 정보가 저장이 됩니다. --global 옵션을 하게되면 시스템 전체에서 해당 사용자의 정보가 저장이 됩니다. */

$ git config --global user.name [사용자명]
$ git config --global user.email [사용자이메일]

/* git 의 각종 설정사항을 확인할 수 있습니다. 여기서 "사용자명"과 "사용자이메일"이 제대로 설정되었는지도 확인이 가능합니다. */

$ git config --list

/* git 의 설정 중 autocrlf 라는 설정이 있는데, 운영체제에 따라 개행문자의 차이가 있어서 서로 다른 운영체제를 사용하여 같은 파일을 관리할 경우 오류가 발생할 수 있습니다. "core.autocrlf" 는 text file 을 git object database 에 checkin, checkout 할 때 어떻게 처리할지를 설정하는 변수입니다. 윈도우 운영체제인 경우 "true" 를 설정해서 text file을 object database 에 넣기전에 CRLF 를 LF 로 변경해주고, 맥이나 유닉스/리눅스의 경우 "input" 을 설정해서 LF를 line ending 으로 사용합니다. */

$ git config --global core.autocrlf [true/false/input]
```

<br>

## `git status`  

현재 파일들의 상태를 확인합니다. 새로 생성된 파일이 있는지, 임시 저장된(Staging) 파일이 수정이 되었는지, 삭제가 된 파일이 있는지 등 파일들의 상태를 확인할 수 있습니다. --short 옵션을 추가하게 되면 파일들의 상태를 간략하게 확인할 수가 있습니다.

> 형식

```
git status [<options>…​] [--] [<pathspec>…​]
```  

> 사용방법

```java
$ git status

/* 현재 파일의 상태를 간략하게 보여줌(A, M, ?? 가 파일 앞에 표시됨) */

$ git status --short 
```

<br>

## `.gitignore`  

"`.gitignore`" 라는 파일을 새로 생성하여 내용에 파일 또는 폴더를 저장해주면 git 은 "`.gitignore`" 파일에 저장된 파일 및 폴더를 관리하지 않게 됩니다. 여기에는 굳이 버전관리를 할 필요가 없는 파일이나 현재 작업하는 내용과 관련없는 파일 또는 폴더를 작성해주면 됩니다. 만약 다시 git 으로 관리를 하고자 한다면 "`.gitignore`" 파일에서 해당 파일 또는 폴더를 삭제해주면 됩니다.

> 형식

```
.gitignore 파일에 텍스트로 작성해서 추가
텍스트 작성은 echo 명령을 사용해도 되고, vi 에디터로 작성해도 됨
```  

> 사용방법

```java
$ echo *.log >> .gitignore  // 모든 이름의 log 형식 파일을 관리하지 않음
$ echo bin/ >> .gitignore  // bin 폴더와 그 하위 파일을 관리하지 않음
```

<br>

## `git add`  

수정된 파일을 Staging Area 에 추가합니다. "파일명.파일형식" 을 입력하면 해당 파일만 Staging Area 에 추가할 수가 있고, "." 또는 "-A" 을 입력하면 수정된 모든 파일을 추가할 수도 있습니다. -p 옵션을 사용하게 되면 수정된 내용을 직접 보여주어 해당 파일을 Staging Area 에 추가할지 말지를 결정할 수 있습니다.

> 형식

```java
git add [--verbose | -v] [--dry-run | -n] [--force | -f] [--interactive | -i] [--patch | -p]
	  [--edit | -e] [--[no-]all | --[no-]ignore-removal | [--update | -u]] [--sparse]
	  [--intent-to-add | -N] [--refresh] [--ignore-errors] [--ignore-missing] [--renormalize]
	  [--chmod=(+|-)x] [--pathspec-from-file=<file> [--pathspec-file-nul]]
	  [--] [<pathspec>…​]
```  

> 사용방법

```java
$ git add *.java  // java 형식의 모든 파일을 추가
$ git add .  // 현재 디렉토리에서 수정된 모든 파일을 추가
$ git add -A  // 작업중인 디렉토리에서 수정된 모든 파일을 추가
$ git add -p  // 수정된 파일을 하나씩 확인하면서 추가할지를 결정
```

<br>

## `git switch`  

브랜치를 변경합니다. 작업을 하다보면 현재 작업 중인 내용과 조금 다른 방향으로 내용을 수정해보고 싶을 때가 있습니다. 이 경우 원본파일에서 계속 수정을 하다보면 원래의 작업 방향으로 돌아오고 싶을 때 작업을 했던 내용을 다 삭제하고 원래대로 돌아가야 합니다. 하지만 어느 시점에서 가지를 뻗어(branch 생성) 원래의 작업방향과 별개로 다른 방향으로도 작업을 하게 되면 언제든지 원래의 작업 방향으로 돌아올 수 있고(branch 이동), 나중에 다른 방향으로 작업한 내용을 원래 파일에 결합(merge)을 하여 내용을 추가할 수도 있습니다. 따라서 원본 파일과 다른 작업을 하기 위해서는 새로운 branch 를 만들어주는 것이 파일 관리에 유리합니다. "git switch" 명령은 branch 를 변경할 수 있으며, 기존의 "git checkout" 명령에서 branch 변경과 파일 복원(restore) 의 기능을 명확히 구분하기 위해 새로 만들어졌습니다. 처음 "git init" 으로 초기화를 하게되면 "main" branch 에 위치하게 됩니다.

> 형식

```java
git switch [<options>] [--no-guess] <branch>
git switch [<options>] --detach [<start-point>]
git switch [<options>] (-c|-C) <new-branch> [<start-point>]
git switch [<options>] --orphan <new-branch>
```  
> 사용방법

```java
$ git switch newbranch  // 기존에 있는 newbranch 로 이동
$ git checkout newbranch  // 기존에 있는 newbranch 로 이동
$ git switch -c anotherbranch  // 기존에 없던 anotherbranch 를 생성하고 이동
$ git checkout -b anothrbranch  // 기존에 없던 anothrbranch 를 생성하고 이동
```
<br>

## `git branch`  

브랜치를 관리하는 명령어는 "git branch" 가 있습니다. 브랜치 목록 확인을 할 수도 있고, 브랜치의 생성/삭제/변경이 가능합니다.

> 형식

```java
git branch [--color[=<when>] | --no-color] [--show-current]
	[-v [--abbrev=<n> | --no-abbrev]]
	[--column[=<options>] | --no-column] [--sort=<key>]
	[--merged [<commit>]] [--no-merged [<commit>]]
	[--contains [<commit>]] [--no-contains [<commit>]]
	[--points-at <object>] [--format=<format>]
	[(-r | --remotes) | (-a | --all)]
	[--list] [<pattern>…​]

etc...
```  

> 사용방법

```java
$ git branch  // 로컬에 있는 브랜치를 확인
$ git branch new  // new 브랜치를 생성
$ git branch -d new  // new 브랜치를 삭제
$ git branch -a  // 모든 브랜치를 확인(로컬, 원격 브랜치)
$ git branch -m other  // 현재 브랜치를 other 브랜치로 이름 변경
```

<br>

## `git commit`  

수정이 되고 Staging Area 에 임시 저장된 파일들을 저장해줍니다. 수정된 내역들과 작성자 이름, 이메일 등의 내용이 기록되며, 각 commit 마다 일련번호(hash)를 생성하게 되어 버전 관리를 할 수 있게됩니다. commit 메세지를 작성할 때는 가능한 파일의 어떤 부분이 수정되었는지 알아보기 쉽게 작성해주는 것이 좋습니다.

> 형식

```java
git commit [-a | --interactive | --patch] [-s] [-v] [-u<mode>] [--amend]
	   [--dry-run] [(-c | -C | --squash) <commit> | --fixup [(amend|reword):]<commit>)]
	   [-F <file> | -m <msg>] [--reset-author] [--allow-empty]
	   [--allow-empty-message] [--no-verify] [-e] [--author=<author>]
	   [--date=<date>] [--cleanup=<mode>] [--[no-]status]
	   [-i | -o] [--pathspec-from-file=<file> [--pathspec-file-nul]]
	   [(--trailer <token>[(=|:)<value>])…​] [-S[<keyid>]]
	   [--] [<pathspec>…​] 
```  

> 사용방법

```java
$ git commit  // vi 에디터가 실행되어 commit 메세지 작성 가능(타이틀, 내용)
$ git commit -m "commit 메세지(타이틀)"  // commit 메세지 작성
$ git commit -am "commit 메세지(타이틀)"  // git add . 와 git commit -m 동시 진행 
```

<br>

## `git log`  

git log 는 commit 한 내역들을 순서대로 보여줍니다. 아무 옵션이 없을 때는 commit 의 일련번호(hash)와 작성자, 작성일자, commit message 를 보여줍니다. 브랜치가 많이 생성되고 병합이 있을 경우에는 시각적으로 보기 쉽도록 --graph 옵션을 적용하면 아스키코드로 표현한 그래프로 보여줍니다.

> 형식

```java
git log [<options>] [<revision-range>] [[--] <path>…​]
```  

> 사용방법

```java
$ git log  // 작성자, 작성일자, commit message 를 보여줌
$ git log --oneline  // commit 내역들을 한 줄로 간략히 보여줌(hash, commit mesage 만 표시)
$ git log --stat   // 수정된 내용을 통계정보로 보여줌
$ git log --name-status  // 수정된 파일의 목록과 추가/수정/삭제 여부를 보여줌
$ git log --graph  // 신규 브랜치와 병합 내역을 그래프로 보여줌
```

<br>

## `git reset`  

git reset 은 작업 중 이전 버전으로 다시 되돌아 갈 때 사용하는 명령입니다. 작업을 취소하고 싶은 commit 의 hash 를 입력하면 해당 commit 이 취소되면서 이 후의 기록은 삭제가 됩니다. 혼자 작업을 할 때에는 github에 있는 기록들도 강제로 push 를 해서 내 컴퓨터에서 reset 한 내용으로 덮어쓸 수 있지만, 협업을 하는 경우 reset 한 내용을 github 에 강제로 push 를 하게 되면 다른 사람이 github 에 올린 파일이 모두 삭제가 되기때문에 reset 은 권장하지 않습니다. 시험삼아 reset 을 해보는 경우에는 reset 하기 전 ".git" 폴더를 다른 곳에 백업을 한 후에 reset 을 해보고, 백업한 ".git" 폴더를 다시 작업 중인 폴더에 덮어쓰면 reset 을 한 작업이 다시 원래대로 돌아갑니다.

> 형식

```java
git reset [-q] [<tree-ish>] [--] <pathspec>…​
git reset [-q] [--pathspec-from-file=<file> [--pathspec-file-nul]] [<tree-ish>]
git reset (--patch | -p) [<tree-ish>] [--] [<pathspec>…​]
git reset [--soft | --mixed [-N] | --hard | --merge | --keep] [-q] [<commit>]
```  

> 사용방법

```java
$ git reset HEAD^  // 가장 최근의 commit 을 취소함
$ git reset --soft [hash 앞 6~7 글자]  // 변경 이력은 삭제되지만 변경 내용은 Staging Area에 남아있음
$ git reset --mixed [hash 앞 6~7 글자]  // 변경 이력은 삭제되지만 변경 내용은 Working Directory에 남아있음
$ git reset --hard [hash 앞 6~7 글자]  // 변경 이력과 변경 내용이 모두 삭제됨 
```

<br>

## `git revert`  

git reset 은 취소한 작업 이후의 기록이 모두 삭제가 되지만, git revert 는 취소하고자 하는 작업을 새로 commit 해주기 때문에 reset 에 비해 위험도가 낮아서 협업 중 작업을 취소할 때 사용이 되는 방법입니다. 이 경우 vi 에디터가 실행되어 commit message 를 작성을 해야하는데 자동으로 "Revert "취소한 작업의 커밋메세지"" 가 입력된 상태이기 때문에 ":wq" 를 입력해서 바로 commit message 를 저장할 수 있습니다.

> 형식

```java
git revert [--[no-]edit] [-n] [-m parent-number] [-s] [-S[<keyid>]] <commit>…​
git revert (--continue | --skip | --abort | --quit)
```  
> 사용방법

```java
$ git revert [hash 앞 6~7 글자]  // 커밋을 새로 생성함
$ git revert --no-commit [hash 앞 6~7 글자]  // 커밋을 진행하지 않음. 추가로 커밋 해줘야 함
```

<br>

## `git remote`  

컴퓨터에서 수정된 파일들을 모두 저장(commit)했으면 원격 저장소에도 업로드를 해야합니다. 가장 많이 사용되는 github 에 파일들을 업로드 하기 위해서는 github 에서 생성한 repository 의 주소가 있어야 합니다. 컴퓨터에서 원격 저장소에 파일을 업로드 할 때마다 긴 주소를 입력하기 번거롭기 때문에 "원격이름" 에 repository 의 주소를 저장해놓으면 파일을 업로드(push) 할 때마다 주소 대신 "원격이름" 을 사용해서 편하게 파일을 업로드 할 수 있습니다. 원격이름으로 "origin" 이 많이 사용되지만, repository 주소를 여러 개 사용하거나 다른 이름을 사용하고 싶으면 다른 이름을 사용할 수 있습니다.

> 형식

```java
git remote [-v | --verbose]
git remote add [-t <branch>] [-m <master>] [-f] [--[no-]tags] [--mirror=(fetch|push)] <name> <URL>
git remote rename <old> <new>
git remote remove <name>

etc...
```  

> 사용방법

```java
$ git remote  // github 의 원격저장소url 을 저장한 이름 목록을 보여줌
$ git remote -v  // 원격이름과 원격저장소url 목록을 보여줌
$ git remote [원격이름] [원격저장소url]  // 원격저장소url 을 원격이름에 저장
```

<br>

## `git push`  

commit 한 기록을 github 에 업로드 합니다. main 또는 master 브랜치가 아닌 다른 브랜치에서 작업 후 업로드를 하면 github 에도 해당 브랜치가 생성이 되며 github 사이트에서 main 또는 master 브랜치와 해당 브랜치를 병합(merge) 할 것인지를 물어봅니다. -u 옵션을 사용하게 되면 업로드를 할 원격이름과 브랜치를 기본으로 설정하여 다음부터 push를 할 때 원격이름과 브랜치를 추가로 입력할 필요가 없이 "`git push`" 만으로 업로드를 할 수 있습니다. 그리고 내 컴퓨터에서 수정된 내역들이 github 에 저장되어있는 내용과 충돌(conflict)이 발생하게 되면 충돌이 발생하는 부분을 해결 후 다시 업로드를 하거나 --force 옵션을 사용해서 내 컴퓨터의 수정 내역을 github 에 강제로 덮어쓸 수도 있습니다. 이 옵션은 협업을 할 때에는 다른 사람이 작업한 내용이 모두 삭제될 가능성이 있기 때문에 사용을 권장하지는 않습니다.

> 형식

```java
git push [--all | --mirror | --tags] [--follow-tags] [--atomic] [-n | --dry-run] [--receive-pack=<git-receive-pack>]
	   [--repo=<repository>] [-f | --force] [-d | --delete] [--prune] [-v | --verbose]
	   [-u | --set-upstream] [-o <string> | --push-option=<string>]
	   [--[no-]signed|--signed=(true|false|if-asked)]
	   [--force-with-lease[=<refname>[:<expect>]] [--force-if-includes]]
	   [--no-verify] [<repository> [<refspec>…​]] 
```  

> 사용방법

```java
$ git push [원격이름] [브랜치]
$ git push -u origin main  // 업로드할 원격이름과 브랜치를 origin 과 main 으로 기본 설정함
$ git push --force [원격이름] [브랜치] // 로컬의 현재 commit 상태를 강제로 원격 repository 에 덮어씀 
```

<br>

## `git clone`  

다른 사람들과 협업을 할 때 다른 사람들이 미리 작업해놓은 파일들을 github 에서 처음 다운로드 받아야 할 경우가 있습니다. 이 때 github 사이트에서 파일을 전부 다운로드 받을 수 있으나, 이 경우에는 ".git" 파일은 같이 다운로드가 되지 않아 이력 관리는 할 수가 없습니다. 하지만 터미널에서 "git clone" 명령을 사용해서 github 에 있는 파일을 다운로드 받으면 ".git" 파일까지 다운로드가 되어 그동안 수정되었던 기록까지 모두 관리를 할 수가 있습니다. github 에서 다운받을 파일이 있는 repository 의 주소를 입력하고 디렉토리명을 작성하면 현재 터미널이 실행되는 위치에서 새로운 디렉토리를 생성하고 그 안에 모든 파일을 다운로드 하게 됩니다. 디렉토리명을 작성하지 않으면 새로운 디렉토리는 생성하지 않고 현재 위치에 모든 파일을 다운로드 합니다.

> 형식

```java
git clone [--template=<template-directory>]
	  [-l] [-s] [--no-hardlinks] [-q] [-n] [--bare] [--mirror]
	  [-o <name>] [-b <name>] [-u <upload-pack>] [--reference <repository>]
	  [--dissociate] [--separate-git-dir <git-dir>]
	  [--depth <depth>] [--[no-]single-branch] [--no-tags]
	  [--recurse-submodules[=<pathspec>]] [--[no-]shallow-submodules]
	  [--[no-]remote-submodules] [--jobs <n>] [--sparse] [--[no-]reject-shallow]
	  [--filter=<filter>] [--] <repository>
	  [<directory>]
```  

> 사용방법

```java
$ git clone [원격저장소url] [디렉토리]
```

<br>

## `git pull`  

git clone 은 해당 repository 에 있는 모든 파일을 다운로드 받는 것이고, git pull 은 선택한 브랜치에 있는 파일을 다운로드 받아서 현재 내 컴퓨터에 작업 중인 파일과 병합(merge)을 진행합니다. git pull 은 현재 내 컴퓨터의 Working Directory 가 git 으로 관리가 되고 있는 상태에서 가능하기 때문에 작업중인 폴더에 ".git" 폴더가 없다면 git pull 은 진행할 수 없습니다. 내 컴퓨터와 github 의 파일 버전이 차이가 나는 경우에는 git push 명령 시 에러가 발생할 수 있기 때문에 github 의 파일이 최신화 되면 git pull 명령을 실행해서 내 컴퓨터의 파일도 업데이트를 진행 후 작업하는 것이 좋습니다.

> 형식

```java
git pull [<options>] [<repository> [<refspec>…​]]
```  

> 사용방법

```java
$ git pull [원격이름] [브랜치명]
```

<br>

## `git fetch`  

git pull 은 commit 기록들을 다운로드 받아서 현재 내 컴퓨터에 있는 작업파일과 병합(merge)을 실행하고, git fetch 는 commit 기록들을 다운로드만 받아서 사용자가 파일들을 비교 후 직접 병합(merge)을 실행해주어야 합니다. 다운로드 받을 파일을 직접 확인하고 수동으로 병합하고자 할 때 사용합니다.

> 형식

```java
git fetch [<options>] [<repository> [<refspec>…​]]
git fetch [<options>] <group>
git fetch --multiple [<options>] [(<repository> | <group>)…​]
git fetch --all [<options>]
```  

> 사용방법

```java
$ git fetch [원격이름] [브랜치명] 
```

<br>

## `git merge`  

현재 위치한 브랜치와 입력한 브랜치를 병합합니다. 병합을 할 때 현재 브랜치와 병합할 브랜치의 파일이 같은 위치를 수정한 경우 충돌(conflict)이 발생하게 되는데, 두 브랜치의 파일 중 하나의 파일에서 중복되는 부분을 제거해주고 git commit 을 해주면 병합이 진행됩니다. 하나의 프로젝트에서 브랜치가 너무 많이 존재하게 되면 나중에 관리가 어려워지기 때문에 새로운 브랜치를 생성해서 파일을 수정한 뒤에는 main 브랜치와 병합을 하고, 새로 만들었던 브랜치는 삭제를 해주는 것이 좋습니다.

> 형식

```java
git merge [-n] [--stat] [--no-commit] [--squash] [--[no-]edit]
	[--no-verify] [-s <strategy>] [-X <strategy-option>] [-S[<keyid>]]
	[--[no-]allow-unrelated-histories]
	[--[no-]rerere-autoupdate] [-m <msg>] [-F <file>]
	[--into-name <branch>] [<commit>…​]
git merge (--continue | --abort | --quit)
```  

> 사용방법

```java
$ git merge [브랜치명]
```

<br>

## `git diff`  

기존 버전(a)과 변경된 버전(b)의 차이점(변경사항)을 알려줌

> 형식

```java
git diff [<options>] [<commit>] [--] [<path>…​]
git diff [<options>] --cached [--merge-base] [<commit>] [--] [<path>…​]
git diff [<options>] [--merge-base] <commit> [<commit>…​] <commit> [--] [<path>…​]
git diff [<options>] <commit>…​<commit> [--] [<path>…​]
git diff [<options>] <blob> <blob>
git diff [<options>] --no-index [--] <path> <path>
```  

> 사용방법

```java
git diff  // commit된 파일상태와 현재 수정중인 상태 비교
git diff --staged  // commit된 파일상태와 add된 파일 상태 비교
git diff [비교할commit해쉬1] [비교할commit해쉬2]  // commit간의 상태 비교하기 - commit hash 이용
git diff HEAD HEAD^  // 가장 최근의 커밋과 그 전의 커밋을 비교
git diff [비교할branch1] [비교할branch2]  // branch간의 상태 비교
```









<br><br><br>

# <strong>Reference</strong>  

- [Git 홈페이지](https://git-scm.com/docs){:target="_blank"}
