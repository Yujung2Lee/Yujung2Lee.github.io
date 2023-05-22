---
layout: post
title: "yujungReact"
author: 이유정
date: 2023-05-19
category: TeamC
icon: react
keywords: tag1, tag2
preview: 0
---

## 💠 리액트(React.js)

<br/>

## 섹션1. JavaScript 기본

### ■ Hello World

- 웹사이트는 HTML, CSS Javascript 3가지 언어로 만들어 진다.

> <b>HTML5</b>: 요소들의 배치와 내용을 기술하는 언어. 색이나 크기 등의 디자인 수행X<br/>
> <b>CSS3</b>: 색, 크기, 애니메이션 등을 정의하는 스타일링을 위한 언어<br/>
> <b>Javascript</b>: 웹사이트에 활력을 부여하는 언어<br/>

<br/>

### ■ 변수와 상수

- let, var, const

### ● let

&nbsp;&nbsp;- <span style="color: red;">변수를 중복해서 사용 불가능</span> 변수선언 후 값 변경 가능

### ● var

&nbsp;&nbsp;- <span style="color: red;">변수 선언 시 중복해서 사용 가능(코드가 중복될 수 있다)</span> 변수선언 후 값 변경 가능

### ● const

&nbsp;&nbsp;- 변하지 않는 값 <span style="color: red;">변수선언 후 값 변경 불가능</span>

<br/>

### ● 변수 설정 규칙

> 1. 변수명에는 기호를 사용할 수 없다. (사용가능 기호: \_ &nbsp; $)<br/>
> 2. 변수명은 반드시 숫자가 아닌 문자로 시작<br/>
> 3. 예약어를 피해야 한다. ex) if<br/>

<br/>

### ■ 자료형과 형 변환

### ● 자바스크립트의 자료형

> -&nbsp;<b>Primmitive Type(원시 타입)</b>: 한번에 하나의 값만 가질 수 있음..하나의 고정된 저장 공간 이용 &nbsp;ex) let numer = 12;<br/>
> -&nbsp;<b>Non-Primitive Type(비 원시 타입)</b>: 한번에 여러 개의 값을 가질 수 있음..여러 개의 고정되지 않은 많은 동적 공간 사용 &nbsp;ex) let array = [1,2,3,4];<br/>

<br/>

### ● 숫자형

```
let age = 25; // 정수

let tall = 175.9; // 실수

let inf = Infinity; // 무한대의 값

let minusInf = -Infinity; // 음의 무한 값

let nan = NaN; // 수학적인 연산의 실패 결과값으로 사용
```

<br/>

### ● 문자형

```
let name = "blws";

let name2 = 'yj';

let name3 = `blws ${name2}` // 문자열 안에 변수 값 집어넣을 때 사용
```

<br/>

### ● boolean

```
let isSwitchOff = false; // true or false
```

<br/>

### ● null / undefined

```
let a = null;

let variable; // 값이 없기 때문에 undefined
```

<br/>

### ● 형 변환

```
let numberA = 12;
let numberB = "2";
console.log(numberA * numberB) //24
console.log(numberA + numberB) //122

//문자를 숫자로 변환
console.log(numberA + parseInt(numberB));
```

<br/>

### ■ 연산자

### ● 산술연산자

```
let a = 1;
let b = 2;

console.log(a + b); //3
console.log(a * b); //2
console.log(a - b); //-1
console.log(a / b); //0.5
console.log(a % b); //1
```

<br/>

### ● 증감연산자

```
let a = 10;
a++;

[ 전위연산자 ]
let b = 10;
console.log(++b); //11(증가하고 출력)

[ 후위연산자 ]
let c = 10;
console.log(c++); //10(출력하고 증가)
```

<br/>

### ● 논리연산자

