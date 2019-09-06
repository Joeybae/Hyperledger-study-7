# Hyperledger-study-7

하이퍼레져 앱 만들기 실습 7일차 - express ejs 네트워크 구성

출처 : https://victorydntmd.tistory.com/29#init

1. 프로젝트 생성

        # express -e seq-crud-exam
        # cd seq-crud-exam
        # npm install
        # npm install mysql2 sequelize
        # npm install -g sequelize-cli
        
2. sequelize 빌드

        # sequelize init
        
3. /config/config.json 수정

        {


          ...
          "development": {
            "username": "root",
            "password": "비밀번호를 입력해주세요.",
            "database": "접근할 데이터베이스를 입력해주세요.",
            "host": "127.0.0.1",
            "dialect": "mysql",
            "operatorsAliases": false
          },
          ...
        }
        
4. 모델 생성

        # sequelize model:create --name post --attributes "title:string, writer:string"
