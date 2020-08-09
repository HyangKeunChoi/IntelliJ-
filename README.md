### [인프런 - 웹 애플리케이션 개발을 위한 IntelliJ IDEA 설정](https://www.inflearn.com/course/%EC%9D%B8%ED%85%94%EB%A6%AC%EC%A0%9C%EC%9D%B4-%EC%9B%B9%EC%95%B1/dashboard)

#### IntelliJ IDEA 환경 설정

+ File -> Setting : intelliJ의 전반적인 환경설정
+ File -> Project Structure : 프로젝트 별로 독립적인 환경설정

#### 첫번째 웹 프로젝트 생성

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

#### JSP파일 생성

+ JSP파일은 변경해도 바로 반영안될수도 있다. (War파일 형태로 경로 지정되어있으면)

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
  - ```<role rolename = "manager" />```
  - ```<role rolename = "manager-gui" />```
  - ```<role rolename = "manager-script" />```
  - ```<role rolename = "manager-jmx" />```
  - ```<role rolename = "manager-status" />```
  - ```<role rolename = "admin" />```
  - ```<user username="admin" password="tomcat" roles="manager, manager-gui, ....(중략)..... " />```
  - 톰캣 재기동
  - /manager 다시 접속 -> 계정입력
  
### [인프런 - IntelliJ를 시작하시는 분들 위한 IntelliJ 가이드](https://www.inflearn.com/course/intellij-guide/dashboard)

#### Toolbox 소개

+ community verison : 웹과 관련되것 사용하지 못한다.(JSP, JS, 스프링 사용 불가)

+ 툴박스에서 heapsize 조절 가능

+ update to 
  - Release     : 릴리즈버전 업데이트
  - Release EAP : 프리뷰버전까지 업데이트
  
#### 프로젝트 생성
+ create project -> Java프로젝트보다는 gradle이나 maven 선택 !
  - 이유 : gradle이나 maven의 빌드환경을 추천하는 이유는 자바 어플리케이션을 개발한다 해도 Junit라이브러리나 Apache Commerce같은 
  유틸성 라이브러리를 사용할 경우가 많아 편리하게 이용할 수 있다.
+ groupId : 프로젝트 그룹 ex) 스프링 프로젝트
+ ArtifactId : IntelliJ-guide로 작성

#### Gradle Projects need to be imported
+ Import changes : Build.gradle이 변경될 때 개발자들이 수동으로 Build.gradle을 새로 고침해서 반영
+ Enable Auto-Import : Build.gradle을 변경사항이 생기면 자동으로 반영

#### OS별 단축키 플러그인 설치

+ action검색이용 (ctrl+shift+A) -> plugins -> presentation Assistant 설치

#### 메인메소드 생성하고 실행하기

+ 단축키 
  - mac : command + N
  - windows/linux : alt + insert
  - directory 선택 : src/main/java 
+ main메소드 자동완성 : psvm + enter (public static void main)

+ system.out.println 자동완성 : sout + enter
+ 실행 : 좌측 실행버튼 (▶) 또는 ctrl + shift + F10 (mac은 ctrl + shift + R)

+ 이전 프로젝트 실행하기 
  - mac : ctrl + R
  - windows/linux : shift + F10 ( 둘다 기준은 우측 상단 셀렉트박스 - Edit configuration 쪽)

#### 라인 수정하기

+ 맥 : command <-> win : ctrl 와 거의 대응된다.

+ 맥 : option <-> wind : alt 와 거의 대응된다.

+ 라인 복사하기 
  - mac : command + D
  - windows/linux : ctrl + D
      
+ 라인 삭제하기 
  - mac : command + delete
  - windows/linux : ctrl + Y

+ 문자열 라인 합치기 
  - mac/windows/linux : ctrl + shift + J (상단으로 이동, 라인단위로 이동)

+ 라인 단위로 옮기기 : mac : option + shift + ↕, windows/linux : alt + shift + ↕
  
  - 메소드를 벗어 나지 못하게 하는 경우 
  - mac : command + shift + ↕
  - windows/linux : ctrl + shift + ↕
  
+ Element 단위로 옮기기 : html, xml같은 것들의 id값이나, name
  - mac : command + option + shift + <->
  - windows/linux : ctrl + shift + alt + <->

#### 코드 즉시보기

+ 인자값 즉시 보기(생성자, 메소드 등 전부 미리보기) 
  - mac : command + P
  - windows/linux : ctrl + P

