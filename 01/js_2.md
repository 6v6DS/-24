### javascript 기초 문법 정리 (2)

1)
* 변수(variable)
  
let const var


var와 let은 크게 다르지 않음.

var는 한 번 선언된 변수를 다시 선언할 수 있음.

let은 다시 선언 불가.

var는 선언하기 전에 선언할 수 있다. 호이스팅(hoisting)

변수는 올려지지만, 할당은 올려지지 않음.


호이스팅: 스코프 내부 어디서든 변수 선언은 최상위에 선언된 것처럼 행동

let과 const도 호이스팅 되긴 함. 

but TDZ .. 영역에 있는 것들은 사용할 수 없음. tdz의 영향을 받음. (( 코드를 예상 가능하게 함 ))


변수의 생성 과정 1.선언 2.초기화 3.할당

var는 1.선언및 초기화 2.할당

let은 1.선언 2.초기화 3.할당

const는 1.선언 초기화 할당

var는 함수스코프 (함수 내에서 선언 된것만 지역변수) // let, const는 블록스코프(코드블록내에서만 유효, 외부에서는 접근 불가)         

2)
* 생성자 함수

객체 리터럴 (object literal)
```
let user = {
  name : 'Mike',
  age : 30
}
```
.. 을 여러개 만들어야 할 때

생성자 함수 사용 ( 첫글자는 대문자로 )
```
function User(name, age){
  this.name = name;
  this.age = age;
  this.sayName = function(){
     console.log(this.name);
  }
}
let user1 = new User('Mike', 30);
let user2 = new User('Jane', 22);
```          

3)
* 객체 메소드, computed property

```  
let a = 'age';
const user = {
  name : 'Mike',
  [a] : 30
} // 이렇게 표현 가능. age : 30
```

'age' -> [a] // computed property 라고 함


Methods

Object.assign() : 객체 복제 // const clone = user; 이렇게 하는 것은 객체가 복제되는 것이 아니라 참조값이 저장되는 것. 
하나의 객체를 두 변수가 접근하는 것. 
```
const clone = Object.assign({}, user);
```
이렇게 해야함. 두 개의 객체도 병합할 수 있음. Object.assign(user, info1, info2)

Object.keys() : 키 배열 반환

Object.values() : 값 배열 반환

Object.entries() : 키,값 배열 반환

Object.fromEntries() : 키,값 배열을 객체로


4)
* 심볼(symbol

property key : 문자형
```
const obj = {
  1 : '1입니다',
  false : '거짓'
}
Object.keys(obj); // ["1", "false"]
```

symbol형 : 유일한 식별자를 만들때 사용 유일성 보장. 전체의 코드중에 한 개.

그냥
```
const id = Symbol('id');
const user = {
  name : 'Mike',
  age : 30,
  [id] : 'myid'
}
```
인 경우, 

Object.keys(user); 

Object.value(user); 

Object.entries(user);

모두 키가 symbol형인 property를 건너뜀.

이를 활용하여, 특정 위치에 원본 데이터는 건드리지 않고 속성을 추가할 수 있음. symbol은 이름이 같더라도 모두 다른 데이터.


Symbol.for() : 전역 심볼

하나의 심볼만 보장, 없으면 만들고 있으면 가져옴, symbol함수는 매번 다른 심볼값을 생성하지만, symbol.for메소드는 하나를 생성한 뒤 키를 통해 같은 심볼을 공유.
```
const id1 = Symbol.for('id');
const id2 = Symbol.for('id');
id1 == id2; // true
```
그냥 Symbol 키는 false 였지만, Symbol.for는 true

Symbol.keyFor(id1)을 이용하면, 심볼의 이름을 알려줌.

전역 심볼이 아니라면, keyFor 대신에 id.description 사용.

Object.getOwnPropertySymbols(user); >하면 모든 심볼을 보여줌

Reflect.ownKeys(user); >하면 심볼을 포함해서 보여줌

-유일한 property를 사용하고 싶을 때 사용하면 됨.


5)
* 숫자, 수학 method

```  
toString() : 10진수 -> 2진수/16진수 로 바꿔줌
let num = 10;
num.toString(2); //2진수로 바꿔줌
num.toString(16); // 16진수로 바꿔줌
```

