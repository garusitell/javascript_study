# 문
표현식을 자바스크립트의 구절이라고 설명했다면 **문** 은 자바스크립트의 문장이나 명령어라고 할 수 있다. 표현식은 ' 평가'를 통해 값으로 바뀌지만 , 문은 **'실행'** 을 통해 어떤 동작을 수행한다.  

문은 종류가 조금 많다.


## 표현문
- 표현문 (expression statement)  : 할당 , 함수 호출처럼 부수효과가 있는 문
``` javascript
//숫자, 문자, 불리언 리터널 
10;
"hello";
true;

// 변수 할당(참조)
let x = 5;

// 함수 호출
console.log("Hello, World!");

// 비교 연산자
5>3;
10 === 10;

//논리 연산자
ture && false;
true || false;

// 산술 계산
let sum = 10 + 20;

// 증가와 감소 연산자 (++ , --)
counter++;

// 삼항 연산자
let isEven = (x % 2 === 0) ? true : false;

// 배열 요소 접근
let number = [1,2,3];
numbers[0]; -> 1로 평가된다.
```
즉 거진 모든 함수는 기본적으로 표현식이다. 변수를 표현하던지, 하던가이다.

>여기에는 평가도 들어가는데, 예시에서는 산술 계산이 평가로 들어간다. 즉 sum이라는 것이 `10+20`으로 인해 `30`으로 평가되는 것이다.  

> 함수에 부수 효과가 없다면 더 큰 표현식이나 할당문의 일부가 아닌 한 호출할 의미가 없다. 예를 들면 `Math.cos(x);`과 같이 그냥 계산만하고 쓰지않는 바보같은 짓이라던가..

> console.log는 함수인가?  
> console.log 는 함수이다.
> console은 전역 객체 ,log 는 console 객체의 메서드로 콘솔에 메세지를 출력하는 함수이다  
 java는 함수가 있는가? -> java는 함수라는 명이 없으며 console.log와 비슷한 기능을 하는 system.out.println은 system의 클래스 out 의 필드 println의 메서드로 나누어져있다.

> 그럼 자바의 메소드는 자바스립트의 함수와 같은 역할을 할까?


## 복합문과 빈문
표현식을 여러 개를 하나로 묶는 콤마 연산자와 마찬가지로 문 블록은 문 여러개를 묶어 복합문으로 만든다. 문 블록은 그저 문 여러개를 중괄호로 묶은 것이며, 하나처럼 행동한다.

```javascript
{
    x = Math.PI;
    cx = Math.cos(x);
    console.log("cos(π) = "+ cx);
}
```
유의할점이 있다.
1. 블록으니 세미콜론으로 끝나지 않는다. 기본 문은 세미콜론으로 끝나지만 블록 자체는 그렇지 않다.
2. 블록에 들어있는 행은 자신을 감싼 중괄호를 기준으로 들여쓴다.

복합문은 하위 문으로 구성될 수 있는 데 이것은 우리가 익숙하게 쓰는 것 이다. 예시를 보자

- 사용하지 않은 예시
```javascript
let x = 5;

if(x > 0) console.log("x is positive");
```

- 사용 한 예시
```javascript
let x = 5;
if(x>0) {
    console.log("x is positive");
}
```

### 단일 하위문의 장점과 단점
- 장점
    - 간결함 : 코드가 간단해지고 읽기 쉬워진다
    - 가독성 : 작은 코드 블록에서는 가독성이 높아질 수 있습니다.
- 단점
    - 유지보수 : 단일 하위문을 사용하는 경우 , 나중에 코드를 실행하거나 추가할 떄 실수할 가능성이 높아진다. 중괄호를 사용하지 않으면 코드 블록이 정확히 어디서 끝나는지 헷갈릴 수 있다.
    - 확장성 : 나중에 더 많은 코드가 추가될 때 , 중괄호를 추가하는 것을 잊어버리면 의도치 않은 동작을 유발할 수 있다.