+ 코드 구현부 즉시 보기(메소드나, 인스턴스나, 클래스) 
  - mac : option + space
  - windows/linux : shift + ctrl + I
  - 얼티메잇버전은 html, JS, css도 즉시 볼 수 있다.

+ Doc 즉시보기 
  - mac : F1
  - windows/linux : ctrl + Q

#### 포커스 에디터

+ 단어별 이동 
  - mac : option + <->
  - windows/linux : ctrl + <->

+ 단어별 선택 
  - mac : option + shift + <-> 
  - windows/linux : ctrl + shift + <->

+ 라인 첫/끝 이동 
  - mac : fn + <-> 
  - windows/linux : home, end

+ 라인 전체 선택 
  - mac : fn + shift + <-> 
  - windows/linux : shift + home/end

+ page up/down 
  - mac : fn + ↕
  - windows/linux : page up + page down

#### 포커스 특수키

+ 포커스 범위 한 단계씩 늘리기 
  - mac : option + ↕
  - windows/linux : ctrl + W / ctrl + shift + W

+ 포커스 뒤로 / 앞으로 가기 
  - mac + [ / ]
  - windows/linux : ctrl + alt +  <->

+ 멀티포커스 : 여러코드를 한번에 수정 
  - mac : option 2번 + ↕
  - windows/linux : ctrl +2번 + ↕  (option, ctrl 누르고 있어야함)

+ 오류 라인으로 자동 포커스 : f2

#### 검색 텍스트

+ 현재 파일에서 검색 : mac : command + F / windows/linux : ctrl + F

+ 현재 파일에서 교체 (replace) : 
  - mac : command + R 
  - windows/linux : ctrl + R

+ 전체에서 검색(전체 프로젝트) : 
  - mac : command + shift + F 
  - windows/linux : ctrl + shift + F

+ 전체에서 교체(프로젝트 전체에서 replace) 
  - mac : command + shift + R 
  - windows/linux : ctrl + shift + R

+ 정규표현식으로 검색, 교체 
  - mac : shift + F -> regex 
  - windows/linux : ctrl + shift + F -> regex

#### 검색 - 기타

+ 파일 검색 (패키지 까지 검색,  패키지/클래스 순서대로 입력하면 클래스도 검색가능) 
  - mac : command + shift + O
  - windows/linux : ctrl + shift + n

+ 메소드 검색 
  - mac : command + option + O 
  - windows/linux : ctrl + shift + alt + n

+ ***Action 검색***
  - mac : command + shift + a
  - windows/linux : ctrl + shift + a

+ 최근 열었던 파일 목록 보기
  - mac : command + E
  - windows/linux : ctrl + E

+ 최근 수정한 파일목록 보기
  - mac : command + shift + E
  - windows/linux : ctrl + shift + E

#### 자동완성

+ 스마트 자동완성 (전부 다 보여줌)
  - mac/windows/linux : ctrl + shift +space 

+ 일반 자동완성
  - mac/windows/linux : ctrl + space

+ 스태틱 메소드 자동완성 : assertThat 같은거 자동완성 할때
  - mac/windows/linux : ctrl + space + space

+ getter/setter/생성자 자동완성
  - mac : command + n
  - windows/linux : alt + insert

+ Override 메소드 자동완성
  - mac/windows/linux : ctrl + i

#### Live Template 소개

+ live template 목록보기
  - mac : command + J
  - windows/linux : ctrl + J
  - action검색 -> Live template 입력
  
+ 나만의 live template 추가
  - other -> "+" -> live template
  - 축약어 ( 설명 ) 입력 -> 템플릿 입력 -> define 클릭 -> 어디에 쓸건지 선택( ex  자바에서 사용)

#### 리팩토링 - Extract(추출하기)

+ 변수 추출하기 (Extract Variable)
  - mac : command + option + V (Variable)
  - windows/linux : ctrl + option + V (Variable)
  
+ 파라미터 추출하기
  - mac : command + option + P (Parameter)        -> Replace All or Delegate Overloading
  - windows/linux : ctrl + option + P (Parameter) -> Replace All or Delegate Overloading

+ 메소드 추출하기
  - mac : command + option + M (Method)
  - windows/linux : ctrl + alt + M (Method)

+ 이너클래스 추출하기
  - mac/windows/linux : f6 (클래스에 포커스)
 
#### 리팩토링 기타

+ 이름 일괄 변경하기( 변수, 클래스... 등등 전부 변경 가능)
  - mac/windows/linux : shift + F6