Math 내장함수
```
Math.PI; 
Math.ceil(); : 올림
Math.floor(); : 내림
Math.round(); : 반올림
```
소수점 둘째짜리까지 표현 같이 소수점 자릿수는,

Math.round(userRate * 100)/100 하면 둘째자리까지 표현

혹은, toFixed() 메소드 사용.

userRate.toFixed(2); //하면 둘째짜리까지 표현

하지만 toFixed는 문자열을 반환하기 때문에, 숫자로 변환.

Number(userRate.toFixed(2));


isNaN() 은 NaN인지 아닌지 판단해줌.

NaN은 .. 자기 자신조차도 false라고 판단.

isNaN만이 NaN을 판단해줌.


parselnt() // 문자열을 숫자로 바꿔줌

Number와 다른 점은,, 문자와 혼용되어 있어도 동작을 함. 읽을 수 있는 부분까지는 읽고, 문자를 만나면 숫자로 반환. 소수점 이하는 무시하고 정수만 반환.


parseFloat() //parseInt와 동일하게 동작하지만, 부동 소수점을 반환해줌

```
Math.random() // 0~1 사이 무작위 숫자 생성
Math.max()
Math.min() //괄호 안의 인수들 중 최소값, 최대값을 구함
Math.abs() //절대값
Math.pow(n,m) //거듭제곱
Math.sqrt() //제곱근
```

6)
* 문자열 메소드
  
String

백틱을 사용하면, 여러줄을 표현할 수 있음. " " 으로 표현하려면 \n으로 표현해야함. 줄바꿈 하면 에러.

length: 문자열 길이

desc[2] 처럼 문자열의 특정 위치에 접근 가능. but 배열과는 다르게 특정한 위치의 문자를 바꾸는 것은 안됨.

toUpperCase() / toLowerCase() 로 문자열의 대소문자를 바꿀 수 있음. 모든 영문 대문자/모든 영문 소문자

str.indexOf(text) : 문자를 인수로 받아 몇번째 인수인지 알려줌
```
  desc.indexOf('to');
```
주의점) 초함된 문자가 여러개여도 첫 문자의 위치만 반환해줌. 

if 문을 쓸 때는
```
if(desc.indexOf('Hi')){ //일 경우 0(false)이기 때문에, 
  console.log('Hi가 포함된 문장입니다.'); //desc.indexOf('Hi')>-1 사용
}
```

```
str.slice(n,m) //특정 범위의 문자열만 뽑기 n(시작점) 부터 m(없으면 문자열 끝까지, 양수면 그 숫자까지(그 숫자 전까지) 음수면 끝에서부터 셈) 까지 반환해줌.
str.substring(n,m) //slice와 비슷하지만, n과 m사이 문자열을 반환. n과 m을 바꿔도 동작함. 음수는 0으로 인식
str.substr(n,m) //n부터 시작, m개를 가져옴. m이 개수임.
str.trim() //앞 뒤 공백 제거.
str.repeat(n) //문자열을 n번 반복
```

문자열도 비교 가능. 아스키 코드를 기반으로 비교.

7)
* Array 배열
  
push, pop, unshift, shift

arr.splice(n,m) // 배열의 특정 요소 지움
```
let arr = [1,2,3,4,5];
arr.splice(1,2); //[1,4,5]
arr.spilce(n,m,x) : 특정 요소 지우고 추가
let arr = ["나는", "철수", "입니다"];
arr.splice(1,0,"대한민국", "소방관"); // 나는 대한민국 소방관 철수 입니다
arr.splice() : 삭제된 요소 반환
let arr = [1, 2, 3, 4, 5];
let result = arr.splice(1,2);
console.log(arr); // [1,4,5]
console.lof(result); //[2,3]
```

arr.slice(n,m) : n부터 m까지 반환
```
let arr = [1,2,3,4,5];
arr.slice(1,4); //2,3,4
```

arr.concat(arr2, arr3 ..) : 합쳐서 새배열 반환
```
let arr = [1,2];
arr.concat([3,4]}; //[1,2,3,4]
arr.concat([3,4],[5,6]); //[1,2,3,4,5,6]
arr.concat([3,4],5,6); //[1,2,3,4,5,6]
```

arr.forEach(fn) : 배열 반복
```
let users = ['Mike', 'Tom', "Jane'];
users.forEach((item, index, arr) -> {  //...
});
```