```
console.log(!false); //true
console.log(!true); //false
console.log(true && true); //true AND true
console.log(true || false); ///true OR false

let compareA = 1 == "1"; // 값 비교
let compareB = 1 === "1"; // 값, 자료형 비교
let compareC = 1 !="1"; //false
let compareD = 1 !=="1"; //true

[ 대소비교 ]
let compareA = 1 >= 2; //false

[ typeof ] 변수형의 자료형 출력
let compareA = 1;
console.log(typeof compareA); //number

[ null 병합 연산자 ]
let a;
a = a ?? 10;
console.log(a); //10(null병합 연산)
```

<br/>

### ■ 조건문

&nbsp;: 어떤 연산의 결과의 참 거짓에 따라서 다른 명령을 실행

```
let a = 6;

if(a >= 7) {
  console.log("7 이상입니다.")
} else if (a >= 5) {
  console.log("5 이상입니다.")
} else if (a >= 4) {
  console.log("4 이상입니다.")
} else {
  console.log("5 미만입니다.")
}

[ if문 ]
let country = "ko";

if(country === 'ko') {
  console.log("한국")
} else if(country === 'cn') {
  console.log("중국");
} else if(country === 'jp') {
  console.log("일본");
} else {
  console.log("미 분류");
}

[ case문 ]
let country = "ko";

switch(country) {
  case 'ko':
    console.log("한국");
    break;
  case 'cn':
    console.log("중국");
    break;
  case 'jp':
    console.log("일본");
    break;
  case 'uk':
    console.log("영국");
    break;
  default:
    console.log("미 분류")
    break;
}
```

<br/>

### ■ 함수

```
let width1 = 10;
let height1 = 20;

let area1 = width1 * height1;
console.log(area1);

// 함수 선언식, 함수선언 방식의 함수 생성
function getArea() {
  let width = 10;
  let height = 20;

  let area = width * height;
  console.log(area);
}

//함수호출
getArea();


// 여러 개의 값을 넣는 함수
function getArea(width, height) {
  let area = width * height;
  console.log(area);
}

//함수호출
getArea(1,200);
getArea(2,200);


let count = 1; //전역변수-내부접근 가능

function getArea(width, height) {
  let area = width * height; //지역변수-외부 접근 불가능
  console.log(count);
  return area;
}

let area1 = getArea(100, 200);
console.log("area1: ", area1);
```

<br/>

### ■ 함수 표현식 & 화살표 함수

```
// 함수 표현식
let hello = function () {
  return "A";
}

// 함수 선언식
function helloFunc() {
  return "B";
}

const helloText = hello();
console.log(helloText);


// 화살표 함수 !순서 지켜서 사용
let helloA = () => {
  return "A";
}

let helloB = () => "AB";

console.log(helloA());
helloB();
```

<br/>

### ■ 콜백 함수

```
function checkMood (mood, goodCallback, badCalback) {
  if(mood === "good") {
    goodCallback();
  } else {
    badCalback();
  }
}

function cry() {
  console.log("ACTION :: CRY")
}

function sing() {
  console.log("ACTION :: SING");
}

function dance() {
  console.log("ACTION :: DANCE");
}

checkMood("good", sing, cry);
```

<br/>

### ■ 객체

```
// 객체 리터럴 방식
let person = {
  key: "value", //프로퍼티(객체 프로퍼티)
  key1: "value1",
  key2: true,
  key3: undefined,
  key4: [1, 2],
  key5: function() {}
};

console.log(person.key1);
console.log(person.key2);
------------------------------------------
// 객체에 함수넣기
const person = {
  name: "이정환",
  age: 25,
  //함수
  say: function() {
    console.log(`Hi ${person["name"]}`);
  }
};

console.log(`name: ${"name" in person}`); //person객체에 name이라는 프로퍼티가 있는지
console.log(`age : ${"age" in person}`); //true
console.log(`gender : ${"gender" in person}`); //false
```

<br/>

### ■ 배열

&nbsp;: 순서 있는 요소들의 집합

```
// 생성자 호출방법#1
let arr1 = new Array();

// 생성자 호출방법#2
let arr2 = [1, 2, 3, 4, 5];
let arr3 = [1, "2", true, null, undefined, {}, [], function() {}];

let arr4 = [1, 2, 3, 4, 5];
console.log(arr[0]);
console.log(arr[1]);
console.log(arr[2]);
console.log(arr[3]);
console.log(arr[4]);

arr.push({ key: "valule" }); // 배열추가
console.log(arr.length); // 현재 배열의 길이
```

