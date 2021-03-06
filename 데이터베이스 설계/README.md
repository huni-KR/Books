# 데이터베이스 설계

<img src=book_cover.jpg width="50%">

|||
|:------:|:---:|
|제목|데이터베이스 설계|
|저자|김은경|
|출판사|한국기술교육대학교 출판부|

<br>

---
## 책 선정 이유
  데이터베이스 수업을 수강한 적이 있지만 막상 데이터베이스를 직접 설계하려니 머리 속에 남아있는 데이터베이스 지식은 sql문 작성법뿐이었다. 그래서 정규화, 인덱스, 트랜잭션 등 데이터베이스 설계 및 운영에 관한 지식이 너무나 부족하다는 것을 알아버렸다.

  여러 데이터베이스 관련 도서 중 이 도서를 선택한 이유는 도서관에서 빌릴 수 있는 책 중 가장 깔끔했고 내가 부족한 기본 지식부터 친절히 설명하고 있어서 이 책을 선택하게 되었다.

---
## CHAPTER01 데이터베이스 개요

<br>

1. 데이터와 정보
    - 데이터 : 단순한 사실 또는 값
    - 정보 : 데이터가 목적에 의해 해석되거나 가공된 형태

<br>

2. 데이터베이스의 기원과 정의
    - 데이터베이스 : 한 조직의 응용 프로그램들이 공동으로 사용하는 데이터를 통합해서 저장한 운영 데이터의 집합
      - 공용 데이터 : 여러 응용 프로그램이 공동으로 사용하는 데이터
      - 통합된 데이터 : 여러 데이터를 통합하여 중복을 최소화함
      - 저장된 데이터 : 직접 호출이 가능한 데이터
      - 운영 데이터 : 응용 프로그램을 운영하는데 반듯이 필요한 데이터

<br>

3. 데이터베이스 특징
   - 동시 공용 : 같은 데이터를 동시에 사용해도 일관성의 문제가 없도록 관리
   - 지속적인 변화 : INSERT, DELETE, UPDATE 등을 지속적으로 수행
   - 실시간 접근성 : 사용자의 요청에 실시간으로 응답
   - 내용에 의한 참조 : 데이터의 주소나 위치가 아닌 내용에 의해 접근
   - DBMS에 의한 관리 : 데이터베이스를 효과적으로 구축하기 위해 DBMS 사용

<br>

4. 데이터베이스 출현 배경
    - 파일 관리 시스템의 문제점
        - 데이터의 중복 저장으로 인한 비효율성
        - 데이터의 일관성 유지 어려움
        - 데이터 무결성 유지 어려움
        - 데이터 공유 어려움

<br>

5. 데이터베이스의 개념적 구성요소
   - 개체 - Entity 
     - 개념이나 정보의 단위
     - 하나의 Entity는 하나 이상의 Attribute로 구성
   - 속성 - Attribute
     - Entity의 특성이나 상태를 나태내는 요소
     - 이름을 가진 정보의 가장 작은 논리적인 단위
   - 관계 - Relationship
     - Entity들 간의 의미 있는 연결 또는 연관성
     - Relationship도 하나의 Entity로 간주 될 수 있음

<br>

6. 데이터베이스의 저장 구조
   - 논리적 구조
     - 데이터 사용자가 바라보는 구조
     - 데이터가 배치된 가상적인 구조
     - 논리적 레코드 : 논리적 구조에서 취급하는 데이터 레코드
     - 응용 프로그램에서 주로 사용
   - 물리적 구조
     - 저장 장치에서 저장되는 실제 구조
     - 저장 레코드 : 물리적 구조에서 취급하는 데이터 레코드
     - 블록, 인덱스, 포인터, 체인, 오버플로우 영역 등

---
## CHAPTER02 데이터베이스 관리 시스템 개요

<br>

1. DBMS 정의
   - DBMS는 사용자와 DB의 중재자 역할
   - 응용 프로그램이 데이터에 종속되지 않는 데이터 독립성을 제공하는 것이 궁극적인 목표

<br>

2. DBMS 필수 기능
   - 데이터 정의 기능
     - 논리적 구조 기술
     - 물리적 구조 기술
     - 사상 명세 기술
   - 데이터 조작 기능
     - 사용자의 요구에 따라 검색, 갱신, 삽입, 삭제 등을 지원
   - 데이터 제어 기능
     - 무결성 유지
     - 보안 및 권한 검사 기능
     - 동시정 제어