arr.indexOf / arr.lastIndexOf
```
let arr = [1,2,3,4,5,1,2,3];
arr.indexOf(3); //2
arr.indexOf(3,3) //7 두번째 인수는 시작 위치를 의미함.
arr.lastIndexOf(3); //7 끝에있는 것 부터
```

arr.includes() : 포함하는지 확인
```
let arr = [1,2,3];
arr.includes(2); //ture
arr.includes(8); //false
```

arr.find(fn) / arr.findIndex(fn)

보다 복잡한 연산 가능. 함수를 이용하여..

첫 번째 true 값만 반환하고 끝. 만약 없으면 undefined를 반환

조건을 만족하는 모든 요소를 알고 싶다면..

arr.filter(fn) : 만족하는 모든 요소를 배열로 변환      

arr.reverse() : 역순으로 재정렬
```
let arr = [1,2,3,4,5];
arr.reverse(); //[5,4,3,2,1]
```

arr.map(fn) : 함수를 받아 특정 기능을 시행하고 새로운 배열을 반환   

arr.join : 배열을 합쳐서 문자열   

arr.split : 문자열을 나눠서 배열로 만들어줌   

Array.isArray(item) : 배열인지 아닌지 판단해줌

8)
* 배열 메소드 arr.sort() / arr.reduce()
  
arr.sort(fn) : 배열 재정렬. 배열 자체가 변경되니 주의

1, 3, 2 인 경우 1, 2, 3 으로 재정렬 되지만, 27, 8, 5 인 경우 27, 5, 8로 정렬됨.
정렬할 때 요소를 문자열로 취급하기 때문. 
때문에 값을 제대로 전달해줄 수 있는 함수를 전달해야함. 함수를 인수로.


// 복잡하기 때문에 실무에서는 Lodash 의 _.sortBy(arr); 을 사용


arr.reduce(fn) : 인수를 함수로 받음. 

(누적 계산값, 현재값) => {return 계산값};

배열을 돌면서 원하는 작업을 하고 최종값을 반환함
```
let arr = [1,2,3,4,5];
const result = arr.reduce((prev,cur) => {
  return prev + cur;
}, 0);
console.log(result); //15
```

9)
* 구조 분해 할당(destructuring assignment)

배열이나 객체의 속성을 분해해서 그 값을 변수에 담을 수 있게 하는 표현식
```
let [x,y] = [1,2];
console.log(x); //1
console.log(y); //2

let users = ['Mike', 'Tom', 'Jane'];
let [user1, user2, user3] = users;
(( let user1 = users[0];
   let user2 = users[1];
   let user3 = users[2];
))
console.log(user1); //'Mike'
```

객체 구조 분해
```
let user = {name : 'Mike', age : 30};
let{name,age} = user;
{{let name = user.name;
  let age = user.age;
))
```
객체 구조 분해: 새로운 변수 이름으로 할당
```
let user = {name: 'Mike', age: 30};
let {name, age} = user;
//은 이거랑 같음 
let {name: userName, age: UserAge} = user;
//이렇게 할당 가능
console.log(userName); //'Mike'
console.log(userAge); //30
```

10)
* 나머지 매개변수, 전개 구문 ( Rest parameters, Spread syntax)
  
...로 사용

함수의 인수를 얻는 방법은 두 가지가 있음

argumetns와 나머지 매개변수 사용


