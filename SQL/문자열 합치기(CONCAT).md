# CONCAT
- 둘 이상의 문자열을 입력한 순서대로 합쳐서 반환해주는 함수
- CONCAT(문자열1, 문자열2, ... )
```SQL
SELECT CONCAT('분당구 수내로 13', 'A동 1107호')
-- 결과 : 분당구 수내로 13A동 1107호 -- 

SELECT CONCAT(SUBSTR(U.TLNO, 1, 3) , '-', SUBSTR(U.TLNO, 4,4) , '-' ,SUBSTR(U.TLNO, 8, 4)) AS '전화번호'
-- 이전 데이터 : 01053422914   =>  결과 : 010-5342-2914 -- 
```