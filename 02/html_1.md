### HTML 기본 문법 정리

-----
HTML (HyperText Markup Language)
HTML은 웹 브라우저에 표시되는 웹 페이지를 만들어달라고 컴퓨터에게 요청하는 언어.

-----

* 기본 태그
```
<!DOCTYPE html>	웹 문서의 유형을 html로 지정
<head> 브라우저의 정보를 입력하는 곳
<meta>	메타 데이터 입력. ex ) <meta charset="UTF-8"> //meta 태그는 닫히는 태그 필요 x.
<title>	문서 제목
<body>	문서 내용을 입력
```
```
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
</head>
<body>
	<header>
	</header>
	<nav>
 	</nav>
<article>
</article>
<footer>
	
</footer>
</body>
</html>
```
```
<article>	본문. 독립적인 콘텐츠.
<aside>	사이드 바 영역. 광고와 같이 페이지의 내용과는 관계가 적은 내용들
<details>	기본적으로 표시되지 화면에 표시되지 않는 정보들을 정의
<figure>	삽화나 다이어그램과 같은 부가적인 요소를 정의
<footer>	화면의 하단에 위치하는 사이트나 문서의 전체적인 정보를 정의
<header>  화면의 상단에 위치하는 사이트나 문서의 전체적인 정보를 정의
<main>	메인 영역. 문서에서 가장 중심이 되는 컨텐츠를 정의
<mark>	참조나 하이라이트 표시를 필요로 하는 문자를 정의
<nav>	문서의 네비게이션 항목을 정의. 문서 내의 다른 위치, 다른 문서로 연결.
<section>	문서의 구획들을 정의 (참고)
<time>	시간을 정의
<section> 콘텐츠 영역
```
```
meta 데이터를 설명하는 데이터
<meta chatset="utf-8">
<meta name="description" content="자료"> //웹페이지에 대한 요약된 정보로 사용 가능
<meta name="keywords" content="키워드들"> //웹페이지를 설명하는 키워드들
<meta name="author" content="저자">
<meta http-equiv="refresh" content="30"> //30초 간격으로 자동으로 refresh
```

-----
* 텍스트 
```
<h1> ~ <h6>	제목. 클수록 작아짐.
<p>	</p> 단락
<br>	줄 바꿈 //닫기 없음
<blockquote>	인용문, 들여쓰기 적용됨
<strong>	텍스트 굵게
<em>	텍스트 기울임
<i>	텍스트 기울임
<u>	텍스트 밑줄
<s>	텍스트 취소선
```
-----
* 목록 
```
<li> 목차
<ol>	순서가 있는 목록(ordered list) //자동으로 목차 넘버링
<ul>	순서가 없는 목록(unordered list) //성격이 같은 것들끼리 grouping 하면 됨
<dl> <dt> 설명할 용어
```
-----
* 표
```
<table>	테이블 만들기
<caption>	표 제목
<tr>	행 삽입
<td>	셀 삽입
<th>	셀 삽입(진하게 표시)
<thead>	표 중 제목, 여러 페이지에 걸쳐 고정 가능
<tbody>	표 중 본문
<tfoot>	표 중 요약, 여러 페이지에 걸쳐 고정 가능
```
```
테이블
<table border = "1">
  <tr> 행
      <td> 열 </td>
      <td> </td>
      <td> </td>
  </tr>
  <tr>
      <td> </td>
      <td> </td>
      <td> </td>
  </tr>
</table>
```
```
표의 구조
<thead>
<tr>
  <th> 진하게 표시됨 </th>
</tr>
</thead>
<tbody>
 <tr>
   <td> </td>
 </tr>
</tbody>
<tfoot>
 <tr>
   <td> </td>
 </tr>
</tfoot>
```
```
표 병합
<td rowspan="2"> </td> // 두 개의 행이 병합된다.
<td colspan="3"> </td> // 세개의 열이 병합된다.
rowspan="2"	2개의 행 합치기
colspan="2"	2개의 열 합치기
```
-----
* 이미지 삽입
```
<img>	이미지 삽입 // <img src=" 이미지 주소 " width = " ">
src=	이미지 파일 경로
alt=	대체용 텍스트
width=
height=	가로, 세로 크기 조절
%	브라우저 창의 크기 단위
px	픽셀 단위
```
-----
* 링크삽입
```
<a>	하이퍼 링크 삽입 
href=	링크 주소
target="_blank"	새 탭에서 열기
//<a href="링크" target="_blank" title=''html specification"> </a>
```
-----
* form
  
form. 사용자가 입력한 정보를 서버로 전송할 때 사용하는 것.