arguments ( 과거에는 이것만 사용 가능 (화살표 함수에는 없음

   - 함수로 넘어 온 모든 인수에 접근. 함수 내에서 이용 가능한 지역변수. lenght / index. array 형태의 객체. -배열의 내장 메서드 없음(forEach, map 사용 불가)
```
fuction showName(name) {
  console.log(arguments.lenght);
  console.log(arguments[0]);
  console.log(arguments[1]);
}
showName('Mike', 'Tom'); //2 //'Mike' // 'Tom'
```

나머지 매개변수 ( 현재는 이것을 주로 사용

정해지지 않은 개수의 인수를 배열로 나타낼 수 있게 함.

점 세개를 쓰고 뒤에 배열 이름을 정해줌. 그럼 names 배열 안에 전달된 인수들이 들어감. 배열의 method 들을 사용할 수 있는 장점.(forEach, reduce)
```
function showName(...names){
  console.log(names);
}
showName(); //[ ]
showName('Mike'); //['Mike']
showName('Mike', 'Tom'); //['Mike', 'Tom']
```
생성자 함수는 첫글자는 대문자..

여러 변수와 함께 받을 때는.. 나머지 매개변수는 항상 마지막에 와야함.

전개 구문(Spread syntax) : 배열
```
let arr1 = [1,2,3];
let arr2 = [4,5,6];
let result = [...arr1, ...arr2]; //...arr1=1,2,3 ...arr2=4,5,6
console.log(result); // [1,2,3,4,5,6]
```
중간에 쓰는 것도 가능
```
let result = [0, ...arr1, ...arr2, 7, 8, 9; //[0,1,2,3,4,5,6,7,8,9]
```
객체도 가능
```
let user = {name:'Mike'}
let mike = {...user, age:30}
console.log(mike) //{name: "Mike", age: 30}
```
복제도 가능
```
let user = {name: "Mike", age: 30};
let user2 = {...user};
user2.name = "Tom";
console.log(user.name); //"Mike"
console.log(user2.name); //"Tom"
```
간편하다!

11)
* 클로저(Closure)
 
JS는 어휘적 환경(Lexical Environment)를 가짐

closure는 함수와 렉시컬 환경의 조합. 함수가 생성될 당시의 외부 변수를 기억. 생성 이후에도 계속 접근 가능.

12)
* setTimeout / setInterval
  
setTimeout : 일정 시간이 지난 후 함수를 실행

setInterval : 일정 시간 간격으로 함수를 반복
```
setTimeout(function(){
  console.log(3)
}, 3000); //3000은 3초를 의미
clearTimeout(tId); //타임아웃을 취소
```

setInterval //반복 수행
```
function showName(name){
  console.log(name);
}
const tId = setInterval(showName, 3000, 'Mike');
//3초마다 mike 가 수행됨
```

주의사항 : 현재 실행중인 스크립트가 종료된 이후 schelduling 함수가 실행됨.

13)
* call, apply, bind : 함수 호출 방식과 관계없이 this를 지정할 수 있음.

call method는 모든 함수에서 사용할 수 있으며 this 를 특정 값으로 지정할 수 있음.

함수를 호출하면서 call을 사용하고 this로 사용할 객체를 넘기면 해당 함수가 주어진 객체 메소드인 것처럼 사용할 수 있다.
```
const mike = {
  name: "Mike",
};
const tom = {
  name: "Tom",
};
function showThisName(){
  console.log(this.name);
}
showThisName.call(mike);
```

apply는 함수 매개변수를 처리하는 방법을 제외하면 call과 같음.

call은 일반적인 함수와 마찬가지로 매개변수를 직접 받지만, apply는 매개변수를 배열로 받음.

call은 순서대로 직접 받고, apply는 배열로 직접 받음.

apply는 array를 받는다.
```
const num = [3, 10, 1, 6, 4];

const minNum = Math.min.apply(null,num);
// = Math.min.apply(null, [3, 10, 1, 6, 4])
const maxNum = Math.max.call(null,...num);
// = Math.max.apply(null, [3, 10, 1, 6, 4])

console.log(minNum);
console.log(maxNum);
```

bind는 함수의 this 값을 영구히 바꿀 수 있음.
```
const mike = {
  name: "Mike",
};
function update(birthYear, occupation){
  this.birthYear = birthYear;
  this.occupation = occupation;
};
const updateMike = update.bind(mike);
updateMike(1980, "police");
console.log(mike);
```
```
const user = {
  name: "Mike",
  showName: function(){
    console.log(`hello, ${this.name}`);
  },
};
user.showName();
let fn = user.showName;
fn.call(user);
fn.apply(user);
let boundFn = fn.bind(user);
boundFn(); //"hello, Mike"
```

14)
* 상속, 프로토타입

객체에는 자신이 프로토티를 가지고 있는지 확인하는 메소드가 있는데, user.hasOwnProperty('name') 임..

hasOwnProperty는 .. "__proto__" 에 있음. 이것을 프로토타입이라고 함.

객체에 있을 때는 찾고 멈추고, 없을 때만 프로토에서 찾음.

