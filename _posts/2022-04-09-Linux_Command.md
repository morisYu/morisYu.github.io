---
published: true
layout: single
title: "[Linux] 기본 명령어"
subtitle: 
categories: [linux]
tag: [linux, command]
toc: true
toc_sticky: true
---  

# [Linux] 기본 명령어   

### pwd  

> 설명  

- print working directory 의 약자이며 현재 위치한 디렉토리를 표시합니다.  

> 실행

```bash
pwd
```  

<br>  

### ls  

> 설명  

- list 의 약자이며 디렉토리 내 파일과 디렉토리를 표시합니다.  

> 실행  

```bash
# 현재 디렉토리에 있는 파일과 디렉토리의 상세정보를 표시
ls -l

# 현재 디렉토리에 숨겨져 있는 디렉토리와 파일을 표시
ls -a

# d드라이브의 test 디렉토리에 있는 모든 파일과 디렉토리를 표시
ls -al /d/test
```  

<br>  

### cd  

> 설명  

- change directory 의 약자이며 디렉토리를 이동합니다.  

> 실행  

```bash
# 현재 디렉토리에서 바로 상위 디렉토리로 이동
cd ..

# root 디렉토리로 이동
cd /

# 절대 경로를 이용하여 d 드라이브 안에 있는 test1-1 디렉토리로 이동
cd /d/test/test1/test1-1

# 상대 경로를 이용하여 test2-1 디렉토리에서 test1-1 디렉토리로 이동
cd ../../test1/test1-1
```  

<br>  

### mkdir  

> 설명  

- make directory 의 약자이며 디렉토리를 생성합니다.  

> 실행  

```bash
# 현재 디렉토리에 test 디렉토리를 생성
mkdir test

# 디렉토리를 이동하지 않고 test 디렉토리 내에 test1 디렉토리 생성
mkdir ./test/test1
```  

<br>  

### rm  

> 설명  

- remove 의 약자이며 디렉토리 또는 파일을 삭제합니다.  

> 실행  

```bash
# test.txt 파일을 삭제
rm text.txt

# 내부에 파일 또는 디렉토리가 없는 test1 디렉토리를 삭제
rm -d ./test/test1

# 내부에 있는 파일 또는 디렉토리를 포함한 test 디렉토리를 삭제
rm -r ./test
```  

<br>  

### touch  

> 설명  

- 내용이 없는 텍스트 파일을 생성합니다.  

> 실행  

```bash
# file1.txt 파일 생성
touch file1.txt

# file2.txt 파일과 file3.txt 파일을 동시에 생성
touch file2.txt file3.txt
```  

<br>  

### cat  

> 설명  

- concatenate 의 약자이며 선택한 파일의 내용을 출력해서 보여줍니다.  

> 실행  

```bash
# file1.txt 파일의 내용을 출력
cat file1.txt
```  

<br>  

### echo  

> 설명  

- 작성한 내용을 바로 출력하거나 텍스트 파일에 저장합니다.  
- redirection(`>>`, `>`)을 사용해서 작성한 내용을 파일에 추가하거나 덮어쓸 수 있습니다.  

> 실행  

```bash
# 작성한 내용을 바로 출력
echo "hello world"

# 작성한 내용을 file1.txt 파일에 덮어쓰기(기존 내용은 사라지고 새로운 내용만 저장)
echo "good morning" > file1.txt

# 작성한 내용을 file1.txt 파일에 추가하기(기존 내용 뒤에 새로운 내용 추가)
echo "hi" >> file1.txt

# 내용을 작성하여 새로운 텍스트 파일을 생성
echo "new file" > newfile1.txt
echo "new file2" >> newfile2.txt

# 옵션을 사용해서 역슬래시 이스케이프를 해석
echo -e "hello everyone \n this is..." >> file1.txt # \n : 새 줄 생성
echo -e "hello\teveryone" >> file1.txt # \t : 가로 탭 공간을 생성
echo -e "\a" >> file1.txt # \a : 텍스트 파일 실행 시 알람을 울림
```  

<br>

### cp  

> 설명  

- copy의 약자이며, 원본파일을 복사하여 사본파일을 생성합니다. 파일명에 경로를 추가하면 파일이 복사되는 경로를 설정할 수 있고, 사본파일의 이름도 바꿀 수 있습니다.  

> 실행  

```bash
# 현재 디렉토리에 file1.txt 파일을 복사하여 file2.txt 파일 생성
cp file1.txt file2.txt

# 현재 디렉토리에 있는 file1.txt 파일을 복사하여 다른 디렉토리에 file2.txt 파일 생성
cp file1.txt ../test/test2/file2.txt
```

<br>

### mv  

> 설명  

