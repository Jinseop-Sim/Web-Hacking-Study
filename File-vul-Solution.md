# File Vulnerability Solution
---
`https://dreamhack.io/wargame/challenges/37/`
>아주 간단한 파일 업로드 / 다운로드에 의한 취약점 문제이다.  

문제의 `File vulnerability.py` 코드를 분석해 보면, 간단한 메모 업로드 및 읽기가 가능한 사이트임을 알 수 있다.  
그리고 `/upload` 루트의 코드를 보면, 조건문에 의해 메모에 `..` 문자가 삽입된 채 업로드를 못하게 막혀있다.  
즉, 업로드 기능에는 취약점이 없다는 것을 알 수 있다.  

![asddsa](https://user-images.githubusercontent.com/71700079/106444770-8bb08800-64c1-11eb-9148-72064d9b7647.png)  

하지만, 이렇게 URI의 리소스 파트에서는 따로 제한이 없으므로 이 부분에서 _File Upload Vulnerability_ 가 발생함을 알 수 있다.  

![qwd](https://user-images.githubusercontent.com/71700079/106444973-caded900-64c1-11eb-804c-f6e91e01809b.png)  


이런 식으로 URI의 name 파라미터를 마음대로 조작하면, 파일의 이름이 `../flag.py` 로 바뀌게 되고  
부모 디렉토리에 강제로 접근 함으로써, 상위 디렉토리에 있던 flag.py를 가져올 수 있다.