상속.
```
const car = {
  wheels: 4,
  drive(){
      console.log("drive..");
 },
};
const bmw = {
  color: "red",
  navigation: 1,
};
bmw.__proto__ = car;
```
이렇게 하면 bmw는 car를 상속받아서.. proto 타입에서 찾을 수 있음.

상속은 계속 이어질 수 있음.

__protoype chain.__

그렇다면, Object.keys() 나 Object.values() 는 ? 

상속된 프로퍼티는 나오지 않음.

for문을 이용해서 객체가 직접 가지고 있는 것들만 나타내고 싶다면,
```
for(p in x5){
  if(x5.hasOwnProperty(p)){
      console.log('0', p);
  } else {
      console.log('x', p);
  }
}
```
하면, 

0 color

0 name

x navigation

x wheels

x drive

이런 식으로 나옴


생성자 함수를 이용하면 비슷한 객체들을 간단하게 만들 수 있었음.
```
Bmw.prototype.wheels = 4;
Bmw.prototype.drive = function(){
  console.log("drive..");
};
const x5 = new Bmw("red");
const z4 = new Bmw("blue");
```
이렇게도 표현 가능. __proto__ 대신에,,

생성자 함수가 새로운 객체를 만들어 낼 때 그 객체는 생성자의 인스턴스라고 불린다. 

js에는 instanceof 연산자가 있음. 

instanceof로 객체와 생성자를 비교할 수 있고 이는 해당 객체가 그 생성자로부터 생성된 것인지를 판단해서 true 혹은 false를 반환함.

z4 instanceof Bmw // true.

생성자로 만들어진 인스턴스 객체는 constructor라는 프로퍼티가 존재함. constructor은 생성자. Bmw를 가리킴.

z4.constructor === Bmw; //true 

프로토타입을 한 번에 쓸 수도 있지만, constructor를 이용하여 비교했을때 한 번에 쓰면 false가 나옴. 
그래서 프로토타입을 덮어쓰지 말고 하나씩 추가하는 것이 좋음. 

혹은, 한 번에 쓴 후 constructor: Bmw, 처럼 수동으로 명시해줘도 됨.

아무나 color를 바꿀 수 있으니
```
const Bmw = function(color){
   const c = color;
   this.getColor = function(){
      console.log(c);
   };
};
const x5 = new Bmw("red");
```
이렇게 하면 바꾸지 못함.

15)
* 클래스(class)

지금까지 비슷한 형태의 객체를 생성하기 위해서 생성자 함수를 사용했음. 이를 class를 통해서 만들 수도 있음. constructor는 객체를 만들어주는 생성자 메소드.
```
const User = function(name, age){
   this.name = name;
   this.age = age;
   this.showName = function() {
      console.log(this.name);
   };
};
const mike = new User("Mike", 30);
```
```
class User2{
   constructor(name, age){
      this.name = name;
      this.age = age;
   }
   showName() {
      console.log(this,name);
   }
}
const tom = new User2("Tom", 19);
```
showName과 같은 클래스 내에 정의한 메소드는 포토로 타입에 저장됨.

클래스의 메서드는 for...in 문에서 제외됨.


class: 상속

생성자에서의 상속은 프로토타입을 이용해서 했음.

class에서 상속은 extends을 이용함.

동일한 이름으로 method를 정의하게 되면 덮어씀.

메소드 오버라이딩

부모의 메소드는 그대로 사용하면서 확장하고 싶다면, super를 사용하면 됨.

16)
* Promise
 
완료되면 요청자에게 알려주는 것
```
const pr = new Promise((resolve(성공), reject(실패)) => {
   //code
});
```
이런 함수를 callback 함수라고 함
```
const pr = new Promise((resolve, reject) =>{
   setTimeout(()=>{
      resolve('OK')
   }, 3000)
});
//소비자 코드 then을 이용하여 result와 reject를 처리할 수 있음
```
```
pr.then(
      function(result){
	 console.log(result + '가지러 가자.');
      },
      function(err){
      	 console.log('다시 주문해주세요..');
      }
);
```
then 이외에 사용할 수 있는 것이

catch와 finally임.

catch는 에러가 발생한 경우 실행하게 설정할 수 있음
```
pr.then(
   function(result){}
).catch(
   function(err){}
)
```
명확하게 구분해줄 수있어 .. catch 문을 사용하는 것이 훨씬 좋음.