<br/>

### ■ 반복문

&nbsp;: 특정 명령을 반복해서 수행할 수 있도록 도와주는 명령어

```
let person = {
  name: "가나다",
  age:25,
  tall: 175
}

const personKeys = Object.keys(person); // 객체자체
console.log(personKeys);

//key, value값 같이 순회
for(let i = 0; i < personKeys.length; i++) {
  console.log(personKeys[i]); //key값 순회

  const curKey = personKeys[i];
  const curValue = person[curKey];

  console.log(`${curKey} : ${curValue}`); //value값 순회
}
```

<br/>

### ■ 배열 내장함수

```
[ 배열을 순회하는 내장함수 ]
const arr = [1, 2, 3, 4];

// 함수 선언 방식1
arr.forEach(function (elm) {
  console.log(elm);
console.log(elm * 2);
});

↓ 코드 한 줄로 줄이기
// 배열 내장 함수
arr.forEach((elm) => console.log(elm));


// 함수 선언 방식2
arr.forEach(function (elm) {
  newArr.push(elm * 2);
});

console.log(newArr);


// 일치하는 값 존재 && 몇 번째에 존재하는지
const arr = [1, 2, 3, 4];

let number = 3;

console.log(arr.indexOf(number)); //문자열은 인식X


// 숫자가 아닌 문자열 객체뽑기
const arr = [
  { color: "red" },
  { color: "black" },
  { color: "blue" },
  { color: "green" }
];

let number = 3;
console.log(
  arr.findIndex((elm) => {
    return elm.color === "blue";
  })
);
```

<br/>

---

## 섹션2. JavaScript 응용

### ■ Truthy & Faisy

- Truthy: 참 같은 값<br/>
- Faisy: 거짓 같은 값<br/>

```
let a = "undefined"; //false 인식

if(a) {
  console.log("TRUE");
} else {
  console.log("FALSE");
} // if a="" -> FALSE / a="string" -> TRUE
```

> 참으로 인식: string, 숫자, "0", [], {}, Infinity<br/>
> 거짓으로 인식: null, undefined, ex)let a;(할당X), 0, -0, NaN, ""

<br/>

```
// undefined
const getName = (person) => {
  if (!person) {
    //false NOT => true (null과 undefined의 예외처리)
    return "객체가 아닙니다";
  }
  return person.name;
};

let person = null;
const name = getName(person);
console.log(name);
```

<br/>

### ■ 삼항 연산자

```
let a = -3;
a >= 0 ? console.log("양수") : console.log("음수");


// 배열의 현재길이
let a = [1, 23];
a.length === 0 ? console.log("빈 배열") : console.log("안 빈 배열");


// 주어진 값이 null이거나 undefined이 아닌지 판단하는 프로그램
let a;

const result = a ? true : false;
console.log(result);


// TODO: 학점 계산 프로그램
// 90점 이상 A+
// 50점 이상 B+
// 둘 다 아니면 F

let score = 40;

[ 삼항연산자 ]
score >= 90
  ? console.log("A+")
  : score >= 50
  ? console.log("B+")
  : console.log("F");
* 중첩삼항연산자는 코드의 가독성을 해칠 수 있기 때문에 중첩 if문 사용하는 것을 권장

[ if문 ]
if (score >= 90) {
  console.log("A+");
} else if (score >= 50) {
  console.log("B+");
} else {
  console.log("F");
}
```

<br/>

### ■ 단락 회로 평가

&nbsp;: 피연산자 중에 뒤에 위치한 피연산자를 확인할 필요없이 연산을 끝내버리는 것

```
// 논리 연산자
console.log(true && true); //true
console.log(true || false); //true
console.log(!true); //false

// 첫 번째 피연산자가 false이면 false값 반환
console.log(false && true);


[ 단락회로평가 ]
const getName = (person) => {
  const name = person && person.name; //null
  return name || "객체가 아닙니다";
};

let person = null;
const name = getName(person);
console.log(name); //객체가 아닙니다
```

