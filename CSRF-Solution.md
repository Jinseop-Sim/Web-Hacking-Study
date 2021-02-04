# CSRF Solution
---
`https://dreamhack.io/wargame/challenges/26/?page=2`
>아주 간단한 _CSRF(Cross Site Request Forgery)_ 실습 문제이다.  

우리는 일전에 __Client Side Basic__ 강의에서 _CSRF_ 에 관해 배웠다.  
`<img src = ...>` 의 Image 형태나,  
`<form action = ...>` 의 Form 형태를 이용해 CSRF 취약점을 발생 시킬 수 있다.  

먼저, 첫 하이퍼 링크에 들어가보면 코드에서도 알 수 있듯이 XSS를 `csrf_replace` 함수로 필터링 하고 있는 것을 알 수 있다.  
우리는 script, frame, on 3가지 단어를 쓸 수 없다. 하지만 알고 있듯이, csrf는 `<img src=..>` 코드로 발생 시키는 것이므로 필터링 당하지 않는다.  
따라서 이 페이지에서 CSRF 공격이 가능하다는 말이 된다.

두번째 링크는 `memo` 이다.  XSS 문제 때와 같은 형식의 메모 업로드 API이다.  
이 기능과 코드를 보고 우리는 `memo` 링크에 `127.0.0.1`의 아이피로 `admin`의 아이디로 요청을 보낼 경우, `FLAG` 값이 적힐 것임을 알 수 있다.

![awd](https://user-images.githubusercontent.com/71700079/106909311-84001600-6743-11eb-92b9-ae89e1475019.png)  

XSS 문제 때와 같이 127.0.0.1의 도메인으로 요청을 보냈을 때, `memo` 링크에 원하는 글이 적히는 것을 알 수 있다.  
따라서 이를 이용해, 127.0.0.1의 도메인으로  
`http://127.0.0.1:8000/csrf?csrf=<img src = "/admin/notice_flag?userid=admin">`  
이런 요청을 보내면, 아까 CSRF 공격이 가능함을 확인했으므로, `127.0.0.1`의 아이피로 `admin`의 아이디로 요청을 보낸 것이 된다.  

따라서 `memo`에 `FLAG` 값이 출력 된다.
