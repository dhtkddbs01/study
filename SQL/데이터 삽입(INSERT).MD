# INSERT
1. 두 가지 타입의 insert
   1. 전체 컬럼에 대한(insert into 테이블 values (변수1, 변수2,,,))
   2. 선택 컬럼에 대한(insert into 테이블 (컬럼1,컬럼3,,,,) values (변수1, 변수3,,,,))
2. 데이터를 insert할 시에는 반드시 해당 컬럼의 데이터 타입과 사이즈에 맞춰야 한다
3. insert 문 수행 후에는 commit을 해줘야 모든 작업이 완료가 된다
4. insert 작업을 되돌이키고 싶을 때에는 rollback을 해주면 된다
   
```sql
-- book_list 테이블 선택
select * from book_list;

-- 테이블 컬럼이 추가되거나 제거되면 오류 발생
-- 데이터의 변수는 컬럼의 수와 동일하게 삽입되어야함, 
insert into book_list values ('97911917891287', '메리골드 마음 세탁소', '윤정은', '북로망스', 15000);

-- 테이블 컬럼이 추가되거나 제거되어도 오류 발생X
-- 선택한 컬럼에 해당하는 데이터만 입력(not null 컬럼의 경우 제외 불가)
insert into book_list (book_no, book_nm, writer, publisher, price)
values ('9791167740984', '도둑맞은 집중력', '요한하리', '어크로스', 18800);

-- insert한 내용 업데이트
commit;

-- 잘못 입력된 데이터(예시)
insert into book_list values ('97911918991000', '메리골드 마음 세탁소', '윤정은', '북로망스', '20230306', 15000)

-- 입력한 데이터 취소하기
rollback;
```