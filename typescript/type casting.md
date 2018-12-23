# type casting

```typescript
const responseGoogle = (response: GoogleLoginResponse | GoogleLoginResponseOffline) => {
  // response instanceof GoogleLoginResponse
  const basicProfile = (response as GoogleLoginResponse).getBasicProfile();
  console.log(basicProfile.getEmail());
}
```

GoogleLoginOfflineResponse에 대한 것은 고려하고 싶지 않았고 고려할 이유도 없었는데 계속 타입에러가 떠서 as를 사용하여 괄호로 묶어주었더니 정상적으로 작동함.