+ 타입 일관 변경하기
  - mac : command + shift + F6 (Type Migration 창)
  - windows/linux : ctrl + shift + F6

+ Import 정리하기( 사용하지 않는 Import지우기)
  - mac : ctrl + option + O
  - windows/linux : ctrl + alt + O
  - 자동 설정 : action 검색 -> optimize imports on -> Auto import -> OFF를 ON으로

+ 코드 자동 정렬하기
  - mac : command + option + l
  - windows/linux : ctrl + alt + l
  
#### 디버깅

+ 라인넘버 보이기 -> 라인 우클릭 -> show line number

+ Debug 모드 즉시 실행하기
  - mac : ctrl + shift + D
  - windows/linux : 없음

+ Debug 모드로 즉시 실행 (이전 것을 실행)
  - mac : ctrl + D
  = window/linux : shift + F9

+ Conditional Break Point
  - 브레이크 포인트 + 우클릭 -> 조건 입력 -> "문자열".equals( 값 ) 형식으로 적으면됨

![디버그 이미지](https://user-images.githubusercontent.com/49984996/89191467-f00b9100-d5dd-11ea-981b-48f659704d0b.jpg)

+ Resume ( 다음 브레이크포인트로 넘어가기)
  = mac : option + command + R
  - windows/linux : F9
  - call stack : 메서드 목록
  - variables : 변수 값 목록

+ Step Over(다음 라인으로 이동)
  - mac/windows/linux : F8

+ Step Into(메소드로 들어가기)
  - mac/window/linux : F7

+ Step Out(메소드 나오기 )
  - mac/linux/windows : shift + F8

+ Evaluate Expression ( 현재 Breaking Point 상태에서 즉시 코드 실행하기)
  
  - mac : option + F8
  - windows/linux : Alt + F8
  - 데이터가 잘 들어갔는지 확인(하이버네이트같은거 쓸때)
  - 현재 브레이크 걸린 상태에서 코드를 실행하는 기능
  - 항상 켤때마다 초기화 됨(단발성)

+ Watch(안경 모양)
  
  - 단축키 없음
  - 값이 어떻게 변하는지 실시간으로 확인
  - Input창에 입력
  - 브레이크 포인트 시점부터 다음 브레이크까지의 변화를 볼때 사용
  

#### Git 기본 기능 사용하기

+ 버전 컨트롤 View 보기 (Git View On)
  - view Tab -> Tool Windows -> Version Control
   - mac : command + 9
   - windows/linux : Alt + 9
   
   - local change 탭 : 최종 변경사항 확인(show diff)
   - log 탭 : 커밋 로그
   
+ Git Option Popup(모든 기능 표시)
  - mac : ctrl + v
  - windows/linux : Alt + '(Back Quote)

+ Git history
  - mac : ctrl + v + 4
  - windows/linux : ctrl + '(Back Quote) + 4

+ Git Branch
  - mac : ctrl + v + 7
  - windows/linux : alt + '(Back Quote) + 7

+ Commit
  - mac : command + k
  - windows/linux : ctrl + k
  
+ Push
  - mac : command + shift + k
  - windows/linux : ctrl + shift + k

+ Pull
  - mac/windows/linux : action 검색 -> git pull 검색

#### 깃헙 연동하기

+ 기존 프로젝트를 Github에 연동하기
  - 액션검색 -> share github 검색 -> password입력 -> save credentials(선택하면 다음에 인증 안해도됨) -> new repository / remote name / description 입력

+ 깃헙 프로젝트 clone 받기
  - 프로젝트 메인화면 -> checkout from Version Control 선택 -> git 선택 -> url 입력 or login(깃헙) -> 프로젝트 선택 + clone -> checkout -> 빌드툴 선택 -> use gradle wrapper task configuration 선택 (프로젝트에 맞는 그래들 설정)
  
#### 플러그인
  + 플러그인 설치 
    - 액션 검색 -> plugins -> preferences의 plugins선택 -> browse repositories 선택 -> sort by download순으로 정렬
  
  + 추천 플러그인
    - Presentation assistant : 다른 OS에서 해당 단축키가 어떤 것인지 알려준다.
    - Bash support : Bash 파일에 대한 기능 제공
  
  + Material Theme UI : 테마 변경
  
  + jojoldu Translation : 영문 코드 -> 한글, 한글-> 영문으로 변역해주는 툴
