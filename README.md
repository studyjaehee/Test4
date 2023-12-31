# Test4


### 과제 : 모의 컨설팅

#### 1. 주요한 자산
  - 보안의 3요소는 기밀성, 무결성, 가용성이 있다.
  - 기밀성은 인가된 사용자만 시스템에 접근해야하는 원칙이다.
  - 무결성은 고의적인, 비인가된 변경으로부터 보호되어야 한다는 원칙이다.
  - 가용성은 사용자가 필요로 하는 시점에 접근 가능해야 한다는 원칙이다.
  - 이 중 고객에게 가장 중요한 요소는 기밀성이라고 생각하는데, 인가된 사용자에게만 정보 자산에 접근할 수 있어야 그 뒤에 무결성과 가용성이 지켜진다고 생각하기 때문이다.

#### 2. 공격 시나리오 준비
  - 모의해킹으로 컨설팅 한 [웹페이지](https://demo.testfire.net/)는 다음과 같다.


    ![컨실팅 페이지](https://github.com/studyjaehee/Test4/assets/91130771/4b17d054-5f56-4a0c-ad75-2d83177b06c2)

  - ibm에서 제공하는 사이트로 취약점을 점검할 수 있도록 설계한 사이트이다.
  - 먼저 취약점으로 발견한 것은 SQL 인젝션 취약점과 XSS 취약점이다.
  - 취약점을 공격 후에 공격 결과 및 보완 방법에 대해 설명하려고한다.

#### 3. 공격 시나리오 및 결과
  - SQL 인젝션
  - 공격자는 boardID 값으로 악성 SQL 쿼리문을 전송한다.
  - ' or 1=1-- 이 쿼리문을 전송했을 때 관리자 권한으로 로그인을 성공했고, 모든 게시물을 조회할 수 있었다.
  - 조회 가능한 정보는 고객들의 최근 거래 내용 및 다른 고객에게 이체 그리고 고객들의 정보까지 관리할 수 있었다.
  - SQL 인젝션 공격이 성공함에 따라 보안의 3요소 중에 기밀성, 무결성을 지키지 못 하였다.
    
    ![컨설팅_sql인젝션_시도](https://github.com/studyjaehee/Test4/assets/91130771/98f382e7-664b-4559-8b79-dd602b21dea5)

    ![컨설팅_sql인젝션_성공](https://github.com/studyjaehee/Test4/assets/91130771/86646ab2-c1af-44dd-b4c1-40f76030656e)

  - XSS 취약점 공격
  - XSS 취약점 공격은 웹 사이트의 취약점을 이용하여 악성 스크립트를 실행하는 공격이다.
  - 공격자는 search 창에 다음과 같은 악성 스크립트를 삽입할 수 있다.
  - <script>alert(document.cookie);</script> 이 스크립트를 실행하면 경고창이 발생하게 된다.
  - 공격자는 사용자의 브라우저에서 정보를 수집하거나, 악성 코드를 실행할 수 있다.
  - XSS 취약점 공격이 성공함에 따라 보안의 3요소 중에 기밀성, 무결성을 지키지 못 하였다.

    ![컨설팅_xss_시도](https://github.com/studyjaehee/Test4/assets/91130771/7634e08a-8c5b-4dd7-8dac-b0739cd229e2)

    ![컨설팅_xss_성공](https://github.com/studyjaehee/Test4/assets/91130771/d0e23a58-f6d7-490c-a4a5-ca47170eb520)


#### 4. 취약점 보완 방법
  - SQL 인젝션
  1. 입력값 검증 : 입력값을 검증하여 악성 SQL 쿼리문이 삽입되지 않도록 한다.
  2. PreparedStatement 사용 : SQL 쿼리문을 작성 중 변수를 사용할 때 반드시 PreparedStatement를 사용하여 인젝션 공격을 방지한다.
  3. 보안 업데이트 : 웹 사이트의 보안 업데이트를 주기적으로 실시하여 취약점을 보완한다.

  - XSS 취약점 공격
  1. 입력값 검증 : 입력값을 검증하여 악성 스크립트가 삽입되지 않도록 한다.
  2. HTML 태그 제거 : 게시물의 내용을 출력할 때는 HTML 태그를 제거하여 악성 스크립트가 실행되지 않도록 한다.
  3. 보안 업데이트 : 웹 사이트의 보안 업데이트를 주기적으로 실시하여 취약점을 보완한다.





    
