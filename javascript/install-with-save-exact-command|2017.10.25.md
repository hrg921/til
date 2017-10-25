# Install With --save-exact

다음 명령으로 Node module(prettier)을 설치해야하는 상황이 있다고 가정하자.

*npm*

```terminal
hangeonhoui-MacBook-Pro:~ hangeonho$ npm install prettier
```

*yarn*

```terminal
hangeonhoui-MacBook-Pro:~ hangeonho$ yarn add prettier
```

이 경우 package.json에 다음과 같이 입력된다.

```json
{
  "dependencies": {
    "prettier": "^1.7.4"
  }
}
```

prettier dependency 앞에 붙어있는 ^표시는 해당 버전과 호환이 되는 최신버전 (1.7.5, 1.7.6)을 다운받아 설치하게 된다. 그러나 이 또한 업데이트가 이루어질 경우 하위 호환성에 대한 우려는 반드시 존재하기 마련이다. 이 위험을 없애기 위해 배포버전에서는 종종 --save-exact 명령과 함께 설치하기도 한다.

*npm*

```terminal
hangeonhoui-MacBook-Pro:~ hangeonho$ npm install prettier --save-exact
```

*yarn*

```terminal
hangeonhoui-MacBook-Pro:~ hangeonho$ yarn add prettier --exact
```

이 경우 package.json에 다음과 같이 입력된다.

```json
{
  "dependencies": {
    "prettier": "1.7.4"
  }
}
```

이제 앞으로 `npm install` 혹은 `yarn` 을 입력할 경우 정확히 1.7.4 버전을 설치하게 된다.