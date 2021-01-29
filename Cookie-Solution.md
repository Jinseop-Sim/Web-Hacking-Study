# Cookie problem solution
---
`https://dreamhack.io/wargame/challenges/6/`

>가장 간단한 쿠키를 이용한 공격 문제이다.

웹 브라우저에는 F12 키를 이용해 개발자 도구를 간편하게 이용할 수 있다.

코드를 보면, 웹 브라우저에서 따로 JavaScript의 스크립트 입력을 막고 있지 않으므로,  
자바 스크립트의 명령어인 `document.cookie`를 이용하여 간단하게 쿠키 변조가 가능하다.

![쿠키 변조](https://user-images.githubusercontent.com/71700079/106289932-32601300-628d-11eb-9170-64a13b44f282.png)


브라우저에 username이 'guest'로 쿠키에 저장되어있었는데, 이걸 공격자 마음대로 'username = admin' 이라는 코드로 변조시키면

![캡처](https://user-images.githubusercontent.com/71700079/106295611-01cfa780-6294-11eb-8889-265ce3ef9321.PNG)

쿠키 변조를 통한 권한 탈취가 완료된다.
