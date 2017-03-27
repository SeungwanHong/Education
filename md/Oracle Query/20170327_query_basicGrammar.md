1) 사번,이름,부서번호,매니저코드(MANAGER 변경),연봉(연봉으로 변경) 나오게하고 매니저코드는 NULL이면 CEO나오게하고
연봉이 8000 ~ 10000 '거지'
10000~12000 '조금거지'
12000~14000 '조금덜거지'
14000~20000 '덜거지'
이외        '덜부자'
연봉 오름차순 하기
```
SELECT EMPNO, ENAME,DEPTNO,
DECODE(MGR, NULL,'CEO',MGR) AS MANAGER,
SAL*12 AS "연봉",
CASE
WHEN SAL*12>=8000 AND SAL*12 <=10000 THEN '거지'
WHEN SAL*12>=10000 AND SAL*12 <=12000 THEN '조금거지'
WHEN SAL*12>=12000 AND SAL*12 <=14000 THEN '조금덜거지'
WHEN SAL*12>=14000 AND SAL*12 <=20000 THEN '덜거지'
ELSE '덜부자'
END
FROM EMP ORDER BY SAL*12;
;
```
3) 직업이 MANAGER, PRESIDENT 인 사람들의 입사날짜,직급,연봉(기본급여 + 커미션으로)을구하세요.(연봉 오름차순)
```
SELECT HIREDATE, JOB, SAL+NVL(COMM,0)
FROM EMP
WHERE JOB = 'MANAGER'
OR JOB = 'PRESIDENT'
ORDER BY SAL+NVL(COMM,0) ASC
;
```
4) 81년도에 입사한 사람은 '팔십일' , 82년도에 입사한 사람은 '팔십이'(이외의 년도는 출력 X) 라고 이름, 입사년도와 함께 출력.
```
SELECT ENAME,  DECODE(TO_CHAR(TRUNC(HIREDATE,'YEAR'),'YY'),'81','팔십일','82','팔십이','출력 X') AS "입사년도"
FROM EMP;
```
5)이름이 6자인 사원들의 사원번호, 성, 이름 출력

6)4000달러 대와 6000달러 대의 급여를 받는 사원들의 성, 직무, 급여 출력

7)사번,이름, 오늘날짜, 고용일, 월차(직원들의 근무한 (개월수+1)를 구하여라) 테이블 컬럼은 한글로 표시하고 월차 별로 내림차순 급여순으로 오름차순 하여 출력하시오
```
SELECT EMPNO AS "사번", ENAME AS "이름", SYSDATE AS "오늘 날자", HIREDATE AS "고용일", MONTHS_BETWEEN(SYSDATE, HIREDATE)+1 AS "월차"
FROM EMP
ORDER BY MONTHS_BETWEEN(SYSDATE, HIREDATE) DESC, SAL ASC;
```
8)지금까지 받은 급여의 총합을 구하시오,커미션는 해당 2번씩 받는다.
이름, 직책, 급여의 총합 출력
```
SELECT ENAME, JOB,  (MONTHS_BETWEEN(SYSDATE,HIREDATE)*SAL) + ((MONTHS_BETWEEN(SYSDATE,HIREDATE)/12)*2*NVL(COMM,0)) AS "급여의 총합"
FROM EMP
```
9)직책 안에 AN이 들어갈때, 연봉이 20000이상이고 커미션을 받지 않은 사람의 이름 구하고 연봉을 기준으로 오름차순으로 구하라
```
SELECT ENAME
FROM EMP
WHERE JOB LIKE '%AN%'
AND SAL*12 >= 20000
AND COMM IS NULL
ORDER BY SAL ASC;
```
10)1983/05/21부터 1997/10/21 까지 입사한 사람중에 급여가 2000이상인 사람은 많이 번다. 미만인 사람은 적게 번다.
```
SELECT DECODE(SAL>=2000,'많이 번다','적게번다')
FROM EMP
WHERE HIREDATE BETWEEN 1983/05/21 AND 1997/10/21
;
```