finally는 이행이든 거부든, 처리된 후에 항상 실행됨.
```
pr.then(
   function(result){}
).catch(
   function(err){}
).finally(
   function(){
      console.log('---주문 끝---')
   }
)
```
```
f1()
.then((resolve) => f2(resolve))
.then((resolve) => f3(resolve))
.then((resolve) => console.log(resolve))
.catch(console.log)
.finally(() => {
  console.log("끝");
});
```
이렇게 프로미스를 이어서 붙이는 것을 프로미스 체이닝(promise chaining) 이라고 함
```
Promise.all([f1(), f2(), f3]).then((resolve) => {
  console.log(resolve);
});
```
이렇게 사용하면 한 번에 사용 가능.

Promise.race 로 하게 되면 all은 모든 작업이 완료될 때까지 기다리지만, race는 하나라도 일등으로 완료되면 끝난다. 
두번째가 reject 되더라도 하나는 보여주는 것.

17)
async await 을 사용한다면

promise chaining보다 가독성이 좋아진다.

함수 앞에 async를 키워드로 붙여주면 항상 promise를 반환한다.

await 키워드는 sink 함수 내부에서만 사용할 수 있다. 오른쪽에는 promise 가 오고. 그 promise가 처리될때까지 기다린다. 
```
function getName(name){
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve(name);
    }, 1000);
  });
};
async function showName(){
  const result = await getName("Mike");
  console.log(result);
}
console.log("시작");
showName();
```
가독성이 훨씬 좋음.
```
async function order(){
  const result1 = await f1();
  const result2 = await f2(result1);
  const result3 = await f3(result2);
  console.log(result3);
}
```
reject인 경우 trt catch 문으로 감싸주면 됨.

Promise all 을 쓸 경우에는,
```
async function order(){
 const result = await Promise.all([f1(), f2(), f3()]);
 console.log(result);
}
```

19)
* generator : 함수의 실행을 중간에 멈췄다가 재개할 수 있는 기능
  

function 옆에 * 을 써서 만들고 함수 내부에 yield 키워드를 사용함.

yield에서 함수의 실행을 멈출 수 있음.

next를 통해 yield 문을 호출할 수 있음. next를 호출하면 가장 가까운 yield 문을 만날때까지 실행되고 데이터 객체를 반환한다.

반환된 데이터 객체는 value와 done 프로퍼티를 가지는데 value는 yield 오른쪽에 있는 값. 값을 생략하면 undefind. 

next(), return(), throw()


generator은 iterable(반복이 가능하다)이다.

Symbol.iterator 메서드가 구현되어 있어야 한다.

Symbol.iterator는 iterator을 반환해야 한다.

iterator

-next method를 가진다

-next method는 value와 done 속성을 가진 객체를 반환한다.

-작업이 끝나면 done은 true가 된다.


generator은 iterable 이면서 iterator 이다.

배열 또한 .. 반복 가능한 객체

generator도 for of 를 쓸 수 있음.

문자열도 가능.


generator는 값을 미리 만들어두지 않음. 메모리 관리 측면에서 효율적임. 필요한 순간에만 연산에서 값을 주기 때문에..

제너레이터는 필요한 값만 그때끄때 생성함,필요한 순간까지 계산을 미룰 수 있음.

다른 작업을 하다가 다시 돌아와서 next() 해주면 진행이 멈췄던 부분부터 이어서 실행한다.


19) 
* 새로운 기능들
 
- replaceAll 모든 문자열에 적용됨. 모든 문자열을 바꿔줌.

str.replaceAll("l", "~"); //모든 l을 ~로 바꿔줌

원래는 str.replace(/l/g, "~"); //이렇게 해야했음


- Promise.any
 
Promise.race 는 전달된 프로미스 중에 가장 먼저 완료된 결과값으로 이행/ 거부

Promise.any 는 전달된 프로미스 중에 가장 먼저 이행된 객체를 반환


- 논리 할당 연산자
 
logical assignment operators

|| = , &&= , ??=이런 식으로 축약할 수 있음.

|| : 앞의 값이 false 이면 뒤의 값

?? : 앞의 값이 null 이나 undefined 이면 뒤의 값


- 숫자 구분자
 
Numeric separators

1,000,000,000 대신에 1_000_000_000


- WeakRef
 
신중하게 사용..

약한 참조 = 가비지 컬렉터 대상


