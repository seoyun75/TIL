# Servlet

## 목차
- [서블릿(Servlet)](#서블릿servlet)
- [HttpServletRequest](#httpservletrequest)
    - [HTTP 요청 메시지 구조](#http-요청-메시지-구조)
    - [기능](#기능)
    - [기본 사용](#기본-사용)

---

## 서블릿(Servlet)

> HTTP 요청을 받아서 처리하고 응답을 생성하는 자바 표준 구조  
> 톰캣과 같은 서블릿 컨테이너 위에서 동작하며, 클라이언트와의 통신 과정에서 필요한 핵심 기능을 담당한다.

- HTTP 요청/응답 처리의 기본 단위
- request / response 객체 제공
- URL 매핑 기반 실행 구조 제공
- 서블릿 컨테이너(예: Tomcat)에 의해 실행 및 관리됨

---

## HttpServletRequest

> HTTP 요청이 들어왔을 때 요청 메시지를 파싱하고 데이터를 추출하는 역할을 담당한다.

### HTTP 요청 메시지 구조

```
POST /save HTTP/1.1
Host: localhost:8080
Content-Type: application/x-www-form-urlencoded

username=kim&age=20
```

#### 구성 요소

- Start Line
    - HTTP Method (GET, POST 등)
    - URL
    - Query String
    - Protocol (HTTP/1.1)

- Header
    - Host
    - Content-Type
    - 기타 메타 정보

- Body
    - 실제 데이터 (ex: username=kim&age=20)

---

### 기능

#### 1. 요청 데이터 조회

```java
request.getParameter("username");
```

---

#### 2. 임시 저장소 기능

```java
request.setAttribute("key", value);
request.getAttribute("key");
```

---

#### 3. 세션 관리

```java
request.getSession(true);
```

---

### 기본 사용

```java
@WebServlet(name = "Beanname", urlPatterns = "/request")
public class RequestServlet extends HttpServlet {

    @Override
    protected void service(HttpServletRequest request,
                           HttpServletResponse response)
            throws ServletException, IOException {

        String username = request.getParameter("username");

        response.getWriter().write("ok");
    }
}
```
