# OpenKiosk_server
- 본 프로젝트의 핵심이 되는 기능을 우선적으로 구현
+ 핵심 기능
  - Amazon API를 활용한 리뷰 분석
  - 리뷰에 대한 통계 도출(긍정,부정 평가)
  - 매출 통계

## 자바 환경변수
- JAVA_HOME 추가 = 설치 경로
- ex\) C:\Program Files\Java\jdk1.8.0_131
- Path 수정 = %JAVA_HOME%\bin
- CLASSPATH 추가 = %JAVA_HOME%\lib

## TomCat 설치 후 프로젝트 생성
- 톰캣 설치시 **jre** 필요
- 설치 후 Intellij에서 web 프로젝트 생성
![logo](https://i.kym-cdn.com/entries/icons/original/000/013/564/doge.jpg)

- 프로젝트 설정시 Tomcat 설치 위치 지정
- 프로젝트 이름을 설정하고 Finish  

## request 메소드에 빨간줄 해결법
intellij jsp cannot resolve method <>

- 이는 servlet-api가 프로젝트에 설정이 안되어 있어서 그런거니 다음 사진을 보고 해결하면 됨. 기본적으로 톰캣을 설치시 톰캣 lib 폴더에 들어있음.
![01](./readmeImg/request_error.JPG)
빨간줄이 뜸  

![02](./readmeImg/request_error_02.JPG)
FIle -> Project Structure -> +

![03](./readmeImg/request_error_03.JPG)
tomcat 설치 폴더의 lib폴더에서

![04](./readmeImg/request_error_04.JPG)
servlet-api.jar 선택  

![05](./readmeImg/request_error_05.JPG)
Apply를 눌러 마무리  

![06](./readmeImg/request_error_06.JPG)

## run jws 실행 문제  
- 아직 해결이 안되서 그냥 서버를 돌리고 URL을 입력하여 직접 접근하는 방식을 사용하고있음.
- 혹시 아시는분은 hwansang5@gmail.com 으로 알려주시길 바랍니다...
---
## 2019-06-24
- 프로젝트 생성 및 Hello world 출력
![test](./readmeImg/helloworld.JPG)
## 2019-06-25

intellij jsp war exploded

- 처음 실행하면 못보던 폴더인 **out 폴더가** 생성
- 이는 run하는 과정에서 war 파일이 풀어지면서 배포 가능한 형태로 생성되는 것
- 이는 Project Structure 에서 몇가지 옵션을 건들면 잡다하게 파일을 생성하는게 아닌 **zip 파일 하나로** 만들수도 있음  

![01](./readmeImg/Project_Structure.JPG)

![02](./readmeImg/Project_Structure_02.JPG)

![03](./readmeImg/war_zip.JPG)
[참고 사이트 : https://whitepaek.tistory.com/27](https://whitepaek.tistory.com/27)

### 웹서비스 동작 원리
 웹서비스는 **[클라이언트-서버](https://ko.wikipedia.org/wiki/%ED%81%B4%EB%9D%BC%EC%9D%B4%EC%96%B8%ED%8A%B8_%EC%84%9C%EB%B2%84_%EB%AA%A8%EB%8D%B8)** 구조로 구성되어있습니다. 서버는 서비스를 제공하는 컴퓨터이고, 클라이언트는 서비스를 이용하는 사용자입니다. 이러한 동작은 요청과 응답이라는 매커니즘을 통해 동작합니다.
![원리](https://i.imgur.com/kvuq6xA.png)  
[ 그림 출처 : https://cloudstudying.kr/lectures/58#web-service](https://cloudstudying.kr/lectures/58#web-service)
간단히 설명하면 어떠한 버튼을 눌러 링크를 불러오게 되는 행위(예를 들어 웹툰)은 **『요청』** 이 되는것이고 누르는 행위에 대해 새로운 페이지가 열리는(웹툰링크를 타고 페이지가 열리는) 동작이 수행되면 이는 **『응답』** 행위가 수행된것입니다.

### JSP(Java Server Pages)
jsp는 HTML과 자바 코드를 같이 사용할 수 있게 해주는 스크립트 언어입니다. 사용 형태는 HTML 코드 사이에 **<% %>** 구문이 적혀있고 그 사이에 원하는 동작(**Java코드**)을/를 지정하면 알아서 서버측에서 재해석 및 변환하여 웹페이지에 적용시킵니다.
![동작](https://i.imgur.com/kV314tG.png)
[그림 출처 : https://i.imgur.com/kV314tG.png](https://i.imgur.com/kV314tG.png)
+ JSP 태그 <% %>
  - <%@  지시지, 페이지 속성 지정 @%>
  - <%-  주  석, 페이지 설명 작성 -%>
  - <%!  선  언, 변수/메쏘드 선언 !%>
  - <%=  표현식, 결과를 문자열로 출력 =%>
  - \<jsp:action> [자바빈](https://ko.wikipedia.org/wiki/%EC%9E%90%EB%B0%94%EB%B9%88%EC%A6%88) 또는 [애플릿 모듈](https://ko.wikipedia.org/wiki/%EC%9E%90%EB%B0%94_%EC%95%A0%ED%94%8C%EB%A6%BF)과 연동 </jsp:action>

## 2019-06-26
- request, response, form을 활용해 로그인/로그아웃 예제 실습
- get, post 를 활용하여 데이터를 주고받는 실습을 진행함.
![01](./readmeImg/getpostTest.JPG)
![02](./readmeImg/getpostTest_02.JPG)
+ 여기에서 더 확장해보겠음
  - 인증이 실패하면 form.jsp를(form_02로 작성)
  - 성공하면 welcome.jsp를 수행

![01](./readmeImg/Login_example_01.JPG)
form_02.jsp

![02](./readmeImg/Login_example_02.JPG)
welcome.jsp

![03](./readmeImg/Login_example_03.JPG)
fail form_02.jsp

## 2019-07-29
- 그래프 띄우는 부분을 좀더 세분화하여 나타낼수 있도록 수정