<br>

3. DBMS의 장점
   - 데이터 동시 공유
     - 동시성 제어 기능을 통해 데이터를 각각의 응용 프로그램에서 동시 사용 가능
   - 데이터 중복 최소화
     - 파일 시스템에 비해 데이터 중복 최소화
     - 검색의 효율성을 위해 최소한의 데이터 중복 허용
   - 데이터 무결성 유지
     - 유효성 검사를 통해 허용되지 않은 값이나 부정확한 값 입력 방지
   - 데이터 일관성 유지
     - 데리터의 중복을 제어함으로써 데이터들 간의 불이치성 발생 방지
   - 프로그램과 데이터 간의 독립성 유지
     - 데이터와 응용 프로그램이 분리
     - 데이터 구조  변경으로 인해 프로그램 수정 필요 X
   - 효율적인 데이터 보안 관리
     - 분산 관리에 비해 접근 통제 효율적

<br>

4. DB 구조 - ANSI/SPARC
   <br>
   <img src=images/image027.jpg width="100%">
   - 외부 단계
     - 개별 사용자의 관점
     - DB의 일부분만 관심     
   - 개념 단계
     - DB에 관한 사용자 공동체의 관점
     - 한 그룹 전체를 위한 DB의 논리적 구조
   - 내부 단계
     - DB의 물리적 저장장치 관점
     - DB에 어떤 데이터가 어떻게 저장되는지
     - 내부 레코드 형식, 인덱스 유무, 저장 데이터 표현 방법 등
     - 실제 물리 단계보다 한 단계 위
     - 물리 단계는 DBMS의 지시에 따라 운영체제가 관리
   - 외부/개념 사상
     - 외부 스키마와 개념 스키마 간의 대응 관계 정의
     - 응용 인터페이스, 논리적 독립성
   - 개념/내부 사상
     - 개념 스키마와 내부 스키마 간의 대응 관계 정의
     - 저장 인터페이스, 물리적 독립성
   - 외부 스키마
     - 특정 사용자나 응용 프로그램이 접근하는 개별적인 DB 정의
     - 각각 필요로하는 개체와 관계만 포함
     - 한정된 논리적 데이터 구조
     - DB의 일부분만 표현 -> 여러 개의 외부 스키마 존재
     - Django의 View
   - 개념 스키마
     - 개념 스키마범 기관적인 관점에서 DB를 정의
     - 모든 사용자와 응용 프로그램이 필요로 하는 모든 데이터를 통함하여 구성
     - 그룹 전체 DB 기술 -> 단 하나의 개념 스키마 존재
     - 개체, 데이터 유형, 관계, 제약 조건, 접근 권한, 무결성 규칙 보안 명세 등 모두 포함
     - Django의 Model
   - 내부 스키마
     - 저장장치 관점에서 DB가 저장되는 방법 정의
     - 개념 스키마에 대한 저장구조 정의 -> 단 하나의 내부 스키마 존재
     - 저장될 내부 레코드 형식, 인덱스 유무, 저장 데이터 항목의 표현 방법, 내부 레코드의 물리적 순서 등
     - 시스템 카탈로그, 데이터 사전이라고도 부름

<br>

5. 데이터 독립성
   - 논리적 데이터 독립성
     - 응용 프로그램에 영향을 주지 않고 DB의 논리적 구조를 변경하는 것
     - 새로운 데이터 항목이나 레코드를 추가해도 현재 정의된 사용자의 관점이나 응용 프로그램 영향 X
     - 외부/개념 사상에 의해 논리적 데이터 독립성 보장
   - 물리적 데이터 독립성
     - 응용 프로그램과 DB의 논리적 구조에 영향을 주지 않고 물리적 구조를 변경하는 것
     - DB의 물리적 구조가 변경되더라도 논리적 데이터 구조나 응용 프로그램에 영향 X
     - 개념/내부 사상에 의해 보장

---
## CHAPTER03 데이터베이스 시스템 개요

<br>

