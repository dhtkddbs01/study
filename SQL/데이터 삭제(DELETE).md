# DELETE 
1. 조건절이 누락되지 않도록 주의
2. commit을 해줘야 모든 작업이 완료
3. 되돌이키고 싶을 때에는 rollback을 해주면 된다.
```sql
-- book_list 테이블 선택
select * from book_list;

-- 조건에 해당하는 행 단위 데이터 삭제
-- book_list에서 publisher 컬럼 데이터가 '북로망스'인 행 데이터 삭제
delete from book_list where publisher = '북로망스';

-- 변경사항 업데이트
commit;

-- book_list의 모든 데이터 삭제
delete from book_list;

-- 변경사항 되돌리기
rollback;
```