## 선언문
- 선언문 (declaratuin statement) : 변수를 선언하거나 함수를 정의하는 문을 의미한다.
```javascript
// 변수 선언
let y;
const z = 10;

// 함수 선언
function greet(name) {
    return `Hello, ${name}!`;
}

// 클래스 선언
class Person {
    constructor(name, age) {
        this.name = name;
        this.age = age;
    }

    introduce() {
        return `My name is ${this.name} and I am ${this.age} years old.`;
    }
}
```

자바스크립트 인터프리터는 기본적으로 문의 작성된 순서대로 실행되며, 실행 순서도 바꾸는 문이 있는데 이를 **제어문(control structure)** 가 있다.

> 여기서 statement(문장)은 프로그램 실행단위, 즉 하나의 작업 또는 명령을 나타내는것  
> structure(구조)는 여러 문장을 표현하는 것으로 더 큰 블록을 의미한다.  
> 즉 statement가 여러게 모여있는 것이 structure라고 단순하게 판단할 수 있다.

## 조건문
- if 나 switch처럼 자바스크립트 인터프리터가 표현식의 값에 따라 다른 문을 실행하거나 실행하지 않게 하는 문이다.분기점 이라 부르기도 한다. 인트프리터는 반드시 그 경로 중 하나를 선택해야 한다.
- **if**
```javascript
if(expression){
    statemenet1
}else{
    statement2
}

if(sum != 10){
    sum = sum + 1
}else{
    console.log(sum);
}
```

- **else if**
```javascript
if (n == 1){
    //코드 블록 #1을 실행
}else if(n == 2){
    //코드 블록 #2을 실행
}else if(n == 3){
    //코드 블록 #3을 실행
}else{
    //전부 실패하면 블록 #4를 실행한다.
}

// else
```
- **switch**
```javascript
switch(n){
    case 1: // n == 1 이면 여기서 시작한다.
    break;
    case 2: // n == 2 이면 여기서 시작한다.
    break;
    case 3: // n == 3 이면 여기서 시작한다.
    break;
    default: // 앞이 모두다 실패하면
    break;
    
}
```

> 이 코드에서는 각 case에 break코드를 썻는데. switch 문의 case절은 코드의 출발점을 지정할 뿐 , 어디서 끝나는지 지정하지 않는다. 즉 break 나 return문이 없는한 쭉 내려가서 default문을 다시 실행한다

## 루프
while 이나 for 처럼 다른 문을 반복적으로 실행하는 문
-자바 스크립트 루트문의 종류
- while 
- do/while 
- for
- for/of(≒ for/await)
- for/in  

우리는 여기서 처음, 생소하게 보는 두가지만 알아보려고 한다. for/of문과 for/in문이다.