- move의 약자이며, 원본파일을 다른 경로로 이동합니다. 경로를 정하지 않으면 현재 디렉토리에서 파일의 이름만 바꿀 수 있습니다.  

> 실행  

```bash
# 현재 디렉토리에 있는 file.txt 파일을 test/test1 디렉토리로 이동
mv file.txt ./test/test1

# 현재 디렉토리에서 file.txt 파일을 file12.txt 로 이름 변경
mv file.txt file12.txt
```  

<br>  

### vi   

> 설명  

- vi에디터를 실행합니다. (윈도우에서 메모장과 같음)  

> 실행  

```bash
# vi에디터 실행
vi [파일명]
vi
```

- 문자, 행 삽입 명령어(처음 vi에디터가 실행되면 바로 내용을 입력할 수는 없고(명령모드), 문자 삽입 명령어를 입력해주어야 내용을 입력할 수 있습니다.)  

| 명령어 | 기능 |  
| :--: | -- |
| a | 커서 오른쪽에 문자 삽입 |  
| A | 커서 오른쪽, 행의 끝에 문자 삽입 |  
| i | 커서 왼쪽에 문자 삽입 |  
| I | 커서 왼쪽, 행의 처음에 문자 삽입 |  
| o | 커서 아래에 행 삽입 |  
| O | 커서 위에 행 삽입 |  
| ESC | 종료(명령 모드로 복귀) |  

<br>

- 보관 및 종료 명령어  

| 명령어 | 기능 |  
| :--: | -- |  
| :w | 변경사항 저장 |  
| :w [파일명] | 파일명으로 변경사항을 저장 |  
| :q! | 변경사항을 저장하지 않고 vi에디터 종료 |  
| :q | vi에디터 종료 |  
| :wq | 변경사항을 저장하고 vi에디터 종료 |  

<br>  

### head  

> 설명  

- 파일의 앞부분부터 확인합니다.

> 실행  

```bash
# file.txt 파일의 처음부터 10 줄의 내용을 보여줌
head file.txt

# file.txt 파일의 처음부터 설정한 줄 만큼 내용을 보여줌
head -n 11 file.txt

# file.txt 파일의 뒤부터 설정한 줄을 제외한 내용을 보여줌
head -n -5 file.txt

# file.txt 파일의 처음부터 설정한 byte 만큼 내용을 보여줌
head -c 5 file.txt
```  

<br>  

### tail  

> 설명  

- 파일의 뒷부분부터 확인합니다.  

> 실행  

```bash
# file.txt 파일의 뒤부터 10 줄의 내용을 보여줌
tail file.txt

# file.txt 파일의 뒤부터 설정한 줄 만큼 내용을 보여줌
tail -n 3 file.txt

# file.txt 파일의 뒤부터 설정한 byte 만큼 내용을 보여줌
tail -c 6 file.txt

# file.txt 파일의 실시간 변화 내용을 보여줌(모니터링 종료는 ctrl+z)
tail -f file.txt
```

<br>  

### df  

> 설명  

- 디스크 사용량을 확인합니다.  

> 실행  

```bash
# 각 디스크의 사용량 확인
df -h
```

<br>  

### find  

> 설명  

- 디렉토리, 파일을 검색합니다.  

> 실행  

```bash
# 현재 디렉토리에서 모든 md 파일을 검색
find *.md

# test 디렉토리에 있는 모든 txt 파일을 검색
find ./test/*.txt
```  

<br>  

### history  

> 설명  

- 이전에 입력한 명령어들을 출력합니다. ! 명령을 사용해서 해당 명령어를 다시 실행할 수 있습니다.  

> 실행  

```bash
# 이전 사용한 명령어 목록 확인
history

# history 에 나온 명령어 중 10 번 명령어를 실행
!10

# 이전 실행한 명령어를 실행
!!

# history 목록 중 특정 행 삭제
history -d 12

# history 목록 삭제
history -c
```  

<br>  

### clear  

> 설명  

- 화면에 출력된 모든 내용을 지웁니다.  

> 실행  

```bash
clear
```  

<br>  

### help  

> 설명  

- 명령어에 대한 설명을 볼 수 있습니다.  

> 실행  

```bash
# 명령어 종류 확인
help

# 해당 명령어에 대한 설명
[명령어] --help
ls --help
```

<br><br><br>

# <strong>Reference</strong>  

- [리눅스 기본 명령어 정리](https://cocoon1787.tistory.com/717){:target="_blank"}  
- [자주 사용하는 리눅스 기본 명령어 모음](https://shanepark.tistory.com/196){:target="_blank"}  
- [리눅스 기초 명령어2](https://seungjuitmemo.tistory.com/123){:target="_blank"}  
- [리눅스 기본 명령어](https://kyuhyuk.kr/article/linux/2020/01/22/Linux-Command-Line){:target="_blank"}  