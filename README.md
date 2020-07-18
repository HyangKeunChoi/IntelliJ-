### [인프런 - 웹 애플리케이션 개발을 위한 IntelliJ IDEA 설정](https://www.inflearn.com/course/%EC%9D%B8%ED%85%94%EB%A6%AC%EC%A0%9C%EC%9D%B4-%EC%9B%B9%EC%95%B1/dashboard)

#### IntelliJ IDEA 환경 설정

+ File -> Setting : intelliJ의 전반적인 환경설정
+ File -> Project Structure : 프로젝트 별로 독립적인 환경설정

#### 첫번쨰 웹 프로젝트 생성

+ New Project -> Maven -> Project SDK -> create from archetype 체크 -> 마지막에 maven-archetype-webapp선택

+ Bundled Maven - 내장되어 있는 버전

+ Maven 변경하면 우측하단에 Import changes라는 창이 뜬다.

+ 마우스 우클릭 genrate : 자동완성

+ servlet등록 하는 방법
  - 1. web.xml에 등록
  ```
     <servlet>
        <servlet-name>이름</servlet-name>
        <servlet-class>패키지명</servlet-class>
     </servlet>
     <servlet-mapping>
        <servlet-name>이름</servlet-name>
        <url-pattern>URL 명<url-pattern>
     </servlet-mapping>
  ```
  - 2. 어노테이션 활용
     클래스 위에 @WebServlet("/URL명")을 붙인다.

#### tomcat server에 등록
+ add Configuration -> +버튼 -> tomcat server -> local -> 톰캣 설정

+ (server 탭) : open browser -> 자동으로 실행되는 브라우저 선택/해제
                             -> URL : 기본 url
+ (Deployment 탭) : 우측 + -> myweb:war와 myweb:war exploded 있는데 exploded는 압축 해제 후 배포하는 방법을 의미(이거선택)

+ Application context : 8080포트 뒤에 설정하는 기본 접근 경로 

+ Tomcat과 Windows간의 환경 차이로 글자 깨지는 현상
  - Edit Configuration -> VM options : -Duser.language=en -Duser.region=us 입력


        
