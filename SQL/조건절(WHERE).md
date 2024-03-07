# WHERE
```sql
-- song 컬럼에 'I AM'인 데이터 출력
select * from melon_chart where song = 'I AM';

-- song 컬럼에 'I AM'혹은 'Spicy'인 데이터 출력
select * from melon_chart where song in ('I AM', 'Spicy');

-- 출력 결과 song = 'I AM'만 출력
-- song = 'I AM' or (song = 'Spicy' and singer = 'NewJeans') 이렇게 묶이기 때문 => and가 우선순위가 높다.
select * from melon_chart where song = 'I AM' or song = 'Spicy' and singer = 'NewJeans';

-- melon_chart 테이블에서 like_no가 100000이상 150000이하인 데이터 출력
select * from melon_chart where like_no between 100000 and 150000;
```

## 정규식
```sql
-- song 컬럼에서 '이브'로 시작하는 데이터 출력
select * from melon_chart where song like '이브%';

-- song 컬럼에서 '말해요'로 끝나는 데이터 출력
select * from melon_chart where song like '%말해요';

-- song 컬럼에서 'S'단어가 들어가는 데이터 출력
select * from melon_chart where song like '%S%';

-- song 컬럼에서 '정'으로 시작하는 두 글자 데이터 출력
select * from melon_chart where song like '정_';

-- song 컬럼에서 '정'으로 끝나는 세 글자 데이터 출력
select * from melon_chart where song like '__정';
```

### escape
```sql
-- '%'가 들어간 데이터 출력 (#바로 뒤에 오는 문자는 문자 그대로 인식)
select * from like_test where col like '%#%%' escape '#';
```