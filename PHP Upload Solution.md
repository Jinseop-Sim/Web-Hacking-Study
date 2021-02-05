# PHP Upload Vulnerability Solution
---
`https://dreamhack.io/wargame/challenges/38/`
>아주 간단한 PHP를 이용한 _File Upload Vulnerability_ 실습이다.  

문제 사이트를 들어가 보면 `Home`, `List`, `Upload` 3개의 항목을 볼 수 있다.  
`Home`은 코드에 있는 `index.php`가 열리는 메인 홈페이지이다.  
`List`는 내가 `Upload` 항목에서 파일을 업로드한 목록을 볼 수 있는 항목이다.  
`Upload` 항목에서는 내가 가지고 있는 파일을 마음대로 업로드 할 수 있는 항목인데,  
코드를 보면 이 과정에서 아무것도 검증을 하지 않는 것을 알 수 있다.  

이를 이용하면, 취약점을 발생시킬 수 있을 것이다!

`Upload`에 파일을 올리는 과정에서 검증이 없으므로, 우리는 php 코드를 파일에 담아 올려서 임의로 조작을 할 수 있을 것임을 예상할 수 있다.  

![php](https://user-images.githubusercontent.com/71700079/107020813-aa2ac200-67e6-11eb-9ccb-34c255cbf5a2.png)  

이런 `$_GET`을 이용한 아주 간단한 _Web Shell_ 을 만들어서 `.php` 확장자로 업로드 하게 되면,  

![get](https://user-images.githubusercontent.com/71700079/107021351-5ec4e380-67e7-11eb-974b-3f91adb11c7b.png)  

이렇게 URL에 `/upload/xxx.php?cmd=명령어` 의 형식으로 `OS command`를 이용을 할 수 있게 된다.

![ready](https://user-images.githubusercontent.com/71700079/107021319-553b7b80-67e7-11eb-848b-53a4be553d11.png)  

그럼 우리가 알고 있는 텍스트 파일 출력 Command인 `cat xxx.txt`를 이용하여 이렇게 원하는 Flag를 탈취할 수 있다.  
간단한 _Web Shell_ 적용 문제!
