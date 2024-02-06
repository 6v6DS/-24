### javascript 기초 문법 정리(1)

1)
* 변수.

alert(); >> 이건 위에 창에 뜨는 것
console.log(); >> 이건 콘솔창에 뜨는 것

변수 선언할 때

let은 한 번 선언해준 것을 나중에 또 썼을 때 에러를 통해 알려줌.(( 한 번 선언 후에 나중에 let을 생략하고 쓰면 선언해준 것을 바꿔줄  수 있음 )) 변할 수 있는 값.

const는 절대로 바뀌지 않는 상수


2)
* 문자열.
`` 백틱은 문자열 내부에 변수를 선언할 때 사용하면 편리.

${name} 처럼.


typeof 연산자는 변수의 자료형을 알아낼 수 있음

null 은 객체가 아님.(object가 아님)


3)
* 대화상자

  
alert 알려줌. 메세지를 띄워줌.

prompt 입력 받음 - 취소를 누르면 null값. 함수를 실행하는 괄호 안 에서 두 개의 인수를 받을 수 있는데, 첫번쨰 인수는 메세지, 두번쨰 인수는 입력받을 디폴트 값이 됨.

confirm 확인 받음 - 확인과 취소 버튼이 함께 있음. 확인일 경우 true, 취소일 경우 false.


4)
* 형변환
  
String()

Number()

Boolean()

자료형이 다르면 의도치 않은 동작이 발생할 수 있음.

prompt로 입력받은 값은 무조건 문자형임.

명시적 형변환. // 의도를 가지고 원하는 타입으로 바꿔주는 것

자동 형변환

String() // 문자열로 바꿔줌

Number() // 숫자로 바꿔줌. 숫자와 문자가 섞이면 안됨((NaN이 됨)). true 와 false는 1 과 0 의 값을 가짐.

Number(null) // 0, Number(undefined) // NaN 이 나옴.

Boolean() // false의 개수를 기억하면 됨.

숫자 0, 빈 문자열, null, undefined, NaN 이 false이고, 이외에는 모두 true를 반환.

Boolean(0) // false, Boolean('0') // true

Boolean('') // false, Boolean(' ') // true


6)
* 비교연산자, 조건문

비교연산자 <, >, <=, >=, ==, !=

=== 은 type까지 비교함. ( 일치 연산자 )

조건문 if else


7)
* 논리연산자

||(OR) - 모든 값이 false 일때만 false

&&(and) - 모든 값이 true 일때만 true

!(Not) - true면 false, false면 true

And > OR 우선순위.


8)
* 반복문 loop
  
for ( let i = 0; //초기값 i < 10;//조건.false가 되면 멈춤 i++//코드 실행 후 작업){

}

while

do while (do 에서 코드를 실행 하니 적어도 한 번은 실행한다는 점이 다름)


break : 멈추고 빠져나옴

continue : 멈추고 다음 반복으로 진행(위로 올라감)


9)

swith (( if else 로도 사용할 수 있지만 , swith문을 사용하면 더 간결하게 사용 가능 ))

swith(평가){
 case A:
 case B:
 ...
}

if 문의 else 처럼 default를 사용하면 

default:

하면 예외값 처리 가능

10)
* 함수(function)

같거나 비슷한 동작들을 자주 사용하거나 여러 곳에서 사용하면 하나로 만든 다음 재활용

console, alert, confirm ...

```
  function functionName(parameter){
  console.log("hello");
  }
```
->이런 식으로 하는 것은 interpreter 함수

hoisting

11)
* 함수 표현식, 화살표 함수

변수를 선언해서 함수를 할당하는 것 = 함수 표현식

이전의 함수 표현과 같은 것임. but 호출할 수 있는 타이밍이 다른 것임.

```
let sayHello = function(){
  console.log('Hello');
}
sayHello();
```

함수 표현식은 한 줄씩 생성하고 사용하므로, 함수 이후에만 호출 가능. 

화살표 함수(arrow function)
```
let add = function(num1, num2){
  return num1 + num2;
}
```
이 함수식을
```
let add = (num1, num2) => (
  return num1 + num2;
)
```
이렇게 사용 가능한 것

또한 
```
let add = (num1, num2) => num1 + num2;
```
이렇게도 사용 가능.

인수가 하나라면, 괄호도 생략 가능.
```
let sayHello = (name) => `Hello, ${name}`;
```

return문이 하나더라도, 여러줄이라면 사용 불가.

13)
* 객체(Object)

중괄호를 활용하고, 키(key)와 값(value)를 사용.
```
const superman = {
  name : 'clark',
  age : 33,
}
```
접근하려면,

superman.name //'clark'

superman['age'] //33


추가하려면,

superman.gender = 'male';

superman['hairColor'] = 'black';


삭제하려면,

delete superman.hairColor;

단축프로퍼티

```
const superman = {
  name, //name:name
 age, //age:age
}
```
프로퍼티 존재 여부 확인은
```
'birthDay' in superman;
//false
```

for..in 반복문

반복문으로 객체를 순회하며 값을 얻어올 수 있음.
```
for(let key in superman){
  console.log(key)
  console.log(superman[key])
}
```

13)
* 객체 - method, this
* 
method : 객체프로퍼티로 할당 된 함수
```
const superman = {
  age : 33,
  name : 'clark',
  fly : function(){
       console.log('날아갑니다.')
    } //function 키워드 생략 가능.
}
superman.fly(); //날아갑니다.
```

this 라는 키워드 사용 가능.
```
const user = {
  name : 'Mike',
  sayHello : function(){
    console.log(`Hello, I'm ${this.name}`);
  }
}
user.sayHello();  //Hello, I'm Mike
```
화살표 함수로 선언하면 동작이 아예 달라짐.

화살표 함수는 일반 함수와 달리 자신만의 this 를 가지지 않음.

화살표 함수 내부에서 this를 사용하면, 그 this는 외부에서 값을 가져 옴. 전역 객체를 가리킴. 

method를 사용한다면, 화살표 함수 사용은 하지 않는 것이 좋음.


14)
* 배열(array) : 순서가 있는 list

``` 
let students = ['mike', 'jane', ... ' '];
```
특징 - 문자, 숫자, 객체, 함수 등도 포함 가능
```
let arr = [
 '민수', //문자
  3, //숫자
  false, 
  {name: 'Mike', //객체
   age:33
  },
  function(){ //함수
  console.log('Test');
  }
];
```
length : 배열의 길이

push : 배열 끝에 추가 //여러 요소 한 번에 추가 가능

pop : 배열 끝 요소 제거

unshift : 배열 앞에 추가 //여러 요소 한 번에 추가 가능

shift : 배열 앞에 제거


for.. of 문 //객체를 순회하는 for .. in과 주의
```
for(let day of days){
  console.log(day)
} //요소를 day 라는 이름으로 얻음
```

