# 2025.03.20

편리성
독립성
보안성

END

함수, 프로시저
선언
언제든지 호출이 가능 -> 재사용이 가능함

프로시저
함수처럼 저장하고 재사용할 수 있는 개념
SQL문을 실행할 수 있다.
JOBS테이블에 PK에 겹치는 값이 없으면 INSERT
PK에 겹치는값이있으면 내용을 UPDATE해라

PK에 값이 있으면 DELETE
값이 없으면 '값이 없습니다.'

프로시저에서 쓰이는 구문
SELECT...INTO
조회가 되서 나온결과를 변수에 할당
-----------------------------------
DECLARE 
   P_employee_id in e.employee_id%type,
   P_first_name in e.first_name%type
begin
 select
    employee_id,
    first_name
into p_employee_id, p_first_name
from employees
where employee_id = 100;
-----------------------------------
DECLARE 
   cnt number := 0;
begin
  select                            --->조회되는게있으면1 없으면0
      count(*)
into dnt
from jobs
where job_id = p_job_id;
-----------------------------------

트리거
지정한 테이블에 dml 또는ddl이 동작할때 실행되는 문법

before -> 지정된 테이블의 쿼리가 실행되기전
ㄴ유효성검사(넣으려는데이터가 유효한가? 검증)
after -> 지정된 테이블에 쿼리가 실행된후
ㄴ로그의 기록
-----------------------------------
:NEW
ㄴDML작업 후 새료 적용될 행의 값을 담고있는 변수
ㄴINSERT, UPDATE에서 많이 사용된다.
ㄴAFTER에서는 읽기전용으로 바뀐다.
:OLD
ㄴDML작업 이전의 행 데이터를 담고 있는 변수
ㄴDELETE, UPDATE에서 사용된다
ㄴINSERT는 기존행이 없으므로 :OLD를 사용할 수 없다.
-----------------------------------
CREATE OR REPLPACE TRIGGER 트리거명
(BEFORE OR AFTER_\)
(INSERT OR UPDATE OR DELETE) ON 테이블명
FOR EACH ROW
BEGIN 
      실행로직
END;
-----------------------------------
시퀀스
계속증가하거나 감소하는 숫자를 가지고 있는 객체
CREATE  SEQUENCE 시퀀스명
Start with 1 -> 1씩 카운팅
INCREMENT BY 1 ->1씩 증가
CACHE 20 -> 20개의 공간을 미리 확보하는것
NOCACHE -> 1개의 INDEX공간만 확보
-----------------------------------
시퀀스 값 수정하기
1. 시퀀스 삭제하고 다시만들기
2. 증가량을 음수로 만들어서 .NEXTVAL실행하고 1로만들기

INSERT INTO PERSON(PERSON_SEQ.NEXTVAL,'홍길동',40);

현재 시퀀스값 확인하기
ㄴ시퀀스명.CURRVAL

시퀀스 삭제하기
DROP SEQUENCE 시퀀스명

-----------------------------------

JAVA

JDK -> 자바 개발도구(자바 개발에 필요한 도구들이 포함)
ㄴ Oracle, Amazon, OpenJDK...
ㄴ LTS(Long Term Service) : 오랜기간 지원하는 버전
ㄴ 8, 11, 17, 21 (spring boot 가 17부터지원됨 왠만하면 17써라)
JVM(Java Virtual Machine) -> 자바 파일을 읽어서 실행해주는 프로그램
JRE(Java Runtime Enviorment) -> 자바 개발을 편하게 하기 위한 라이브러리들이 들어가 있다.
위를
바이트코드로 바꿧어야했는데 
바이트코드 -> 0,1로 이루어진 코드

컴파일 -> 자바 파일을 바이트 코드로 변환하는 과정
컴파일러 -> 컴파일 작업을 해주는 프로그램

클래스 파일 : 자바프로그램의 최소 단위
패키지 : 관련있는 기능이 있는 클래스끼리 묶어놓은 폴더
프로젝트 : 패키지의 묶음


-----------------------------------
클래스명은 파일의 이름과 같아야함

public class 클래스명{
       메인함수(자바프로그램이 실행되면 메인함수에 있는 코드가 실행된다)
       public static void main(String[] args){
                   System.out.println();
        }
}
-----------------------------------
pakage ex01_print;

public class EX1_ print {
      public static void main(String[] args) {

      //자바에서 문자열은 반드시 ""안에 넣어야한다
      //print() : 출력을 하고 줄을 바꾸지 않는다.
//     System.out.print("welcome");
//     System.out.print(" Java World")

     //println() : 출력을 하고 줄을 바꾼다.
       System.out.println("welcome");
       System.out.println("Java World")


   }
}


--------------------------------------
pakage ex01_print;

public class EX1_ print {
      public static void main(String[] args) {
          //자료형(기본자료형)
          //자바가 처리할 수 있는 데이터의 종류
          //논리형 boolean 1bit  true,false
          //문자형 char    2byte
          //정수형 byte 1byte   -128 ~ 127
          //      short 2byte  -32,768 ~ 32,767
          //      int   4byte  -21,4748,3648 ~ 21억
          //      long  8byte  -900경 ~ 900경
          //실수형 float 4byte
          //      double 8byte

          //float
          //메모리를 덜사용하면서 소수점을 포함한 숫자를 다룰수있다
          //하지만 정확도가 제한적이기 때문에 금융 계산이나 높은 정확도가
          //필요한 작업에 부적합하다.

          //double
          //훨씬 더 낣은 범위와 높은 정확도를 제공
          //과학적 계산, 통계, 시뮬레이션 등에서 사용

          //정수형을 쓸때 주의점
          //자료형이 표현할수 있는 범위를 벗어난 데이터를 저장하면
          //오버플로우가 발생해 전혀 다른값이 저장될수 있다.

          //오버플로우
          //자료형이 표현할 수 있는 최대범위보다 큰수를저장
          //발생하는 현상으로 잘못된결과를 얻을 수 있다.

          //언더플로우
          //자료형이 표현할 수 있는 최소 범위보다 작은 수를 
          //저장할 떄 발생하는 현상

          //문자형과 문자열
          //문자형(char)
          //한글자 짜리 데이터''안에 사용을 한다.
          //문자열(String)
          //문자들의 나열 ""안에 사용을 한다.

          //참조 자료형
          //메모리 상에 데이터가 저장된 주소를 저장하기위한 공간
          //대표적으로는 문자열을 저장하는 String 이 있다.
          //개발자가 직접 만들어 추가할 수 있는 자료형 이기 때문에
          //그 수가 정해져 있지는 않다.
    }
}

--------------------------------------

Stack 에는 정수, 실수, 문자형 등이 저장된다.
참조자료형은 Heap 이라는 공간에 데이터를저장한다. 그주소를 Stack에 저장한다.
Heap에 저장되는것은 문자열"문자열", 배열[1,2,3,4], 객체{  } 가 저장된다.

주소값에 매몰되지않기!

System.out.println <<<<복사

--------------------------------------

//printf()
//printf() 문자열속에서 다른타입의 데이터를 같이 출력할 수 있게 해주는 형식
//서식문자
//%d   정수(1진수)
//%o   정수(8진수)
//%x   정수(16진수)
//%s   문자열
//%c   문자형
//%b   논리형


sysout.printf("저는 대학교 4학년에 재학중입니다")

print






















  
