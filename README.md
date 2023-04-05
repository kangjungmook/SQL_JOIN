## 조인 이란?
 join 또는 결합 구문은 한 데이터베이스 내의 여러 </br>
 테이블의 레코드를 조합하여 하나의 열로 표현한 것이다. </br>
 따라서 조인은 테이블로서 저장되거나, 그 자체로 이용할 수 있는 결과 셋을 만들어 낸다. </br>

## 내부 조인은?
 NNER JOIN(내부 조인)은 두 테이블을 조인할 때, 두 테이블에 모두 지정한 열의 데이터가 있어야 한다.

```sql
SELECT <열 목록>
FROM <첫 번째 테이블>
    INNER JOIN <두 번째 테이블>
    ON <조인 조건>
[WHERE 검색 조건]
```

> 예제
```sql
SELECT  LAST_NAME, DEPARTMENT_ID FROM EMPLOYEES where EMPLOYEE_ID = 176;
```

* INNER JOIN을 JOIN이라고만 써도 INOUTER JOIN


## 외부 조인은?
 테이블을 조인할 때, 1개의 테이블에만 데이터가 있어도 결과가 나온다.NER JOIN으로 인식합니다.

```sql
SELECT <열 목록>
FROM <첫 번째 테이블(LEFT 테이블)>
    <LEFT | RIGHT | FULL> OUTER JOIN <두 번째 테이블(RIGHT 테이블)>
     ON <조인 조건>
```

> 예제
```sql
SELECT LAST_NAME, DEPARTMENT_ID,
(SELECT DEPARTMENT_NAME FROM DEPARTMENTS D WHERE E.DEPARTMENT_ID = D.DEPARTMENT_ID)
FROM EMPLOYEES E;
```

## 셀프 조인은?
1개의 테이블(X)에 가상으로 x1, x2라는 별칭을 부여하여 2개의 테이블인 것처럼 간주한 뒤 JOIN하는 것입니다.

```sql
SELECT <열 목록>
FROM <테이블> 별칭A
    INNER JOIN <테이블> 별칭B
```

> 예제
```sql
SELECT  E.LAST_NAME, D.DEPARTMENT_NAME, L.LOCATION_ID, L.CITY
FROM EMPLOYEES E, DEPARTMENTS D, LOCATIONS L
WHERE E.DEPARTMENT_ID = D.DEPARTMENT_ID AND D.LOCATION_ID = L.LOCATION_ID AND E.COMMISSION_PCT IS NOT NULL;
```
