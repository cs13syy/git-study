GIT 설치 및 SSH 설정
==============
windows 기준입니다

***

## 1. GIT 설치하기
- [GIT 공식 사이트](https://git-scm.com/downloads "GIT 공식 사이트")에서 GIT 프로그램 다운로드
- PC에 적합한 bit의 installer로 자동 다운로드됨
- 다운 받은 파일을 열어 설치 진행
- 설치 내역 모두 default 상태로 next 버튼만 클릭
   - default 상태로 설치 진행하면 GIT 환경변수가 자동 설정됩니다
- finish 버튼 클릭하면 설치 완료

***

## 2. GIT SSH 생성하기
- windows 시작 버튼에서 "git bash" 검색하고 실행
- **ssh-keygen -t rsa -C "git계정"**을 입력 
   - 따옴표 안에는 GITHUB에 가입한 이메일 입력합니다
- enter를 세 번 누르면 ssh 공개키 생성 완료
   - enter만 누르면 추가적인 비밀번호 생성 없이 key 접근 가능 
- **your public key has been saved in** 뒤에 나오는 디렉토리에 들어가면 ssh public key가 생성된 것을 확인할 수 있습니다
   - 여기서 .pub 확장자는 microsoft publisher가 아닙니다. 해당 파일을 열면 windows에서 자동으로 publisher 앱으로 연결하는데, publisher가 아닌 public이라는 뜻이니 참고해주세요.
- bash 창에 다음 두 코드를 각각 입력하고 enter를 누름
   - **eval $(ssh-agent -s)**
   - **ssh-add ~/.ssh/id_rsa**
- 다음 코드를 입력하여 ssh public key를 확인하고 복사
   - **cat ~/.ssh/id_rsa.pub**

***

## 3. GITHUB에 SSH KEY 등록하기
- GITHUB 로그인 후 우측 상단 자신의 프로필을 클릭, 하단의 settings 클릭
- 좌측 personal settings에서 **SSH and GPG keys** 클릭 
- 우측 상단의 **New SSH key** 버튼을 클릭
- title에는 GIT을 설치한 PC의 닉네임을 입력
- key에는 위에서 복사한 ssh public key를 붙여넣기
- **Add SSH key**를 클릭하여 등록을 완료

***

## 4. GITHUB SSH 연결 확인하기
- windows 시작 버튼에서 "git bash" 검색하고 실행
- 창에 다음 코드를 입력 **ssh -T git@github.com**
- 창에 나타난 key fingerprint가 맞다면 질문에 **yes**를 입력하고 enter
- 창에 다음의 메시지가 나타나면 ssh가 정상적으로 연결된 것입니다
   - **Hi username! You've successfully authenticated, but GitHub does not provide shell access.**