### for / of
for / of는 ES6에서 정의한 새 반복문이며 , for 키워드를 사용하지만 일반적인 for 루프와는 완전히 다르다. 
for/of문은 이터러블 객체(iterable object)에서 동작한다. 반복 가능한 객체로, 순회할수 있는 객체, 연속체 또는 일련의 요소들을 말한다.  
 리스트,튜플,딕셔너리,문자열,집합 등이 있다. for/of문을 사용하는 프로그래밍 언어는 (python, typescript, swift, c# , Ruby)가 있다.
```javascript
let data = [1,2,3,4,5,6,7,8,9] , sum = 0
for ( let elemet of data){
    sum += elelemt;
}
sum //45
```
`data[i]` 를 줘서 순회할 수 도 있지만 여기서는 `elemet`의 요소가 for문 안의 `data`안의 값을 받아서 수행하는것을 볼 수 있다.

#### for/of와 객체
객체는 기본적으로 이터러블이 아니며 , 일반적인 객체에 for/of를 사용하려 하면 TypeError가 뜬다.
```javascript
let o = { x:1 ,y : 2,z : 3}

for(let element of o){
    console.log(element); // o는 이터러블이 아니므로 TypeError가 일어납니다.
}

// 고친 코드
let o = { x:1 , y:2 , z:3};
let keys = "";
for(let k of Object.keys(o)){
    keys += k;
}
keys // => "xyz"


```
#### for/of 와 문자열 , 세트 , 맵
ES6 이후에는 문자열을 순회할 수 있으며, Set과 Map 클래스는 이터러블이다.
```javascript
/// 문자열
let frequency = {}
for (let letter of "mississippi"){
    if(frequency[letter]{
        frequency[letter];
    })else{
        frequency[letter] = 1;
        }
}
frequency -> {m:1 , i : 4 , s : 4 ,p :2}
// Set
let text = "Na na na na na na Batman!";
let wordSet = new Set(text.split(" "));
let unique = [];
for (let word of wordSet{
    unique.push(word);
})
unique // => ["Na","na","Batman"]

// Map
let m = new Map{[1 , "One"]};
for ( let [ky, value] of m){
    key // =>1
    value // =>"one
}
```

### for / in
for / in은 of 키워드가 in으로 바뀐것일뿐 거의 비슷하다. 하지만 몇가지 다른점 이 있다.
- 자바스크립트 인터프리터는 for / in  문을 첫 번째로 object 표현식을 평가하며 , null이나  undefined 로 평가되면 인터프리터는 루프를 건너뛰고 다음문으로 이동한다.
- 하지만 정의된 평가문이면 열거가능한 프로퍼티 각각에 한 번씩 루프 바디를 실행한다. 각 부분에 앞서 인터프리터는 variavle 표현식을 평가하고 그 변수에 프로퍼티 이름을 할당한다.  

**즉 배열을 대상으로 할떄는 for / of 문이 맞다.**

### 차이점을 알아보자.
1. 순회대상
    - for / in :  객체의 열거 가능한 속성(키)를 순회
    - for / of :  이터러블 객체의 요소(값)를 순회
2. 사용용도
    - for / in : 객체의 속성을 반복할떄 유용
    - for / of : 배열이나 다른 이터러블 속성의 요소를 반복할떄  유용
3. 동작방식
    - for / in : 객체의 프로토타입 체인에 있는 열거 가능한 속성도 포함될 수 있다.
    - for / of : 이터레이터 프로토콜을 따르는 이터러블 객체를 순회하며, 배열의 인덱스가 아니라 요소 그 자체를 반환한다.

```javascript
const arr = [10, 20, 30];
arr.someProperty = 'value';

console.log('Using for/in:');
for (let key in arr) {
    console.log(key); // 0, 1, 2, someProperty
}

console.log('Using for/of:');
for (let value of arr) {
    console.log(value); // 10, 20, 30
}
```




## 점프 
break , return , thorw는 인터프리터가 프로그램의 다른 부분으로 건너뛰게 하는 문  
### 라벨 문
- 어떤 문이든 라벨을 붙일 수 있는데 , 문에 라벨을 붙이는 것은 프로그램 다른곳에서 참조할 수 있는 이름을 짓는 것과 같다. 
- 라벨문을 할당할떄 주의 사항:
    - 같은 식별자를 문 라벨에 쓰고 , 다시 변수와 함수의 이름에 쓸 수 도 있다. 문 라벨이 정의 되는 영역은 해당 라벨이 적용되는 문 뿐이다. 
    - 즉 모든 문은 라벨을 중복으로 여러개 받을 수 있다. 즉 문에서 실행하는 부가 설명이라고 할 수 있다.

###  break 
break : 단독으로 사용하면 자신을 포함하고 있는 가장 가까운 루프 또는 switch문을 즉시 빠져 나간다.
- 일반적으로 어떤 이유로든 루프를 더 진행할 필요가 없을 때 일찍 끝내는 용도로 사용한다. 즉 원하는 것을 찾으면 일찍 끝내는 용도가 일반적이다.
- break 에 라벨을 사용하면 해당 라벨이 붙은 문을 종료한다. 예시를 보자
    ```javascript
    let matrix = getData(); // 숫자로 구성된 2차원 배열을 만든다
    // 행렬에 포함한 숫자를 모두 더한다.
    let sum = 0 , success = false;
    // 에러가 발생했을 때 빠져나갈 수 있도록 라벨 붙은 문으로 시작한다.
    computeSum : if(matrix){
        for(let x = 0; x < matrix.lenght; x++){
            let row = matrix[x];
            if (!row) = break computeSum;
            for(let y = 0 ; y < row.length; y++){
                let cell = row[y];
                of(isNaN(cell)) break computeSum;
                sum += cell
            }
        }
        success = true;
    }
    ```
### continue 
comtinue : 루프 안에서 continue 를 사용하면 루프의 다음 반복으로 넘어간다. 라벨과 함께 사용할 수도 있다. 여러가지 반복문에서 사용할 수 있는데
- while 루프에서는 expression(표현식)을 루프의 맨 위에서 다시 평가하고 , true a면 루프 바디를 맨 위에서부터 실행한다.
- do/while 루프에서는 루프 맨 아래까지 건너 뛴 다음 , 루프 조건을 다시 평가한 후 맨위에서부터 다시 재시작한다.
- for 루프에서는 increment(증가) 표현식을 평가하고 나서 test(테스트) 표현식을 평가해서 반복을 재개할지 결정
- for/of와 for/in 루프에서는 다음 값 또는 프로퍼티 이름이 variable(변수)에 할당된다.

### reutrn 
return : 함수 호출의 값을 지정한다.
``` javascript
function square(x){return x*x};
square(2) // => 4
```
### yield 
yield은 reuturn 문과 아주 비슷하지만 ES6 제너레이터 함수 안에서만 사용하며 실제로 제어권을 넘기지 않고 다음갑만 넘길때 사용합니다.
```javascript
function* range(from , to){
    for (let i = from , to){
        yield i;
    }
}
```
yield 는 이터레이터와 제너레이터를 이해해야 한다. 연산자에 가깝다.

### throw
**예외** 란 (Exception)은 예외적인 조건이나 에러가 일어났다는 신호이다. 예외를 일으키는(throw)것은 그런 에러나 예외적 조건이 일어났다는 신호를 보내는 것이다.  
즉 throw는 자바스크립트에서 예외를 일으킨다고 생각하면 편하다. 여기서 보내는 오류는 try/catch/finally 문에서 캐치한다.

예외가 일어나면 자바스크립트 인터프리터는 즉시 프로그램 실행을 멈추고 가장 가까운 예외 핸들러로 점프한다. 이 말은 try/catch/finally 에서 catch문으로 넘어가고 , 없다면 가장 가까운 코드 블록에 예외 핸들러가 있는지 검색한다. 하지만 없으면 해당 함수를 호출한 코드까지 올라간다.

```javascript
function checkNumber(number) {
    if (number < 0) {
        throw 'Negative number'; // 문자열을 예외로 던짐
    }
    return number;
}

try {
    checkNumber(-1);
} catch (e) {
    console.log('Caught an exception:', e); // "Caught an exception: Negative number"
}
```

### try/catch/finally
try/catch/finally 문은 자바스크립트 예외처리 매커니즘이다.
try블록에서 예외가 일어나면 catch블록에서 무슨일이 일어났든 관계없이 실행되는 일종의 정리코드이다.  
catch와 finally는 선택사항이지만, try 뒤에는 하나는 써야한다.예시를 보자
```javascript
try{
    /// 문제가 없을 경우 이 코드는 블록 위쪽에서 아래쪽으로 실행된다.
    /// 이 코드는 예외를 일으킬수 있는데 throw문을 통해서 직간접적으로 일으킬 수 있다.
}catch{
    // 이 블록은 try 블록에서 예외를 일으킬때만 사용한다.
    // Erorr 객체 뙤는 전달 받은 값을 참조하며 변수 e를 사용 할 수 있다.
    // 예외를 처리, 무시 , 다시 throw를 통해 예외를 일으킬 수 있다.
}finally{
    // try블록에서 무슨일이 있든 항상 실행된다.
    // 1) 정상저긍로 try 블록의 끝에 도달한 경우
    // 2) break , continue , return 문을 통해 try 문을 통과하는 경우
    // 3) 위 catch 절에서 처리한 예외 때문에 try 블록이 종료된 경우
    // 4) 예외가 캐치되지않고 계속 전파하는 경우
}
``` 
catch 키워드 뒤에는 일반적으로 괄호 안에 식별자를 사용하며 , 함수 매개변수와 비슷하다.  
예외를 캐치하면 그 예외와 연결된 값이 매개변수에 할당된다.

try - finally 문은 try문에서 어떠한 일이 일어나든 그냥 finally로 넘기는 용도로 사용됩니다.  
try - catch 는 catch 절을 예외를 감지하고 전파를 막을 목적으로만 사용하거나 예외의 타입이나 값에는 관심이 없을 때 사용된다. 왜 사용하는지는 모르겠다.

#### 브라우저에서의 디버깅



1.	소스 코드 탐색: 브라우저의 디버거 창에서 자바스크립트 파일을 열어 소스 코드를 탐색할 수 있습니다.
2.	브레이크포인트 설정: 특정 코드 줄에 브레이크포인트를 설정하여 해당 줄에서 코드 실행을 일시 중지할 수 있다.
3.	변수 검사: 코드 실행이 중단된 상태에서 변수의 현재 값을 확인할 수 있다.
4.	단계별 실행: 코드 라인을 하나씩 실행하며, 함수 호출 내부로 들어가거나, 함수 호출을 완료하고 다음 줄로 넘어갈 수 있다.
5.	호출 스택 검사: 코드 실행이 중단된 지점까지의 함수 호출 스택을 확인할 수 있습니다.
6.	네트워크 요청 검사: 페이지의 네트워크 요청을 모니터링하고, 요청 및 응답 데이터를 검사할 수 있다.

#### 디버거 사용 방법

1.	브라우저 개발자 도구 열기: 대부분의 브라우저에서 F12 키 또는 오른쪽 클릭 후 “검사”를 선택하여 개발자 도구를 열 수 있다.
2.	소스 코드 패널: 개발자 도구에서 “Sources” (소스) 탭을 선택하여 자바스크립트 파일을 탐색다.
3.	브레이크포인트 설정: 디버거에서 중단하고 싶은 줄 번호를 클릭하여 브레이크포인트를 설정한다.
4.	디버깅 시작: 페이지를 새로 고치거나 debugger 문이 있는 코드를 실행하면 디버거가 중단된다.
5.	단계별 실행 및 검사: 개발자 도구의 디버깅 버튼을 사용하여 코드 실행을 한 줄씩 진행하고, 변수 값을 확인하며, 코드 흐름을 추적한니다.

## 기타 문
### with
with : 객체의 프로퍼티가 해당 블록의 스코프 안에 있는 변수인것 처럼 코드 블록을 실행한다.
```javascript
with (object)
    statement

with(document.forms[0]){
    name.value = "";
    address.value = "";
    email.value = "";
}
```
object(객체)의 프로퍼티를 사용해 임시 스코프를 만들고 , 그 스코프 안에서 statement(문)을 실행한다. 근데 잘 안쓴다.. 이유는 몇가지 있다.
1. 성능저하 : 자바스크립트 엔진이 스코프체인을 관리하는 방식을 복잡하게 만든다.
2. 디버깅 어려움 : 어떤 변수가 어디서 왔는지 읽기 힘들다
3. 코드 가독성 저하 

### debugger 
dubugger 문은 일반적으로는 아무 일도 하지 않지만 , 디버거 프로그램이 존재하고 실행중이라면 실행환경에 따라서는 일종의 디버깅 동작을 수행할 수 있다. 현실적으로 이 문은 일종의 중단점 기능을 해서 자바스크립트 코드 실행을 멈춘다. 이것은 웹 서버를 공부할떄 조금 더 현실적으로 다가 온다

### use strict 
use strict는 ES5에서 도입한 지시자 이다.  
use strict 지시자와 일반적인 문 사이에는 다음과 같은 중요한 차이가 있다.
- 이 지시자에는 아무런 키워드가 없으며 , 지시자는 특별한 문자열 리터널로 구성된 표현문 이다.
- 이 지시자는 스크립트나 함수 바디의 맨 처음에만 존재할 수 있고 , 이앞의 실제 문이 있어서는 안된다.

use strict 지시자는 스트릭트 모드를 따르라는 선언이다. 스트릭트 모드란 자바스크립트의 중요한 결점을 수정하고 더 강력한 에러를 체크하며 , 보안을 강화한 것이다. 

## 선언
const, let , var, function , class , import ,expart 은 문이라기 보다는 선언이라고 표현해야 더 정확하다.  
선언은 새 값을 정의하고 이름을 부여해서 나중에 참조할 수 있게 하며 , 값에 이름을 부여한다는 것은 프로그램에 속한 문의 의미가 바뀐다는 것이므로 중요하다.  
자바스크립트의 선언은 상수 , 변수 , 함수 , 클래스를 정의하고 모듈에서 값을 가져오고 내보낼 때 사용한다. 
### const,let,var
const는 상수를 let은 변수를 선언한다. ES6 전에는 var 키우드가 변수를 선언하는 유일한 방법이었다. var로 선언한 변수는 포함하는 블록이 아니라 함수를 스코프로 가진다. 근데 이제 var let사이의 버그는 없다고 한다. 변수 선언은 다음과 같다
```javascript
const TAU = 2*Math.PI;
let radius = 3;
var circumference = TAU * radius;
```

### 함수
function 선언은 함수를 정의 할 때 사용한다. 함수 선언은 다음과 같이 선언한다.
```javascript
function area(radius){
    return Math.PI *radius*radius ; 
}
```
함수 선언은 함수 객체를 생서앟고 이를 지정된 이름애 할당한다. 프로그램 다른 고셍서 이 이름을 사용해 함수를 참조하고 그 코드를 실행할 수 있다.  
함수 선언은 어떤 블록에 있든 해당 블록의 코드보다 먼저 처리되며 **호이스팅** 된다 라고 표현된다. 어떤 스코프에서 정의 됬든 항상 그 맨 위에 있는 코드에서 호출할 수 있다.
> var로 선언된 변수는 초기화 이전에 접근할 수 있지만, 값은 undefined이다. let과 const로 선언된 변수는 선언 전 접근 시 ReferenceError가 발생한다. 함수 선언은 전체 함수가 호이스팅되지만, 함수 표현식은 변수 선언만 호이스팅된다.
그 뒤의 다른 함수인 제너레이터 함수가 존재한다..

### 클래스 
ES6 이후에는 class 선언으로 새 클래스를 생성하고 이름을 붙인다 클래스 선언은 다음과 같은 형태이다.
```javascript
class Circle{
    constructor(radius){this.r = radius}
    area(){return Math.PI * this.r * this.r}
    circumference(){return 2 * Math.PI * this.r}
}
```
함수와 달리 클래스 선언은 끌어올리지 않으며 위와 같이 선언한 클래스는 선언하기 전에는 사용할 수 없다.

### 가져오기와 내보내기 
import 와 export선언은 다른 모듈에서 정의한 값을 사용할 수 있다. 한 모듈에서 정의한 값을 다른 모듈에서 사용하는 방법은 정의한 모듈에서 export로 값을 내보내고 사용할 모듈에서 import 로 가져오는 방법밖에 없다.  
import 지시자는 다른 모듈에서 하나 이상의 값을 가져오고 , 현재 모듈에서 사용할 이름을 부여한다. 다음 예시를 보자
```javascript
import Circle from './url~~.js'
import {PI,TAU} from './url~~.js'
import {magntitude as hypotenuse} from'./url~~.js'
```
자바스크립트 모듈에 들어있는 값은 비공개이며 명시적으로 내보내지 않은 한 다른 모듈에서 가져올 수 없다 . export 지시자가 이를 내보내는 역할을 한다. 

