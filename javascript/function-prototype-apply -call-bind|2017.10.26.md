# Function Prototype Apply Call Bind

자바스크립의 모든 함수는 기본적으로 객체이다. 따라서 function 키워드를 통해 함수를 생성하게 되면 함수객체가 생성되고 각 함수 객체에는 기본적으로 몇가지의 메소드가 있다.

이 중에서도 많이, 그리고 흔하게 사용되는 것이 apply, call, bind 함수이다.

이 세 메소드의 공통점은 대상 함수의 컨텍스트를 바꾸는 메소드라는 것이다.

아래 코드는 apply, call을 이용하여 컨텍스트를 바꾸려고 시도해본 코드이다. (apply와 call의 유일한 차이점은 arguments를 배열로 받느냐, 그렇지 않느냐이다.)

```javascript
const add = (a, b) => {
	return a + b;
};

const object = {
	a: 1,
	b: 2
};

add(0, 1); 						// 1
add.call(null, 2, 4); 			// 6
add.call(object, 2, 4); 		// 6
add.apply(null, [4, 5]); 		// 9
add.apply(object, [4, 5]);		// 9
```

위 코드를 실행하였을때 object를 인자로 넣어줬음에도 불구하고 아무런 변화가 일어나지 않는 이유는 컨텍스트가 바뀌어도 함수 내부에서 컨텍스트를 참조해야 하는 부분이 없기 때문이다.

즉 쉽게 말해 `this`를 다루는 부분이 없기 때문이다.

그렇다면 this를 다루는, 컨텍스트를 다루는 예제를 추가하여 그 결과를 확인해 보도록 하자.

```javascript
const object = {
	str1: 'string1',
	str2: 'string2',
	say: function() {
		console.log(this.str1 + this.str2 + Array.prototype.join.call(arguments));
	}
};

const binded = {
	str1: 'binding1',
	str2: 'binding2'
};

object.say('argument1', 'argument2');
object.say.call(binded, 'call1', 'call2');
object.say.apply(binded, ['apply1', 'apply2']);
```

위 코드를 실행하면 대상 객체의 str1과 str2그리고 인자로 전달된 모든 문자열이 합쳐져 콘솔에 출력된다. 즉, call, apply는 대상 객체의 함수를 빌려오는 것이다.

say 함수 내부엔 Array.prototype.join 메소드가 있는데 이는 배열의 모든 엘리먼트들을 문자열로 합쳐 반환하는 메소드이다. call, apply가 사용되는 가장 대표적인 예라고 할 수 있다.

bind메소드는 컨텍스트를 입력받아 그 컨텍스트를 다루는 함수를 반환하는 메소드이다. 즉 위 예에서

```javascript
const bindedFunc = object.say.bind(binded);
```
를 추가하면 bindedFunc를 실행할 시에 `object.say.call(binded, arguments);` 가 실행되는 것과 동일한 결과를 내게 된다.