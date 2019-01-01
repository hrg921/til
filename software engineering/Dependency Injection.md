# Dependency Injection

In software engineering, dependency injection is a technique whereby one object (or static method) supplies the dependencies of another object.

Redux스토어와 비슷한 개념이다.

```typescript
import "reflect-metadata";
import {Service, Container} from "typedi";

@Service()
class SomeClass {

    someMethod() {
    }

}

let someClass = Container.get(SomeClass);
someClass.someMethod();
```

TypeDI를 이용한 예제