<br/>

### ■ 조건문 업그레이드(Upgrade)

```
// 주어진 값에 따라서 다른 결과물을 반환하는 함수
const getMeal = (mealType) => {
  if (mealType === "한식") return "불고기";
  if (mealType === "양식") return "파스타";
  if (mealType === "중식") return "멘보샤";
  if (mealType === "일식") return "초밥";
  return "굶기";
};

console.log(getMeal("한식"));
console.log(getMeal("중식"));
console.log(getMeal());


// 객체의 프로퍼티에 접근하는 괄호 표기법
const meal = {
  한식: "불고기",
  중식: "멘보샤",
  일식: "초밥",
  양식: "스테이크",
  인도식: "카레"
};

const getMeal = (mealType) => {
  return meal[mealType] || "굶기";
};

console.log(getMeal("중식"));
console.log(getMeal());
```

<br/>

### ■ 비 구조화 할당

```
[ 비구조화 ]
let object = { one: "one", two: "two", three: "three" };

let { one, two, three } = object;
console.log(one, two, three);


// 객체의 비구조화 할당은 배열의 인덱스를 이용하는 게 아니라 키 값을 할당
let object = { one: "one", two: "two", three: "three", name: "이정환" }; //순서상관없음

let { one, two, three, name } = object;
console.log(one, two, three, name);



let object = { one: "one", two: "two", three: "three", name: "이정환" };

let { name: myName, one: oneOne, two, three } = object;
console.log(oneOne, two, three, myName);



let object = { one: "one", two: "two", three: "three", name: "이정환" };

let { name: myName, one: oneOne, two, three, abc = "four" } = object;
console.log(oneOne, two, three, myName, abc);
```

<br/>

### ■ Spread 연산자

```
const cookie = {
  base: "cookie",
  madeIn: "korea"
};

const chocochipCookie = {
  ...cookie, // Spread 연산자..객체의 중복되는 요소 펼치기
  topoing: "chocochip"
};

const blueberryCookie = {
  ...cookie,
  topoing: "blueberry"
};

const strawberryCookie = {
  ...cookie,
  topoing: "strawberry"
};

console.log(chocochipCookie);
console.log(blueberryCookie);
console.log(strawberryCookie);


const noTopingCookies = ["촉촉한쿠키", "안촉촉한쿠키"];
const topingCookies = ["바나나쿠키", "블루베리쿠키", "딸기쿠키", "초코칩쿠키"];

const allCookies = [...noTopingCookies, "함정쿠키", ...topingCookies]; // 중간에 값을 유연하게 넣을 수 있음
console.log(allCookies);
```

<br/>

### ■ 동기 & 비동기

### &nbsp;● 동기 방식의 처리

&nbsp;&nbsp;&nbsp;- 자바스크립트는 코드가 작성된 순서대로 작업을 처리<br/>
&nbsp;&nbsp;&nbsp;- 이전 작업이 진행중일 때는 다음 작업을 수행하지 않고 기다림<br/>
&nbsp;&nbsp;&nbsp;- 먼저 작성된 코드를 먼저 다 실행하고 나서 뒤에 작성된 코드를 실행<br/><br/>

> 동기처리 방식의 문제점
>
> > 하나의 작업이 너무 오래 걸리게 될 시,<br/>
> > 그 작업이 종료되기 전까지 올 스탑 되기 때문에 전반적인 흐름이 느려진다.

### &nbsp;● 블로킹

: 스레드에서 작업 하나가 수행되고 있을 때 다른 작업을 동시에 할 수 없는 방식<br/>

### &nbsp;● 멀티 쓰레드

: Thread를 여러 개 사용하는 방식<br/>
&nbsp;&nbsp;&nbsp;- 코드를 실행하는 일꾼 Thread를 여러 개 사용하는 방식인 `MultiThread` 방식으로 작동시키면 작업 분할 가능<br/>
&nbsp;&nbsp;→ 그러나 자바스크립트는 싱글 쓰레드로 동작.. 이런 방식으로 일꾼을 여러 개 사용하는 방법은 불가<br/>

