# CONV
- 숫자 기반 시스템을 다른 진법의 수로 표시
- CONV(데이터, 원본 진법, 변환할 진법)
  
```SQL
SELECT CONV(15, 10, 2)
FROM DUAL
-- 10진수 표시된 15를 2진수로 변환 --

SELECT CONV(1111, 2, 10)
FROM DUAL
-- 2진수로 표시된 1111을 10진수로 변환 --

SELECT CONV('F', 16, 8)
FROM DUAL
-- 16진수로 표시된 F를 8진수로 변환 -- 
```
