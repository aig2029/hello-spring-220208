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
<br /><br /><br /><br />

## 기간
[220208~]
<br /><br /><br /><br />

## 수강일지
![시스템 구성도2](https://user-images.githubusercontent.com/28974240/152991297-57ef60c6-d985-43aa-a933-d628ac121348.png)


① 웹브라우저에서 localhost:8080/hello를 던지면, <br />
② springBoot에 내장된 톰캣 서버가 받아와서 Controller에 던져줌. <br />
③hello에 mapping된 method(@GetMapping("hello"))를 실행하여<br />
④ ViewResolver에 return값(hello) 보냄<br />
(그림에서는 model에 data:hello!! 데이터도 첨가했음 hello.html에서 thymeleaf를 통해 치환되는 데이터)<br />
⑤컨트롤러에서 리턴 값으로 문자를 반환하면 뷰리졸버가 화면을 찾아서 처리한다





