# ALTER
alter로 가능한 작업
1. CHANGE : 컬럼명 변경
2. MODIFY : 컬럼의 데이터 타입 및 사이즈 변경
3. ADD : 컬럼 추가
4. DROP : 컬럼 삭제
5. RENAME : 테이블명 변경
```sql
-- book_list 테이블의 모든 컬럼 선택
select * from book_list;

-- book_list테이블에 description컬럼을 varchar(1000)인 타입으로 추가
alter table book_list add column description varchar(1000);

-- book_list테이블의 book_name컬럼의 데이터 길이를 varchar(100)으로 변경
alter table book_list modify column book_name varchar(100);

-- 테이블의 스키마 확인
desc book_list;

-- 컬럼의 이름을 description에서 book_desc로 변경
alter table book_list change column description book_desc varchar(1000);

-- book_list테이블에서 book_desc컬럼 삭제
alter table book_list drop column book_desc;

-- 테이블 명 변경
alter table book_list rename book_info;
```