# HTTP 요청 프로토콜 / GET, POST

## HTTP 요청 프로토콜의 구조

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/cd9d6154-b01e-4b89-901b-6a03f5ca467c/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/21f3c856-ee74-4983-a717-281d1e1e9014/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/618a7da7-f7d9-4ed8-b447-07a01c91dac3/Untitled.png)

### request라인

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/de904e57-419c-4a76-89db-45b73074145c/Untitled.png)

**요청 타입**

|  | GET | POST | PUT | DELETE | HEAD | PATCH | CONNECT | OPTIONS | TRACE |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 요청에 본문 존재 | X | O | O | M | X | O | X | X | X |
| 성공 응답에 본문 존재 | O | O | M | M | X | O | O | O | X |
| *안전함 | O | X | X | X | O | X | X | O | O |
| *멱등성 | O | X | O | O | O | X | X | O | O |
| 캐시가능 | O | *1 | X | X | O | X | X | X | X |

***1 : 새로운 정보가 포함되어있을 때만**

***멱등성: 특정 작업을 여러 번 수행해도 결과값이 항상 일관하다는 것**

멱등성을 보장하는 작업은 서비스 안전성에 큰 도움을 준다. 같은 작업을 여러 번 실행시켜도 동일한 결과를 만들어내기 때문에 작업이 한 번 실패했어도 다시 실행시키면 된다는 것을 보장해준다. 반대로 멱등하지 않는 작업은 여러 번 실행시켰을 때의 결과가 그 때마다 다르므로 조심해야한다. 주로 네트워크 상에서 작업 실행이 실패했을 상황을 대비하기 위해 멱등성을 지키는 작업으로 설계를 많이 한다.

***안전함: HTTP 메서드가 서버의 상태를 바꾸지 않는 것. (읽기 작업만 수행하는 메서드)**

모든 안전한 메서드는 멱등성 또한 갖지만, 모든 멱등성을 지닌 메서드가 안전한 것은 아닙니다. 예컨대 `PUT`과 `DELETE`는 둘 다 멱등성을 가졌지만 안전하지는 않은 메서드입니다.

get post 빼고 나머지 메서드는 보안상 관리자가 막아둘 수 있음.

### post

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/152c0a08-000d-4f78-a996-859411130964/Untitled.png)

POST방식은 body에 포함시켜서 보낸다.

-> 보일 수 있으니 https를 쓰자. (보통 로그인할 때만큼은 https를 사용한다.)

### get

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f1b4f9a7-6af5-4dcc-b724-476e4bb0991c/Untitled.png)

데이터를 서버로 보낼 때 URI에 포함시켜보냄.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/af38c6e8-79c6-451d-a975-5482b099ddc8/Untitled.png)

## URL(Uniform Resource Locator)

## URI(Uniform Resource Identifier)의 구조

:인터넷상에서 특정 자원(파일)을 나타내는 유일한 주소

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/68161c49-e72c-49ea-98ad-35e4e4f0512a/Untitled.png)

7계층 프로토콜/ DNS가 도메인주소를 ip주소로 바꿈 (DNS 서버가): 80 or 443(웹브라우저가 알아서 써줌. 생략돼있는것) / 경로

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f85e350e-434b-40b2-8c41-dc8400b86938/Untitled.png)

# HTTP 응답 프로토콜

## HTTP 응답 프로토콜의 구조

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e9afd47c-5fdc-4ebd-93a5-cba951bcacea/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/afe7454c-7016-493a-aa76-67041fa68fc5/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5dd559d1-a286-48cb-84bf-da9823106d29/Untitled.png)

### **상태 코드**

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/26883668-dd56-445a-b91a-35c1b9a02755/Untitled.png)

- 200번대: 정상
- 400번대: 클라이언트 잘못
    
    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/8000fd77-674f-4be1-81e7-6ffbd6ce21ba/Untitled.png)
    
- 500번대: 서버 잘못