input 으로 사용자가 정보를 입력.
```
<form>	
method=	get	사용자 입력 내용이 드러나게 서버로 넘겨줌
post	사용자 입력 내용이 드러나지 않게 서버로 넘겨줌
name=	자바스크립트로 폼 이름 지정
action=	서버 프로그램 지정
target=	열어볼 파일 위치 지정
autocomplete=	자동 완성 기능 지정(기본값 on)
<fieldset>	폼 내부에서 구역을 나눔
<legend>	구역 제목 붙이기
```
```
action= "서버주소" 서버 주소를 입력
name= 서버로 접속될 때 각각의 이름으로 보내짐.
submit 전송할 때 사용하는 버튼

<input type ="submit">
<form action=" 서버 주소 "> </form>
아이디: <input type="text" name="id">
비밀번호: <input type="password" name="pws">
주소: <input type="text" name="address">
```
```
text로 입력 받을때
text: <input type="text" name="id" value="default value"> //기본값
password: <input type="password" name="pwd" value="default value">
textarea. 여러 줄 입력받을때
textarea: 
  <textarea cols=" " rows=" ">default value</textarea>
```
```
dropdown list. 여러가지 선택지 중에 하나를 선택하는 경우. 

<form action="서버주소">
<h1>색상</h1>
<select name="color">
	<option value="black">검은색</option>
	<option value="red">붉은색</option>
	<option value="blue">파란색</option>
</select>
<h1>색상2(다중선택)</h1>
<select name="color" multiple>
	<option value="black">검은색</option>
	<option value="red">붉은색</option>
	<option value="blue">파란색</option>
</select>
<input type="submit">
</form>
```
```
radio, checkbox 여러개의 선택지 중의 하나.
radio. 같은 이름을 가진 것들끼린 다중선택X
name값이 같은 것들끼리 grouping

<p>
	붉은색: <input type="radio" name="color" value="red">
	검은색: <input type="radio" name="color" value="black">
	파란색: <input type="radio" name="color2" value="blue">
</p>
checkbox. 같은 그룹에 있는 것이 여러개 선택
<form action="서버주소">
<p>
	<h1>사이즈(다중선택)</h1>
	95: <input type="checkbox" name="size" value="95">
	100: <input type="checkbox" name="size" value="100" checked>
	105: <input type="checkbox" name="size" value="105">
</p>
<input type="submit">
</form>
단일선택 radio, 다중선택 checkbox
```
```
hidden field
서버로 데이터를 전송하지만, 눈에 보이지 않게 데이터를 전송하는.
<form action="서버주소">
	<input type="text" name="id">
	<input type="hidden" name="hide" value="egoing">
	<input type="submit">
</form>
```
```
label. 
텍스트가 어떤 의미인지.. 알려주는 label은 무언가의 이름이다. 라는 뜻
<form action="서버주소">
<p>
	<label for="id_txt">text</label>:
	<input id="id_txt" type="text" name="id" value="default value"> 
</p>
<p>
	<label for="pwd_txt">password</label>:
	<input id="pwd_txt" type="password" name="pwd" value="default value">
</p>
<p>
	<label for="comment">textaea</label>:
	<textarea id="comment" cols=" " rows=" ">default value</textarea>
</p>
<p>
	<label for="check">붉은색</label>
	<input id="check" type=:"checkbox" name="color" value="red">
</p>
...다른방법
<label>textarea:
	<textarea rows = "2">defult value</textarea>
</label>
<label>
	<input type="checkbox" name="color" value="red">붉은색
</label>
```
```
form: 파일 업로드
<html>
 <head>
	<meta charset="utf-8">
 </head>
 <body>
	<form action="서버주소" method="post">
	 <input type="file" name="profile">
	 <input type="submit">
	</form>
 </body>
</html>
```
-----
* 버튼 button
```
submit과 다르게 단순한 버튼.
<input type="button" value="버튼">
재설정 버튼
<input type="reset">
```
-----
* method 메소드
```
여태까지는  GET 방식이었음.
...
하지만 정보를 url이 아니라, 감춰서 전달해야 할 경우 POST를 사용
method를 지정해주지 않으면 자동으로 get 방식으로 동작.
<html>
 <head>
	<meta charset="utf-8">
 </head>
 <body>
	<form action="서버주소" method="post">
	  <input type="text" name="id">
	  <input type="submit">
	</form>
 </body>
</html>
.. 보통 form을 이용해서 전송하면 post를 이용.
```

-----
```
검색엔진최적화
html 코드를 의미론적으로 타당한 태그로 잘 설명하는 것이 기본임.
명확하고 독창적인 타이틀의 사용..
<title> 태그는 사용자와 검색엔진에 특정 페이지의 주제를 알려줌
페이지의 콘텐츠를 정확하게 설명하는 제목. 페이지마다 고유한 타이틀 태그 작성.
<meta> 태그는 내용 미리보기 로 사용할 수 있음. 
url은 주소에 해당되는 컨텐츠를 잘 알 수 있음. url이 담고 있는 정보를 표현하는 이름을 작성하는 것이 유리하다.
canonical.. 한 가지 형태의 url만 제공하기 위해 rel="canonical" 을 넣고, href=" " 안에 있는 것이 진짜 라는 것을 알려줌.
하이퍼텍스트가 잘 작성되어있어야 한다.
사이트 이동 경로를 제공
이동 경로를 위해 텍스트구조를 제공
사용자를 위한 콘텐츠 작성
html은 정보로서의 가치를 높이기 위해 노력해야함..
```
-----
* number

숫자만 입력하게 할 수 있는 기능
```
<input type="number"> //의도하는 정보만 입력할 수 있게..
<input type="number" min="10" max="15"> //사용자의 입력을 강제하거나, 모바일에서는 쉽게 입력 가능하게 할 수 있다.
input types
-color
-date <input type="date" name="datev">
-email 
-month <input type="month" name="monthv">
-number
-range //슬라이더. <input type="range" name="rangev" min="0' max="10">
-search //정보로서의 가치를 높이는..
-tel
-time
-url
-week
```
-----
* 자동완성기능 autocomplete
* 자동으로 커서이동 autofocus
```
<form action=" .." autocomplete="on">
	<input type="text" name="id" placeholder="id를입력해주세요" autofocus>
	<input type="password" name="password" autocomplete="o ff" placeholder="비밀번호를입력해주세요">
	<input type="submit">
</form>
```
-----
* 입력 값 체크, 유효성 검사
```
text
<input type="text" name="id" placeholder="아이디를입력해주세요" required pattern="[a-zA-Z][a-zA-Z]">
```
-----