### &nbsp;● 비동기

: 먼저 작성된 코드의 결과를 기다리지 않고 다음 코드를 바로 실행

<img src="https://github.com/BlueWings2017/BlueWings2017.github.io/blob/main/post-img/TeamC/reactYujung1.jpg?raw=true" width="800" height="auto"/>

<br/>

### ■ Promise

&nbsp;&nbsp;&nbsp;- 비동기 작업은 한번 성공하거나 실패하면 작업 끝<br/>

<img src="https://github.com/BlueWings2017/BlueWings2017.github.io/blob/main/post-img/TeamC/reactYujung2.jpg?raw=true" width="750" height="auto"/>

```
function taskA(a, b) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      const res = a + b; // 지역상수
      resolve(res); //callback
    }, 3000);
  });
}

function taskB(a) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      const res = a * 2;
      resolve(res);
    }, 1000);
  });
}

function taskC(a) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      const res = a * -1;
      resolve(res);
    }, 2000);
  });
}

const bPromiseResult = taskA(5, 1).then((a_res) => {
  console.log("A RESULT:", a_res);
  return taskB(a_res); //then 콜백함수가 수행이 되면서 마지막에 taskB를 호출해서 그 결과값을 반환
});

console.log("abcdefghijklmn"); //중간에 코드추가 가능

bPromiseResult //다시수행
  .then((b_res) => {
    console.log("B RESULT:", b_res);
    return taskC(b_res);
  })
  .then((c_res) => {
    console.log("C RESULT:", c_res);
  }); //then메서드가 계속 되는 것 - then체이닝
```

<br/>

### ■ async & await - 직관적인 비 동기 처리 코드 작성하기

&nbsp;&nbsp;&nbsp;- async, await은 Promise를 더 쉽고 가독성 좋게 작성가능<br/>

```
//async
function hello() {
  return "hello";
}

// async를 붙여주면 이 함수는 자동적으로 Promise를 return하는 비동기처리 함수가 된다.
async function helloAsync() {
  return "hello Async";
}

// Promise를 return하기 때문에 .then사용가능
helloAsync().then((res) => {
  console.log(res); //hello Async
});

function delay(ms) {
  return new Promise((resolve) => {
    setTimeout(resolve, ms); //callback함수 자체 resolve전달을 해도 상관X
  });
}

// async를 붙여주면 이 함수는 자동적으로 Promise를 return하는 비동기처리 함수가 된다.
async function helloAsync() {
  await delay(3000); //await을 비동기 함수 앞에 붙이면 비동기가 동기인 것처럼 작동
  return "hello Async";
}

async function main() {
  const res = await helloAsync();
  console.log(res);
}

main();
```

<br/>

### ■ API 호출하기(API & fetch)

### &nbsp;● API(Application Programming Interface) - 응용프로그램 프로그래밍 인터페이스

: 응용 프로그램에서 사용할 수 있도록 운영체제나 프로그래밍 언어가 제공하는 기능을 제어할 수 있게 만든 인터페이스<br/>

> -&nbsp;(내장함수) fetch: 자바스크립트에서 api를 호출할 수 있도록 도와주는 내장함수.. promise를 반환<br/>
> -&nbsp;promise를 반환하는 함수는 비동기처리를 하는 함수이고 함수의 처리결과는 then을 통해 사용가능<br/>
> -&nbsp;fetch를 통해 api를 호출하게 되면 그 api의 결과값 반환X api자체객체를 반환하기 때문에 Response라는 객체가 출력<br/>

```
async function getData() {
  let rawResponse = await fetch("https://jsonplaceholder.typicode.com/posts");
  let jsonResponse = await rawResponse.json();
  console.log(jsonResponse);
}

getData();
```

<br/>

---

## 섹션3. Node.js 기초

### ■ Node.js란?

