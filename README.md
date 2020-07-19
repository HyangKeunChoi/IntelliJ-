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

#### JSP파일 생선

+ JSP파일은 변경해도 바로 반여안될수도 있따. (War파일 형태로 결오 지정되어있으면)

+ 해결 : output directory를 war파일이 아닌 src > main > webapp으로 변경한다.

#### 서버 개발 환경

+ local : 개발자 개인환경

+ Dev : 로컬환경에 있는 코드를 하나로 합치는 환경 + 각종 테스트 환경

+ Integration : Dev들의 집합(Dev를 하나의 모듈 코드라고 생각한다면), 없을수도 있는 환경

+ QA : QA엔지니어들이 사용하는 환경 - Integration / Dev 환경

+ Staging : 운영환경과 거의 동일한 환경, 비 기능적 테스트환경(보안, 성능, 장애)

+ Production : 서비스 운영 환경

#### Maven 빌드와 Tomcat Server 실행

+ maven compile : 컴파일 오류나는지 확인하는 작업

+ maven clean : target 폴더를 삭제하는 작업

+ maven package : compile + package + test + 지정된 폴더로 이동하는 작업 (war파일로 생성)

+ 위에 말한 war파일이 생성되면 복사해서 -> tomcat설치 경로로 이동 -> webapps붙여넣기

+ 이제 서버 재기동
  - 방법 1 : bin 디렉토리 이동 -> startup.bat 파일 더블클릭
  - 방법 2 : cmd로 bin디렉토리 이동 -> 명령어 : startup.bat
  
+ 톰캣 폴더 -> webapps로 이동해보면 -> .war파일의 압축이 해제 되어있는것을 볼 수 있다.

#### 톰캣 manager 이용

+ 새로운 브라우저 탭에 localhost:8080/manager 입력 하면 사용자 입력정보창이 나온다.

+ 이 사용자 입력정보창 설정하는 방법
  - 톰캣 중지 : shutdown.bat
  - cd conf로 이동 / tomcat-users.xml을 연다. (VSCODE나 메모장)
  - <role rolename = "manager" />
  - <role rolename = "manager-gui" />
  - <role rolename = "manager-script" />
  - <role rolename = "manager-jmx" />
  - <role rolename = "manager-status" />
  - <role rolename = "admin" />
  - <user username="admin" password="tomcat" roles="manager, manager-gui, ....(중략)..... " />
  - 톰캣 재기동
  - /manager 다시 접속 -> 계정입력
  








        
