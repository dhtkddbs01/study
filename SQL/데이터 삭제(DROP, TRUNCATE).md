# DROP
1. 테이블과 데이터를 모두 삭제하는 명령어
2. 실행하면 돌이킬 수 없다(ROLLBACK 불가능)
```sql
-- book_list 테이블에 있는 모든 데이터 선택
select * from book_list;

-- book_list 테이블과 데이터 모두 삭제
drop table book_list;
```

# TRUNCATE
1. 데이터만 삭제하는 명령어
2. 특정 행만 삭제할 수가 없기 때문에 `반드시 모든 행을 통째로 삭제하는 경우에만 사용`
3. 실행하면 돌이킬 수 없다(ROLLBACK 불가능)
```SQL
-- book_list 테이블에 있는 모든 데이터 선택
select * from book_list;

-- book_list테이블에 있는 모든 데이터 삭제
truncate table book_list;
```