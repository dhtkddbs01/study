# RIGHT
- RIGHT : 문자에 오른쪽을 기준으로 일정 갯수를 가져오는 함수.
- RIGHT(문자, 가져올 갯수);
```SQL
SELECT RIGHT('abcdefg', 3);
-- 결과 : efg --
```
# LEFT
- LEFT : 문자에 왼쪽을 기준으로 일정 갯수를 가져오는 함수
- LEFT(문자, 가져올 갯수)
```SQL
SELECT LEFT('abcdefg', 3);
-- 결과 : abc --
```
# MID
- MID : 문자에 지정한 시작 위치를 기준으로 일정 갯수를 가져오는 함수.
- SUBSTR과 같음
- MID(문자, 시작 위치, 가져올 갯수)
```SQL
SELECT MID('abcdefg', 2, 4);
-- 결과 : bcde --```