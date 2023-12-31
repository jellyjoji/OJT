# vi/vim 편집기 비교 및 기본 명령어

## vi(visual editor) 
파일의 내용을 보여줌과 동시에 파일의 내용을 편집할 수 있게 해주는 프로그램이다.

## VIM (vi improved)
Vim(Vi Improved)이란 Unix, Linux 환경에서 사용되는 텍스트 편집기(editor)인 Vi의 업그레이드 버전이다.

### VIM 의 4가지 모드

1. 일반모드(Normal Mode) or 명령모드(Command Mode)
사용자가 키보드를 통해서 타이핑 하는 모든 내용을 하나의 명령으로 받아들이는 모드이다.
Vim 기본 설정 모드이다. 

2. 명령줄 모드(Command Line Mode)
사용자가 입력한 문장이 특정 명령어가 되는 모드이다.

3. 편집/입력 모드(Insert Mode)
입력하는 모든 내용들이 문서의 내용이 되는 모드이다.
메모장처럼 단순히 타이핑할 수 있는 모드에 해당한다.

4. 비쥬얼/선택 모드(Visual Mode)
문서를 구성하는 특정 부분의 내용을 선택할 때 사용하는 모드이다. 
많이 사용되지 않는 모드이다.

### (이렇게 불편한) Vim 사용 이유

서버와 클라이언트 구조로 구축된 시스템을 사용하는 일이 많고 수많은 소프트웨서, 프로그램 시스템들이 리눅스 서버에서 진행되는 경우가 상당히 많기 때문에 리눅스 서버를 활용할수 있어야 한다. **리눅스 서버상에서** 소스파일이나 문서파일을 편집할때 **대표적으로 사용하는 VIM 에디터가 VIM** 이다.

# vi / vim 기본 명령어
## 실행
```bash
vi file : file 열기
vi file1 file2 : file1과 file2를 순서대로 열기
view file / vi -R file : file을 읽기모드로 열기
vi + file : file을 열고 커서를 본문의 마지막 줄에 위치 시킴
vi +n file : file을 열어 n번째 줄에 위치 시킴
vi -r file : 손상된 파일 회복
```

## 저장 및 종료
```bash
:w : 저장하기
:wq : 저장 후 종료
:q : 저장하지 않고 종료
:q! : 저장하지 않고 강제 종료 
```

## 입력모드 전환
```bash
i :  커서의 위치에서 입력모드로 전환
l : 커서가 위치한 줄의 맨 앞에서 입력모드로 전환
a : 커서가 위치한 다음 칸에서 입력모드로 전환
A : 커서가 위치한 줄의 맨 마지막에서 입력모드로 전환
o : 커서가 위치한 줄의 아래에 빈 줄 삽입
O : 커서가 위치한 줄의 위에 빈 줄 삽입
R : 수정모드로 전환
```

## 커서 이동
```bash
w : 다음 단어의 끝 부분으로 커서 이동
e : 다음 단어 앞 부분으로 커서 이동
b : 이전 단어로 이동
^,0 : 줄의 처음으로 이동
$ : 줄의 마지막으로 이동
H : 화면 맨 위로 이동
M : 화면 중간으로 이동
L : 화면 맨 아래로 이동
G : 글의 맨 밑으로 이동
nG : n번째 줄로 이동
n% : n퍼센트에 해당하는 위치로 이동
'Shift' + ↑ : 한 페이지 앞으로 이동
'Shift' + ↓ : 한 페이지 뒤로 이동
'Ctrl' + i : 한 화면 위로 이동
'Ctrl' + b : 한 화면 아래로 이동
'Ctrl' + d : 한 화면 위로 이동
'Ctrl' + u : 반 화면 아래로 이동
'Ctrl' + e : 한 줄 위로 이동
'Ctrl' + y : 한 줄 아래로 이동
```

## 복사 및 붙여넣기
```bash
yy : 현재 커서가 위치한 줄을 버퍼로 복사
p : 버퍼에 복사되어있는 내용을 커서 뒤에 삽입
P : 버퍼에 복사되어있는 내용을 커서 앞에 삽입
ny :  현재 커서가 위치한 줄에서부터 아래로 n줄 복사
:n1, n2y : n1~n2번째줄을 버퍼로 복사
:npu : n행에 버퍼에 복사되어있는 내용을 삽입
d : 현재 커서가 위치해있는 단어 복사
nyy : 현재 커서에서 부터 n만큼의 행 복사
```

## 삭제
```bash
x : 현재 커서가 위치한 문자 삭제
dw : 단어 삭제
dd : 현재 커서가 위치한 줄 삭제
ndd : 현재 커서에서 부터 n만큼의 줄 삭제
d + ↑ : 현재 커서가 위치한 줄의 위로 2줄 삭제
d + ↓ : 현재 커서가 위치한 줄의 위로 2줄 삭제
D : 한줄 내에서 커서의 위치 뒤로 모두 삭제
u :  바로 전에 수행한 명령 취소
```

## 문자열 찾기
```bash
/name : name 문자열 찾기
n : 다음 name으로 이동(아래로 검색)
N : 이전 name으로 이동(위로 검색)
```

## 문자열 대체
```bash
:s/str/rep : 현재 줄의 str을 rep로 대체
:l,.s/str/rep/ : 1부터 현재 줄의 str을 rep로 대체
:%s/str/rep/g : 파일 전체 str을 rep로 전부 대체
:.$/aaa/bbb : 커서의 위치로부터 파일의 끝까지 있는 모든 aaa를 bbb로 대체
```

## 기타
```bash
:set nu : 줄 번호 보여주기
:set nonu : 줄 번호 보여주기 취소
. : 바로 전에 실행한 명령어 재 실행
'Ctrl' + l : 불필요한 화면 정리후 다시 표시
```