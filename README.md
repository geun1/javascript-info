# Javascript info

### 자바스크립트 기본

- 개발자 콘솔
    
    브라우저에서는 스크립트에 에러가 발생해도 사용자에게 직접적으로 보여주지 않는다.
    
    발생하는 에러 및 다양한 정보를 개발자 도구를 통해 확인할 수 있다. 
    
    맥의 경우 `option + command + i` 를 통해서 개발자 도구를 확인할 수 있다. 
    
    개발자 도구 내에 `Console` 을 통해 자바스크립트 명령어를 입력할 수 있고 이를 `커맨드 라인` 이라고 부른다. 
    
- Hello world!
    
    ‘script’ 태그
    
    <script> 태그를 이용해서 자바스크립트 프로그램을 HTML 문서 대부분의 위치에 삽입할 수 있다.
    
    ```html
    <!DOCTYPE HTML>
    <html>
    
    <body>
    	
    <p>스크립트 전</p>
    
    <script>
    	alert('hello wordl!');
    </script>
    
    <p>스크립트 후</p>
    
    </body>
    
    </html>
    ```
    
    type 속성: <script type=…>
    
    HTML4에선 스크립트에 type 명시가 필수적이었다. 
    
    따라서 type=”text/javascript”속성이 붙은 스크립트가 많았지만 이젠 타입 명시가 필수가 아니다.
    
    모던 HTML 표준에선 이속성의 의미가 바뀌었다. 
    
    language 속성: <script language=…>
    
    현재 사용하고 있는 스크립트 언어를 나타낸다.
    
    지금은 자바스크립트가 기본 언어이므로 속성의 의미가 퇴색된 상황이다. 
    
- 

### 객체: 기본

### 자료구조와 자료형

### deep info

- 객체가 왜 값이 바뀔 수 있는지
    
    기존 원시값(number, string, … )을 할당한 변수의 메모리 주소에는 원시값 자체가 존재한다. 
    
    하지만 객체의 경우에는 객체를 할당한 변수에는 참조값이 존재한다. 참조값은 생성된 객체가 저장된 메모리 공간의 주소 그 자체이다. 
    
    ![Untitled](Javascript%20info%2005c1a08dc1234c159b99b67fd81291bc/Untitled.png)
    
    이에 따라 객체의 프로퍼티 또는 value를 동적으로 바꿀 수 있다.
    
    참조값 자체는 바뀌지 않고 참조값에 해당하는 객체값만 변한다. 
    
    이러한 이유는 객체는 기존 원시값과 다르게 크기가 매우 클 수 있으며 복잡하게 구성될 수 있는데 이때마다 변경값을 적용할 때 원시값처럼 재할당을 통해 이루어지는 방식은 매우 비효율적일 수 있기 때문에 객체를 변경가능한 값으로 구성했다. 
    
    하지만 이를 통해 생기는 문제점이 발생할 수 있는데 여러 개의 식별자가 하나의 객체를 공유할 수 있다는 점이다. 
    
    ```jsx
    const person = {
    	name: "song";
    };
    
    const copy = person;
    ```
    
    위의 코드의 경우에는 person에 객체에 대한 참조값이 저장되고, copy에도 똑같은 참조값이 저장되어 copy를 통해 객체의 프로퍼티 또는 value를 변경할 경우 person에서 참조하는 객체의 값또한 변한다.
    
    값에 의한 전달 → 원시값
    
    참조에 의한 전달 → 객체 (다른 프로그래밍 언어와 다르게 자바스크립트의 경우에는 포인터가 존재하지 않아 다른 언어에서의 참조에 의한 전달과 다른 의미일 수 있다.)
    
