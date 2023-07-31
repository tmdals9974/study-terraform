# Section 0. DevOps 이론

## 1강 - DevOps의 기본적 이해

- DevOps의 기본적 이해
  - DevOps: Devlopment + Operations의 합성어
    - 현재의 DevOps는 단순한 개발과 운영의 통합을 의미하는 것이 아니다. 초기에는 개발팀과 운영팀 생각의 차이를 인지하고 그 간극을 좁히는게 시작이었으나, 지속적으로 발전하여 `소프트웨어 개발 및 우리의 일에 관한 포괄적인 철학과 방법론`이 되었다.
  - DevOps의 5가지 철학
    - 문화: DevOps를 통해 하나의 문화를 만들어 나간다
    - 자동화: 자동화를 통해 효율성과 빠른 속도를 지향한다 (프로그래밍 언어와 도구를 통해 자동화하여 재사용 가능하고 탄력적이고 유연하도록.)
    - 측정: 지표를 측정하여 지속적으로 개선해 나간다 (변경사항 발생 시 항상 측정해야 한다. 예측 불가능한 영역을 예측 가능하도록. 지속적으로 나아지고 있는지.)
    - 공유: 공유를 통해 함께 발전해 나간다 (데이터 공유, 지식 공유, 함께 문제 해결)
    - 축적: 기록을 축적하여 자산을 만들어 나간다
  - DevOps는 어떤 요구사항을 효율적으로 만족시키기 위하여, 일을 자동화하며 변경사항 지표들을 측정하고 공유하고, 이 모든 결과물들을 지속적으로 축적해 나아가는 문화를 만들어가는 철학, 방법론, 기술.

## 2강 - DevOps 엔지니어의 역할

- 역할
  - 올바른 DevOps 문화를 위해 서비스 혹은 S/W LifeCycle 에서 반복적인 일들을 자동화 하고, 팀간의 차이를 기술적으로 해소시키는 담당하는 사람
- 필요 역량
  - Soft Skill: 문제인식, 선택과 집중, 결정, 업의 속성, 사용자
  - Technical Skill: 프로그래밍, 운영체제, 서버관리, 오픈소스, 클라우드
- IaC (Infrastructure as Code) : 코드로써의 인프라
  - Infrastructure as Code, 즉 코드로써의 인프라는 인프라를 이루는 서버, 미들웨어 그리고 서비스 등 인프라 구성요소들을 코드를 통해 구축하는 것.
  - **IaC는 코드로써의 장점 (작성용이성, 재사용성, 유지보수)을 가진다.**
  - `Terraform`은 쉽고 사용자가 많은 IaC다.

## 2강 보너스 - DevOps 로드맵

- DevOps 로드맵을 보며 하나하나 코멘트 해주셨다. 직접 강의로 재확인할 것.

# Section 1. 사전 준비

## 3강 - Terraform 기본

- 테라폼 구성요소
  - `provider`: 테라폼으로 생성할 인프라의 종류를 의미합니다.
  - `resource`: 테랴폼으로 실제로 생성할 인프라 자원을 의미합니다.
  - `state`: 테라폼을 통해 생성한 자원의 상태를 의미합니다.
  - `output`: 테라폼으로 만든 자원을 변수 형태로 state에 저장하는 것을 의미합니다.
  - `module`: 공통적으로 활용할 수 있는 코드를 문자 그대로 모듈 형태로 정의하는 것을 의미합니다.
  - `remote`: 다른 경로의 state를 참조하는 것을 말합니다. output 변수를 불러올때 주로 사용합니다.
- 테라폼 명령어
  - `init`: 테라폼 명령어 사용을 위해 각종 설정을 진행합니다.
  - `plan`: 테라폼으로 작성한 코드가 실제로 어떻게 만들어질지에 대한 예측 결과를 보여줍니다.
  - `apply`: 테라폼 코드로 실제 인프라를 생성하는 명령어입니다.
  - `import`: 이미 만들어진 자원을 테라폼 state 파일로 옮겨주는 명령어입니다.
  - `state`: 테라폼 state를 다루는 명령어입니다. 하위 명령어로 mv, push와 같은 명령어가 있습니다.
  - `destrody`: 생성된 자원들 state 파일 모두 삭제하는 명령어 입니다.

## 4-1강 - AWS EC and SSH

- AWS EC2에 대한 소개와 인스턴스 생성법 안내
- VPC (Security Group)와 EC2에 대한 구조 간단 안내
- SSH
  - default tcp 22번 포트에 sshd라는 데몬 프로그램이 실행됨.
  - ssh 연결 시 프로그램이 계속 실행되며 명령을 기다림.
  - RSA 암호를 이용해 SSH 연결. ~/.ssh/authorized_keys에 공개키가 등록되어있음.

## 4-2강 - Zsh 및 Oh-my-zsh 설치

- **EC2 OS : Amazon Linux**
- Linux 기본 세팅
  - sudo는 기본으로 세팅되어 있음.
  - 기본 계정의 password 설정: `sudo passwd ec2-user`
  - 기본 쉘 세팅
    - 기본 쉘의 형태나 여러가지 기능들을 변경해주어 `편의성`을 높여줌 
      - ex 1) 파일명의 중간부분만 입력하고 탭을 눌러도 자동완성됨. app-test 라는 파일이 있을때, test 를 입력하고 탭키를 눌러도 자동완성이 된다는 뜻!
      - ex 2) 위아래 방향키로 이전에 입력했던 명령어 히스토리를 탐색하는 기능이 업그레이드됨. vi 까지 입력후 위아래로 움직이면 vi 를 기준으로 히스토리 탐색해줌.
    - 테마를 통해 `가독성`을 높여줌
    - **zsh 설치**
      - 설치 명령어: `sudo yum install -y zsh`
      - OS의 기본쉘 변경
        - 기본쉘을 bash 에서 zsh로 변경
        - 기본쉘 변경 명령어: chsh -s /bin/zsh
        - 위 명령어 실행 중 오류가 발생했을 경우, 특정 os에서는 util-linux-user.x86_64를 설치해야함 (`sudo yum install -y util-linux-user.x86_64`)
    - **oh-my-zsh 설치**
      - 설치 명령어: `curl -L https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh | sh`
        - 명령어 실행중 깃 설치 메시지가 나오면 `sudo yum install -y git`으로 깃설치 먼저 진행
        - 최초에 zsh 실행 될 때 `~/.zshrc` 파일에 있는 명령어를 가장 먼저 실행함. 해당 파일에서 각종 옵션 부여 가능.
        - `github.com/ohmyzsh/ohmyzsh/wiki/Themes`에서 테마를 골라 적용할 수 있음. (`~/.zshrc` 파일의 `ZSH_THEME` 값 변경)

## 5-1강 - AWS CLI 및 Terraform 설치

- AWS CLI v2 설치
  - aws linux는 AWS CLI 기본 내장
  - 설치(업데이트) 명령어 : 
    1. `curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"`
    2. `unzip awscliv2.zip`
    3. `sudo ./aws/install`
    4. `/usr/local/bin/aws --version` 으로 버전 확인 (`aws --version`은 exit 후 재연결 또는 쉘 재실행 후 확인 가능)
    5. rm -rf aws, rm awscliv2.zip으로 설치파일 제거
- Terraform 설치
  - https://developer.hashicorp.com/terraform/downloads