1. 데이터베이스 시스템(DBS)의 구성
   - DBS는 데이터를 DB에 저장하고, DBMS를 사용하여 정보를 관리하는 컴퓨터 중심 시스템
   - DBS 구성 요소
     - DB : 데이터 저장
     - DBMS : DB 생성, 관리, 조작 - 사용자와 DB 연결하는 소프트웨어
     - 데이터 언어 : DB 정의, 조작, 제어를 위한 언어
     - DB 사용자 및 관리자 : 데이터 언어를 이용해 DB에 접근하는 사람
     - DB 컴퓨터 : DB에 대한 연산을 전담하는 DB 관리 컴퓨터

<br>

2. 데이터 언어
   - DB 정의, 조작, 제어를 위한 언어
   - 데이터 언어의 종류
     1. DDL - 데이터 정의어
         - DB 구조 정의, 변경을 위해 사용하는 언어
         - DB 스키마를 DBMS가 이해할 수 있도록 작성하는데 사용
         - DB 관리자나 설계자가 사용
     2. DML - 데이터 조작어
         - 사용자 및 응용 프로그램과 DBMS 사이 통신 수단
         - DBMS가 데이터를 처리할 수 있도록 기술하는 언어
         - 데이터 검색, 삽입, 삭제, 변경 및 다양한 연산
         1. Procedural(절차적) DML
            - 무슨 데이터를 어떻게 접근하여 처리하는지 기술하는 저수준 데이터 언어
            - 한 번에 하나의 레코드 처리
            - 응용 프로그램 속에 삽입하여 사용
            - 사용이 어려움
         2. Nonprocedural(비절차적) DML
            - 무슨 데이터를 원하는지만 기술
            - 어떻게 접근하여 처리하는지는 DBMS에게 위임하는 고수준 데이터 언어
            - 데이터 검색 방법을 DBMS에게 위임함으로 독자적으로 사용 가능
            - SQL Query가 여기에 속함
     3. DCL - 데이터 제어어
         - 내부 규정에 따라 데이터 제어 정의하고 기술하는 언어
         - 주로 관리자가 사용
         - DCL 포함 내용
           - Security : 권한이 없는 사용자로부터 데이터 보호하기 위한 데이터 보안
           - Integrity : 데이터의 정확성을 유지하기 위한 데이터 무결성
           - Recovery : 시스템 장애에 대비한 데이터 복구
           - Concurrency control : DB에 대한 동시 접근을 처리하기 위한 동시성 제어

<br>

3. DB 사용자
   1. 일반 사용자
      - Query 사용하여 DB 접근
      - Terminal User / End User로 칭함
   2. 응용 프로그래머
      - 호스트 언어를 사용해 DML이나 DSL을 삽임하여 DB에 접근
      - 프로그래밍 개발 능력과 DB 지식 갖춰야함
   3. 관리자
      - DB 시스템이 원활히 작동할 수 있도록 관리 및 운영에 대한 책임
      - DB 설계, 구축, 변경 계획 수립
      1. DB 설계 및 운영
      2. 행정 관리 및 불만 해결
      3. DB 시스템 감시 및 성능 분석

<br>

4. DB 컴퓨터
  <br>
  <img src=images/image044.jpg width="100%">
   - 대규모 DB를 사용하기 위해서는 DB 관리 전용 컴퓨터 필요
   - DB 규모가 작을 경우 필요 X

<br>

5. DBMS의 구성 요소
   1. DBMS 연산 수행 절차
       1. 사용자의 접근 요구 분석
       2. 사용자 요구를 시스템이 이해할 수 있는 형태로 변환
       3. 외부 스키마 - 외부/개념 사상 - 개념 스키마 - 개념/내부 사상 - 내부 스키마 - 저장 구조의 순으로 거치며 저장된 데이터에 접근
       4. 필요한 연산 수행
   2. DBMS 관리 시스템의 구성 요소
  <br>
  <img src=images/image045.jpg width="100%">
      1. 질의어 처리기
      2. DML 예비 컴파일러
      3. DML 컴파일러
      4. DDL 컴파일러
      5. 트랜잭션 관리자
      6. 런타임 데이터베이스 처리기
      7. 저장 데이터 관리자

---
## CHAPTER04 데이터 모델링 개요

<br>

1. 데이터의 구분
    1. 데이터 3가지 관점
       - 11
    3. 
2. 