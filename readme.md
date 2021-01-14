# Web Hacking Study Review
---
## What is web?
- Web browser : 웹에 접속하기 위한 **소프트웨어**
- Web Resource : 웹 상에 존재하는 모든 __콘텐츠__(HTML, JS, PDF, PNG etc.)
- URI(Uniform Resource Identifier) : 리소스를 식별하기 위한 식별자.
- HTTP(HyperText Transfer Protocol) : 웹을 이용하기 위한 __Protocol(통신규약)__
- HTTPS : HTTP의 __암호화된__ 통신규약
- Cookie : __Web browser__ 에 저장되는 데이터.
- Session : __Server__ 에 저장되는 데이터.
- Domain name : 컴퓨터를 식별하는 이름(e.g. www.naver.com).
- Server : 사용자(__Client__)에게 서비스를 제공하는 컴퓨터, HTTP를 이용하여 통신.
- Application : 서버에서 설정한 특정 기능들을 수행하는 **소프트웨어**
- DataBase(DB) : 데이터의 저장소.

## Web Resource
> http://dreamhack.io/index.html 이라는 주소에서, index.html 부분을 __Web Resource__ 라고 한다.  
- HTML(HyperText Markup Language)  
	웹 문서의 뼈대를 구현하기 위한 마크업 언어.
- CSS(Cascading Style Sheets)  
	HTML의 표시 방법을 정의 해주는 스타일 시트.
- JS(Java Script)  
	HTML과 CSS는 화면에 출력되는 뼈대, JS는 화면의 동작을 담당.
	
## URI(URL)
>Uniform Resource Identifier, 리소스의 식별자.  
우리가 흔히 아는 URL은, __리소스의__ __위치__ 를 식별하기 위한 식별자. (URI의 하위 개념)  
  >> `http://example.com:80/path?search=1#fragment`
- Scheme  
	웹 서버에 접속 할때 어떤 __Protocol__ 을 이용할 것인가?
- Host  
	example.com이 Host가 된다.
- Port  
	접속할 웹 서버의 __포트__ 를 담고있다.
- Path  
	접속할 웹 서버의 경로, /path의 위치에 해당한다.
- Query  
	웹 서버에 전달하는 매개변수에 해당, ? 문자 뒤에 붙는다.
- Fragment  
	__서브__ __리소스__ 를 식별하기 위한 정보에 해당, # 문자 뒤에 붙는다.

## Encoding
> Encoding이란, 보안을 위하여, 문자 또는 정보를 원래 형태와는 다르게 처리하는 것.
- URL encoding  
   URI 내에서, 구분자로 사용되는 __?__ __#__ __&__ __=__ 문자들을 인코딩하는 것  
   ㅣ문자ㅣURL 인코딩ㅣ
   ㅣ:-ㅣ:------:ㅣ
   ㅣ?ㅣ%3Fㅣ
   ㅣ#ㅣ%23ㅣ
   ㅣ&ㅣ%26ㅣ
   ㅣ=ㅣ%3Dㅣ
   