# SQL Injection solution
---
`https://dreamhack.io/wargame/challenges/24/`
>아주 간단한 _Query Injection_ 공격에 대한 실습이다.  

문제의 코드를 뜯어 보면 `FLAG`를 얻기 위해서는 `admin`의 아이디로 로그인 해야 함을 알 수 있다.  
문제의 `/login` 부분을 보면, 로그인 정보를  
`select * from users where userid="{userid}" and userpasswd="{userpasswd}"`  
로 받고 있음을 알 수 있다.  
그리고 이 문제에서는 따로 `"`나 `'`에 대한 입력을 막고 있지 않다.  
그러므로, userid와 userpasswd의 입력란에 공격 페이로드를 집어넣어 쉽게 권한을 탈취 할 수 있다.  

![쿼리](https://user-images.githubusercontent.com/71700079/106383213-01581d80-6408-11eb-951b-a57e2016bbe6.png)  

흔히 사용되는 `"or"1` 공격 페이로드 이다.  
이런식으로 입력을 하게 되면 쿼리에서는,  
`select * from users where userid="admin"or"1" and userpasswd="{userpasswd}"`    
로 코드가 받아들여지는데, 이는 and 조건 대신 or 조건에 의해 `userid`가 `admin`이나 `1`이기만 하면,  
`userpasswd`에 상관없이 `admin` 계정으로 로그인이 된다.  
