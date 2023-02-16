# linux

23-02-16 배운것
___
# 디렉토리 구조 및 기능
![image](https://user-images.githubusercontent.com/121842148/219260222-3bf6c5d4-f15a-4504-bda8-078163b7d235.png)

/

- 마운트 되는 리눅스 파일 시스템이 있는 최상위 디렉토리
- 시스템의 근간을 이루는 가장 중요한 디렉토리
- 파티션 설정 시 반드시 존재하여야 함
- 절대경로의 기준이 되는 디렉토리
절대경로 : / 디렉토리 기준 예) /usr/local
상대경로 : 현재 작업 디렉토리 기준 예) ./local

/bin

- binarise의 약어
- 리눅스의 기본 명령어(binary)들이 들어있는 디렉토리
- 기본적인 명령어들이 모여있는 디렉토리
- 부팅에 필요한 명령어들이 위치하며 부팅 후 시스템의 사용자들이 사용할 수 있는 일반적인 명령어들도 위치하고 있음

# 디렉토리 구조
/bin: 사용자가 사용하는 명령어 모음

![image](https://user-images.githubusercontent.com/121842148/219260492-30c17231-8b54-40ee-87f9-15415a5f5358.png)

/sbin: 관리자가 사용하는 명령어 모음
/etc: 프로그램 설정을 관리하는 디렉토리
/etc/init.d: daemon의 목적을 가진 프로그램들 있음.
/var: 내용이 바뀔 수 있는 파일들 모음
/tmp: 임시파일들. 컴퓨터가 꺼지면 날아간다.
/home: 사용자들의 파일들이 저장되는 디렉토리
/lib: /bin과 /sbin에 있는 프로그램들이 사용하는 라이브러리 모음
/usr: 유저가 다운받은 프로그램들 저장..

# 필수 명령어

ls - 현재 위치의 파일 목록 조회

cd - 디렉터리 이동

touch - 0바이트 파일 생성, 파일의 날짜와 시간을 수정

mkdir - 디렉터리 생성

cp - 파일 복사

mv - 파일 이동

rm - 파일 삭제

cat - 파일의 내용을 화면에 출력, 리다이렉션 기호('>')를 사용하여 새로운 파일 생성

redirection - 화면의 출력 결과를 파일로 저장 ex )echo "fist line" > test1.txt, cp test1.txt test2.txt, echo "second line" >> test2.txt

alias - 자주 사용하는 명령어들을 별명으로 정의하여 쉽게 사용할 수 있도록 설정

top - 현재 내컴퓨터의 프로세스,상태를 출력

