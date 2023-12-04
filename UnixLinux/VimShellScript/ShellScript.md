# Shell Script

쉘에게 어떤 명령을 내릴지 스트립트 파일을 **`.sh` 확장자**로 작성하여 알려주는 것이다. 
리눅스 실행파일 만들 때 확장자를 `.sh` 로 해주는 것은 쉘 스크립트 실행파일을 생성하는 암묵적인 약속이다. 

리눅스에서는 **VIM 편집기를** 사용하여 쉡 스크립트를 만든다.

## Shell Script 사용법

1. 리눅스 실행파일 만들기
`test_script.sh` 파일명으로 빈파일 생성
```jsx
touch test_script.sh
```

2. 리눅스 sh 실행 권한 부여
실행할 수 있는 권한을 부여해야 쉘 스크립트를 실행할 수 있다.
```jsx
chmod 755 test_script.sh
```

3. 리눅스 쉡 스크립트 쉡 선언
test_script.sh 파일에 실행 권한을 부여했으면 쉡 스크립트를 만들기 위해 쉘 선언을 해야 한다.
```jsx
// echo 명령어로 리눅스 쉘 확인
echo $SHELL
 
// 리눅스 쉘 선언
vi test_script.sh
```
i 를 눌러 insert 입력 모드로 전환시킨 후 아래 내용을 복붙하여 hello world 를 출력하는 쉘 스크립트 실행 파일을 만든다.
```jsx
// #! 는 스크립트를 실행할 쉘을 지정하는 선언문이다.
// bin/bash 는 bash 명령의 절대 경로이다.
// 즉, #!bin/bash 는 bin/bash 의 쉘로 스크립트를 작성하겠다고 선언한 것이다. 
#!bin/bash
 
echo "Hello World"
```

4. 리눅스 쉡 스크립트 실행
```jsx
// sh 명령어로 쉘 스크립트 실행
sh test_script.sh
 
// bash 명령어로 쉘 스크립트 실행
bash test_script.sh
```