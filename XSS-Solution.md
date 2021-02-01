# XSS Solution 
---
`https://dreamhack.io/wargame/challenges/28/`

>가장 간단한 XSS(Cross Site Scripting) 공격에 대한 실습이다.  

먼저 문제의 사이트에 `XSS` 하이퍼링크를 클릭하면,  

![XSS](https://user-images.githubusercontent.com/71700079/106424527-abd24e00-64a5-11eb-9efc-a760b0b8ae01.png)  

이런 화면이 출력되는데, 이것으로 이 사이트가 `javascript`에 대한 접근을 막지 않고 있음을 알 수 있다.  
이에 따라, 우리는 XSS 취약점이 존재 함을 알 수 있다.  

그리고 2번째 하이퍼링크인 `memo`를 클릭하면,  

![xsss](https://user-images.githubusercontent.com/71700079/106425117-b3debd80-64a6-11eb-8964-ba6b9740943a.png)  

이렇게 메모를 쓸 수 있는 공간이 나오는데 URI의 리소스를 보면, 현재 HTTP request가 __GET__ 메소드로 들어가고있음을 알 수 있다.  
따라서, `memo?memo=plumber` 이런 형식으로, 내가 원하는 문구를 메모에 적어 넣을 수 있다.  

여기서 우리는, 한 가지를 떠올릴 수 있다. 스크립트에 대한 제약도 없고, GET 메소드에 의해 파라미터에 내가 원하는 값을 넘겨줄 수 있다.  
따라서, memo에 스크립트를 이용하여 우리가 원하는 값을 얻어낼 수 있을 것이다.  

`XSS.py` 문제 코드에 있는 `read_url` 함수를 보면, url을 읽어 들인 후 `http://127.0.0.1:8000/` 도메인으로 쿠키를 보내고 있음을 알 수 있다.  
우리는 이 쿠키를 3번째 링크인 `flag` 링크에서 탈취를 시도할 것이다.  

![xssssss](https://user-images.githubusercontent.com/71700079/106426861-af67d400-64a9-11eb-82da-f5351b0c59b0.png)  

이와 같은 화면에서 `http://127.0.0.1:8000/` 라는 도메인에 우리가 원하는 결과를 만들어 내기 위해,  
`<script>location.href="/memo?memo="+document.cookie</script>` 이런 스크립트로 요청을 보낸다.  
그럼, href 스크립트에 의해, 뒤의 주소로 이동되어 메모장에 cookie가 적힌다.  

![asd](https://user-images.githubusercontent.com/71700079/106432861-a7606200-64b2-11eb-8503-9166542f6402.png)  

탈취 완료.