<img src="https://github.com/BlueWings2017/BlueWings2017.github.io/blob/main/post-img/TeamC/reactYujung3.jpg?raw=true" width="780" height="auto"/>

<br/>

### ■ Node.js HelloWorld & Common JS

```
[ index.js ]
const calc = require("./calc"); //node.js에 있는 내장함수이기 때문에 vanilla.js에서는 이용이 제한됨

console.log(calc.add(1, 2));
console.log(calc.add(4, 5));
console.log(calc.sub(10, 2));

[ calc.js ]
// 계산 기능을 하는 파일
const add = (a, b) => a + b;
const sub = (a, b) => a - b;

// 계산 모듈 내보내기
module.exports = { //node.js에 있는 내장함수
    moduleName : "calc module",
    add: add,
    sub: sub,
};
```

<br/>

### ■ Node.js 패키지 생성 및 외부 패키지 사용하기(프로젝트 & npm)

### ● npm(Node Package Manager): Node.js의 패키지 관리 도구

> TERMINAL → npm init 실행 - package.json 생성

&nbsp;&nbsp;- package.json: 'scripts'는 자주 실행해야하는 명령어를 사전에 정의해둘 수 있는 곳

```
[ index.js ] - randomcolor실습

const randomColor = require('randomcolor');

let color1 = randomColor();
let color2 = randomColor();
let color3 = randomColor();

// console.log(randomColor());
console.log(color1, color2, color3);
```

<br/>

---

## 섹션4. React.js 기초

### ■ Why React?

1. 컴포넌트화 방식을 통해 중복되는 코드를 줄일 수 있다. (Component 기반의 UI 라이브러리 React를 사용)
2. 목적을 바로 말하는 선언형 프로그래밍
3. Virtual Dom 사용

<br/>

### ■ Create React App

<img src="https://github.com/BlueWings2017/BlueWings2017.github.io/blob/main/post-img/TeamC/reactYujung4.jpg?raw=true" width="800" height="auto"/>

<br/>

### ■ JSX

: JavaScript와 HTML을 혼합해서 쓸수 있는 React에서 주로 사용하는 표현식

> -&nbsp;index.js에서 최상위 컴포넌트를 정의가능<br/>
> -&nbsp;하나의 컴포넌트로 만들어서 return하려면 반드시 하나의 최상위 태그로 묶어주어야 한다.<br/>&nbsp;&nbsp;(react.Fragment 기능을 이용해서 최상위 태그를 대체가능)

<br/>

### ■ State(상태)

: 계속해서 변화하는 특정 상태.. 상태에 따라 각각 다른 동작을 함

```
[ Couter.js ]
const Counter = () => {

  // 0에서 출발 1씩 증가하고, 1씩 감소하는 count 상태
  console.log("counter 호출"); //버튼을 누를 때마다 함수가 호출

  const [count, setCount] = useState(0); //useState를 호출하면서 0이라는 인자를 넘김(초기값)

  const onIncrease = () => {
    setCount(count + 1);
  }

  const onDecrease = () => {
    setCount(count - 1);
  }

  //여러 개의 State를 하나의 컴포넌트가 가져도 문제X
  const [count2, setCount2] = useState(0);

  const onIncrease2 = () => {
    setCount2(count2 + 1);
  }

  const onDecrease2 = () => {
    setCount2(count2 - 1);
  }

    return (
        <div>
            <h2>{count}</h2>
            <button onClick={onIncrease}>+</button>
            <button onClick={onDecrease}>-</button>

            <h2>{count2}</h2>
            <button onClick={onIncrease2}>+</button>
            <button onClick={onDecrease2}>-</button>
        </div>
    )
}

export default Counter;
```

<br/>

### ■ Props

: 자식 컴포넌트에 이름을 붙여 값을 넘겨줌

```
[ Container.js ]

const Container = ({ children }) => {
  console.log(children);
  return (
    <div style={{ margin: 20, padding: 20, border: "1px solid gray" }}>
      {children}
    </div>
  );
};

export default Container;
```

<br/>
