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
        
5. /models/post.js 수정

        'use strict';
        module.exports = (sequelize, DataTypes) => {
          var post = sequelize.define('post', {
            title: {
              type: DataTypes.STRING,
              allowNull: false,
            },
            writer: {
              type: DataTypes.STRING,
              allowNull: false,
            }
          });
          return post;
        };

6. /migrations/20190720033800-create-post.js 수정

        'use strict';
        module.exports = {
          up: (queryInterface, Sequelize) => {
            return queryInterface.createTable('posts', {
              id: {
                allowNull: false,
                autoIncrement: true,
                primaryKey: true,
                type: Sequelize.INTEGER
              },
              title: {
                type: Sequelize.STRING,
                allowNull: false,
              },
              writer: {
                type: Sequelize.STRING,
                allowNull: false,
              },
              createdAt: {
                allowNull: false,
                type: Sequelize.DATE
              },
              updatedAt: {
                allowNull: false,
                type: Sequelize.DATE
              }
            });
          },
          down: (queryInterface, Sequelize) => {
            return queryInterface.dropTable('posts');
          }
        };
        
7. 변경 반영

        sequelize db:migrate

        npm start
        
8. 테이블 확인
        
        desc posts;
