#오니온파이브 #Test
## 문제 상황
DB를 사용한 Integration Test 진행 시, django.db.utils.OperationalError: (1005, 'Can\'t create table `test_db`.`brand_restrict` (errno: 150 "Foreign key constraint is incorrectly formed")')
      에러 발생
## 문제 원인
테스트 실행 시, brand_restrict 테이블에서 FK로 member_main의 id값을 참조하고 있는 charge_member_id값 생성시에, 오류 발생
2023-11-08 03:04:20 0x14ffabcfa700 Error in foreign key constraint of table `test_db`.`brand_restrict`:
Alter  table `test_db`.`brand_restrict` with foreign key constraint failed. Referenced table `test_db`.`member_main` not found in the data dictionary ne ar ' FOREIGN KEY (`charge_member_id`) REFERENCES `member_main` (`id`)'.

## 해결 과정
- 데이터베이스 DDL문과, 테스트 실행 시 migration이 실행되는 부분이 동기화 되어있지 않아 생기는 문제라면
	- makemigration을 통해, DB테이블 생성
	- 이렇게 하면 추후 프로덕션 DB 테이블 구조가 변경되거나 추가될 때 마다 makemigration해야하는건 아닌지?
- DDL문을 복사해서 직접 DB 테이블 생성
	- 이 또한 위와 같은 문제점을 갖고 있을 듯(DB 변경시마다, DDL문을 통해 직접 테이블 생성해줘야 함)
- 현재 test DB로 sqlite3로 설정을 해서 생긴 에러인지 추측, 맞다면 testDB도 동일하게 mariaDB로 설정
	- 테스트용 DB와 프로덕션 DB 솔루션이 다르고, engine이 달라서 생긴문제라면 해당 방법이 맞을것이나
	- 다른 테이블들은 정상 생성 되고, brand_restrict에서 오류가 발생하는 것같아 가능성이 적어보임
- team-dev 환경이 존재하고 테스트 데이터들이 존재하니, 테스트용 DB도 local과 동일하게 연결하는게 좋을지 고민
	- 그렇다면 테스트때 마다 데이터가 더럽혀지지 않도록, rollback또는 truncate를 해줘야 할 수도
	- 그리고 기존 데이터로 인해 테스트 실패가 이루이지기에, 잘 부서지는 테스트가 될 수도
- managed false의 영향도 있을수도 있음
	- managed false는 delete되어도 상관없음
---
managed=false로 설정된 것으로 인한 문제였음
해당 값을 설정하게 되면, migration 파일로 DDL을 할 때, 제외되게 되는데 그 과정에서 제외된 테이블들에 연관 관계가 걸려있는 테이블들에서 에러가 발생함
- 따라서 현재, 우리 서비스에서는 마이그레이션 파일을 사용하고 있지 않기에 managed=false값을 삭제함
- 아니면 Migration이라는 클래스를 만들어서 직접 RAW SQL로 DDL 해주는 방법도 있음
	- https://stackoverflow.com/questions/7625674/utility-of-managed-false-option-in-django-models
- readonly와 default를 동시에 접근할 때 문제가 되었음
- 
## 참고 자료
