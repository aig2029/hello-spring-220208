## 스프링 입문 - 코드로 배우는 스프링 부트, 웹 MVC, DB 접근 기술 강의 (김영한)
[https://www.inflearn.com/course/%EC%8A%A4%ED%94%84%EB%A7%81-%EC%9E%85%EB%AC%B8-%EC%8A%A4%ED%94%84%EB%A7%81%EB%B6%80%ED%8A%B8/dashboard]
<br /><br /><br /><br />
 
 
## 개발환경
![IntelliJ IDEA](https://img.shields.io/badge/IntelliJIDEA-000000.svg?style=for-the-badge&logo=intellij-idea&logoColor=white)
![Windows](https://img.shields.io/badge/Windows-0078D6?style=for-the-badge&logo=windows&logoColor=white)
<br /><br /><br /><br />

## 기술스택
![Java](https://img.shields.io/badge/java-%23ED8B00.svg?style=for-the-badge&logo=java&logoColor=white)
![Spring](https://img.shields.io/badge/spring-%236DB33F.svg?style=for-the-badge&logo=spring&logoColor=white)
![Thymeleaf](https://img.shields.io/badge/Thymeleaf-%23005C0F.svg?style=for-the-badge&logo=Thymeleaf&logoColor=white)
<br /><br /><br /><br />

## 기간
[220208~]
<br /><br /><br /><br />

## 수강일지
<div align="center"><h3>
[Thymeleaf템플릿 엔진 동작 확인]
 </h3></div>

![시스템 구성도2](https://user-images.githubusercontent.com/28974240/152991297-57ef60c6-d985-43aa-a933-d628ac121348.png)


① 웹브라우저에서 localhost:8080/hello를 던지면, <br />
② springBoot에 내장된 톰캣 서버가 요청을 받아와서 Controller에 던져줌. <br />
③ hello에 mapping된 method(@GetMapping("hello"))를 실행하여<br />
④ ViewResolver에 return값(hello) 보냄<br />
(그림에서는 model에 data:hello!! 데이터도 첨가했음 hello.html에서 thymeleaf를 통해 치환되는 데이터)<br />
⑤ 컨트롤러에서 리턴 값으로 문자를 반환하면 뷰리졸버가 화면을 찾아서 처리한다

<br /><br /><br /><br /><br /><br /><br /><br /><br /><br />
<div align="center"><h3>
[SpringBoot정적 컨텐츠 기능(Controller에 Mapping되지 않은 요청을 할 경우)]
</h3></div>
 
![시스템 구성도2](https://user-images.githubusercontent.com/28974240/153049551-c8395642-b580-4a48-af85-0554b0c9db13.png)
① 웹브라우저에서 localhost:8080/hello-static.html을 던지면, <br />
② springBoot에 내장된 톰캣 서버가 요청을 받아와서 Controller에 던져줌.( 우선 순위가 SpringContainer의 Controller에 있음)<br />
③ mapping이 된 Controller가 없으면 SpringBoot가 resources안에 있는 hello-static.html을 찾아서 반환해줌.<br />
④ hello-static.html를 웹브라우저에 뿌려줌
<br /><br /><br /><br /><br /><br /><br /><br /><br /><br />


<div align="center"><h3>
[@ResponseBody로 Http의 Body에 데이터를 직접 반환]
</h3></div>

![시스템 구성도3](https://user-images.githubusercontent.com/28974240/153072050-eddbaf2d-6539-42dc-bbeb-0c3cdfcaf57b.png)
① 웹브라우저에서 localhost:8080/hello-api를 던지면<br />
② SpringBoot에 내장된 톰캣 서버가 요청을 받아와서 Controller에 던져줌<br />
③ httpRequest메시지의 parameter값으로 GetMapping된 메소드에 @ResponseBody가 붙으면 httpResponse메시지에 데이터(return값)를 그대로 넘김<br />
(@ResponseBody의 Body는 html의 body부가 아니라 httpResponse 메시지의 body를 일컫는 것임)<br />
④ viewResolver 대신에 HttpMessageConverter 가 동작<br />
기본 문자처리: StringHttpMessageConverter<br />
기본 객체처리: MappingJackson2HttpMessageConverter<br />
byte 처리 등등 기타 여러 HttpMessageConverter가 기본으로 등록되어 있음<br />
<br /><br /><br /><br /><br /><br /><br /><br /><br /><br />

<div align="center"><h3>
[스프링 빈을 등록하는 2가지 방법 - 컴포넌트 스캔과 자동 의존관계(@Autowired) 설정]
</h3></div>

1. 생성자에 @Autowired가 있으면 스프링이 연관된 객체를 스프링 컨테이너에 찾아서 넣어준다.<br />
이렇게 객체 의존 관계를 외부에서 넣어주는 것을 DI(의존성 주입)이라 한다.<br />
기존에는 개발자가 직접 주입했지만, 스프링에서는 @Autowired에 의해 주입된다.<br />
![2022-02-10 19;13;06](https://user-images.githubusercontent.com/28974240/153385906-91516b7f-72cf-4dcd-87d2-917e8fa9495e.PNG)<br />
(스프링 빈에 등록되어 있지 않은 클래스를 @Autowired로 DI하려고 하면 컴파일에 실패한다.)<br />


2. @SpringBootApplication 애노테이션을 가지고 있고, main함수를 가지고 있는 클래스의<br /> 
package안에 속해 있는(pacakage가 같거나 그 하위 패키지) 스프링 빈만을 사용할 수 있다.<br />
다른 package에 스프링 빈을 등록해도 그것을 사용할 수 없다.<br />
(@SpringBootApplication 애노테이션은 @ComponentScan 애노테이션을 가지고 있음)<br />

3. @Component를 포함하는 애노테이션은 스프링 빈으로 자동 등록된다. <br />
ex) @Controller @Servcie @Repository<br />
![2022-02-10 19;18;19](https://user-images.githubusercontent.com/28974240/153386615-620d6332-ac8c-44c0-91c7-e95df052a104.PNG)<br />
(참고 : 스프링은 컨테이너에 스프링 빈을 등록할 때, 기본적으로 싱글톤으로 등록한다. 따라서 같은 스프링 빈이면 모두 같은 인스턴스이다. 특별한 경우를 제외하고 대부분 싱글톤을 사용한다.)
<br /><br /><br /><br /><br /><br /><br /><br /><br /><br />
 

<div align="center"><h3>
[스프링 빈을 등록하는 2가지 방법 - 자바 코드로 직접 스프링 빈 등록]
</h3></div>
- @Configuration 애노테이션을 가진 클래스(ex)SpringConfig 클래스)를 따로 작성하여 스프링 컨테이너에 스프링 빈을 등록하는 방법 
<br /><br /><br /><br /><br /><br /><br /><br /><br /><br />
