# Why we bind component method in react

다음과 같은 React 컴포넌트가 존재한다고 가정하자.

```javascript
import React from 'react';

class MyForm extends React.Component {
	constructor(props) {
		super(props);
		this.state = {
			data: null
		};
	}
	
	render() {
		return (
			<form onSubmit={this.handleSubmitEvent}>
				/* ~ get Datas ~ */
			</form>
		);
	}
	
	handleSubmitEvent() {
		this.state.data = { /* ~ get Datas ~ */ };
		this.setState({data:this.state.data});
	}
}
```

위 컴포넌트의 메소드중 handleSubmitEvent는 ES5에서 다음과 같이 해석된다.

```
handleSubmitEvent: function() {
  this.state.data = { /* ~ get Datas ~ */ };
  this.setState({data:this.state.data});
}
```

여기서 function에는 기본적으로 어떤 객체를 자신의 실행환경으로 설정할 것인지에 대한 정보가 없다. function 자체가 일단 객체이기 때문이다.
따라서 constructor 내부에 this바인딩을 해주어 그 실행환경을 알 수 있도록 해주는 것이다.

만약 이와 같은 방식이 귀찮다면 ES2015의 Arrow function을 이용하면 된다. 이는 자동으로 this 바인딩을 실시한다.