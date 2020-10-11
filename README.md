# dev_support
로컬 개발환경 구축을 위한 가이드. 궁금한 사항이 있으면 Slack 질문방에서 질문해주세요.

### !필수 : Docker 설치

* 윈도우 환경
  * https://hub.docker.com/editions/community/docker-ce-desktop-windows/
* 우분투 환경
  * `apt install docker.io docker-compose`

### 기본 사용법

* 개발에 필요한 요소가 적힌 폴더속으로 들어가 `docker-compose up -d`를 입력한다.
  * foreground로 실행하고싶을경우 `docker-compose up`
* 종료하고 싶을 경우 폴더속에 들어가 `docker-compose down`를 입력한다.

### MySQL

* 명령어

  * ```bash
    cd mysql
    docker-compose up -d
    ```

* 설명

  * local 환경에 mysql db를 배포한다.
  * db 내부 상황을 볼 수 있는 phpmyadmin도 같이 배포된다.

* 권한

  * mysql / phpmyadmin
    * id: `root`
    * pw: `root`

* 포트

  * `127.0.0.1:3306`
    * DB 통신용
  * `127.0.0.1:10080 [http]`
    * phpmyadmin 접속용

### mongoDB

* 명령어

  * ```bash
    cd mongodb
    docker-compose up -d
    ```

* 설명

  * local 환경에 mongoDB를 배포한다.

* 권한

  * mongodb
    * id: `root`
    * pw: `root`

* 포트

  * `127.0.0.1:27017`
    * DB 통신용

### Vault

* 명령어

  * ```bash
    cd vault
    docker-compose up -d
    ```

* 설명

  * local 환경에 vault를 배포한다.
  * vault는 (DB 접속 ID/PW와 같은) 공개되서는 곤란한 정보를 관리하는 곳으로 CSUOS 프로젝트 권장사항이다.

* 권한

  * Vault 해독키
    * `a7cd4867a2dcd0a2a1569144ec8e108c09a2b5824ea84e3aaf347ddb21047553`
    * 모든 정보가 암호화되어 저장되어있으므로 매 실행시 위 키를 입력해야지 제대로 작동함
  * Vault root 접속토큰
    * `s.j8NTMpe5JEsYA2OArp1qE9xf`
    * 각 애플리케이션에서는 토큰을 사용하여 자신에게 필요한 정보를 가져간다.

* 포트

  * `0.0.0.0:8200 [http]`
    * API 서버 겸 Web UI 서버

