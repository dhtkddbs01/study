# DATE_FORMAT
DATE_FORMAT(날짜 , 형식) 
날짜를 지정한 형식으로 출력
- %Y : 4자리 년도 
- %m : 숫자 월 ( 두자리 ) 
- %y : 2자리 년도  
- %c : 숫자 월(한자리는 한자리)  
- %M : 긴 월(영문) 
- %d : 일자 (두자리)  
- %b : 짧은 월(영문)  
- %W : 긴 요일 이름(영문)  
- %I : 시간 (12시간) 
- %H : 시간(24시간) 
- %i : 분  
- %r : hh:mm:ss AM,PM  
- %T : hh:mm:SS 
- %S : 초

```SQL
SELECT DATE_FORMAT(NOW(),'%Y-%m-%d') AS DATE FROM DUAL
-- 2016-09-22 -- 

SELECT DATE_FORMAT(NOW(),'%Y %M %d') AS DATE FROM DUAL
-- 2016 September 22 --

SELECT DATE_FORMAT(NOW(),'%Y년%m월%d일 %H시%i분%S초') AS DATE FROM DUAL
-- 2016년09월22일 17시00분05초 --
```