find – 현재 폴더에서 들어있는 모든 파일을 검색한다. (https://coding-factory.tistory.com/804)

파일 : find ex -type f -name "*.txt“

디렉토리 : find . -type d -name "ex"

grep - 파일 내에서 지정한 패턴이나 문자열을 찾은 후에, 그 패턴을 포함하고 있는 모든 행을 표준 출력. find | grep tt : tt이름이 있는 파일의 경로를 찾아준다.

which - 명령어가 어디에서 비롯되는지 알려준다.

echo - 출력할 것

![image](https://user-images.githubusercontent.com/121842148/219260694-21f1f975-25b4-4bf1-91d9-2641d3bf81fb.png)

## 파일형식 짤막팁

![image](https://user-images.githubusercontent.com/121842148/219260773-9eb08341-6a04-43f5-9110-1bd550ca3a00.png)

읽는권한/쓰는권한/실행권한

drwxr/xr/x

chmod : 특정 파일 또는 디렉토리의 퍼미션 수정

chown : 파일이나 디렉토리의 소유자, 소유 그룹 수정

chgrp : 파일이나 디렉토리의 소유 그룹 수정

* find

- 현재 디렉토리에서 모든 디렉토리 찾기
find . -type d
- 현재 디렉토리에서 test가 들어가는 디렉토리 찾기
find . -name "*test*" -type d
- 현재 디렉토리에서 모든 파일 찾기
find . -type f
- 현재 디렉토리에 "test"가 들어가는 파일을 찾아서 상세정보 출력
find . -name "*test*" -exec ls -l {} \;
- 현재 디렉토리에 있는 파일에서 "test"가 들어가는 내용 찾기
find . -type f -exec grep "test" {} \;
- 현재 디렉토리에 ".txt" 확장자를 찾아서 모두 삭제
find . -name "*.txt" -exec rm {} \;

# 명령어 옵션

## ls (List segments) : 현재 위치의 파일 목록 조회
ls -l : 파일의 상세정보

ls -a : 숨김 파일 표시

ls -t : 파일들을 생성시간순(제일 최신 것부터)으로 표시

ls -rt : 파일들을 생성시간순(제일 오래된 것부터)으로 표시

ls -f : 파일 표시 시 마지막 유형에 나타내는 파일명을 끝에 표시

('/' : 디렉터리, '*' : 실행파일, '@' : 링크 등등,,,)

## cd (Change directory) :디렉터리 이동
cd [디렉터리 경로] : 이동하려는 디렉터리로 이동 (경로 입력 시 '[', ']'부분은 빼고 입력!)

cd ~ : 홈 디렉터리로 이동

cd / : 최상위 디렉터리로 이동

cd . : 현재 디렉터리

cd .. : 상위 디렉터리로 이동

cd - : 이전 경로로 이동

## touch : 0바이트 파일 생성, 파일의 날짜와 시간을 수정
touch filename : filename의 파일을 생성

touch -c filename : filename의 시간을 현재시간으로 갱신

touch -t 202110291608 filename : filename의 시간을 날짜 정보(YYYYMMDDhhmm)로 갱신

(20211029160 => 2021.10.29.16:08)

touch -r oldfile newfile : newfile의 날짜 정보를 oldfile의 날짜 정보와 동일하게 변경

## mkdir (Make dirctory) : 디렉터리 생성
mkdir dirname : dirname이라는 디렉터리 생성

mkdir dir1 dir2: 한 번에 여러 개의 디렉터리 생성

mkdir -p dirname/sub_dirname : dirname이라는 디렉터리 생성, sub_dirname이라는 하위디렉터리도 생성

mkdir -m 700 dirname : 특정 퍼미션(권한)을 갖는 디렉터리 생성

## cp (Copy) : 파일 복사
cp file1 file2 : file1을 file2라는 이름으로 복사

cp -f file1 file2 : 강제 복사(file2라는 파일이 이미 있을 경우 강제로 기존 file2를 지우고 복사 진행)

cp -r dir1 dir2 : 디렉터리 복사. 폴더 안의 모든 하위 경로와 파일들을 복사

## mv (Move) : 파일 이동
mv file1 file2 : file1 파일을 file2 파일로 변경

mv file1 dir : file1 파일을 dir 디렉터리로 이동

mv file1 file2 dir : 여러 개의 파일을 dir 디렉터리로 이동

mv dir1 dir2 : dir1 디렉터리를 dir2 디렉터리로 이름 변경

## rm (Remove) : 파일 삭제
rm file1 : file1을 삭제

rm -f file1 : file1을 강제 삭제

rm -r dir : dir 디렉터리 삭제 (디렉터리는 -r 옵션 없이 삭제 불가)

## cat (Catenate) : 파일의 내용을 화면에 출력, 리다이렉션 기호('>')를 사용하여 새로운 파일 생성
cat file1 : file1의 내용을 출력

cat file1 file2 : file1과 file2의 내용을 출력

cat file1 file2 | more : file1과 file2의 내용을 페이지별로 출력

cat file1 file2 | head : file1과 file2의 내용을 처음부터 10번째 줄까지만 출력

cat file1 file2 | tail : file1과 file2의 내용을 끝에서부터 10번째 줄까지만 출력

## redirection ('>', '>>') : 화면의 출력 결과를 파일로 저장
'>' 기호 : 기존에 있는 파일 내용을 지우고 저장

'>>' 기호 : 기존 파일 내용 뒤에 덧붙여서 저장

'<' 기호 : 파일의 데이터를 명령에 입력

cat file1 firle2 > file3 : file1, file2의 명령 결과를 합쳐서 file3라는 파일에 저장

car file4 >> file3 : file3에 file4의 내용 추가

cat < file1 : file1의 결과 출력

cat < file1 > file2 : file1의 출력 결과를 file2에 저장

## alias : 자주 사용하는 명령어들을 별명으로 정의하여 쉽게 사용할 수 있도록 설정

# 쉘 스크립트 기본 문법

1. 쉘 스크립트는 파일로 작성 후, 파일을 실행 한다.
2. 파일의 가장 위 첫 라인은 #!/bin/bash로 시작한다.
3. 쉘 스크립트 파일은 코드를 작성한 후에는 실행 권한을 부여해야한다.
4. 일반적으로 '파일이름.sh' 와 같은 형태로 파일 이름을 작성한다.
5. 주석은 #내용 으로 처리한다

'vi 파일이름.sh' 로 파일을 만들고 insert 를 눌러 작성한 다음 다시 insert 를 누르고 esc 를 누른다음 :wq로 저장한다. 

# tar

- 현재 디렉토리의 모든 파일과 디렉토리를 tar로 묶기 :$ tar cvf 파일명.tar *
- 대상 디렉토리를 포함한 모든 파일과 디렉토리를 tar로 묶기 : tar cvf 파일명.tar [PATH]
- 파일을 지정하여 tar 아카이브로 묶기 :$ tar cvf 파일명.tar [FILE_1] [FILE_2]
- tar 아카이브의 내용 확인하기 :$ tar tvf 파일명.tar
- tar 아카이브를 현재 디렉토리에 풀기 :$ tar xvf 파일명.tar
- tar 아카이브를 지정된 디렉토리에 풀기 :$ tar xvf 파일명.tar -C [PATH]
- tar 아카이브 묶거나 풀 때 파일 별 진행 여부 확인하기 : $ tar cvfw 파일명.tar *

# Navigating file system
- pwd : 현재 경로
- ls : list의 약자
ls dir1, ls –l, ls –a, ls –la
- cd : [이동 할 디렉토리 경로]
cd dir1, cd ..(상위 폴더), cd ~(home dir), cd –(이전 경로)
cd ex) cd / : root로 이동
ex) cd project : 현재 디렉토리 내부에 있는 project 디렉토리로 이동
ex) cd /user/jtaewu : /user/jtaewu 경로의 디렉토리로 이동
- find . –type file –name “*.txt”, find . –type file –name “*2”, find . –type directory –name “*2”
- which : 명령어의 경로, which find

# Create and manage file
- touch new_file.txt
- cat new_file.txt
- echo “first line”> new_file1.txt, echo “second line” >> new_file1.txt, echo “Hello World” > new_file2.txt

# Directory
- mkdir
- mkdir –p dir1/subdir1/subdir2
- cp file1.txt dir1/
- mv file2.txt dir1/, mv file1.txt file2.txt
- rm file2.txt, rm dir2, rRm –r dir2
