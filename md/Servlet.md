# Servlet
: SUN사에서 제안한 웹서비스를 위한 인터페이스로, 원칙적으로 javax.servlet.Servlet 인터페이스의 구현체 입니다. 일반적으로 자바 독립 실행과 달리 main 매소드가 없고, servlet container에 의해서 생성, 서비스, 소멸이 일어난다.
* Servlet은 Sever + Applet의 합성어라고 생각하면 쉽다 서버 어플 객체이다.
*  Servlet은 웹에서 java 프로그래밍을 구현하기 위해 탄생함
* JAVA로 구현된 CGI(Common Gateway Interface)라고함
* HTTP protocal 서비스를 지원하는 HttpServlet 클래스를 상속하여 개발하고, Servlet은 Container에 의해서 실행되고, 관리된다.
* HTTP 변경시 Servlet을 재컴파일 해야한다.

# Container
: 이러한 서블릿을 관리하며 네트워크 통신, 서블릿의 생명주기 관리, 스레드 기반의 병렬처리를 대행한다. 클라이언트로 부터  HTTP요청을 서비스하고, 응답해줍니다.
* HTTP 요청을 받아서 Servlet을 실행 시키고, 그 결과를 사용자 브라우저에게 전달하는 기능을 제공하는 컴포넌트이다.
* Servlet을 실행하고 생명주기를 관리하는 역할을 한다.
* Servlet과 웹서버가 서버와 통신할수 있는 방법을 제공한다.
* 대표적인 Container에는 tomcat이 있다.
* __GenericServlet__
:서비스 메소드를 제외한 나머지 Servlet 인터페이스의 매소드를 구현해 놓은 Abstract 클래스입니다. 이 클래스를 상속받아 실제 클라이언트의 REQUEST 처리에 필요한 service 매소드를 구현해 놓은 거이 바로 HttpServlet 입니다.
http://anster.tistory.com/128
모델1, 모델2 비교
# Servlet과 JSP 비교
|Servlet|JSP|
|:-------|:-------|
|자바코드로구현하고 컴파일하고 배포해야한다.|키워드가 태그화되어 서블릿에 비해 배우기 쉽다.|
|코드가 수정되면 다시 컴파일하고 배포하여야 한다.|자바코드를 스크립트릿(<% %>)이용하여야 한다.|