- 일반함수와 화살표 함수의 차이점
    - 함수 정의
        
        ```jsx
        // 함수 표현식(함수 리터럴) 
        const a = function (x,y) {
            return x+y;
        }
        // 함수 선언문
        function b(x,y){
            return x+y;
        }
        //Function 생성자 함수 (잘 안씀)
        const c = new Function('x', 'y','return x+y');
        // 화살표 함수
        const d = (x,y) => x+y;
        ```
        
        함수 표현식(리터럴)은 `function` 과 매개변수 사이에 함수 이름을 생략할 수 있다. 
        
        함수 선언문은 함수 표현식(리터럴)과 형태가 동일하지만 함수 표현식은 함수 이름을 생략할 수 있는데 반면 함수 선언문은 생략할 수 없다. 
        
        - 화살표 함수
            
            기존 함수 표현식과 함수 선언문을 그대로 대체하기 위해 나온 것이 아니다. 
            
            표현만 간략해진 것이 아닌 내부동작 또한 간략화 되었다.
            
            화살표 함수는 생성자 함수로 사용할 수 없고 기존 함수와 this 바인딩 방식도 다르고 prototype 프로퍼티가 없으며 arguments 객체를 생성하지 않는다.  
            
            - 함수 정의
                
                화살표 함수는 함수 선언문으로 정의할 수 없고 함수 표현식으로 정의해야한다. 호출방식은 기존 함수와 동일하다.
                
            - 매개변수 선언
                
                매개변수가 여러개인 경우에는 소괄호 () 안에 매개변수를 선언한다.
                
                매개변수가 하나인 경우에는 소괄호 ()를 생략할 수 있다.
                
                매개변수가 없는 경우에는 소괄호 ()를 생략할 수 없다.
                
                ```jsx
                const arrow1 = (x,y) => {...};
                const arrow2 = x => {...};
                const arrow3 = () => {...};
                ```
                
                > 함수 몸체 선언
                > 
                
                함수 몸체가 하나의 문으로 구성된다면 함수 몸체를 감싸는 중괄호 {}를 생략할 수 있다. 
                
                이때 함수 몸체 내부의 몸이 값으로 평가되는 표현식인 문이라면 암묵적으로 반환된다.(return이 생략된다.)
                
                함수 몸체를 감싸는 중괄호 {} 를 생략한 경우에는 함수 내부의 문이 표현식이 아닌 문이라면 에러가 발생한다. 표현식이 아닌 문은 반환할 수 없기 때문이다.
                
                ```jsx
                const power = x => x**2; // 중괄호 생략
                const power = x => { return x ** 2; }; // 위와 동일
                const arrow = () => const x = 1; //SyntaxError 중괄호 필요
                ```
                
                따라서 함수 몸체가 하나의 문으로 구성된다 해도 함수 몸체의 문이 표현식이 아닌 문이라면 중괄호를 생략할 수 없다. 
                
                함수의 반환값이 객체라면 소괄호로 감싸주어야 한다.
                
                ```jsx
                const create = (id, content) => ({ id, content });
                create(1, 'Js'); // -> {id: 1, content: 'Js'}
                
                // 위와 동일한 내용의 표현
                const create = (id, content) => {return {id, content};};
                ```
                
                함수 몸체가 여러개의 문으로 구성된다면 중괄호를 생략할 수 없다. 이때 반환값이 있다면 명시적으로 return 을 써주어야한다.
                
                *(아직잘모르겠음) 화살표 함수는 즉시 실행 함수로 사용할 수 있다. 
                
                ```jsx
                const person = ( name -> ({
                	sayHi() { return `Hi? My name is $(name)`;}
                }))('Lee');
                
                console.log(person.sayHi()); // Hi? My name is Lee
                ```
                
                화살표 함수도 일급 객체이므로 고차함수에 인수로 전달할 수 있다. 이 경우 일반적인 함수 표현식보다 표현이 간결하고 가독성이 좋다. 
                
                ```jsx
                //ES5
                [1,2,3].map(function (v) {
                	return v * 2;
                });
                
                //ES6
                [1,2,3].map(v => v * 2); // -> [2,4,6]
                ```
                
    - 일반 함수와 화살표 함수의 차이
        1. 화살표 함수는 인스턴스를 생성할 수 없는 non-constructor이다.
        2. 중복된 매개변수 이름을 선언할 수 없다.
        3. 화살표 함수는 함수 자체의 ths, arguments, super, [new.target](http://new.target) 바인딩을 갖지 않는다.
        
        무엇보다 화살표 함수가 일반 함수와 구별되는 가장 큰 특징은 this 이다.
        
        또한 화살표 함수는 다른 함수의 인수로 전달되어 콜백 함수로 사용되는 경우가 많다. 
        
        → 그 이유는 “콜백 함수 내부의 this 문제" 를 해결할 수 있기 때문이다. 
        
        일반 함수로서 호출되는 콜백 함수의 경우, 고차 함수의 인수로 전달되어 고차 함수 내부에서 호출되는 콜백 함수 (중첩 함수)에서의 일반적인 this 바인딩은 전역 객체를 바인딩한다. 
        
        이때 화살표 함수를 콜백함수 또는 중첩함수로 사용하게 된다면 this 바인딩 문제를 해결할 수 있다.
        
        **화살표 함수는 함수 자체의 this 바인딩을 갖지 않는다. 따라서 화살표 함수 내부에서 this를 참조하면 상위 스코프의 this를 그대로 ckawhgksek. 이를 lexical this 라고 한다.** 
        
        화살표함수가 이러한 장점이 있지만 반대로 메서드의 경우에서 화살표 함수를 사용하는 경우에는 this바인딩을 객체 상위의 함수를 바인딩하기 때문에 메서드를 써야할 경우에는 화살표 함수를 피해야한다. 
        
        대신 ES6 메서드 축약 표현으로 정의한 ES6 메서드를 사용하는 것이 좋다.
        
        ```jsx
        // Bad
        const person = {
        	name: 'song',
        	sayHi: () => console.log(`Hi~ ${this.name}`)
        };
        person.sayHi(); // Hi~
        
        // Good
        const person = {
        	name: 'song',
        	sayHi() {
        		console.log(`Hi~ $[this.name}`);
        	}
        };
        person.sayHi(); //Hi~ song
        ```
        
        프로토 타입 객체의 프로퍼티에 화살표 함수를 할당하는 것도 동일한 문제가 발생한다.
        
        프로퍼티를 동적 추가할 경우에는 ES6 메서드 정의를 사용할 수 없으므로 일반 함수를 할당한다.
        
- This 에 대해
    - 객체의 특성과 this의 필요성
        
        상태를 나타내는 프로퍼티와 동작을 나타내는 메서드를 하나의 논리적인 단위로 묶은 복합적인 자료구조
        
        동작을 나타내는 메서드는 자신이 속한 객체의 상태, 즉 프로퍼티를 참조하고 변경할 수 있어야 한다. 
        
        이때 메서드가 자신이 속한 객체의 프로퍼티를 참조하려면 먼저 **자신이 속한 객체를 가리키는 식별자를 참조할 수 있어야한다.**
        
        객체 리터럴 방식으로 생성한 객체의 경우 메서드 내부에서 메서드 자신이 속한 객체를 가리키는 식별자를 재귀적으로 참조할 수 있다. 
        
        하지만 생성자 함수 방식으로 인스턴스를 생성하는 경우를 보자
        
        ```jsx
        function Circle(radius) {
        // 이 시점에는 생성자 함수 자신이 생성할 인스턴스를 가리키는 식별자를 알 수 없다.
        	????.radius = radius;
        }
        
        Circle.prototype.getDiameter = function() {
        	// 이 시점에는 생성자 함수 자신이 생성할 인스턴스를 가리키는 식별자를 알 수 없다.	
        	return 2 * ????.radius;
        };
        
        // 생성자 함수로 인스턴스를 생성하려면 먼저 생성자 함수를 정의해야 한다.
        const circle = new Circle(5);
        ```
        
        ^ 위 코드의 문제점 
        
        1. 생성자 함수 내부에서 프로퍼티 또는 메서드를 추가하기 위해서는 자신이 생성할 인스턴스를 참조할 수 있어야한다.
        2. 생성자 함수에 의한 객체 생성 방식은 먼저 생성자 함수를 정의한 이후 new 연산자와 함께 생성자 함수를 호출하는 단계가 추가로 필요하다. → 인스턴스를 만들려면 먼저 생성자 함수가 있어야한다.
        
        → 서로가 서로를 필요로 하는 상황
        
        이러한 문제점을 해결하기 위해 즉 자신이 속한 객체 또는 자신이 생성할 인스턴스를 가리키는 특수한 식별자가 필요한 상황을 위해 자바스크립트는 this 라는 특수한 식별자를 제공한다.
        
        `**this` 는 자신이 속한 객체 또는 자신이 생성할 인스턴스를 가리키는 `자기참조 변수` 이다. this를 통해 자신이 속한 객체 또는 자신이 생성할 인스턴스의 프로퍼티나 메서드를 참조할 수 있다.**
        
        this는 자바스크립트 엔진에 의해 암묵적으로 생성되며, 코드 어디서든 참조할 수 있다. 함수를 호출하면 `arguments` 객체와 `this` 가 암묵적으로 함수 내부로 전달된다. 
        
        함수 내부에서 `arguments` 객체를 지역 변수 처럼 사용할 수 있는 것처럼 `this` 도 지역변수처럼 사용할 수 있다. 
        
        단 this가 가르키는 값, 즉 this 바인딩은 함수 호출 방식에 의해 동적으로 결정된다.
        
        > this 바인딩
        > 
        
        바인딩이란 식별자와 값을 연결하는 과정을 의미한다. 예를 들어, 변수 선언은 변수 이름(식별자)과 확보된 메모리 공간의 주소를 바인딩하는 것이다. this 바인딩은 this(키워드로 분류되지만 식별자의 역할을 한다)와 this가 가리킬 객체를 바인딩하는 것이다.
        
    - this의 동적 결정
        
        this는 함수가 호출되는 방식에 따라 this 에 바인딩될 값, 즉 this 바인딩이 동적으로 결정된다.
        
        ```jsx
        //this 는 어디서든 참조 가능하다.
        //전역에서 this는 전역 객체  window를 가리킨다.
        console.log(this); //window
        
        function square(number) {
        	// 일반 함수 내부에서 this는 전역 객체 window를 가리킨다.
        	console.log(this); //window
        }
        
        const person = {
        	name: 'song',
        	getName() {
        		// 메서드 내부에서 this는 메서드를 호출한 객체를 가리킨다.
        		console.log(this); //{name:'song', getName: f}
        		return this.name;
        	}
        };
        console.log(person.getName()); // 'song'
        
        function Person(name) {
        	this.name = name;
        	// 생성자 함수 내부에서 this는 생성자 함수가 생성할 인스턴스를 가리킨다.
        	console.log(this); // Person {name: 'song'}
        }
        
        const me = new Person('song');
        ```
        
        하지만 this 는 일반적으로 객체의 프로퍼티나 메서드를 참조하기 위한 자기 참조 변수이므로 객체의 메서드 내부나 생성자 함수 내부에서만 의미가 있다. 따라서 strict mode가 적용된 일반 함수 내부의 this에는 undefined 가 바인딩된다. 
        
    - 함수 호출 방식과 this 바인딩
        
        this 바인딩은 함수 호출 방식, 즉 함수가 어떻게 호출되었는지에 따라 동적으로 결정된다.
        
        함수호출 방식
        
        | 함수 호출 방식 | this 바인딩 |
        | --- | --- |
        | 일반 함수 호출 | 전역 객체 |
        | 메서드 호출 | 메서드를 호출한 객체 |
        | 생성자 함수 호출 | 생성자 함수가 (미래에) 생성할 인스턴스 |
        | Function.prototype.apply/call/bind 메서드에 의한 간접 호출 | Function.prototype.apply/call/bind 메서드에 
        첫번째 인수로 전달한 객체 |
    - 발생하는 문제점과 해결 방법
        
        일반 함수 호출시 this 바인딩은 전역 객체로 바인딩 된다. ‘use strict’을 사용할 경우 undefined 로 뜬다.
        
        일반적으로는 일반 함수 호출시에 this를 사용할 경우가 없지만 콜백함수나 중첩 함수 내부의 this도 전역 객체가 바인딩되는 것은 문제가 있다.
        
        이를 해결하기위한 3가지 방법이 있다.
        
        1. 새로운 변수에 this 바인딩을 할당한다.
            
            ```jsx
            var value = 1;
            
            const obj = {
            	value: 100,
            	foo() {
            		//this 바인딩(obj)을 변수 that에 할당한다.
            		const that = this;
            		
            		// 콜백 함수 내부에서 this 대신 that을 참조한다.
            		setTimeout(function () {
            			console.log(that.value) // value == 100 ,this를 쓸경우 1이 바인딩 되어있다.
            		}, 100);
            	}
            };
            
            obj.foo();	
            ```
            
        2. Function.prototype.apply, Function.prototype.call, Function.prototype.bind 메서드를 사용한다.
            
            ```jsx
            var value = 1;
            const obj = {
            	value: 100,
            	foo() {
            		//콜백 함수에 명시적으로 this를 바인딩한다.
            		setTimeout(function() {
            			console.log(this.value);
            		}.bind(this), 100);
            	}
            };
            
            obj.foo();
            ```
            
        3. 화살표 함수를 사용해서 this 바인딩을 일치시킨다.
            
            ```jsx
            	var value = 1;
            
            const obj = {
            	value: 100,
            	foo () {
            		//화살표 함수 내부의 this 는 상위 스코프의 this를 가르킨다.
            		setTimeout(() => console.log(this.value), 100); // 100
            	}
            };
            
            obj.foo();
            ```
