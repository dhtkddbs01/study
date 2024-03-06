# UPDATE
1. UPDATE 명령어를 작성할 시에는 조건절이 누락되지 않도록 주의
2. 변경할 데이터는 해당 컬럼의 데이터 타입과 사이즈에 맞아야 함
3. UPDATE 문 수행 후에는 COMMIT을 해줘야 모든 작업이 완료
4. UPDATE 작업을 되돌이키고 싶을 때에는 ROLLBACK을 해줘야함
5. 조건절을 빼먹으면 모든 데이터가 변경됨
```SQL
-- 테이블 선택
select * from book_list;

-- set 변경사항 where 조건절
-- book_nm이 '도둑맞은 집중력'인 데이터의
-- reg_date 컬럼에 20230815데이터 입력 
update book_list set reg_date = '20230815' where book_nm = '도둑맞은 집중력';

-- 변경 사항 업데이트
commit;

-- 입력 오류(예시)
update book_list set writer ='오상윤';

-- 변경 취소
rollback;