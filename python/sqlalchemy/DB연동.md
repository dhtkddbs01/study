## DB연동
### database
- 특정 다수의 이용자들에게 조직 내에서 필요로 하는 정보를 체계적으로 축적하는 저장소
- 이 저장소에 자주 쓰이는 언어로 sql이 있다.

>
```python
# db연동
import sqlalchemy
# DB연동(sqlite)
engine = sqlalchemy.create_engine('sqlite:///test.sqlite')
# DB연동
conn = engine.connect()
# DB실행 구문(sql 로직)
conn.execute("CREATE TABLE test (col1 text, col2 text)")
conn.execute("INSERT INTO test VALUES ('test1', 'test2')")
conn.execute('select + from test').fetchall()
conn.close()
```