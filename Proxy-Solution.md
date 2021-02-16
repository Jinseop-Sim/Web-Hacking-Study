# Proxy Solution
---
`https://dreamhack.io/wargame/challenges/13/writeups`
> 간단한 HTTP request 요청 변조를 통한 문제이다.

문제의 홈페이지는, _Raw Socket Sender_ 서비스를 구현해놓은 서버이다.  
이는 사용자 임의의 __HTTP Request__ 를 보낼 수 있는 서비스이다.  

`Socket` 항목에 들어가보면, `Host`와 `Port`를 적어내는 칸이 있다.  
제출한 호스트와 포트로 `Data` 칸에 적어낸 `HTTP Request`를 요청하겠다는 의미이다.  

그런데, 문제의 코드를 보면 알 수 있듯이, 마지막 줄에 `app.run(host='0.0.0.0', port=8000)` 라는 코드가 있다.  
이것이 의미하는 바는 우리가 요청을 보내면 웹 서버로 바로 가는 것이 아닌, __Flask__ 가 여는 포트 8000의 서버로 요청이 보내진다는 것이다.  

따라서, 웹 서버인 `host1.dreamhack.games`가 아닌 `0.0.0.0`과 `8000`으로 `host`, `port`가 기입이 되어야한다.  
그리고 `Data` 칸에는 코드 `/admin` 단의 조건문들을 모두 만족하는 `Header`와 `Body`를 기입하면 된다.  

![image](https://user-images.githubusercontent.com/71700079/108049072-2779f080-708b-11eb-9f01-7b6c6e864468.png)  

__Method__ 는 POST, HTTP version 1.1  
그리고 조건에 있는 `User-Agent`는 `Admin Browser`, `Content-Type`은 보통 사용하는 `x-www-form-urlencoded`  
조건에서 원하는 `DreamhackUser`, `Cookie` 헤더까지 헤더 부분에 모두 넣어주고, 이제 남은 `userid=admin` 부분은 __Body__ 로 들어간다.  

그런데 여기서, __Body__ 부분의 데이터를 POST 메소드에 맞춰 인식 시키려면, 헤더 부에 Content-Length 헤더를 반드시 추가해 주어야 한다.  
이 헤더가 빠질 시, __Body__ 부의 데이터를 인식하지 못한다.

이대로 요청을 보내면, 오류 메시지 없이 `FLAG` 값이 화면에 출력된다.
